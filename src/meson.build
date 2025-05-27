project(
  'cornbread',
  ['c', 'cpp'],
  version: '0.6.0',
  default_options: [
    'warning_level=3',
    'cpp_std=c++17',
    'optimization=2',
  ],
)

host_os = host_machine.system()
host_arch = host_machine.cpu_family()

cc = meson.get_compiler('c')
cxx = meson.get_compiler('cpp')

cmake = import('cmake')

# add common as a default incdir
common_inc = [include_directories('common')]

# load unicorn subproject
unicorn_cmake_opts = cmake.subproject_options()
unicorn_subproject = cmake.subproject('unicorn', options: unicorn_cmake_opts)
unicorn_dep = unicorn_subproject.dependency('unicorn')

test_secretfunctions_exe = executable('test_uc_hello1',
  './test_uc_hello1.cpp',
  dependencies: [unicorn_dep],
  include_directories: common_inc,
)
