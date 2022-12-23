pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dckr_pat_PjVGFwIzZgLuPc1bd5cgFKgG-K0')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/rahulpayyoor/Jenkintask1.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t rahulrampayyoor/dockertaskrep .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push rahulrampayyoor/dockertaskrep'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}

