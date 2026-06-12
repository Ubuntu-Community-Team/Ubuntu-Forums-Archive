---
title: "problem installing conky 1.7.2"
date: 2009-08-24
forum: Desktop Environments
---

### Post by vincedba on 2009-08-24
Hi all   

does anyone have tried installing conky 1.7.2?? 

i got this error when installing  

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for fopencookie... yes
checking for funopen... no
checking for X11... yes
checking for LUA... no
checking for LUA51... no
checking for LUA51... configure: error: Package requirements (lua5.1 >= 5.1) were not met:

No package 'lua5.1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LUA51_CFLAGS
and LUA51_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.




any ideas???

---

### Post by londonali1010 on 2009-08-31
It looks like you're missing a dependency. Have you tried installing via a deb, instead? You can find one here: [https://launchpad.net/~norsetto/+archive/ppa](https://launchpad.net/~norsetto/+archive/ppa)

HTH.

---

### Post by Bruce M. on 2009-09-13
> **londonali1010 said:**
> It looks like you're missing a dependency. Have you tried installing via a deb, instead? You can find one here: [https://launchpad.net/~norsetto/+archive/ppa](https://launchpad.net/~norsetto/+archive/ppa)

HTH.

Yea, but none for 8.10 - 64bit.  :(

And I see: *There were build failures. lpia* with the Ubuntu 9.04 version.

CHIMO!
Bruce

---

### Post by theZoid on 2009-09-13
> **londonali1010 said:**
> It looks like you're missing a dependency. Have you tried installing via a deb, instead? You can find one here: [https://launchpad.net/~norsetto/+archive/ppa](https://launchpad.net/~norsetto/+archive/ppa)

HTH.

Thanks for the link londonali1010

---

