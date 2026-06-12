---
title: "Beryl installation error(s)"
date: 2007-09-12
forum: Desktop Effects &amp; Customization
---

### Post by 127.0.0.1 on 2007-09-12
Hi, i am haveing trouble installing Beryl. mostly because i am a newb at Linux lol

but here is the error i am getting:
[IMG]http://img251.imageshack.us/img251/7937/snapshot1jj7.png[/IMG]

and here is what is in config.log:

```
configure:2161: checking build system type
configure:2179: result: i686-pc-linux-gnulibc1
configure:2201: checking host system type
configure:2216: result: i686-pc-linux-gnulibc1
configure:2238: checking target system type
configure:2253: result: i686-pc-linux-gnulibc1
configure:2314: checking for a BSD-compatible install
configure:2370: result: /usr/bin/install -c
configure:2385: checking for -p flag to install
configure:2398: result: yes
configure:2409: checking whether build environment is sane
configure:2452: result: yes
configure:2504: checking for gawk
configure:2534: result: no
configure:2504: checking for mawk
configure:2520: found /usr/bin/mawk
configure:2531: result: mawk
configure:2542: checking whether make sets $(MAKE)
configure:2563: result: yes
configure:2765: checking for kde-config
configure:2827: result: /usr/bin/kde-config
configure:2922: checking where to install
configure:2926: result: /usr (as returned by kde-config)
configure:2981: checking for style of include used by make
configure:3009: result: GNU
configure:3159: checking for gcc
configure:3175: found /usr/bin/gcc
configure:3186: result: gcc
configure:3424: checking for C compiler version
configure:3431: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3434: $? = 0
configure:3441: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:3444: $? = 0
configure:3451: gcc -V >&5
gcc: '-V' option must have argument
configure:3454: $? = 1
configure:3477: checking for C compiler default output file name
configure:3504: gcc     conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:3507: $? = 1
configure:3545: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "aquamarine"
| #define VERSION "0.3.0-svn"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3552: error: C compiler cannot create executables
See `config.log' for more details.

```

please help :X

---

### Post by mrmiserable on 2007-09-12
try the repos for aquamarine (synaptic package manager)

---

### Post by 127.0.0.1 on 2007-09-12
> **mrmiserable said:**
> try the repos for aquamarine (synaptic package manager)

mind telling me the server?

---

