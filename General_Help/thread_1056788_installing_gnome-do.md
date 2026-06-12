---
title: "installing gnome-do"
date: 2009-02-01
forum: General Help
---

### Post by malcolmx82 on 2009-02-01
i'm having a lot of problems installing the last version of gnome do..
i download it and then follow this [instructions]("http://do.davebsd.com/wiki/index.php?title=Installing_Do#Ubuntu") to install it from source...
but when i run ./autogen.sh i got this:

```
marco@marco-laptop:~/downloads/internet/gnome-do-0.8.0/gnome-do$ ./autogen.sh 
I am going to run ./configure with no arguments - if you wish 
to pass any to it, please specify them on the ./autogen.sh command line.
Running libtoolize ...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.
Running aclocal -I . -I m4/shamrock  ...
Running automake --gnu  ...
Running autoconf ...
Running intltoolize --force --copy --automake ...
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite
grep: po/Makefile.in.in: Nessun file o directory
./autogen.sh: line 30: error: command not found
rm: impossibile rimuovere `.autogen.log': Nessun file o directory
Running ./configure ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
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
checking for intltool >= 0.35.0... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for catalogs to be installed...  ar ast bg br ca cs da de el en_AU en_CA en_GB es et fa fi fr ga hu id is it ja lt lv mk nb nl nn pl pt_BR pt ru sk sl sr sv ta te th tr uk vi zh_CN zh_HK zh_TW
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for gmcs... /usr/bin/gmcs
checking for LINQ flag for mcs... -langversion:linq
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking pkg-config is at least version 0.9.0... yes
checking for LIBDO... yes
checking for GCONF_SHARP_20... yes
checking for GLADE_SHARP_20... yes
checking for GLIB_SHARP_20... yes
checking for GNOME_DESKTOP_SHARP_20... configure: error: Package requirements (gnome-desktop-sharp-2.0) were not met:

No package 'gnome-desktop-sharp-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_SHARP_20_CFLAGS
and GNOME_DESKTOP_SHARP_20_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

what should i do?

---

### Post by x33a on 2009-02-01
try the instructions here:

[http://do.davebsd.com/wiki/index.php?title=Installing_Do](http://do.davebsd.com/wiki/index.php?title=Installing_Do)

---

### Post by malcolmx82 on 2009-02-01
> **x33a said:**
> try the instructions here:

[http://do.davebsd.com/wiki/index.php?title=Installing_Do](http://do.davebsd.com/wiki/index.php?title=Installing_Do)

those instruction are exactly the one i followed for installing from source because i have added the repository for my ubuntu 7.10 but there isn't the last version and i don't know why...

---

### Post by x33a on 2009-02-01
you mean the repositories didn't work?

make sure you have universe checked under system -> administration-> software sources.

after that add the repositories, as instructed in the tutorial. and run apt-get update.

after that you should have the latest version, though i haven't tried it myself.

---

### Post by malcolmx82 on 2009-02-02
> **x33a said:**
> you mean the repositories didn't work?

make sure you have universe checked under system -> administration-> software sources.

after that add the repositories, as instructed in the tutorial. and run apt-get update.

after that you should have the latest version, though i haven't tried it myself.

i did this way adding the gutsy repository but even if i do this way and even if i run the update the only version i could install via synaptyc is the 0.4 and not the 0.8...

---

### Post by x33a on 2009-02-02
That means that latest version in those repos is 0.4.

well, then i guess you'll have to return to the compilation route :)

did you try installing gnome-desktop-sharp-2.0

---

### Post by malcolmx82 on 2009-02-02
> **x33a said:**
> 

did you try installing gnome-desktop-sharp-2.0


well..i don't know what it is nor where to find it ^_^

---

### Post by x33a on 2009-02-02
open a terminal and type sudo apt-get install gnome-desktop-sharp-2.0

after that again try the compilation.

---

### Post by malcolmx82 on 2009-02-02
> **x33a said:**
> open a terminal and type sudo apt-get install gnome-desktop-sharp-2.0

after that again try the compilation.


i don't remember if i already tried to do this but to be sure when i'll be at home this evening i'll try and then i'll tell you...don't leave me alone ^_^

---

