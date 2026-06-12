---
title: "Problem installing iRiverter from source"
date: 2006-06-10
forum: Desktop Environments
---

### Post by seditiousmonkey on 2006-06-10
im not sure if this is a real problem or a user-being-a-total-idiot problem but while trying to install iriverter (front end to menconder) from source it seems the 'make' command is not recognised.

> joe@Joe-Downstairs:~/Desktop/iriverter-0.16$ make
bash: make: command not found

I dont really know what im doing so any help would be hugely appreciated.

Im following this [Howto]("http://ubuntuforums.org/showthread.php?t=138904&highlight=iriverter") and ./configure gave me this which might make more sense to you than it did to me:

> joe@Joe-Downstairs:~/Desktop/iriverter-0.16$ ./configure --with-swt=/usr/share/java/swt-gtk-3.1.jar--with-gcj
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for style of include used by make... none
checking for gcj... no
checking dependency style of gcj... none
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... none
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
checking dependency style of g++... none
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
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
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
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj static flag -static works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... ./configure: line 17265: gcj: command not found
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a BSD-compatible install... /usr/bin/install -c
checking for javac... /usr/bin/javac
checking for fastjar... /usr/bin/fastjar
checking for gcj-jar... no
checking for jar... /usr/bin/jar
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/doc/Makefile
config.status: creating src/doc/html/Makefile
config.status: creating src/doc/images/Makefile
config.status: creating src/org/thestaticvoid/iriverter/Config.java
config.status: creating src/profiles/Makefile
config.status: creating src/launcher/Makefile
config.status: creating src/launcher/iriverter
config.status: executing depfiles commands


---

### Post by FredB on 2006-06-10
Just try to enter sudo apt-get install build-essential (or essentials)... And you'll be fine ;)

The wiki is full of infos like this one. But as you are new here, there is no trouble answering ;)

---

### Post by seditiousmonkey on 2006-06-10
thanks FredB, glad its somthing easy

---

