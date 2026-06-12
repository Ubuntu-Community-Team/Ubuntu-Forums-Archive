---
title: "Installing Guichan &amp; The Mana World From Source"
date: 2005-11-03
forum: Gaming &amp; Leisure
---

### Post by lrmall01 on 2005-11-03
I'm trying to install Guichan from source - with the ultimate goal of getting The Mana World running again.

When I do a ./configure, it tells me Guichan is ready to be installed.  When I do a make, I get a ton of errors and it won't install.

Am I missing some things needed for installation?  I thought automake and checkinstall would do it.

Thanks for any help.

---

### Post by monkey89 on 2005-11-03
It's hard to help without seeing the actual errors. :)

---

### Post by lrmall01 on 2005-11-03
Here you go:

lrmall01@crom:/usr/src/guichan-0.4.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for glBegin in -lGL... yes
checking SDL/SDL_image.h usability... yes
checking SDL/SDL_image.h presence... yes
checking for SDL/SDL_image.h... yes
checking for IMG_Load in -lSDL_image... yes
checking allegro.h usability... yes
checking allegro.h presence... yes
checking for allegro.h... yes
checking for allegro-config... yes
checking SDL/SDL.h usability... yes
checking SDL/SDL.h presence... yes
checking for SDL/SDL.h... yes
checking for sdl-config... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating include/guichan/Makefile
config.status: creating include/guichan/allegro/Makefile
config.status: creating include/guichan/opengl/Makefile
config.status: creating include/guichan/sdl/Makefile
config.status: creating include/guichan/widgets/Makefile
config.status: creating include/guichan/x/Makefile
config.status: creating src/Makefile
config.status: creating src/allegro/Makefile
config.status: creating src/opengl/Makefile
config.status: creating src/sdl/Makefile
config.status: creating src/widgets/Makefile
config.status: creating src/x/Makefile
config.status: creating include/config.hpp
config.status: include/config.hpp is unchanged
config.status: executing depfiles commands

IMPORTANT! You are about install a BETA version of Guichan
which most likely will lose binary compatibility with the
future stable release. This release should only be used
for testing.

-------------------------------
Guichan ready for compilation!
-------------------------------
* Allegro   = yes
* OpenGL    = yes
* SDL       = yes
* SDL Image = yes
--------------------------------
lrmall01@crom:/usr/src/guichan-0.4.0$ make
/bin/sh: -c: line 0: syntax error near unexpected token `)'
/bin/sh: -c: line 0: `if test ! -f )].in; then  rm -f ./stamp-h2.in;  make ./stamp-h2.in;  else :; fi'
make: *** [)].in] Error 2

---

