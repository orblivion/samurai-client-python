desc "Delete created files and directories."
task :clean do
  rm_rf "build"
  rm_rf "dist"
  rm_f "MANIFEST"
end

desc "Run tests."
task :test do
  sh "nosetests"
end

namespace :pypi do
  desc "Register the package with PyPI"
  task :register => :clean do
    sh "python setup.py register"
  end

  desc "Upload a new version to PyPI"
  task :upload => :clean do
    sh "python setup.py sdist upload"
    Rake::Task["clean"].reenable
    Rake::Task["clean"].invoke
  end
end