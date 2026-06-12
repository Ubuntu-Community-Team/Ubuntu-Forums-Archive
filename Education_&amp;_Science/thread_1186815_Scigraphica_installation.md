---
title: "Scigraphica installation"
date: 2009-06-13
forum: Education &amp; Science
---

### Post by spinoza666 on 2009-06-13
Hey people,

I'm trying to install Scigraphica from source as I can't seem to find any packages. I've downloaded scigraphica and libscigraphica. When I cd into the latter directory and run the ./configure command I get an error:

atle@spinoza:~/Desktop/libscigraphica-2.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/atle/Desktop/libscigraphica-2.1.1/missing: Unknown `--run' option
Try `/home/atle/Desktop/libscigraphica-2.1.1/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
./configure: line 1938: /bin: is a directory
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.27.2... 0.33 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for some Win32 platform... no
checking for native Win32... no
checking for ANSI C header files... (cached) yes
checking for unistd.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking fnmatch.h usability... yes
checking fnmatch.h presence... yes
checking for fnmatch.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for gzwrite in -lz... yes
checking for pkg-config... /usr/bin/pkg-config
checking for libxml-2.0 >= 2.4.10... Package libxml-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libxml-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libxml-2.0' found
configure: error: Library requirements (libxml-2.0 >= 2.4.10) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
atle@spinoza:~/Desktop/libscigraphica-2.1.1$ 

I can't find any libxml package in the repositories, but I do have libxml2 installed, and as far as I can figure, this is just a newer version. Does anybody have any experience with this, or know what to do? I guess I need to tell ./configure that libxml2 is the package that it wants, but how do I do this?

Cheers:)

---

### Post by spinoza666 on 2009-06-14
Well I just learnt that Scigraphica is no longer maintained:

[http://www.unmaintained-free-software.org/wiki/Scigraphica](http://www.unmaintained-free-software.org/wiki/Scigraphica)

And looking at the dates on their downloads on Sourcefourge, it's probably true. This would also explain the out-dated dependencies....

But it would still be fun to get it to work! Just to prove that it is possible:)

---

