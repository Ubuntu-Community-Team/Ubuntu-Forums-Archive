---
title: "Liferea build error: gecko not found"
date: 2009-05-12
forum: General Help
---

### Post by navneeth on 2009-05-12
I'm trying to build the latest stable version of Liferea from source. (1.4.28 as of this post) I have all the development packages installed including **xulrunner-1.9-dev** and **xulrunner-dev**, and in fact I also have the Liferea from the repos installed (1.4.26). The latter works, but it is very sluggish - something that has been take care of in the latest version.

This is the output of the ./configure command. 

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
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
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether NLS is requested... yes
checking for intltool >= 0.35.0... 0.40.6 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for ANSI C header files... (cached) yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for 64bit platform... no
checking for some Win32 platform... no
checking for strsep... yes
checking for getaddrinfo... yes
checking for fsync... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for X11 session management library... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBNOTIFY... no
checking for LUA50... yes
checking for LUA51... no
checking for gawk... (cached) mawk
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking which gecko to use... 
configure: error: No gecko found; you may need to adjust PKG_CONFIG_PATH or install a mozilla/firefox/xulrunner -devel package

```

Of importance are the last two lines, viz.

```

checking which gecko to use... 
configure: error: No gecko found; you may need to adjust PKG_CONFIG_PATH or install a mozilla/firefox/xulrunner -devel package

```

However, with *./configure --with-gecko=xulrunner*, I get

```
checking which gecko to use... xulrunner
checking manual gecko home set... Package xulrunner was not found in the pkg-config search path.
Perhaps you should add the directory containing `xulrunner.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xulrunner' found
Package xulrunner-unstable was not found in the pkg-config search path.
Perhaps you should add the directory containing `xulrunner-unstable.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xulrunner-unstable' found
checking for compiler -fshort-wchar option... yes
checking whether to enable C++ RTTI... no
checking whether we have a gtk 2 gecko build... configure: error: This program needs a gtk 2 gecko build

```


I get a similar output as above for the option --with-gecko=libxul, with libxul in the place of xulrunner. 

FWIW, these last two commands were the result of an Internet search. 


I don't know what's wrong. Please, could someone help me?

---

### Post by navneeth on 2009-05-12
*Slightly nudges it up*

---

### Post by oldos2er on 2009-05-12
According to the readme, "The library dependencies for Liferea are: gtk2, gconf2, libxml2, libxslt, sqlite3 and either libgtkembedmoz, libxul or gtkhtml2." Do you have libxul-dev installed?

---

### Post by navneeth on 2009-05-13
> **oldos2er said:**
> According to the readme, "The library dependencies for Liferea are: gtk2, gconf2, libxml2, libxslt, sqlite3 and either libgtkembedmoz, libxul or gtkhtml2." Do you have libxul-dev installed?

Apparently, I did not. 

Now, while installing that, apt-get has also removed xulrunner-dev and xulrunner-1.9-dev.

```
navneeth@ubuntu:~$ sudo apt-get install libxul-dev --yes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmozjs-dev libmozjs0d libxul-common libxul0d xulrunner
Suggested packages:
  xulrunner-gnome-support
The following packages will be REMOVED
  xulrunner-1.9-dev xulrunner-dev
The following NEW packages will be installed
  libmozjs-dev libmozjs0d libxul-common libxul-dev libxul0d xulrunner
0 upgraded, 6 newly installed, 2 to remove and 0 not upgraded.
Need to get 10.6MB of archives.
After this operation, 16.3MB of additional disk space will be used.

```

Here's the output of configure...

```
checking which gecko to use... xulrunner
checking manual gecko home set... checking for compiler -fshort-wchar option... yes
checking whether to enable C++ RTTI... no
checking whether we have a gtk 2 gecko build... yes
checking whether we have a gecko debug build... no
checking whether we have a xpcom glue... no
checking for gecko version... 1.8.1
checking for XULRUNNER... configure: error: Package requirements (libxul-embedding xulrunner-gtkmozembed) were not met:

No package 'libxul-embedding' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XULRUNNER_CFLAGS
and XULRUNNER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by oldos2er on 2009-05-13
If I were you I'd email the devs, and see what they have to say.

---

### Post by navneeth on 2009-05-13
> **oldos2er said:**
> If I were you I'd email the devs, and see what they have to say.

That was done a long time ago. They gave up. :(

---

### Post by Yellow Pasque on 2009-05-13
Try:
```
sudo apt-get build-dep liferea
```

---

### Post by navneeth on 2009-05-13
> **Temüjin said:**
> Try:
```
sudo apt-get build-dep liferea
```

That's been done, too. As I said, I could without trouble install the version from the repository.

---

