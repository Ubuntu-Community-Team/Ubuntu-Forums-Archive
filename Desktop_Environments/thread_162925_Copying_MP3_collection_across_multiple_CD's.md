---
title: "Copying MP3 collection across multiple CD's"
date: 2006-04-19
forum: Desktop Environments
---

### Post by speedybits on 2006-04-19
Hello,

I have been through the forum and on google to find a simple solution for this, but have not found one. Please forgive me if this is a no-brainer...

I'm running Breezy (probably doesn't matter) and I have a single folder containing about 4GB of MP3's. I want to copy these MP3's to CD's one-by-one, having the next CD begin copying where the last one left off. That's all. When it's done burning to one CD, go to the next one.

The idea is that I want to play my MP3's on my Panasonic DVD/CD/MP3 5-disc changer, which can play CD-RW's with MP3 files on them. Since I update my music now and then, it would be great if I could do this. Using 5 CD-RW's with MP3's, I should be able to play about 3GB of my collection at a time.

I've tried Gnomebaker, but it gives up, saying that all the files won't fit on a single CD-RW (I wish it was smart enough to give me the option to span multiple CD's!).

Disc-o-matic looks good, but I can't seem to install it from source on Breezy.

Can anyone help me get this to work? Please don't suggest hooking my PC up to my stereo...been there...done that. Can't afford an iPod either...

Thanks!

---

### Post by speedybits on 2006-05-04
I am very surprised that I haven't had a response to this issue...is there really no way to do this in Ubuntu/Linux?

I have found out that iTunes is able to do this (but not under Wine/Crossover Office). And I've been told that Roxio and Nero can do this.

I posted the issue to the Gnomebaker forums, and someone replied saying it sounded interesting. I find it hard to believe that nobody else would find this useful!

---

### Post by louis_nichols on 2006-05-04
Well... I'll think about it. In the meantime, let's see if we can help you compile disc-o-matic, just in case we won't find a better solution.

What errors are you getting?

---

### Post by speedybits on 2006-05-05
Thanks for the reply....Here is the output when I run the configure script with discomatic 0.3

================================
user@ubuntu1:~/discomatic-0.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.2 glib-2.0 >= 2.2... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.2 glib-2.0 >= 2.2) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
================================

I'm not sure what to do with the GTK problem...any help is much appreciated!

Thanks!

---

### Post by louis_nichols on 2006-05-05
for starters, you need to install the following 2 packages:

libglib2.0-dev
libgtk2.0-dev

and any dependencies they will require. Then try the configure script again.

---

### Post by speedybits on 2006-05-05
Thanks for the help!

I was able to get discomatic 0.3 installed after installing the libraries you mentioned. It looks like it will do what I need it to do, although the interface is cumbersome.

I'll post my results once I try to copy my MP3 collection...

---

### Post by louis_nichols on 2006-05-05
Glad it works! I was expecting it to require even more deb packages, but it's good it didn't.

As a general rule, if you'll ever compile other packages: if the configure script says it can't find abcd, then you have to install a package called abcd-dev or libabcd-dev.

---

### Post by speedybits on 2006-05-05
Okay, so I was able to install and run discomatic 0.3 and test it out with my MP3 collection, but the functionality does not work like I need it to.

Basically, it lets me select the number and type of discs I think I'll need. Then I point to a directory (/home/mymusic). However, if the directory has more than the amount of space a single disc will hold, it says "Not enough space on disc"!

This is crazy...I'm so frustrated. Should I focus on getting Roxio or Nero to work under wine?

---

### Post by louis_nichols on 2006-05-06
[QUOTE=speedybits]
This is crazy...I'm so frustrated. Should I focus on getting Roxio or Nero to work under wine?[/QUOTE]

I don't think that's gonna work. Too much hardware access involved. Sorry to hear the app doesn't do what you were hoping. I've never heard of an app having such a feature.

Try looking for more cd burning project at [freshmeat]("http://freshmeat.net/") or [sourceforge]("http://www.sf.net"). Perhaps a search like [this one]("http://freshmeat.net/search/?q=cd+burning&section=projects&Go.x=0&Go.y=0"), then browse through the result and see if any of them fits.

---

### Post by bsmonks on 2007-08-27
Louis, I hope you're still browsing this forum... anyway, I'm trying to install Disc-O-Matic and have almost no EARTHLY idea what I'm doing. I haven't done command line stuff since MSDOS 5.something. And this just seems so much more involved. whew! So, here is my config log. The only thing I understand is that it can't create any executables. Can you (or anybody?) help me?  





This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.57.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = DIsc-Copier
uname -m = i686
uname -r = 2.6.20-15-generic
uname -s = Linux
uname -v = #2 SMP Sun Apr 15 07:36:31 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1279: checking for a BSD-compatible install
configure:1333: result: /usr/bin/install -c
configure:1344: checking whether build environment is sane
configure:1387: result: yes
configure:1402: checking whether make sets $(MAKE)
configure:1422: result: yes
configure:1454: checking for working aclocal-1.4
configure:1465: result: missing
configure:1469: checking for working autoconf
configure:1480: result: missing
configure:1484: checking for working automake-1.4
configure:1495: result: missing
configure:1499: checking for working autoheader
configure:1510: result: missing
configure:1514: checking for working makeinfo
configure:1525: result: missing
configure:1577: checking for gcc
configure:1593: found /usr/bin/gcc
configure:1603: result: gcc
configure:1847: checking for C compiler version
configure:1850: gcc --version </dev/null >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:1853: $? = 0
configure:1855: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:1858: $? = 0
configure:1860: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1863: $? = 1
configure:1887: checking for C compiler default output
configure:1890: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1893: $? = 1
configure: failed program was:
| #line 1866 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "hello"
| #define VERSION "0.1"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1932: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='/home/copier/discomatic-0.3/missing aclocal-1.4'
AUTOCONF='/home/copier/discomatic-0.3/missing autoconf'
AUTOHEADER='/home/copier/discomatic-0.3/missing autoheader'
AUTOMAKE='/home/copier/discomatic-0.3/missing automake-1.4'
CC='gcc'
CFLAGS=''
CPP=''
CPPFLAGS=''
CXX=''
CXXFLAGS=''
DEFS=''
DEPS_CFLAGS=''
DEPS_LIBS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKEINFO='/home/copier/discomatic-0.3/missing makeinfo'
OBJEXT=''
PACKAGE='hello'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PKG_CONFIG=''
SET_MAKE=''
SHELL='/bin/bash'
VERSION='0.1'
ac_ct_CC='gcc'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${prefix}/share'
exec_prefix='NONE'
host_alias=''
includedir='${prefix}/include'
infodir='${prefix}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE "hello"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define VERSION "0.1"

configure: exit 77

## ---------------------- ##
## Running config.status. ##
## ---------------------- ##

This file was extended by config.status, which was
generated by GNU Autoconf 2.57.  Invocation command line was

  CONFIG_FILES    = Makefile
  CONFIG_HEADERS  = 
  CONFIG_LINKS    = 
  CONFIG_COMMANDS = 
  $ ./config.status 

on DIsc-Copier

config.status:642: creating Makefile
config.status:933: executing default-1 commands

---

### Post by rsambuca on 2007-08-28
Compiling any program from source is very easy.  Just download the source tarball first and extract in into a folder of your choice.

Then change directories into that folder containing the files using the "cd /folder/..."
then type:  ./configure
let it do its stuff.

type:  make

type:  sudo make install

done!

If that doesn't work for some reason, let us know.

---

### Post by bsmonks on 2007-08-28
[COLOR="Blue"]**Thanks, rsambuca. I'm not sure what exactly is supposed to happen, but I don't think it did. Here's what happened in the terminal window:**[/COLOR]

copier@DIsc-Copier:~$ cd discomatic-0.3
copier@DIsc-Copier:~/discomatic-0.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
copier@DIsc-Copier:~/discomatic-0.3$ make
cd . && autoheader
/bin/sh: autoheader: not found
make: *** [stamp-h.in] Error 127
copier@DIsc-Copier:~/discomatic-0.3$ sudo make install
Making install in src
make[1]: Entering directory `/home/copier/discomatic-0.3/src'
g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/X11R6/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include                 -DPIXMAPS_DIR=\""/usr/local/share/pixmaps"\"   -g -O2 -c main.cpp
/bin/sh: g++: not found
make[1]: *** [main.o] Error 127
make[1]: Leaving directory `/home/copier/discomatic-0.3/src'
make: *** [install-recursive] Error 1
copier@DIsc-Copier:~/discomatic-0.3$



**[COLOR="Blue"]And here is my config.log:[/COLOR]**

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.57.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = DIsc-Copier
uname -m = i686
uname -r = 2.6.20-15-generic
uname -s = Linux
uname -v = #2 SMP Sun Apr 15 07:36:31 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1279: checking for a BSD-compatible install
configure:1333: result: /usr/bin/install -c
configure:1344: checking whether build environment is sane
configure:1387: result: yes
configure:1402: checking whether make sets $(MAKE)
configure:1422: result: yes
configure:1454: checking for working aclocal-1.4
configure:1465: result: missing
configure:1469: checking for working autoconf
configure:1480: result: missing
configure:1484: checking for working automake-1.4
configure:1495: result: missing
configure:1499: checking for working autoheader
configure:1510: result: missing
configure:1514: checking for working makeinfo
configure:1525: result: missing
configure:1577: checking for gcc
configure:1593: found /usr/bin/gcc
configure:1603: result: gcc
configure:1847: checking for C compiler version
configure:1850: gcc --version </dev/null >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:1853: $? = 0
configure:1855: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:1858: $? = 0
configure:1860: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1863: $? = 1
configure:1887: checking for C compiler default output
configure:1890: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1893: $? = 1
configure: failed program was:
| #line 1866 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "hello"
| #define VERSION "0.1"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1932: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='/home/copier/discomatic-0.3/missing aclocal-1.4'
AUTOCONF='/home/copier/discomatic-0.3/missing autoconf'
AUTOHEADER='/home/copier/discomatic-0.3/missing autoheader'
AUTOMAKE='/home/copier/discomatic-0.3/missing automake-1.4'
CC='gcc'
CFLAGS=''
CPP=''
CPPFLAGS=''
CXX=''
CXXFLAGS=''
DEFS=''
DEPS_CFLAGS=''
DEPS_LIBS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKEINFO='/home/copier/discomatic-0.3/missing makeinfo'
OBJEXT=''
PACKAGE='hello'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PKG_CONFIG=''
SET_MAKE=''
SHELL='/bin/bash'
VERSION='0.1'
ac_ct_CC='gcc'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${prefix}/share'
exec_prefix='NONE'
host_alias=''
includedir='${prefix}/include'
infodir='${prefix}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE "hello"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define VERSION "0.1"

configure: exit 77


**[COLOR="Blue"]Like I said, I'm not familiar enough with Ubuntu (but willing to learn [-o<) to understand what's going on.[/COLOR]**

---

### Post by rsambuca on 2007-08-29
hmmm... The make and make install commands won't work because it is not configuring properly.

I think you will have to install the automake package first.  You can either do it in the Synaptic Package Manager, or via command line```
sudo apt-get install automake
```

---

### Post by bsmonks on 2007-08-30
> **speedybits said:**
> 
checking for gtk+-2.0 >= 2.2 glib-2.0 >= 2.2... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.2 glib-2.0 >= 2.2) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.



OK. Now I'm getting this same message when I configure. I checked my packages and gtk and glib were both there. I even reinstalled them for good measure. But I still get the message.  PKG_CONFIG_PATH is an executable so I can't edit it (like I would a config.sys or autoexec.bat file in my old MSDOS days). Now what...

I have tried many variations of "sudo apt-get install"
libglib2.0-dev
glib2.0-dev
glib-2.0-dev

All return the same message: E: couldn't find package XXXXXX

This is getting bloody ridiculous! All I want to do is install a program I'm not even sure will meet my needs! And I have to jump through 27 bloody hoops to do it. Can't you linux people just package your programs in neat, tidy installers?

---

### Post by bsmonks on 2007-08-31
Any other posts I make will be [here]("http://ubuntuforums.org/showthread.php?t=539694").

---

