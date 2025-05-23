// pipeline {
//     agent any

//     environment {
//         SONARQUBE = 'sonarqube'   // Must match the SonarQube server name in Jenkins
//         IMAGE_NAME = 'node-app'
//         IMAGE_TAG = "v${env.BUILD_NUMBER}"
//         NEXUS_REPO = 'nexus:8082'
//     }

//     stages {
//         stages {
//     stage('Checkout') {
//       steps {
//         git url: 'https://github.com/pre3thi19/ci-cd-project.git', branch: 'main' // Replace accordingly
//       }
//     }

//         stage('Install') {
//             steps {
//                 sh 'npm install'
//             }
//         }

//         stage('SonarQube Analysis') {
//             steps {
//                 withSonarQubeEnv("${SONARQUBE}") {
//                     withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_TOKEN')]) {
//                         sh 'sonar-scanner -Dsonar.login=$SONAR_TOKEN'
//                     }
//                 }
//             }
//         }

//         stage('Docker Build') {
//             steps {
//                 sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
//             }
//         }

//         stage('Security Scan - Trivy') {
//             steps {
//                 sh "trivy image --exit-code 1 --severity HIGH,CRITICAL ${IMAGE_NAME}:${IMAGE_TAG}"
//             }
//         }

//         stage('Push to Nexus') {
//             steps {
//                 script {
//                     sh '''
//                         docker tag ${IMAGE_NAME}:${IMAGE_TAG} ${NEXUS_REPO}/${IMAGE_NAME}:${IMAGE_TAG}
//                         echo 'admin:admin123' | docker login ${NEXUS_REPO} --username admin --password-stdin
//                         docker push ${NEXUS_REPO}/${IMAGE_NAME}:${IMAGE_TAG}
//                     '''
//                 }
//             }
//         }
//     }
// }

pipeline {
  agent {
    docker {
      image 'node:18-alpine'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh 'node -v'
        sh 'echo "Hello from Jenkins"'
      }
    }
  }
}
