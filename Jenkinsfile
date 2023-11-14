pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git '/home/Documents/Github/JenkinsDependencyCheckTest'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			}
		}
	}	
	post {
	    always {
            // Publish the OWASP Dependency-Check report
            step([$class: 'DependencyCheckPublisher', pattern: '**/dependency-check-report.xml'])
        }

	}
}