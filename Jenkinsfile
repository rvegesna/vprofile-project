pipeline {
    agent any
    tools { 
      maven 'mvn' 
      jdk 'java' 
    }
      stages {
        stage('clone') {
            steps {
                git branch: 'vp-rem', url: 'https://github.com/rvegesna/vprofile-project.git'
            }
        }
        stage('build') {
            steps {
                dir("/var/lib/jenkins/workspace/test") {
                sh 'mvn clean package'
            }
        }
    }
    stage('deploy') {
            steps {
                sh 'cd /var/lib/jenkins/playbook; ansible-playbook -i hosts deploy.yml'
            }
        }
 }
}
