pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/rameshandroid/How-to-Push-docker-image-to-Docker-Hub-using-Jenkins-Pipeline.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t rameshandroid99/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
				 sh 'docker login -u rameshandroid99 -p ${dockerhubpwd}'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push rameshandroid99/nodeapp_test:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
