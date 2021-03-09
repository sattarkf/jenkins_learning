pipeline {
  agent any
  stages {
    stage('One') {
      steps {
        echo 'Hi, Learning Jenkins Declarative Pipeline'
      }
    }
    stage('Two') {
      steps {
        input('Do you want to proceed?')
      }
    }
    stage('Three') {
      when {
        not {
          branch 'master'
        }
      }
      steps {
        echo "Hello"
      }
    }
    stage('Four') {
      parallel {
        stage('Unit Test') {
          steps {
            echo 'Running the unit tests..'
          }
        }
        stage('Integration Test') {
          agent {
            docker {
              reuseNode false
              image 'ubuntu'
            }
          }
          steps {
            echo 'Running Integration Tests..'
          }
        }
      }
    }
  }
}
