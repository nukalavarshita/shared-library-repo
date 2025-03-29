pipeline {
  agent any
  stages {
    stage('Back-end') {
      steps {
        sh 'docker run -d --name backend-container maven:3.8.1-adoptopenjdk-11 tail -f /dev/null'
        sh 'docker exec backend-container javac HelloWorld.java'
        sh 'docker exec backend-container java HelloWorld'
      }
    }
    stage('Front-end') {
      steps {
        sh 'docker run -d --name frontend-container node:16-alpine tail -f /dev/null'
        sh 'docker exec frontend-container node -e "console.log(\'Hello, World from Node.js!\')"'
      }
    }
  }
}
