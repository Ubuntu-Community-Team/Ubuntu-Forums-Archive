---
title: "c compliler will not create executables???"
date: 2006-01-29
forum: Desktop Environments
---

### Post by pbibb1657 on 2006-01-29
Hello
 Im running an older compaq desktop and i decided to give unbuntu a spin , I love the os so far only I cant get shntool or shorten to compile below is the config logs if anyone knows of a work around Id be happy to listen



# --------- ##
## Platform. ##
## --------- ##

hostname = ubuntudesktop
uname -m = i686
uname -r = 2.6.12-10-386
uname -s = Linux
uname -v = #1 Mon Jan 16 17:18:08 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/bin
PATH: /usr/local/sbin
PATH: /sbin
PATH: /usr/sbin
PATH: /bin
PATH: /usr/bin
PATH: /usr/bin/X11
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1314: checking build system type
configure:1332: result: i686-pc-linux-gnulibc1
configure:1340: checking host system type
configure:1354: result: i686-pc-linux-gnulibc1
configure:1377: checking for a BSD-compatible install
configure:1432: result: /usr/bin/install -c
configure:1443: checking whether build environment is sane
configure:1486: result: yes
configure:1543: checking for gawk
configure:1572: result: no
configure:1543: checking for mawk
configure:1559: found /usr/bin/mawk
configure:1569: result: mawk
configure:1579: checking whether make sets $(MAKE)
configure:1603: result: no
configure:1820: checking for gcc
configure:1836: found /usr/bin/gcc
configure:1846: result: gcc
configure:2090: checking for C compiler version
configure:2093: gcc --version </dev/null >&5
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2096: $? = 0
configure:2098: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
configure:2101: $? = 0
configure:2103: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2106: $? = 1
configure:2129: checking for C compiler default output file name
configure:2132: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2135: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "shntool"
| #define VERSION "2.0.3"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2174: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnulibc1
ac_cv_build_alias=i686-pc-linux-gnulibc1
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnulibc1
ac_cv_host_alias=i686-pc-linux-gnulibc1
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=no

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/phillip/Desktop/shntool-2.0.3/missing --run aclocal-1.8'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/phillip/Desktop/shntool-2.0.3/missing --run tar'
AUTOCONF='${SHELL} /home/phillip/Desktop/shntool-2.0.3/missing --run autoconf'
AUTOHEADER='${SHELL} /home/phillip/Desktop/shntool-2.0.3/missing --run autoheader'
AUTOMAKE='${SHELL} /home/phillip/Desktop/shntool-2.0.3/missing --run automake-1.8'
AWK='mawk'
CC='gcc'
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
FLAC=''
FORMAT_OBJS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LN_S=''
LPAC=''
LTLIBOBJS=''
MAC=''
MAKEINFO='${SHELL} /home/phillip/Desktop/shntool-2.0.3/missing --run makeinfo'
MODES_CONFIGURED=''
MODE_OBJS=''
OBJEXT=''
OPTIMFROG=''
PACKAGE='shntool'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
SET_MAKE='MAKE=make'
SHELL='/bin/sh'
SHORTEN=''
SOX=''
STRIP=''
VERSION='2.0.3'
WAVPACK=''
ac_ct_CC='gcc'
ac_ct_STRIP=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__include=''
am__leading_dot='.'
am__quote=''
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnulibc1'
build_alias=''
build_cpu='i686'
build_os='linux-gnulibc1'
build_vendor='pc'
datadir='${prefix}/share'
exec_prefix='NONE'
host='i686-pc-linux-gnulibc1'
host_alias=''
host_cpu='i686'
host_os='linux-gnulibc1'
host_vendor='pc'
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/phillip/Desktop/shntool-2.0.3/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
mkdir_p='mkdir -p -- .'
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

#define PACKAGE "shntool"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define VERSION "2.0.3"

configure: exit 77



          Thanks if anyone can help
                Phillip

---

### Post by RAOF on 2006-01-29
Quick question: have you installed the "build-essential" package?  If not, install it.

---

### Post by pbibb1657 on 2006-01-30
Ok
 Im at work now but I will look into the "build essential"program thanks.

                           Phillip

---

### Post by skwid on 2006-01-30
You may want to make sure you have gcc and build essential loaded like RAOF said.

---

