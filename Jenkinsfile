stage("Build and Publish") {
  node {
    ws('workspace/d2l-ja') {
      checkout scm
      sh "git submodule update --init"
      sh "build/utils/sanity_check.sh"
      sh "build/utils/clean_build.sh"
      sh "conda env update -f build/env.yml"
      sh "build/utils/build_html.sh ja"
      sh "build/utils/build_pdf.sh ja"
      sh "build/utils/build_pkg.sh ja"
      if (env.BRANCH_NAME == 'master') {
        sh "build/utils/publish_website.sh ja"
      }
	}
  }
}
