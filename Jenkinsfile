
pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:\\JenkinsDeploy'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Downloading project from GitHub...'
                git branch: 'main',
                url: 'https://github.com/yashrasal/Jenkins-Web-CICD.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the website...'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing website files...'

                bat '''
                if not exist index.html exit /b 1
                if not exist style.css exit /b 1
                if not exist script.js exit /b 1
                echo All website files are present!
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website...'

                bat '''
                if not exist "%DEPLOY_DIR%" mkdir "%DEPLOY_DIR%"
                xcopy /E /I /Y * "%DEPLOY_DIR%\\"
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed! Check console output.'
        }
    }
}
