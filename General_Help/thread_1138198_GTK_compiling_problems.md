---
title: "GTK compiling problems"
date: 2009-04-26
forum: General Help
---

### Post by Jackofwack on 2009-04-26
Hi guys. at the moment i'm trying to make my parent convert to ubuntu by installing it on their desktop computer but a problem i have encountered is that the computer has to use an external wireless adapter connected through usb to connect to wireless networks.

I thought that i would have no problem locating a driver for it and I didn't (thank god) but when trying to compile it I am told that the version of GTK is not good enough. So i went on my laptop to find the source for the latest version of GTK found it (2.8) and transferred the source onto the desktop where I tried to compile it following the instructions in the readme. it tells you to first invoke the ./configure, make then make install but the problem is after I run the ./configure the make file cannot be found afterwards. This is what comes up in the terminal when I run the ./configure and then try to invoke the makefile.

root@jack-laptop:~/source/gtk+-2.8.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for native Win32... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
root@jack-laptop:~/source/gtk+-2.8.0# sudo apt-get install libc6-dev g++ gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
The following extra packages will be installed:
  g++-4.2 libstdc++6-4.2-dev linux-libc-dev
Suggested packages:
  g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg glibc-doc
  manpages-dev libstdc++6-4.2-doc
The following NEW packages will be installed
  g++ g++-4.2 libc6-dev libstdc++6-4.2-dev linux-libc-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 8020kB of archives.
After this operation, 32.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-23.52 [704kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4 [3344kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main libstdc++6-4.2-dev 4.2.4-1ubuntu3 [1187kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main g++-4.2 4.2.4-1ubuntu3 [2784kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Fetched 8020kB in 35s (224kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 99727 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-23.52_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Setting up linux-libc-dev (2.6.24-23.52) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
Setting up g++-4.2 (4.2.4-1ubuntu3) ...
Setting up libstdc++6-4.2-dev (4.2.4-1ubuntu3) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

root@jack-laptop:~/source/gtk+-2.8.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for native Win32... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for nm... /usr/bin/nm -B
checking whether to enable maintainer-specific portions of Makefiles... no
checking for some Win32 platform... no
checking whether build environment is sane... yes
checking for strerror in -lcposix... no
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES_CFLAGS... 
checking for BASE_DEPENDENCIES_LIBS... 
configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.9.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the BASE_DEPENDENCIES_CFLAGS and BASE_DEPENDENCIES_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
root@jack-laptop:~/source/gtk+-2.8.0# make
make: *** No targets specified and no makefile found. Stop.

If you have a solution to this problem then please get back to me quickly or my parent may force me to delete Ubuntu and revert back to m$ and we don't want that... do we?

---

### Post by Jackofwack on 2009-04-26
woops ignore the first few terminal commands that was me trying to install gcc to fix the c compiler error (which worked). try to help me with the next part please =)

---

