#!groovy
@Library('latest-stable') _

def isReleaseBranch = env.BRANCH_NAME.startsWith("release/")
def isDevelopBranch = env.BRANCH_NAME == "develop"
def isHotfixBranch = env.BRANCH_NAME.split("/")[0] == "hotfix"

mavenPipelinePlugin {

    ait = "98765"
    spk = "WIRETFR"
    repo = "wire"

    cleanWorkspace = false
    mavenLocation = "/efs/dist/horizon/maven/3.6.3/common"
    pipelineJDKToolName = "JDK18"
    buildDefinitionFile = "pom.xml"
    buildParameters = "install -U"

    executeUnitTest = true
    unitTestFramework = "junit"
    unitTestFailFast = true
    junitTestResultPath = "**/target/surefire-reports/*.xml"

    executePublishArtifact = isReleaseBranch || isDevelopBranch
    executeCreateArtifact = true
    packageParamters = "dependency:copy-dependencies"
    artifactoryRepo = "maven"
    enableAutoVersioning = false
    publishParameters = "install"

    executeCodeScan = true
    sonarPropertyFIle = "sonar-project.properties"
    pipelineScanServerToolName = "Enterprise_sonar_2"


}