pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/sankarb91/Jenkinsfile.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy to Demo') {
            steps {
                // In a real project, you might have a more complex deployment process.
                // For this demo, let's just copy the built JAR file to the demo environment.
                sh 'cp target/Jenkinsfile.jar /path/to/demo/environment/'
            }
        }
    }

    post {
        always {
            // Clean up workspace to avoid conflicts in future builds
            cleanWs()
        }
        success {
            echo 'Pipeline succeeded! Your Java application is deployed to the demo environment.'
        }
        failure {
            echo 'Pipeline failed! Please check the build logs for more information.'
        }
    }
}
