pipeline {
    
    agent any 
    
    environment {
        IMAGE_TAG = "${BUILD_NUMBER}"
    }
    
    stages {
        
        stage('Checkout'){
           steps {
               // git credentialsId: 'f87a34a8-0e09-45e7-b9cf-6dc68feac670', 
               git url: 'https://github.com/sheshdhar3/cicd-end-to-end.git', branch: 'main'
           }
        }

        stage('Build Docker'){
            steps{
                script{
                    sh '''
                    echo 'Buid Docker Image'
                    docker build -t sheshdhar3/cicd-e2e:${BUILD_NUMBER} .
                    '''
                }
            }
        }

        stage('Push the artifacts'){
           steps{
                script{
                    sh '''
                    echo 'Push to Repo'
                    docker push sheshdhar3/cicd-e2e:${BUILD_NUMBER}
                    '''
                }
            }
        }
        
        stage('Checkout K8S manifest SCM'){
            steps {
                // git credentialsId: 'f87a34a8-0e09-45e7-b9cf-6dc68feac670', 
                git url: 'https://github.com/sheshdhar3/cicd-end-to-end.git', branch: 'main'
            }
        }
        
        
    }
}
