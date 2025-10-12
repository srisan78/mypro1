pipeline{
    agent any
    stages{
        stage('checkout the code from the github'){
            steps{
                 git url: 'https://github.com/srisan78/mypro1.git'
                 echo 'github url checkout'
            }
        }
        stage('code compile'){
            steps{
                echo 'starting the  compiling'
                sh 'mvn compile'
            }
        }
        stage('code testing '){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package the code'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t sridhar76/banking1 .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name bankcont sridhar76/banking1 '
            }
        }   
    }
}
