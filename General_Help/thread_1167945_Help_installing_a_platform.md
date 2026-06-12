---
title: "Help installing a platform"
date: 2009-05-23
forum: General Help
---

### Post by haimkras on 2009-05-23
Hi all,

My name is Haim.i'm new here and new to Ubuntu.
i am doing a project that is using the open source code of the OpenIKEv2 platform.([http://openikev2.sourceforge.net/](http://openikev2.sourceforge.net/))
I have installed Ubuntu 9.04 using vmware.
As you can see in the openikev2 documentation in order to install this i need to do the following: './configure' , make, make install.
At first,'./configure' didn't work because of a lack of cpp compiler.
i have installed g++ using the synaptic application and it worked.
But now i get errors about 'alarm.h' and 'alarmable.h'
according to the website,openikev2 should be installed easily on ubuntu,so i dont no why it doesn't.should i try using another compiler? should i add some certain attributes?

attached is the log file,any help would be appreciated!

Thanks a lot,Haim.


haim@ubuntu:~/Desktop/libopenikev2-0.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... myes
checking for g++... g++
achecking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
kchecking whether we are cross compiling... no
checking for suffix of executables... e
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
haim@ubuntu:~/Desktop/libopenikev2-0.5$ make
make  all-recursive
make[1]: Entering directory `/home/haim/Desktop/libopenikev2-0.5'
Making all in src
make[2]: Entering directory `/home/haim/Desktop/libopenikev2-0.5/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT alarm.lo -MD -MP -MF .deps/alarm.Tpo -c -o alarm.lo alarm.cpp
 g++ -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT alarm.lo -MD -MP -MF .deps/alarm.Tpo -c alarm.cpp  -fPIC -DPIC -o .libs/alarm.o
In file included from alarm.h:29,
                 from alarm.cpp:21:
alarmable.h:29: warning: ‘typedef’ was ignored in this declaration
In file included from alarm.cpp:21:
alarm.h:46: error: ‘int64_t’ does not name a type
alarm.h:47: error: ‘int64_t’ does not name a type
alarm.h:57: error: ‘uint32_t’ has not been declared
alarm.h:73: error: ‘uint32_t’ has not been declared
alarm.h:79: error: ‘uint32_t’ does not name a type
alarm.h:90: error: ‘string’ does not name a type
In file included from threadcontrollerimpl.h:27,
                 from threadcontroller.h:24,
                 from alarm.cpp:22:
ikesa.h:49: warning: ‘typedef’ was ignored in this declaration
In file included from alarm.cpp:24:
log.h:40: warning: ‘typedef’ was ignored in this declaration
alarm.cpp:28: error: prototype for ‘openikev2::Alarm::Alarm(openikev2::Alarmable&, uint32_t)’ does not match any in class ‘openikev2::Alarm’
alarm.h:39: error: candidates are: openikev2::Alarm::Alarm(openikev2::Alarm&)
alarm.h:57: error:                 openikev2::Alarm::Alarm(openikev2::Alarmable&, int)
alarm.cpp: In destructor ‘virtual openikev2::Alarm::~Alarm()’:
alarm.cpp:41: error: ‘class openikev2::Alarm’ has no member named ‘getLogId’
alarm.cpp: In member function ‘virtual void openikev2::Alarm::reset()’:
alarm.cpp:47: error: ‘class openikev2::Alarm’ has no member named ‘msec_left’
alarm.cpp:47: error: ‘class openikev2::Alarm’ has no member named ‘msec_total’
alarm.cpp:50: error: ‘class openikev2::Alarm’ has no member named ‘getLogId’
alarm.cpp: In member function ‘virtual void openikev2::Alarm::disable()’:
alarm.cpp:58: error: ‘class openikev2::Alarm’ has no member named ‘getLogId’
alarm.cpp: At global scope:
alarm.cpp:61: error: prototype for ‘void openikev2::Alarm::setTime(uint32_t)’ does not match any in class ‘openikev2::Alarm’
alarm.h:73: error: candidate is: virtual void openikev2::Alarm::setTime(int)
alarm.cpp:71: error: no ‘uint32_t openikev2::Alarm::getTotalTime() const’ member function declared in class ‘openikev2::Alarm’
alarm.cpp:75: error: no ‘std::string openikev2::Alarm::getLogId()’ member function declared in class ‘openikev2::Alarm’
make[2]: *** [alarm.lo] Error 1
make[2]: Leaving directory `/home/haim/Desktop/libopenikev2-0.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/haim/Desktop/libopenikev2-0.5'
make: *** [all] Error 2

---

