pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'stage:Build'
      }
    }

    stage('test') {
      parallel {
        stage('unitaire') {
          steps {
            bat 'php bin/phpunit tests/unit'
          }
        }

        stage('intégration') {
          steps {
            bat 'php bin/phpunit tests/integration'
          }
        }

        stage('fonctionnel') {
          steps {
            bat 'php bin/phpunit tests/functional'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        bat 'symfony  server:start'
      }
    }

  }
}