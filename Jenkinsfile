pipeline {
    agent any

    environment {
        NODEJS_HOME = tool name: 'NodeJS' // Ensure NodeJS is installed on Jenkins
        PATH = "${env.NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git url: 'https://github.com/sujit-ghodajkar/node-hello.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }

        /*stage('Deploy') {
            steps {
                sshagent(['your-ssh-credentials-id']) {
                    sh """
                    ssh -o StrictHostKeyChecking=no $ubuntu@$DEPLOY_SERVER 'bash -s' < deploy-script.sh
                    """
                }
            }
        }*/
    }

    post {
        success {
            echo 'Build and packaging successful!'
        }
        failure {
            echo 'Build or packaging failed.'
        }
    }
}
