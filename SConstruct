#!/bin/python

import sys

print('Target Platform = ' + sys.platform)

cxx = ARGUMENTS.get('CXX', 'g++')
prefix = ARGUMENTS.get('PREFIX', '/usr/include')

env = Environment(CXX=cxx, CPPFLAGS=['-std=c++17', '-Wall'], CPPPATH='.', PREFIX=prefix)

if sys.platform == 'win32' or sys.platform == 'msys' or 'mingw' in cxx:
    env.Append(LIBS=['ws2_32'], LINKFLAGS=['-static', '-static-libstdc++'])

env.Program('bin/xsock-basic', source=['examples/xsock-basic.cpp'])
env.Program('bin/tcp-ipecho', source=['examples/tcp-ipecho.cpp'])
env.Program('bin/udp-ipecho', source=['examples/udp-ipecho.cpp'])
env.Program('bin/resolve', source=['examples/resolve.cpp'])

env.Install(prefix, 'xsocket.hpp')
env.Alias('install', prefix)
