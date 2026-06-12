---
title: "[SOLVED] Awn extras - applets and plugins"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by Inxsible on 2007-10-25
I installed AWN from source in 64 bit Gutsy using reacocard's HowTO. When I try to follow the howto for awn-extras this is what I get

```
inxsible@inxsible:~/avant-window-navigator$ sudo apt-get install build-essential automake1.9 autotools-dev bzr libgnome-menu-dev librsvg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
automake1.9 is already the newest version.
autotools-dev is already the newest version.
autotools-dev set to manual installed.
bzr is already the newest version.
E: Couldn't find package librsvg-dev
```I still went ahead and tried to make install although I knew it wouldnt work and I got this
```
inxsible@inxsible:~/Installs/avant/awn-extras/awn-applets/awn-core-applets$ ./autogen.sh && make && sudo make install
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
src/stacks/Makefile.am:4: whitespace following trailing backslash
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking the maximum length of command line arguments... 98304
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.34... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  awn
                  libwnck-1.0
                  libglade-2.0
                  libgnome-menu
                  gnome-desktop-2.0
                  librsvg-2.0
                  libgtop-2.0
                  glib-2.0
                      dbus-1
                      dbus-glib-1
                  libsexy
                      gconf-2.0
                      gdk-2.0
                      gdk-pixbuf-2.0
                  ) were not met:

No package 'libgnome-menu' found
No package 'librsvg-2.0' found
No package 'libgtop-2.0' found
No package 'libsexy' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

inxsible@inxsible:~/Installs/avant/awn-extras/awn-applets/awn-core-applets$
```I cannot install the applets or the plugins in the Awn Manager.

Can someone tell me how to do that?

---

### Post by bgpete on 2007-10-26
I suspect typo, this package does exist: libsvg-dev

---

### Post by cldmello on 2008-03-21
I got the same issue. The error I get is about a missing package called libsexy. 

checking for LIBSEXY... configure: error: Package requirements (libsexy) were not met:

No package 'libsexy' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBSEXY_CFLAGS
and LIBSEXY_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Any idea what this package is? I didnt find anything related to this error message on Google!!

---

