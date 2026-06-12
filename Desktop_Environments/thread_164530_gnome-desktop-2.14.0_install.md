---
title: "gnome-desktop-2.14.0 install"
date: 2006-04-22
forum: Desktop Environments
---

### Post by philetus on 2006-04-22
I extracted and ./configured.
When I type "make" it tells me "bash: make: command not found"

./configure belowhttp://ubuntuforums.org/images/smilies/eusa_wall.gif](*,) ](*,) 


tom@ubuntu:~$ cd Desktop/gnome-desktop-2.14.0
tom@ubuntu:~/Desktop/gnome-desktop-2.14.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for style of include used by make... none
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
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
checking for pkg-config... /usr/bin/pkg-config
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler...
Building with libstartup-notification
checking pkg-config is at least version 0.9.0... yes
checking for GNOME_DESKTOP... yes
checking for GNOME_ABOUT... yes
checking for GDU_MODULE_VERSION_CHECK... yes
checking for scrollkeeper-config... /usr/bin/scrollkeeper-config
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
checking for msgfmt... no
checking for mawk... /usr/bin/mawk
checking for perl5... no
checking for perl... /usr/bin/perl
configure: creating ./config.status
config.status: creating Makefile
config.status: creating gnome-desktop.spec
config.status: creating gnome-about/Makefile
config.status: creating gnome-about/gnome-about.desktop.in
config.status: creating gnome-about/headers/Makefile
config.status: creating libgnome-desktop/Makefile
config.status: creating libgnome-desktop/libgnome/Makefile
config.status: creating libgnome-desktop/libgnomeui/Makefile
config.status: creating libgnome-desktop/gnome-desktop-2.0.pc
config.status: creating libgnome-desktop/gnome-desktop-2.0-uninstalled.pc
config.status: creating gnome-version.xml.in
config.status: creating po/Makefile.in
config.status: creating pixmaps/Makefile
config.status: creating desktop-docs/Makefile
config.status: creating desktop-docs/fdl/Makefile
config.status: creating desktop-docs/gpl/Makefile
config.status: creating desktop-docs/lgpl/Makefile
config.status: creating desktop-docs/gnome-feedback/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing intltool commands
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing default-2 commands
config.status: executing po/stamp-it commands
tom@ubuntu:~/Desktop/gnome-desktop-2.14.0$

---

### Post by Sutekh on 2006-04-22
You should start by installing the build-essential package
```
sudo apt-get install build-essential
```
It contains make, some C compilers and dpkg packages.

---

### Post by philetus on 2006-04-23
Thank you Sutekh, that helped a lot.
It almost installed except for:

make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/local/share/gnome/help/gpl/C
/bin/sh ../../mkinstalldirs /usr/local/share/gnome/help/gpl/es
/bin/sh ../../mkinstalldirs /usr/local/share/gnome/help/gpl/fi
/bin/sh ../../mkinstalldirs /usr/local/share/gnome/help/gpl/fr
/bin/sh ../../mkinstalldirs /usr/local/share/gnome/help/gpl/pa
/usr/bin/install -c -m 644 C/gpl.xml /usr/local/share/gnome/help/gpl/C/gpl.xml
/usr/bin/install -c -m 644 es/gpl.xml /usr/local/share/gnome/help/gpl/es/gpl.xml
/usr/bin/install -c -m 644 fi/gpl.xml /usr/local/share/gnome/help/gpl/fi/gpl.xml
/usr/bin/install -c -m 644 fr/gpl.xml /usr/local/share/gnome/help/gpl/fr/gpl.xml
/usr/bin/install -c -m 644 pa/gpl.xml /usr/local/share/gnome/help/gpl/pa/gpl.xml
/bin/sh ../../mkinstalldirs /usr/local/share/omf/gpl
/usr/bin/install -c -m 644 gpl-C.omf /usr/local/share/omf/gpl/gpl-C.omf
/usr/bin/install: cannot stat `gpl-C.omf': No such file or directory
/usr/bin/install -c -m 644 gpl-es.omf /usr/local/share/omf/gpl/gpl-es.omf
/usr/bin/install: cannot stat `gpl-es.omf': No such file or directory
/usr/bin/install -c -m 644 gpl-fi.omf /usr/local/share/omf/gpl/gpl-fi.omf
/usr/bin/install: cannot stat `gpl-fi.omf': No such file or directory
/usr/bin/install -c -m 644 gpl-fr.omf /usr/local/share/omf/gpl/gpl-fr.omf
/usr/bin/install: cannot stat `gpl-fr.omf': No such file or directory
/usr/bin/install -c -m 644 gpl-pa.omf /usr/local/share/omf/gpl/gpl-pa.omf
/usr/bin/install: cannot stat `gpl-pa.omf': No such file or directory
make[3]: *** [install-doc-omf] Error 1
make[3]: Leaving directory `/home/tom/Desktop/gnome-desktop-2.14.0/desktop-docs/ gpl'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/tom/Desktop/gnome-desktop-2.14.0/desktop-docs/ gpl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/tom/Desktop/gnome-desktop-2.14.0/desktop-docs'
make: *** [install-recursive] Error 1

I looked for gpl and .omf in Synaptic, but didn't find the right files.
root@ubuntu:/home/tom/Desktop/gnome-desktop-2.14.0#

---

### Post by Sutekh on 2006-04-23
Ok, had to do some research on this.

The **gnome-desktop** README says this
> The package contains the libgnome-desktop library
which contains APIs that really belong in libgnome[ui] but
have not seen enough testing or development to be considered
stable. Use at your own risk.

	Also contained here are documents installed as part
of the core GNOME distribution, e.g. a copy of the GPL, the
gnome-about program, some manpages and GNOME's core graphics
files and icons. 

It's not what you think it is.  It doens't install the entire GNOME 2.14 desktop.

You need to download ALL the GNOME sources from their website.

[GNOME 2.14 Sources](http://ftp.gnome.org/pub/GNOME/desktop/2.14/2.14.0/sources/)

and install them in this order.

[Installing GNOME 2.14](http://www.gnome.org/start/2.14/notes/en/rninstallation.html)

---

### Post by adamkane on 2006-04-23
Try this, if you have large error messages to post:

[ quote]
blah 
blah
[ /quote]

---

### Post by philetus on 2006-04-23
Thanks Sutekh. I think I'll wait for it to be included in a repository.

---

### Post by Sutekh on 2006-04-23
I'm pretty confident that will never happen.  At least not in an Ubuntu repository.  You would have to compile it all yourself.

If you really want GNOME 2.14, you could try upgrading to Ubuntu Dapper 6.06, which uses GNOME 2.14.1

I should warn you that Dapper is only just beta now, so there still may be problems with using it as a full time desktop.

---

