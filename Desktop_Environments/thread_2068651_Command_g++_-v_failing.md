---
title: "Command g++ -v failing"
date: 2012-10-09
forum: Desktop Environments
---

### Post by rawat on 2012-10-09
Hi all,

When I run ```
g++ -v 
```, I get below error

> 
gcc-opt: Failed to open /CurrentlyBuilding
ccache: FATAL: /usr/bin/g++-4.0.gcc-opt: execv returned (No such file or directory)
Whereas ```
gcc -v
``` runs fine.

Please tell me how to resolve it.

Ubuntu version : 11.04

Thanks,
Rawat

---

### Post by rawat on 2012-10-12
Anyone??:(

---

### Post by spjackson on 2012-10-12
> **rawat said:**
> 
gcc-opt: Failed to open /CurrentlyBuilding
ccache: FATAL: /usr/bin/g++-4.0.gcc-opt: execv returned (No such file or directory)

g++ 4.0 is very old, much older than Ubuntu 11.04. 4.1 was released in 2006, so I don't know where a reference to 4.0 is coming from.

You probably need to install g++. I suggest you do this by installing the build-essential package.

---

### Post by lee170 on 2012-10-12
In 12.04 I installed the g++ package from the Ubuntu Software Center.  Everything works fine:

host:~$ g++ -v
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.6/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.3-1ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 

Not sure if things are the same in 11.04 but maybe this will help.

---

### Post by rawat on 2012-10-13
Thanks spjackson.

Updating g++ worked. 

@lee170 . Yeah your are right. Same results I also found on 12.04

---

