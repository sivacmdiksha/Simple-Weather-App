pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/sivacmdiksha/Simple-Weather-App.git'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: "${REPO_URL}"
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Check if package manager is npm or yarn
                    if (fileExists('package.json')) {
                        if (fileExists('yarn.lock')) {
                            sh 'yarn install'
                        } else {
                            sh 'npm install'
                        }
                    }
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run tests
                    if (fileExists('package.json')) {
                        if (fileExists('yarn.lock')) {
                            sh 'yarn test'
                        } else {
                            sh 'npm test'
                        }
                    }
                }
            }
        }

        stage('Build Application') {
            steps {
                script {
                    // Build the application
                    if (fileExists('package.json')) {
                        if (fileExists('yarn.lock')) {
                            sh 'yarn build'
                        } else {
                            sh 'npm run build'
                        }
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Add deployment steps here
                    echo 'Deploying the application...'
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
