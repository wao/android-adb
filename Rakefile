require 'rubygems'
require 'bundler'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'

require 'jeweler'
require './lib/android-adb/version.rb'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "android-adb"
  gem.version = AndroidAdb::Version::STRING
  gem.homepage = "http://github.com/nicstrong/android-adb"
  gem.license = "Apache 2.0"
  gem.summary = %Q{Ruby bindings for the Android SDK adb command.}
  #gem.description = %Q{TODO: longer description of your gem}
  gem.email = "nic.strong@gmail.com"
  gem.authors = ["Nic Strong"]
  gem.add_development_dependency('bundler',  '~> 1.0')
  gem.add_development_dependency('rake', '~> 0.8')
  gem.add_runtime_dependency('POpen4', '~> 0.1.4')
end
Jeweler::RubygemsDotOrgTasks.new

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

require 'rcov/rcovtask'
Rcov::RcovTask.new do |test|
  test.libs << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "android-adb #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
