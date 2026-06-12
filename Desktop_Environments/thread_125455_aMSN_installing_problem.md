---
title: "aMSN installing problem"
date: 2006-02-04
forum: Desktop Environments
---

### Post by baseball116 on 2006-02-04
I've recently just installed Ubuntu on my computer and I wanted to install aMSN. I've installed gcc and tcl/tk are installed, but when i type ./configure I get this error message:

checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

config.log looks like this (shortened):

## ----------- ##
## Core tests. ##
## ----------- ##

configure:1328: checking for wish
configure:1346: found /usr/bin/wish
configure:1358: result: /usr/bin/wish
configure:1461: checking for gcc
configure:1477: found /usr/bin/gcc
configure:1487: result: gcc
configure:1731: checking for C compiler version
configure:1734: gcc --version </dev/null >&5
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:1737: $? = 0
configure:1739: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
configure:1742: $? = 0
configure:1744: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1747: $? = 1
configure:1770: checking for C compiler default output file name
configure:1773: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1776: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1815: error: C compiler cannot create executables

Any help would be appreciated, thanks :)

---

### Post by baseball116 on 2006-02-04
bump

---

### Post by cutOff on 2006-02-04
I think you need to install build-essential package

```
sudo aptitude install build-essential
```

---

### Post by baseball116 on 2006-02-04
Thank you! That's exactly what I had to do.

---

