pipeline {
  agent any
  environment {
    SPECTRAL_DSN = 'https://spu-2ec864fed0874ad892cca53201af9782@spectral-eu.checkpoint.com'
  }
  stages {
    stage('install Spectral') {
      steps {
        sh "curl -L 'https://spectral-eu.checkpoint.com/latest/x/sh?dsn=$SPECTRAL_DSN' | sh"
      }
    }
    stage('scan for issues') {
      steps {
        sh "$HOME/.spectral/spectral scan --ok --engines secrets,iac,oss --include-tags base,audit3,iac"
      }
    }
    stage('build') {
      steps {
        // your build scripts
        sh "./build.sh"
      }
    }
  }
}
