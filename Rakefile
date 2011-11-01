task :gem do
  system "gem build deadweight.gemspec"
  system "mkdir -p pkg"
  system "mv deadweight-*.gem pkg"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.test_files = FileList['test/**/*_test.rb']
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.test_files = FileList['test/**/*_test.rb']
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end

desc "Build documentation"
task :doc do
  system "yard"
end

task :default => :test

