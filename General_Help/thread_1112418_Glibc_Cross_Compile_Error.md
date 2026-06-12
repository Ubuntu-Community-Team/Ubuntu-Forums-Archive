---
title: "Glibc Cross Compile Error"
date: 2009-03-31
forum: General Help
---

### Post by Orbit45244 on 2009-03-31
I'm trying to build a cross compiler for my Sabayon box (CHOST:x86_64-pc-linux-gnu) on my Jaunty Xubuntu PS3 box (CHOST:powerpc64-unknown-linux-gnu). I'm using [this]("http://www.pages.drexel.edu/~sg64/stuff/cross-compile.htm") guide, and the binutils, gcc, and glibc versions I'm compiling are 2.18, 4.3.2, and 2.8, respectively. I'm down to the part where you compile glibc, and I get this error about "unwind":

```
$ ./configure --prefix=/usr/local --target=x86_64-pc-linux-gnu --host=x86_64-pc-linux-gnu --with-tls

configure: WARNING: If you wanted to set the --build type, don't use --host.
    If a cross compiler is detected then cross compile mode will be used.
checking build system type... powerpc64-unknown-linux-gnu
checking host system type... x86_64-pc-linux-gnu
configure: running configure fragment for add-on nptl
checking sysdep dirs... sysdeps/x86_64/elf nptl/sysdeps/unix/sysv/linux/x86_64 sysdeps/unix/sysv/linux/x86_64 sysdeps/unix/sysv/linux/wordsize-64 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet nptl/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/x86_64 nptl/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/x86_64/fpu nptl/sysdeps/x86_64 sysdeps/x86_64 sysdeps/wordsize-64 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for x86_64-pc-linux-gnu-gcc... x86_64-pc-linux-gnu-gcc
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether x86_64-pc-linux-gnu-gcc accepts -g... yes
checking for x86_64-pc-linux-gnu-gcc option to accept ISO C89... unsupported
checking for gcc... gcc
checking how to run the C preprocessor... x86_64-pc-linux-gnu-gcc -E
checking for x86_64-pc-linux-gnu-g++... no
checking for x86_64-pc-linux-gnu-c++... no
checking for x86_64-pc-linux-gnu-gpp... no
checking for x86_64-pc-linux-gnu-aCC... no
checking for x86_64-pc-linux-gnu-CC... no
checking for x86_64-pc-linux-gnu-cxx... no
checking for x86_64-pc-linux-gnu-cc++... no
checking for x86_64-pc-linux-gnu-cl.exe... no
checking for x86_64-pc-linux-gnu-FCC... no
checking for x86_64-pc-linux-gnu-KCC... no
checking for x86_64-pc-linux-gnu-RCC... no
checking for x86_64-pc-linux-gnu-xlC_r... no
checking for x86_64-pc-linux-gnu-xlC... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as is GNU as... yes
checking whether /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld is GNU ld... yes
checking for /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as... /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as
checking version of /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as... 2.18, ok
checking for /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld... /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld
checking version of /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld... 2.18, ok
checking for pwd... /bin/pwd
checking for x86_64-pc-linux-gnu-gcc... (cached) x86_64-pc-linux-gnu-gcc
checking version of x86_64-pc-linux-gnu-gcc... 4.3.2, ok
checking for gnumake... no
checking for gmake... no
checking for make... make
checking version of make... 3.81, ok
checking for gnumsgfmt... no
checking for gmsgfmt... no
checking for msgfmt... msgfmt
checking version of msgfmt... 0.17, ok
checking for makeinfo... makeinfo
checking version of makeinfo... 4.11, ok
checking for sed... sed
checking version of sed... 4.1.5, ok
checking for autoconf... autoconf
checking whether autoconf works... yes
checking whether ranlib is necessary... no
checking LD_LIBRARY_PATH variable... ok
checking whether GCC supports -static-libgcc... -static-libgcc
checking for bash... /bin/bash
checking for gawk... gawk
checking for perl... /usr/bin/perl
checking for install-info... /usr/sbin/install-info
checking for bison... /usr/bin/bison
checking for signed size_t type... no
checking for libc-friendly stddef.h... yes
checking whether we need to use -P to assemble .S files... no
checking whether .text pseudo-op must be used... yes
checking for assembler global-symbol directive... .globl
checking for .set assembler directive... yes
checking for assembler .type directive prefix... @
checking for .symver assembler directive... yes
checking for ld --version-script... yes
checking for .previous assembler directive... yes
checking for .protected and .hidden assembler directive... yes
checking whether __attribute__((visibility())) is supported... yes
checking for broken __attribute__((visibility()))... no
checking for broken __attribute__((alias()))... no
checking whether to put _rtld_local into .sdata section... no
checking for .preinit_array/.init_array/.fini_array support... yes
checking for libunwind-support in compiler... no
checking for -z nodelete option... yes
checking for -z nodlopen option... yes
checking for -z initfirst option... yes
checking for -z relro option... yes
checking for -Bgroup option... yes
checking for libgcc_s suffix... 
checking for --as-needed option... no
checking whether --noexecstack is desirable for .S files... yes
checking for -z combreloc... yes
checking for -z execstack... yes
checking for -fpie... no
checking for --hash-style option... yes
checking for -fno-toplevel-reorder -fno-section-anchors... yes
checking for -fstack-protector... no
checking for -fgnu89-inline... yes
checking whether cc puts quotes around section names... no
checking for assembler .weak directive... yes
checking whether CFI directives are supported... yes
checking for ld --no-whole-archive... yes
checking for gcc -fexceptions... yes
checking for __builtin_expect... no
checking for __builtin_memset... yes
checking for redirection of built-in functions... yes
checking for __thread... yes
checking for tls_model attribute... yes
checking for libgd... no
checking for is_selinux_enabled in -lselinux... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... no
checking for sys/types.h... no
checking for sys/stat.h... no
checking for stdlib.h... no
checking for string.h... no
checking for memory.h... no
checking for strings.h... no
checking for inttypes.h... no
checking for stdint.h... no
checking for unistd.h... no
checking for long double... no
checking size of long double... 0
running configure fragment for sysdeps/x86_64/elf
checking for x86-64 TLS support... yes
running configure fragment for nptl/sysdeps/pthread
checking for forced unwind support... no
configure: error: forced unwind support is required
```

...and compiling stops. This is my config.log:

```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by GNU C Library configure (see version.h), which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ../glibc-2.8/configure --prefix=/usr/local --target=x86_64-pc-linux-gnu --host=x86_64-pc-linux-gnu --with-tls

## --------- ##
## Platform. ##
## --------- ##

hostname = slavery-box
uname -m = ppc64
uname -r = 2.6.28-5-powerpc64-smp
uname -s = Linux
uname -v = #14-Ubuntu SMP Sun Mar 22 18:13:15 UTC 2009

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

configure:2180: checking build system type
configure:2198: result: powerpc64-unknown-linux-gnu
configure:2220: checking host system type
configure:2235: result: x86_64-pc-linux-gnu
configure:2416: running configure fragment for add-on nptl
configure:2553: checking sysdep dirs
configure:2789: result: sysdeps/generic/elf sysdeps/generic
configure:2867: checking for a BSD-compatible install
configure:2923: result: /usr/bin/install -c
configure:2938: checking whether ln -s works
configure:2942: result: yes
configure:2958: checking for x86_64-pc-linux-gnu-gcc
configure:2974: found /usr/local/bin/x86_64-pc-linux-gnu-gcc
configure:2985: result: x86_64-pc-linux-gnu-gcc
configure:3263: checking for C compiler version
configure:3270: x86_64-pc-linux-gnu-gcc --version >&5
x86_64-pc-linux-gnu-gcc (GCC) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3273: $? = 0
configure:3280: x86_64-pc-linux-gnu-gcc -v >&5
Using built-in specs.
Target: x86_64-pc-linux-gnu
Configured with: ../gcc-4.3.2/configure --target=x86_64-pc-linux-gnu --disable-shared --disable-threads --enable-languages=c --with-newlib
Thread model: single
gcc version 4.3.2 (GCC) 
configure:3283: $? = 0
configure:3290: x86_64-pc-linux-gnu-gcc -V >&5
x86_64-pc-linux-gnu-gcc: '-V' option must have argument
configure:3293: $? = 1
configure:3297: checking for suffix of object files
configure:3323: x86_64-pc-linux-gnu-gcc -c   conftest.c >&5
configure:3326: $? = 0
configure:3349: result: o
configure:3353: checking whether we are using the GNU C compiler
configure:3382: x86_64-pc-linux-gnu-gcc -c   conftest.c >&5
configure:3388: $? = 0
configure:3405: result: yes
configure:3410: checking whether x86_64-pc-linux-gnu-gcc accepts -g
configure:3440: x86_64-pc-linux-gnu-gcc -c -g  conftest.c >&5
configure:3446: $? = 0
configure:3545: result: yes
configure:3562: checking for x86_64-pc-linux-gnu-gcc option to accept ISO C89
configure:3636: x86_64-pc-linux-gnu-gcc  -c -g -O2  conftest.c >&5
conftest.c:9:19: error: stdio.h: No such file or directory
conftest.c:10:23: error: sys/types.h: No such file or directory
conftest.c:11:22: error: sys/stat.h: No such file or directory
conftest.c:14: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:48: error: expected declaration specifiers or '...' before 'FILE'
configure:3642: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3636: x86_64-pc-linux-gnu-gcc -qlanglvl=extc89 -c -g -O2  conftest.c >&5
x86_64-pc-linux-gnu-gcc: unrecognized option '-qlanglvl=extc89'
conftest.c:9:19: error: stdio.h: No such file or directory
conftest.c:10:23: error: sys/types.h: No such file or directory
conftest.c:11:22: error: sys/stat.h: No such file or directory
conftest.c:14: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:48: error: expected declaration specifiers or '...' before 'FILE'
configure:3642: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3636: x86_64-pc-linux-gnu-gcc -qlanglvl=ansi -c -g -O2  conftest.c >&5
x86_64-pc-linux-gnu-gcc: unrecognized option '-qlanglvl=ansi'
conftest.c:9:19: error: stdio.h: No such file or directory
conftest.c:10:23: error: sys/types.h: No such file or directory
conftest.c:11:22: error: sys/stat.h: No such file or directory
conftest.c:14: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:48: error: expected declaration specifiers or '...' before 'FILE'
configure:3642: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3636: x86_64-pc-linux-gnu-gcc -std -c -g -O2  conftest.c >&5
cc1: error: unrecognized command line option "-std"
configure:3642: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3636: x86_64-pc-linux-gnu-gcc -Ae -c -g -O2  conftest.c >&5
<command-line>: error: missing '(' after predicate
conftest.c:9:19: error: stdio.h: No such file or directory
conftest.c:10:23: error: sys/types.h: No such file or directory
conftest.c:11:22: error: sys/stat.h: No such file or directory
conftest.c:14: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:48: error: expected declaration specifiers or '...' before 'FILE'
configure:3642: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3636: x86_64-pc-linux-gnu-gcc -Aa -D_HPUX_SOURCE -c -g -O2  conftest.c >&5
<command-line>: error: missing '(' after predicate
conftest.c:9:19: error: stdio.h: No such file or directory
conftest.c:10:23: error: sys/types.h: No such file or directory
conftest.c:11:22: error: sys/stat.h: No such file or directory
conftest.c:14: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:48: error: expected declaration specifiers or '...' before 'FILE'
configure:3642: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3636: x86_64-pc-linux-gnu-gcc -Xc -D__EXTENSIONS__ -c -g -O2  conftest.c >&5
x86_64-pc-linux-gnu-gcc: unrecognized option '-Xc'
conftest.c:9:19: error: stdio.h: No such file or directory
conftest.c:10:23: error: sys/types.h: No such file or directory
conftest.c:11:22: error: sys/stat.h: No such file or directory
conftest.c:14: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:48: error: expected declaration specifiers or '...' before 'FILE'
configure:3642: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3668: result: unsupported
configure:3688: checking for gcc
configure:3704: found /usr/bin/gcc
configure:3715: result: gcc
configure:3733: checking how to run the C preprocessor
configure:3773: x86_64-pc-linux-gnu-gcc -E  conftest.c
configure:3779: $? = 0
configure:3810: x86_64-pc-linux-gnu-gcc -E  conftest.c
conftest.c:8:28: error: ac_nonexistent.h: No such file or directory
configure:3816: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3849: result: x86_64-pc-linux-gnu-gcc -E
configure:3878: x86_64-pc-linux-gnu-gcc -E  conftest.c
configure:3884: $? = 0
configure:3915: x86_64-pc-linux-gnu-gcc -E  conftest.c
conftest.c:8:28: error: ac_nonexistent.h: No such file or directory
configure:3921: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3973: checking for x86_64-pc-linux-gnu-g++
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-c++
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-gpp
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-aCC
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-CC
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-cxx
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-cc++
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-cl.exe
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-FCC
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-KCC
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-RCC
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-xlC_r
configure:4003: result: no
configure:3973: checking for x86_64-pc-linux-gnu-xlC
configure:4003: result: no
configure:4017: checking for g++
configure:4033: found /usr/bin/g++
configure:4044: result: g++
configure:4075: checking for C++ compiler version
configure:4082: g++ --version >&5
g++ (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4085: $? = 0
configure:4092: g++ -v >&5
Using built-in specs.
Target: powerpc-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --disable-softfloat --enable-secureplt --enable-targets=powerpc-linux,powerpc64-linux --with-cpu=default32 --with-long-double-128 --enable-checking=release --build=powerpc-linux-gnu --host=powerpc-linux-gnu --target=powerpc-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
configure:4095: $? = 0
configure:4102: g++ -V >&5
g++: '-V' option must have argument
configure:4105: $? = 1
configure:4108: checking whether we are using the GNU C++ compiler
configure:4137: g++ -c   conftest.cpp >&5
configure:4143: $? = 0
configure:4160: result: yes
configure:4165: checking whether g++ accepts -g
configure:4195: g++ -c -g  conftest.cpp >&5
configure:4201: $? = 0
configure:4300: result: yes
configure:4443: checking whether /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as is GNU as
configure:4457: result: yes
configure:4462: checking whether /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld is GNU ld
configure:4476: result: yes
configure:4486: checking for /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as
configure:4513: result: /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as
configure:4528: checking version of /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as
configure:4538: result: 2.18, ok
configure:4549: checking for /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld
configure:4576: result: /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld
configure:4591: checking version of /usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld
configure:4601: result: 2.18, ok
configure:4616: checking for pwd
configure:4634: found /bin/pwd
configure:4647: result: /bin/pwd
configure:4667: checking for x86_64-pc-linux-gnu-gcc
configure:4694: result: x86_64-pc-linux-gnu-gcc
configure:4709: checking version of x86_64-pc-linux-gnu-gcc
configure:4719: result: 4.3.2, ok
configure:4730: checking for gnumake
configure:4760: result: no
configure:4730: checking for gmake
configure:4760: result: no
configure:4730: checking for make
configure:4746: found /usr/bin/make
configure:4757: result: make
configure:4772: checking version of make
configure:4782: result: 3.81, ok
configure:4794: checking for gnumsgfmt
configure:4824: result: no
configure:4794: checking for gmsgfmt
configure:4824: result: no
configure:4794: checking for msgfmt
configure:4810: found /usr/bin/msgfmt
configure:4821: result: msgfmt
configure:4836: checking version of msgfmt
configure:4846: result: 0.17, ok
configure:4857: checking for makeinfo
configure:4873: found /usr/bin/makeinfo
configure:4884: result: makeinfo
configure:4899: checking version of makeinfo
configure:4909: result: 4.11, ok
configure:4920: checking for sed
configure:4936: found /bin/sed
configure:4947: result: sed
configure:4962: checking version of sed
configure:4972: result: 4.1.5, ok
configure:4984: checking for autoconf
configure:5000: found /usr/bin/autoconf
configure:5011: result: autoconf
configure:5026: checking whether autoconf works
configure:5037: result: yes
configure:5087: checking whether ranlib is necessary
configure:5108: result: no
configure:5121: checking LD_LIBRARY_PATH variable
configure:5131: result: ok
configure:5145: checking whether GCC supports -static-libgcc
configure:5156: result: -static-libgcc
configure:5162: checking for bash
configure:5180: found /bin/bash
configure:5193: result: /bin/bash
configure:5268: checking for gawk
configure:5284: found /usr/bin/gawk
configure:5295: result: gawk
configure:5308: checking for perl
configure:5326: found /usr/bin/perl
configure:5339: result: /usr/bin/perl
configure:5353: checking for install-info
configure:5372: found /usr/sbin/install-info
configure:5385: result: /usr/sbin/install-info
configure:5395: checking for bison
configure:5414: found /usr/bin/bison
configure:5427: result: /usr/bin/bison
configure:5436: checking for signed size_t type
configure:5451: result: no
configure:5461: checking for libc-friendly stddef.h
configure:5495: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c: In function 'main':
conftest.c:20: warning: incompatible implicit declaration of built-in function 'abort'
configure:5501: $? = 0
configure:5516: result: yes
configure:5523: checking whether we need to use -P to assemble .S files
configure:5533: x86_64-pc-linux-gnu-gcc   -c conftest.S 1>&5
configure:5536: $? = 0
configure:5544: result: no
configure:5551: checking whether .text pseudo-op must be used
configure:5561: x86_64-pc-linux-gnu-gcc  -c conftest.s 1>&5
configure:5564: $? = 0
configure:5575: result: yes
configure:5579: checking for assembler global-symbol directive
configure:5592: x86_64-pc-linux-gnu-gcc  -c conftest.s 1>&5
configure:5595: $? = 0
configure:5603: result: .globl
configure:5616: checking for .set assembler directive
configure:5642: result: yes
configure:5651: checking for assembler .type directive prefix
configure:5667: x86_64-pc-linux-gnu-gcc  -c conftest.s 1>&5
configure:5670: $? = 0
configure:5678: result: @
configure:5687: checking for .symver assembler directive
configure:5704: result: yes
configure:5706: checking for ld --version-script
configure:5732: x86_64-pc-linux-gnu-gcc -g -O2  -shared
				-o conftest.so conftest.o
				-nostartfiles -nostdlib
				-Wl,--version-script,conftest.map
		       1>&5
configure:5735: $? = 0
configure:5750: result: yes
configure:5774: checking for .previous assembler directive
configure:5784: x86_64-pc-linux-gnu-gcc -c  conftest.s 1>&5
configure:5787: $? = 0
configure:5795: result: yes
configure:5833: checking for .protected and .hidden assembler directive
configure:5845: x86_64-pc-linux-gnu-gcc -c  conftest.s 1>&5
configure:5848: $? = 0
configure:5858: result: yes
configure:5862: checking whether __attribute__((visibility())) is supported
configure:5873: x86_64-pc-linux-gnu-gcc -Werror -S conftest.c -o conftest.s 1>&5
configure:5876: $? = 0
configure:5887: result: yes
configure:5897: checking for broken __attribute__((visibility()))
configure:5909: x86_64-pc-linux-gnu-gcc -Werror -S conftest.c -o conftest.s1>&5
configure:5912: $? = 0
configure:5921: result: no
configure:5930: checking for broken __attribute__((alias()))
configure:5945: x86_64-pc-linux-gnu-gcc -Werror -S conftest.c -o conftest.s 1>&5
configure:5948: $? = 0
configure:5958: result: no
configure:5967: checking whether to put _rtld_local into .sdata section
configure:5981: result: no
configure:5991: checking for .preinit_array/.init_array/.fini_array support
configure:6004: x86_64-pc-linux-gnu-gcc -g -O2   -o conftest conftest.c
		     -static -nostartfiles -nostdlib 1>&5
configure:6007: $? = 0
configure:6020: result: yes
configure:6028: checking for libunwind-support in compiler
configure:6045: result: no
configure:6055: checking for -z nodelete option
configure:6067: x86_64-pc-linux-gnu-gcc -g -O2  
		     -fPIC -shared -o conftest.so conftest.c
		     -nostartfiles -nostdlib
		     -Wl,--enable-new-dtags,-z,nodelete 1>&5
configure:6070: $? = 0
configure:6081: result: yes
configure:6084: checking for -z nodlopen option
configure:6096: x86_64-pc-linux-gnu-gcc -g -O2  
			-fPIC -shared -o conftest.so conftest.c
			-nostartfiles -nostdlib
			-Wl,--enable-new-dtags,-z,nodlopen 1>&5
configure:6099: $? = 0
configure:6110: result: yes
configure:6113: checking for -z initfirst option
configure:6125: x86_64-pc-linux-gnu-gcc -g -O2  
			-fPIC -shared -o conftest.so conftest.c
			-nostartfiles -nostdlib
			-Wl,--enable-new-dtags,-z,initfirst 1>&5
configure:6128: $? = 0
configure:6139: result: yes
configure:6144: checking for -z relro option
configure:6151: x86_64-pc-linux-gnu-gcc -v --help 2>&1|grep z relro 1>&5
  -z relro		Create RELRO program header
  -z relro		Create RELRO program header
configure:6154: $? = 0
configure:6158: x86_64-pc-linux-gnu-gcc -Wl,--verbose 2>&1|grep DATA_SEGMENT_RELRO_END 1>&5
  . = DATA_SEGMENT_RELRO_END (24, .);
configure:6161: $? = 0
configure:6168: result: yes
configure:6179: checking for -Bgroup option
configure:6190: x86_64-pc-linux-gnu-gcc -g -O2  
			      -fPIC -shared -o conftest.so conftest.c
			      -Wl,-Bgroup -nostdlib 1>&5
configure:6193: $? = 0
configure:6202: result: yes
configure:6206: checking for libgcc_s suffix
configure:6220: result: 
configure:6224: checking for --as-needed option
configure:6236: x86_64-pc-linux-gnu-gcc -g -O2  
			      -fPIC -shared -o conftest.so conftest.c
			      -lgcc_s -Wl,--as-needed
			      -nostdlib 1>&5
/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
configure:6239: $? = 1
configure:6248: result: no
configure:6253: checking whether --noexecstack is desirable for .S files
configure:6263: x86_64-pc-linux-gnu-gcc -g -O2 
		     -S -o conftest.s conftest.c 1>&5
configure:6266: $? = 0
configure:6271: x86_64-pc-linux-gnu-gcc -g -O2  -Wa,--noexecstack
		       -c -o conftest.o conftest.s 1>&5
configure:6274: $? = 0
configure:6283: result: yes
configure:6290: checking for -z combreloc
configure:6304: x86_64-pc-linux-gnu-gcc -g -O2  
			-fPIC -shared -o conftest.so conftest.c
			-nostdlib -nostartfiles
			-Wl,-z,combreloc 1>&5
configure:6307: $? = 0
configure:6320: result: yes
configure:6330: checking for -z execstack
configure:6342: x86_64-pc-linux-gnu-gcc -g -O2  
			      -fPIC -shared -o conftest.so conftest.c
			      -Wl,-z,execstack -nostdlib
			      1>&5
configure:6345: $? = 0
configure:6354: result: yes
configure:6358: checking for -fpie
configure:6369: x86_64-pc-linux-gnu-gcc -g -O2   -pie -fpie
			      -o conftest conftest.c 1>&5
/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld: Scrt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:6372: $? = 1
configure:6381: result: no
configure:6386: checking for --hash-style option
configure:6397: x86_64-pc-linux-gnu-gcc -g -O2  
			      -fPIC -shared -o conftest.so conftest.c
			      -Wl,--hash-style=both -nostdlib 1>&5
configure:6400: $? = 0
configure:6409: result: yes
configure:6414: checking for -fno-toplevel-reorder -fno-section-anchors
configure:6424: x86_64-pc-linux-gnu-gcc -g -O2  -S -fno-toplevel-reorder -fno-section-anchors
			    conftest.c 1>&5
configure:6427: $? = 0
configure:6436: result: yes
configure:6445: checking for -fstack-protector
configure:6456: x86_64-pc-linux-gnu-gcc -g -O2   -fstack-protector
			    -o conftest conftest.c 1>&5
/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:6459: $? = 1
configure:6468: result: no
configure:6472: checking for -fgnu89-inline
configure:6487: x86_64-pc-linux-gnu-gcc -g -O2  -S -std=gnu99 -fgnu89-inline
			    -o conftest.s conftest.c 1>&5
conftest.c:3: warning: return type defaults to 'int'
configure:6490: $? = 0
configure:6499: result: yes
configure:6569: checking whether cc puts quotes around section names
configure:6590: result: no
configure:6704: checking for assembler .weak directive
configure:6717: x86_64-pc-linux-gnu-gcc  -c conftest.s 1>&5
configure:6720: $? = 0
configure:6728: result: yes
configure:6775: checking whether CFI directives are supported
configure:6794: x86_64-pc-linux-gnu-gcc  -c conftest.s 1>&5
configure:6797: $? = 0
configure:6805: result: yes
configure:6814: checking for ld --no-whole-archive
configure:6827: x86_64-pc-linux-gnu-gcc -g -O2  
			    -nostdlib -nostartfiles -Wl,--no-whole-archive
			    -o conftest conftest.c 1>&5
configure:6830: $? = 0
configure:6838: result: yes
configure:6844: checking for gcc -fexceptions
configure:6857: x86_64-pc-linux-gnu-gcc -g -O2  
			    -nostdlib -nostartfiles -fexceptions
			    -o conftest conftest.c 1>&5
configure:6860: $? = 0
configure:6868: result: yes
configure:6934: checking for __builtin_expect
configure:6949: x86_64-pc-linux-gnu-gcc -g -O2   -nostdlib -nostartfiles
			    -o conftest conftest.c -lgcc >&5
/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status
configure:6952: $? = 1
configure:6960: result: no
configure:6969: checking for __builtin_memset
configure:6981: x86_64-pc-linux-gnu-gcc -O3 -S conftest.c -o - | fgrep memset > /dev/null
configure:6984: $? = 1
configure:6993: result: yes
configure:7002: checking for redirection of built-in functions
configure:7015: x86_64-pc-linux-gnu-gcc -O3 -S conftest.c -o - | fgrep my_strstr > /dev/null
configure:7018: $? = 0
configure:7027: result: yes
configure:7037: checking for __thread
configure:7046: x86_64-pc-linux-gnu-gcc -g -O2  -c conftest.c >&5
configure:7049: $? = 0
configure:7057: result: yes
configure:7070: checking for tls_model attribute
configure:7079: x86_64-pc-linux-gnu-gcc -g -O2  -S -Werror conftest.c >&5
configure:7082: $? = 0
configure:7090: result: yes
configure:7100: checking for libgd
configure:7130: x86_64-pc-linux-gnu-gcc -o conftest -g -O2     conftest.c  -lgd -lpng -lz -lm >&5
conftest.c:21:16: error: gd.h: No such file or directory
configure:7136: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <gd.h>
| int
| main ()
| {
| gdImagePng (0, 0)
|   ;
|   return 0;
| }
configure:7158: result: no
configure:7167: checking for is_selinux_enabled in -lselinux
configure:7202: x86_64-pc-linux-gnu-gcc -o conftest -g -O2   conftest.c -lselinux   >&5
/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:7208: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| 
| /* Override any GCC internal prototype to avoid an error.
|    Use char because int might match the return type of a GCC
|    builtin and then its argument prototype would still apply.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| char is_selinux_enabled ();
| int
| main ()
| {
| return is_selinux_enabled ();
|   ;
|   return 0;
| }
configure:7226: result: no
configure:7460: checking for grep that handles long lines and -e
configure:7534: result: /bin/grep
configure:7539: checking for egrep
configure:7617: result: /bin/grep -E
configure:7622: checking for ANSI C header files
configure:7652: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:20: error: stdlib.h: No such file or directory
conftest.c:23:20: error: string.h: No such file or directory
configure:7658: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdlib.h>
| #include <stdarg.h>
| #include <string.h>
| #include <float.h>
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:7786: result: no
configure:7810: checking for sys/types.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:23: error: sys/types.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <sys/types.h>
configure:7853: result: no
configure:7810: checking for sys/stat.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:22: error: sys/stat.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <sys/stat.h>
configure:7853: result: no
configure:7810: checking for stdlib.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:20: error: stdlib.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <stdlib.h>
configure:7853: result: no
configure:7810: checking for string.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:20: error: string.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <string.h>
configure:7853: result: no
configure:7810: checking for memory.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:20: error: memory.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <memory.h>
configure:7853: result: no
configure:7810: checking for strings.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:21: error: strings.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <strings.h>
configure:7853: result: no
configure:7810: checking for inttypes.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:22: error: inttypes.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <inttypes.h>
configure:7853: result: no
configure:7810: checking for stdint.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:20: error: stdint.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <stdint.h>
configure:7853: result: no
configure:7810: checking for unistd.h
configure:7831: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:55:20: error: unistd.h: No such file or directory
configure:7837: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| 
| #include <unistd.h>
configure:7853: result: no
configure:7865: checking for long double
configure:7895: x86_64-pc-linux-gnu-gcc -c -g -O2  conftest.c >&5
conftest.c:21:19: error: stdio.h: No such file or directory
configure:7901: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| typedef long double ac__type_new_;
| int
| main ()
| {
| if ((ac__type_new_ *) 0)
|   return 0;
| if (sizeof (ac__type_new_))
|   return 0;
|   ;
|   return 0;
| }
configure:7916: result: no
configure:7923: checking size of long double
configure:8225: x86_64-pc-linux-gnu-gcc -o conftest -g -O2   conftest.c  >&5
conftest.c:21:19: error: stdio.h: No such file or directory
conftest.c:58:20: error: stdlib.h: No such file or directory
conftest.c: In function 'main':
conftest.c:63: error: 'FILE' undeclared (first use in this function)
conftest.c:63: error: (Each undeclared identifier is reported only once
conftest.c:63: error: for each function it appears in.)
conftest.c:63: error: 'f' undeclared (first use in this function)
conftest.c:71: warning: incompatible implicit declaration of built-in function 'fprintf'
conftest.c:78: warning: incompatible implicit declaration of built-in function 'fprintf'
configure:8228: $? = 1
configure: program exited with status 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #ifdef HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #ifdef HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #ifdef STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # ifdef HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #ifdef HAVE_STRING_H
| # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #ifdef HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #ifdef HAVE_INTTYPES_H
| # include <inttypes.h>
| #endif
| #ifdef HAVE_STDINT_H
| # include <stdint.h>
| #endif
| #ifdef HAVE_UNISTD_H
| # include <unistd.h>
| #endif
|    typedef long double ac__type_sizeof_;
| static long int longval () { return (long int) (sizeof (ac__type_sizeof_)); }
| static unsigned long int ulongval () { return (long int) (sizeof (ac__type_sizeof_)); }
| #include <stdio.h>
| #include <stdlib.h>
| int
| main ()
| {
| 
|   FILE *f = fopen ("conftest.val", "w");
|   if (! f)
|     return 1;
|   if (((long int) (sizeof (ac__type_sizeof_))) < 0)
|     {
|       long int i = longval ();
|       if (i != ((long int) (sizeof (ac__type_sizeof_))))
| 	return 1;
|       fprintf (f, "%ld\n", i);
|     }
|   else
|     {
|       unsigned long int i = ulongval ();
|       if (i != ((long int) (sizeof (ac__type_sizeof_))))
| 	return 1;
|       fprintf (f, "%lu\n", i);
|     }
|   return ferror (f) || fclose (f) != 0;
| 
|   ;
|   return 0;
| }
configure:8260: result: 0
configure:8292: result: running configure fragment for sysdeps/x86_64/elf
configure:6: checking for x86-64 TLS support
configure:25: x86_64-pc-linux-gnu-gcc -c -g -O2 conftest.s 1>&5
configure:28: $? = 0
configure:36: result: yes
configure:8292: result: running configure fragment for nptl/sysdeps/pthread
configure:27: checking for forced unwind support
configure:56: x86_64-pc-linux-gnu-gcc -o conftest -g -O2   conftest.c  >&5
/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:62: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "GNU C Library"
| #define PACKAGE_TARNAME "c-library"
| #define PACKAGE_VERSION "(see version.h)"
| #define PACKAGE_STRING "GNU C Library (see version.h)"
| #define PACKAGE_BUGREPORT "glibc"
| #define ASM_GLOBAL_DIRECTIVE .globl
| #define HAVE_ASM_SET_DIRECTIVE 1
| #define ASM_TYPE_DIRECTIVE_PREFIX @
| #define DO_VERSIONING 1
| #define HAVE_ASM_PREVIOUS_DIRECTIVE 1
| #define HAVE_Z_COMBRELOC 1
| #define NO_UNDERSCORES 1
| #define HAVE_ASM_WEAK_DIRECTIVE 1
| #define HAVE_ASM_CFI_DIRECTIVES 1
| #define HAVE_BUILTIN_MEMSET 1
| #define HAVE_BUILTIN_REDIRECTION 1
| #define HAVE___THREAD 1
| #define HAVE_TLS_MODEL_ATTRIBUTE 1
| #define SIZEOF_LONG_DOUBLE 0
| #define HAVE_TLS_SUPPORT 1
| #define PI_STATIC_AND_HIDDEN 1
| /* end confdefs.h.  */
| #include <unwind.h>
| int
| main ()
| {
| 
| struct _Unwind_Exception exc;
| struct _Unwind_Context *context;
| _Unwind_GetCFA (context)
|   ;
|   return 0;
| }
configure:79: result: no
configure:150: error: forced unwind support is required

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=powerpc64-unknown-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
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
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=set
ac_cv_env_host_alias_value=x86_64-pc-linux-gnu
ac_cv_env_target_alias_set=set
ac_cv_env_target_alias_value=x86_64-pc-linux-gnu
ac_cv_header_inttypes_h=no
ac_cv_header_memory_h=no
ac_cv_header_stdc=no
ac_cv_header_stdint_h=no
ac_cv_header_stdlib_h=no
ac_cv_header_string_h=no
ac_cv_header_strings_h=no
ac_cv_header_sys_stat_h=no
ac_cv_header_sys_types_h=no
ac_cv_header_unistd_h=no
ac_cv_host=x86_64-pc-linux-gnu
ac_cv_lib_selinux_is_selinux_enabled=no
ac_cv_objext=o
ac_cv_path_BASH_SHELL=/bin/bash
ac_cv_path_BISON=/usr/bin/bison
ac_cv_path_EGREP='/bin/grep -E'
ac_cv_path_GREP=/bin/grep
ac_cv_path_INSTALL_INFO=/usr/sbin/install-info
ac_cv_path_PERL=/usr/bin/perl
ac_cv_path_PWD_P=/bin/pwd
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AS=/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as
ac_cv_prog_AUTOCONF=autoconf
ac_cv_prog_AWK=gawk
ac_cv_prog_BUILD_CC=gcc
ac_cv_prog_CC=x86_64-pc-linux-gnu-gcc
ac_cv_prog_CPP='x86_64-pc-linux-gnu-gcc -E'
ac_cv_prog_LD=/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld
ac_cv_prog_MAKE=make
ac_cv_prog_MAKEINFO=makeinfo
ac_cv_prog_MSGFMT=msgfmt
ac_cv_prog_SED=sed
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_cc_c89=no
ac_cv_prog_cc_g=yes
ac_cv_prog_cxx_g=yes
ac_cv_sizeof_long_double=0
ac_cv_type_long_double=no
libc_cv_Bgroup=yes
libc_cv_as_needed=no
libc_cv_as_noexecstack=yes
libc_cv_asm_cfi_directives=yes
libc_cv_asm_global_directive=.globl
libc_cv_asm_previous_directive=yes
libc_cv_asm_protected_directive=yes
libc_cv_asm_set_directive=yes
libc_cv_asm_symver_directive=yes
libc_cv_asm_type_prefix=@
libc_cv_asm_underscores=no
libc_cv_asm_weak_directive=yes
libc_cv_autoconf_works=yes
libc_cv_broken_alias_attribute=no
libc_cv_broken_visibility_attribute=no
libc_cv_cc_with_libunwind=no
libc_cv_dot_text=.text
libc_cv_fno_toplevel_reorder=yes
libc_cv_forced_unwind=no
libc_cv_fpie=no
libc_cv_friendly_stddef=yes
libc_cv_gcc___thread=yes
libc_cv_gcc_builtin_expect=no
libc_cv_gcc_builtin_memset=yes
libc_cv_gcc_builtin_redirection=yes
libc_cv_gcc_exceptions=yes
libc_cv_gcc_static_libgcc=-static-libgcc
libc_cv_gcc_tls_model_attr=yes
libc_cv_gcc_unwind_find_fde=no
libc_cv_gnu89_inline=-fgnu89-inline
libc_cv_hashstyle=yes
libc_cv_have_bash2=yes
libc_cv_have_ksh=yes
libc_cv_have_sdata_section=no
libc_cv_have_section_quotes=no
libc_cv_idn=no
libc_cv_initfini_array=yes
libc_cv_ld_no_whole_archive=yes
libc_cv_ld_version_script_option=yes
libc_cv_libgcc_s_suffix=
libc_cv_need_minus_P=no
libc_cv_prog_as_gnu=yes
libc_cv_prog_ld_gnu=yes
libc_cv_ranlib_necessary=no
libc_cv_signed_size_t=no
libc_cv_ssp=no
libc_cv_sysconfdir='${prefix}/etc'
libc_cv_visibility_attribute=yes
libc_cv_weak_symbols=yes
libc_cv_x86_64_tls=yes
libc_cv_z_combreloc=yes
libc_cv_z_execstack=yes
libc_cv_z_initfirst=yes
libc_cv_z_nodelete=yes
libc_cv_z_nodlopen=yes
libc_cv_z_relro=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

AR='/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ar'
AS='/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/as'
ASFLAGS_config=' -Wa,--noexecstack'
AUTOCONF='autoconf'
AWK='gawk'
BASH_SHELL='/bin/bash'
BISON='/usr/bin/bison'
BUILD_CC='gcc'
CC='x86_64-pc-linux-gnu-gcc'
CFLAGS='-g -O2'
CPP='x86_64-pc-linux-gnu-gcc -E'
CPPFLAGS=''
CXX='g++'
CXXFLAGS='-g -O2'
CXX_SYSINCLUDES=''
DEFINES=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='/bin/grep -E'
GREP='/bin/grep'
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_INFO='/usr/sbin/install-info'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
KSH='/bin/bash'
LD='/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/ld'
LDFLAGS=''
LIBGD='no'
LIBOBJS=''
LIBS=''
LN_S='ln -s'
LTLIBOBJS=''
MAKE='make'
MAKEINFO='makeinfo'
MIG=''
MSGFMT='msgfmt'
OBJDUMP='/usr/local/lib/gcc/x86_64-pc-linux-gnu/4.3.2/../../../../x86_64-pc-linux-gnu/bin/objdump'
OBJEXT='o'
PACKAGE_BUGREPORT='glibc'
PACKAGE_NAME='GNU C Library'
PACKAGE_STRING='GNU C Library (see version.h)'
PACKAGE_TARNAME='c-library'
PACKAGE_VERSION='(see version.h)'
PATH_SEPARATOR=':'
PERL='/usr/bin/perl'
PWD_P='/bin/pwd'
RANLIB=':'
RELEASE=''
SED='sed'
SHELL='/bin/bash'
SYSINCLUDES=''
VERSION=''
VERSIONING='yes'
ac_ct_CC=''
ac_ct_CXX='g++'
add_on_subdirs=''
add_ons='nptl'
all_warnings=''
base_machine='x86_64'
bindir='${exec_prefix}/bin'
bindnow='no'
bounded='no'
build='powerpc64-unknown-linux-gnu'
build_alias=''
build_cpu='powerpc64'
build_os='linux-gnu'
build_vendor='unknown'
cross_compiling='maybe'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
elf='yes'
enable_check_abi='no'
exceptions='-fexceptions'
exec_prefix='NONE'
fno_unit_at_a_time='-fno-toplevel-reorder -fno-section-anchors'
force_install='yes'
have_libaudit=''
have_libcap=''
have_selinux='no'
host='x86_64-pc-linux-gnu'
host_alias='x86_64-pc-linux-gnu'
host_cpu='x86_64'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
ldd_rewrite_script='no'
libc_cv_Bgroup='yes'
libc_cv_as_needed='no'
libc_cv_cc_with_libunwind='no'
libc_cv_forced_unwind='no'
libc_cv_fpie='no'
libc_cv_gcc_static_libgcc='-static-libgcc'
libc_cv_gcc_unwind_find_fde='no'
libc_cv_gnu89_inline='-fgnu89-inline'
libc_cv_hashstyle='yes'
libc_cv_have_bash2='yes'
libc_cv_have_initfini=''
libc_cv_have_ksh='yes'
libc_cv_libgcc_s_suffix=''
libc_cv_localedir=''
libc_cv_rootsbindir=''
libc_cv_slibdir=''
libc_cv_ssp='no'
libc_cv_sysconfdir='${prefix}/etc'
libc_cv_z_combreloc='yes'
libc_cv_z_execstack='yes'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mach_interface_list=''
mandir='${datarootdir}/man'
no_whole_archive='-Wl,--no-whole-archive'
nopic_initfini=''
old_glibc_headers=''
oldest_abi='default'
oldincludedir='/usr/include'
omitfp='no'
pdfdir='${docdir}'
pic_default=''
prefix='/usr/local'
profile='no'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
shared='default'
sharedstatedir='${prefix}/com'
sizeof_long_double='0'
static='yes'
static_nss='no'
subdirs=' '
submachine=''
sysconfdir='${prefix}/etc'
sysdeps_add_ons=' nptl'
sysnames=' sysdeps/x86_64/elf nptl/sysdeps/unix/sysv/linux/x86_64 sysdeps/unix/sysv/linux/x86_64 sysdeps/unix/sysv/linux/wordsize-64 nptl/sysdeps/unix/sysv/linux nptl/sysdeps/pthread sysdeps/pthread sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet nptl/sysdeps/unix/sysv sysdeps/unix/sysv sysdeps/unix/x86_64 nptl/sysdeps/unix sysdeps/unix sysdeps/posix sysdeps/x86_64/fpu nptl/sysdeps/x86_64 sysdeps/x86_64 sysdeps/wordsize-64 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic'
target_alias='x86_64-pc-linux-gnu'
uname_release=''
uname_sysname=''
uname_version=''
use_ldconfig='no'
with_cvs='yes'
with_fp='yes'
xcoff='no'

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "GNU C Library"
#define PACKAGE_TARNAME "c-library"
#define PACKAGE_VERSION "(see version.h)"
#define PACKAGE_STRING "GNU C Library (see version.h)"
#define PACKAGE_BUGREPORT "glibc"
#define ASM_GLOBAL_DIRECTIVE .globl
#define HAVE_ASM_SET_DIRECTIVE 1
#define ASM_TYPE_DIRECTIVE_PREFIX @
#define DO_VERSIONING 1
#define HAVE_ASM_PREVIOUS_DIRECTIVE 1
#define HAVE_Z_COMBRELOC 1
#define NO_UNDERSCORES 1
#define HAVE_ASM_WEAK_DIRECTIVE 1
#define HAVE_ASM_CFI_DIRECTIVES 1
#define HAVE_BUILTIN_MEMSET 1
#define HAVE_BUILTIN_REDIRECTION 1
#define HAVE___THREAD 1
#define HAVE_TLS_MODEL_ATTRIBUTE 1
#define SIZEOF_LONG_DOUBLE 0
#define HAVE_TLS_SUPPORT 1
#define PI_STATIC_AND_HIDDEN 1

configure: exit 1
```

Analysis of the log shows that crt1.o is missing, but I apparently have it:

```
$ whereis crt1

crt1: /usr/lib/crt1.o /usr/lib64/crt1.o
```

Any help in resolving this issue is greatly appreciated.

---

