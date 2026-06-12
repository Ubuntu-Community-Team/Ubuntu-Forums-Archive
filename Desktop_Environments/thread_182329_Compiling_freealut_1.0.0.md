---
title: "Compiling freealut 1.0.0"
date: 2006-05-25
forum: Desktop Environments
---

### Post by trop on 2006-05-25
I see this package is available via synaptic in dapper drake. Any ideas to get this to build?


Thanks,

-d

Using cmake:
tbothwel@shirley:~/dt_dep_src_1.2.0/freealut-1.0.0$ cmake . -DCMAKE_INSTALL_PREFIX:STRING="/usr/local" -DCMAKE_C_FLAGS:STRING="-O2"
CMake Error: Invalid escape sequence \$
in argument \${prefix}
CMake Error: Invalid escape sequence \$
in argument \${exec_prefix}/lib
CMake Error: Invalid escape sequence \$
in argument \${exec_prefix}/bin
CMake Error: Invalid escape sequence \$
in argument \${prefix}/include
-- Check for working C compiler: gcc -- works
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:22:
INCLUDE Could not find include file: /usr/share/CMake/Modules/CheckCSourceCompiles.cmake
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:117:
Unknown CMake command "CHECK_C_SOURCE_COMPILES".
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:48:
Unknown CMake command "CHECK_C_SOURCE_COMPILES".
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:131:
A command failed during the invocation of macro "CHECK_FUNCTION_DEFINE".
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:48:
Unknown CMake command "CHECK_C_SOURCE_COMPILES".
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:135:
A command failed during the invocation of macro "CHECK_FUNCTION_DEFINE".
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:48:
Unknown CMake command "CHECK_C_SOURCE_COMPILES".
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:136:
A command failed during the invocation of macro "CHECK_FUNCTION_DEFINE".
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:48:
Unknown CMake command "CHECK_C_SOURCE_COMPILES".
CMake Error: Error in cmake code at
/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/CMakeLists.txt:144:
A command failed during the invocation of macro "CHECK_FUNCTION_DEFINE".
-- Configuring done
tbothwel@shirley:~/dt_dep_src_1.2.0/freealut-1.0.0$


---------------
And now the end half of 'make' afterwords

make[2]: Entering directory `/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/src'
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -I/usr/local/inc -D_XOPEN_SOURCE=500 -D__NO_CTYPE -Wall -ansi -pedantic -g -O2 -MT libalut_la-alutInit.lo -MD -MP -MF ".deps/libalut_la-alutInit.Tpo" -c -o libalut_la-alutInit.lo `test -f 'alutInit.c' || echo './'`alutInit.c; \
then mv -f ".deps/libalut_la-alutInit.Tpo" ".deps/libalut_la-alutInit.Plo"; else rm -f ".deps/libalut_la-alutInit.Tpo"; exit 1; fi
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -I/usr/local/inc -D_XOPEN_SOURCE=500 -D__NO_CTYPE -Wall -ansi -pedantic -g -O2 -MT libalut_la-alutInit.lo -MD -MP -MF .deps/libalut_la-alutInit.Tpo -c alutInit.c -fPIC -DPIC -o .libs/libalut_la-alutInit.oalutInit.c: In function 'alutExit':
alutInit.c:150: error: wrong type argument to unary exclamation mark
make[2]: *** [libalut_la-alutInit.lo] Error 1
make[2]: Leaving directory `/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tbothwel/dt_dep_src_1.2.0/freealut-1.0.0'
make: *** [all] Error 2


-----------

---

