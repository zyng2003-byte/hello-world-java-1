pipeline {
    agent any

    environment {// change the below to your jdk path
        JAVA_HOME = "C:\\Program Files\\Java\\jdk-21.0.10"
        PATH = "${JAVA_HOME}\\bin;${env.PATH}"
    }

    stages {

        stage('Verify Environment') {
            steps {
                bat 'echo JAVA_HOME=%JAVA_HOME%'
                bat 'java -version'
            }
        }

        stage('Checkout') { //change the below path to your repositoy url
            steps {
                git branch: 'master', url: 'https://github.com/zyng2003-byte/hello-world-java-1.git'
            }
        }

        stage('Build') {
            steps {
                bat 'gradlew.bat clean build --no-daemon'
            }
        }

        stage('Test') {
            steps {
                bat 'gradlew.bat test --no-daemon'
            }
        }


        stage('Deploy') {
            steps {
                bat 'java -jar build\\libs\\hello-world-java-V1.0.jar'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!!!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}