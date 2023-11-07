node {
	stage('prepare') {
		git branch: 'main', poll: false, url: 'GITHUB URL'
	}
	
	stage('build') {
		def mvnHome = tool 'MAVEN'
		withEnv(["MVN_HOME=$mvnHome"]){
			sh '"$MVN_HOME/bin/mvn" clean compile package'
		}
	}
	
	stage('deploy') {
		deploy adapters: [tomcat9(credentialsId: 'CRED-ID', path: '', url: 'TOMCAT URL')], contextPath: null, onFailure: false, war: '**/*.war'
	}

}