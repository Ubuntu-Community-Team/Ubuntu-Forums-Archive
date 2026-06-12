---
title: "Compiling dependency problem"
date: 2009-01-14
forum: General Help
---

### Post by jrstan17 on 2009-01-14
Hello all. I've never posted anything before, so let me know if you need more information. I'm trying to compile the latest Power Manager for Gnome under Intrepid, but I run into a dependency problem when I try to ./configure the package. This is what happens in the terminal:

```
root@aspireone:~/Desktop/gnome-power-manager-2.25.2# ./configure
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
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether NLS is requested... yes
checking for intltool >= 0.35.0... 0.40.5 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for glib-genmarshal... /usr/bin/glib-genmarshal
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... no
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for GLIB... yes
checking for HAL... configure: error: Package requirements (hal >= 0.5.8) were not met:

No package 'hal' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables HAL_CFLAGS
and HAL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I checked out apt-get to see where I stand on HAL, and I get this:

```
root@aspireone:~/Desktop/gnome-power-manager-2.25.2# apt-get install hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hal is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I've never messed with configuration files before, so I'm not sure how to adjust an environmental variable for it. I also know that I'm using HAL version 0.5.11, so that's not a problem. Any idea? Thank you so much in advance.

Jason

---

### Post by _sleeper on 2009-01-14
i'm not sure, but try to install libhal-dev. this might be it.

---

### Post by adamlau on 2009-01-14
You need the development files for HAL which are provided for by either libhal-dev, or libhal-storage-dev.

---

### Post by jrstan17 on 2009-01-14
Thanks sleeper! That's exactly what I needed to do.

Jason

---

### Post by zvacet on 2009-01-15
Before you try to compile some package it is good to run this command from directory where you downloaded source package

```
sudo apt-get build-dep package_name
```

That way you will get every dependecies you need for compiling.

---

### Post by jamaas on 2009-03-04
Thanks zvacet

I'm having a similar problem where make is not finding a g77 compiler, although I have gcc 4.4.3.1 installed.  I am attempting to compile a package called octave.  The file I downloaded is an archive in the form of  ... .tar.gz   I've looked and not found a source package as you suggest but it might be just my ignorance, not looking for the right thing.  Is it possible to use the command you suggest on the .gz file?  Alternatively what file in the unzipped archive that I need to check?

I get the following errors from make

checking for ranlib... ranlib
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no


Any help most welcome, thanks. relative noob here.

Jim

---

### Post by mc4man on 2009-03-04
There is an octave 3.0 version, and many 'extra' packages available in ubuntu repo, maybe try that first, (just search octave in synaptic

as far as build-deps you run
```
sudo apt-get build-dep octave3.0
```

(you may need to manually install/upgrade libcurl4-gnutls-dev first, build-deps will take care of gfortran

satisfying build-deps doesn't insure all runtime capabilities - read thru the configure and search out missing packages

---

