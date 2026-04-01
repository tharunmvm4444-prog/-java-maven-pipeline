pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            when {
                expression { currentBuild.currentResult == 'SUCCESS' }
            }
            steps {
                echo 'Deploying application (simulation)...'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar'
        }
    }
}
