---
title: "ripping out my hair trying to compile :'-("
date: 2006-01-29
forum: Desktop Environments
---

### Post by vindicta on 2006-01-29
so... im bad at this linux thing.  i was hoping someone could tell me specifically what the last few lines mean. "checking for gtkmm-2.0... configure: error: gtkmm-2.0 headers are needed to compile and link this program" mostly. i am so confused.  i have build-essential and one other thing that i cant remember the name of. but i cant configure and cant make. :( 

```
psheffie@psheffie:~/Desktop/gnomadic-0.11$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fl32... no
checking for af77... no
checking for fort77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for lf95... no
checking for g95... no
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
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.0... configure: error: gtkmm-2.0 headers are needed to compile and link this program
psheffie@psheffie:~/Desktop/gnomadic-0.11$ make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by tufkakf on 2006-01-29
You simply need the gtkmm development files, probably:
sudo apt-get install libgtkmm-2.4-dev

---

### Post by vindicta on 2006-01-29
/cry.  no. i was hopefull, but that didnt work. it did install many things, but not what i needed. thank you though.

---

### Post by gunderwood on 2006-01-29
I think you may need to pass a path to the configure script telling it where it can check for the header files if it's not finding them. Ensure that the headers are in your /usr/include/gtkmm2.0/ directory. Ensure that you have the correct libgtkmm2.0-dev package, not the libgtkmm2.4-dev package. You can check which files are supposed to be installed by using apt-cache to look at a list of the files that are supposed to be installed. I can't remeber off the top of my head the exact argument to pass to ./configure but I'm sure if you read the README or the INSTALL fiole of the package you're trying to compile it will tell you.

Hope that helps a bit

Greg

---

### Post by tufkakf on 2006-01-29
[QUOTE=vindicta]/cry.  no. i was hopefull, but that didnt work. it did install many things, but not what i needed. thank you though.[/QUOTE]
Are you still getting the same error message?

I looked around synaptic and there are also dev packages for gtkmm2.0, so you maybe need these? (sudo apt-get install libgtkmm2.0-dev).

From looking at the gnomadic homepage you probably also need the liblame dev-package. (sudo apt-get install liblame-dev)

Also, I'm not really sure why you are trying to compile this program, if you just want an application to access your nomad, I think simply installing gnomad2 from synaptic should do the trick.

---

