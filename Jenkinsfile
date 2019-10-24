pipeline {
	agent {
		docker {
			image 'node:6-alpine'
			args '-p 3000:3000'
		}
	}
	environment {
		CI = 'true'
	}
	stages {
		stage('Build') {
			steps {
				sh 'npm cache clean -f'
				sh 'rm -rf node_modules && npm cache clean --force && npm install'
			}
		}
		stage('Test') {
			steps {
				sh './jenkins/scripts/test.sh'
			}
		}
	}
}
