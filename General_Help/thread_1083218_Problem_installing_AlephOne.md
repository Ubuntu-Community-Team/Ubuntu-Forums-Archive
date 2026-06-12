---
title: "Problem installing AlephOne"
date: 2009-02-28
forum: General Help
---

### Post by burdock on 2009-02-28
Im pretty much a linux n00b, but Im learning. Please bear with me.

Running Ubuntu 8.10.

I have been trying to install AlephOne so that I can install Excaliber:Morgana's Revenge but I am having a problem.

When I enter ./configure in the console, this is what I get.

burdock@Sophocles:/usr/local/src/AlephOne/AlephOne-20081226$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/usr/local/src/AlephOne/AlephOne-20081226':
configure: error: C compiler cannot create executables
See `config.log' for more details.

Anyone know how to solve this?

---

### Post by taurus on 2009-02-28
You need to install the build-essential package first before you can build anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```
Then, run the **./configure** again.

---

### Post by burdock on 2009-02-28
I have already installed build-essential

I did this when getting an error about not having a c++ compiler installed...

---

### Post by taurus on 2009-02-28
What are the outputs of these commands from a terminal?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by burdock on 2009-02-28
saving space

---

### Post by burdock on 2009-02-28
Terminal output is as follows:

burdock@Sophocles:/usr/local/src/AlephOne/AlephOne-20081226$ sudo apt-get update[sudo] 
password for burdock: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done
burdock@Sophocles:/usr/local/src/AlephOne/AlephOne-20081226$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


***Whoops....didnt mean to post that twice.

---

### Post by taurus on 2009-02-28
What about

```
gcc -v
```

---

### Post by burdock on 2009-02-28
Terminal output as follows:

burdock@Sophocles:/usr/local/src/AlephOne/AlephOne-20081226$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12)

---

### Post by taurus on 2009-02-28
Have a look at the configure file.

```
more configure
```
Hit the space key for the next 24 lines.  Otherwise, tell me where you downloaded AlephOne-20081226 and I will have a look at it.

p.s.  I assume you are running 32bit (x86) intrepid.

---

### Post by burdock on 2009-02-28
I am 32bit Ubuntu.

I downloaded AlephOne from here:
[http://sourceforge.net/project/platformdownload.php?group_id=1997&sel_platform=2265](http://sourceforge.net/project/platformdownload.php?group_id=1997&sel_platform=2265)

I will take a look at the config file...

---

### Post by burdock on 2009-02-28
The configure file is huge!!!!

Any idea what I should be looking for?

---

### Post by taurus on 2009-02-28
Well, I just ran the ./configure and here was the output.

```

./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
[B][COLOR="Blue"]checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes[/COLOR][/B]
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
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
checking for unistd.h... (cached) yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: You need SDL 1.2 to run Aleph One.

```

---

### Post by burdock on 2009-02-28
The output when I run ./configure is missing
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes

---

### Post by taurus on 2009-02-28
What do you mean missing?  Don't you get something similar to my output in the previous post?

---

### Post by burdock on 2009-02-28
Here is my output:

burdock@Sophocles:/usr/local/src/AlephOne/AlephOne-20081226$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/usr/local/src/AlephOne/AlephOne-20081226':
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by burdock on 2009-02-28
Here is what the config.log file says:

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by Aleph One/SDL configure 20081226, which was
generated by GNU Autoconf 2.63.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = Sophocles
uname -m = i686
uname -r = 2.6.27-11-generic
uname -s = Linux
uname -v = #1 SMP Thu Jan 29 19:24:39 UTC 2009

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
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

configure:1930: checking build system type
configure:1948: result: i686-pc-linux-gnu
configure:1970: checking host system type
configure:1985: result: i686-pc-linux-gnu
configure:2007: checking target system type
configure:2022: result: i686-pc-linux-gnu
configure:2067: checking for a BSD-compatible install
configure:2135: result: /usr/bin/install -c
configure:2146: checking whether build environment is sane
configure:2189: result: yes
configure:2214: checking for a thread-safe mkdir -p
configure:2253: result: /bin/mkdir -p
configure:2266: checking for gawk
configure:2296: result: no
configure:2266: checking for mawk
configure:2282: found /usr/bin/mawk
configure:2293: result: mawk
configure:2304: checking whether make sets $(MAKE)
configure:2326: result: yes
configure:2625: checking for gcc
configure:2652: result: gcc
configure:2884: checking for C compiler version
configure:2892: gcc --version >&5
gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2896: $? = 0
configure:2903: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
configure:2907: $? = 0
configure:2914: gcc -V >&5
gcc: '-V' option must have argument
configure:2918: $? = 1
configure:2941: checking for C compiler default output file name
configure:2963: gcc  ”-I/usr/local/include/boost-1_33_1  conftest.c  >&5
gcc: ”-I/usr/local/include/boost-1_33_1: No such file or directory
configure:2967: $? = 1
configure:3005: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Aleph One/SDL"
| #define PACKAGE_TARNAME "AlephOne"
| #define PACKAGE_VERSION "20081226"
| #define PACKAGE_STRING "Aleph One/SDL 20081226"
| #define PACKAGE_BUGREPORT "http://sourceforge.net/bugs/?group_id=1997"
| #define PACKAGE "AlephOne"
| #define VERSION "20081226"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3011: error: in `/usr/local/src/AlephOne/AlephOne-20081226':
configure:3014: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=set
ac_cv_env_CC_value=gcc
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=set
ac_cv_env_CPPFLAGS_value=”-I/usr/local/include/boost-1_33_1
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnu
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes
ac_cv_target=i686-pc-linux-gnu

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /usr/local/src/AlephOne/AlephOne-20081226/missing --run aclocal-1.10'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /usr/local/src/AlephOne/AlephOne-20081226/missing --run tar'
AUTOCONF='${SHELL} /usr/local/src/AlephOne/AlephOne-20081226/missing --run autoconf'
AUTOHEADER='${SHELL} /usr/local/src/AlephOne/AlephOne-20081226/missing --run autoheader'
AUTOMAKE='${SHELL} /usr/local/src/AlephOne/AlephOne-20081226/missing --run automake-1.10'
AWK='mawk'
CC='gcc'
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS='”-I/usr/local/include/boost-1_33_1'
CXX=''
CXXCPP=''
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
GREP=''
HAVE_SDL_NET_FALSE=''
HAVE_SDL_NET_TRUE=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /usr/local/src/AlephOne/AlephOne-20081226/missing --run makeinfo'
MAKE_WINDOWS_FALSE=''
MAKE_WINDOWS_TRUE=''
MKDIR_P='/bin/mkdir -p'
OBJEXT=''
PACKAGE='AlephOne'
PACKAGE_BUGREPORT='http://sourceforge.net/bugs/?group_id=1997'
PACKAGE_NAME='Aleph One/SDL'
PACKAGE_STRING='Aleph One/SDL 20081226'
PACKAGE_TARNAME='AlephOne'
PACKAGE_VERSION='20081226'
PATH_SEPARATOR=':'
RANLIB=''
SDL_CFLAGS=''
SDL_CONFIG=''
SDL_LIBS=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
VERSION='20081226'
WINDRES=''
ac_ct_CC='gcc'
ac_ct_CXX=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE=''
am__fastdepCXX_TRUE=''
am__include=''
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /usr/local/src/AlephOne/AlephOne-20081226/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target='i686-pc-linux-gnu'
target_alias=''
target_cpu='i686'
target_os='linux-gnu'
target_vendor='pc'

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "Aleph One/SDL"
#define PACKAGE_TARNAME "AlephOne"
#define PACKAGE_VERSION "20081226"
#define PACKAGE_STRING "Aleph One/SDL 20081226"
#define PACKAGE_BUGREPORT "http://sourceforge.net/bugs/?group_id=1997"
#define PACKAGE "AlephOne"
#define VERSION "20081226"

configure: exit 77

---

### Post by taurus on 2009-02-28
By the way, do you have permission to write to /usr/local/src?  Maybe that is the problem, no writing permission to /usr/local/src.

Why not unpack AlephOne-20081226.tar.bz2 in your $HOME.  Then, change to AlephOne-20081226 and build it from there.

```
tar xvjf AlephOne-20081226.tar.bz2
cd AlephOne-20081226
./configure
make
sudo make install
```

---

### Post by burdock on 2009-02-28
I tried moving the files but Im still getting the same error.

When I use Nautilus to browse through the files, the directory that contains the AlephOne files has a little "lock" icon on it. Does this mean that I still dont have write permission inside that directory?

Also, I have AlephOne-20081226.tar.gz instead of AlephOne-20081226.tar.bz2

I tried unpacking it with the terminal (at the very beginning of all this) and got an error so I used the graphical Archive Manager to extract the files.

Could that have something to do with the errors?

---

### Post by taurus on 2009-02-28
Where did you move AlephOne-20081226.tar.bz2 to now?  Yes, you are not the owner of the directory so that's why there is a lock on it.  I think that is your problem; don't have the write permission in that directory since ./configure will need to write/modify files in that directory, according to your machine.

---

### Post by burdock on 2009-02-28
I put it in /home/burdock/Programs.

---

### Post by taurus on 2009-02-28
Run these two commands and post the output of the second one.

```
cd ~/Programs
ls -la
```
If AlephOne-20081226.tar.bz2 doesn't belong to you, burdock, then you need to change the ownership back to you before you unpack it.

```
sudo chown burdock:burdock AlephOne-20081226.tar.bz2
tar xvjf AlephOne-20081226.tar.bz2
ls -la
```

---

### Post by burdock on 2009-02-28
Terminal output as follows:

burdock@Sophocles:~/Programs$ ls -la
total 235696
drwxr-xr-x  3 burdock burdock      4096 2009-02-28 17:56 .
drwxr-xr-x 42 burdock burdock      4096 2009-02-28 17:56 ..
drwxr-xr-x 10 burdock burdock      4096 2009-02-28 17:56 AlephOne-20081226
-rw-r--r--  1 burdock burdock   3002611 2009-02-28 17:47 AlephOne-20081226.tar.bz2
-rw-------  1 burdock burdock 238090322 2009-02-28 14:58 emr-3.0-0602.tgz



I tried running ./configure again but am still getting the same error.

---

### Post by taurus on 2009-02-28
Now cd to AlephOne-20081226 and see who owns those files & directories.

```
cd AlephOne-20081226
ls -la
```

---

### Post by burdock on 2009-02-28
Looks like I am the owner of everything in there too.

Terminal output as follows:

burdock@Sophocles:~/Programs/AlephOne-20081226$ ls -la
total 2232
drwxr-xr-x 10 burdock burdock   4096 2009-02-28 17:56 .
drwxr-xr-x  3 burdock burdock   4096 2009-02-28 17:56 ..
-rw-r--r--  1 burdock burdock  39101 2008-12-26 19:34 aclocal.m4
-rwxr-xr-x  1 burdock burdock 702098 2008-12-26 19:35 Aleph One Classic SDL.mcp
-rw-r--r--  1 burdock burdock   2416 2008-12-26 19:35 AlephOne.spec
-rw-r--r--  1 burdock burdock   2418 2008-10-23 19:52 AlephOne.spec.in
-rw-r--r--  1 burdock burdock    455 2008-10-23 19:52 AUTHORS
-rw-r--r--  1 burdock burdock 874113 2008-12-13 16:02 ChangeLog
-rwxr-xr-x  1 burdock burdock  45468 2008-10-23 19:53 config.guess
-rw-r--r--  1 burdock burdock   3103 2008-12-26 19:35 config.h.in
-rw-r--r--  1 burdock burdock   7703 2009-02-28 17:56 config.log
-rwxr-xr-x  1 burdock burdock  33653 2008-10-23 19:53 config.sub
-rwxr-xr-x  1 burdock burdock 313256 2008-12-26 19:35 configure
-rw-r--r--  1 burdock burdock   7896 2008-12-26 19:33 configure.ac
-rw-r--r--  1 burdock burdock  17992 2008-10-23 19:52 COPYING
-rw-r--r--  1 burdock burdock  23244 2008-10-23 19:52 COPYING.SDL
drwxr-xr-x  3 burdock burdock   4096 2008-12-26 19:35 data
-rwxr-xr-x  1 burdock burdock  17867 2008-10-23 19:53 depcomp
drwxr-xr-x  2 burdock burdock   4096 2008-12-26 19:35 docs
drwxr-xr-x  3 burdock burdock   4096 2008-12-26 19:35 examples
drwxr-xr-x  3 burdock burdock   4096 2008-12-26 19:35 Expat
-rw-r--r--  1 burdock burdock   2689 2008-10-23 19:52 INSTALL.BeOS
-rwxr-xr-x  1 burdock burdock  13620 2008-10-23 19:53 install-sh
-rw-r--r--  1 burdock burdock   4357 2008-10-23 19:52 INSTALL.Unix
-rw-r--r--  1 burdock burdock   6042 2008-10-23 19:52 INSTALL.Windows
-rw-r--r--  1 burdock burdock   2890 2008-12-13 16:01 Makefile.am
-rw-r--r--  1 burdock burdock   9104 2008-10-23 19:52 Makefile.BeOS
-rw-r--r--  1 burdock burdock  24287 2008-12-26 19:35 Makefile.in
-rwxr-xr-x  1 burdock burdock  11135 2008-10-23 19:53 missing
drwxr-xr-x  4 burdock burdock   4096 2008-12-26 19:35 PBProjects
-rw-r--r--  1 burdock burdock  16603 2008-10-23 19:52 README
drwxr-xr-x  3 burdock burdock   4096 2008-12-26 19:35 Resources
drwxr-xr-x 17 burdock burdock   4096 2008-12-26 19:35 Source_Files
drwxr-xr-x  2 burdock burdock   4096 2008-12-26 19:35 tools

---

### Post by taurus on 2009-02-28
So you still get the same error message as before!  Reboot.  Then, log in and see what happens this time when you run ./configure in ~/Programs/AlephOne-20081226.

```
cd ~/Programs/AlephOne-20081226
./configure
```

---

### Post by burdock on 2009-02-28
A simple restart seems to have done the trick!

Still getting an error about needing boost/bind.hpp but I can work on that on my own for a while before I ask for help.

Thanks for all the help. You sir, are awesome:P

---

