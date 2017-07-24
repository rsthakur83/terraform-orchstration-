node {
   
   	stage 'Stage 1'
   		echo 'Hello Deploying Docker App'
   	stage 'Checkout'
   		git url: 'https://github.com/rsthakur83/terraform-orchstration-'
      stage 'Execute'
         sh 'chmod +x docker.sh'
      stage 'Deploy'
         sh './docker.sh'
   
   post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeeded!'
            mail to: 'rsthakur83@yahoo.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Build successful ${env.BUILD_URL}"
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
  
}
