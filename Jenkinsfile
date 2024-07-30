pipeline {
    agent any

    tools {
        // Install the Maven version configured in Jenkins
        maven 'Maven 3.9.8'
    }

    environment {
        // Set Java Home if needed
        JAVA_HOME = "${tool 'JDK11'}"
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clean workspace before cloning
                cleanWs()
                // Clone repository
                git url: 'https://github.com/pallavijk05/Maven-Web-pallavi.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Run Maven build
                    sh 'mvn clean package'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run Maven tests
                    sh 'mvn test'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Deploy step (this can be customized based on your deployment process)
                    echo 'Deploying...'
                    // Example: copy the war file to the deployment directory
                    sh 'cp target/01-Maven-WebApp-StarAgile.war'
                }
            }
        }
    }

    post {
        always {
            // Clean up the workspace
            cleanWs()
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
