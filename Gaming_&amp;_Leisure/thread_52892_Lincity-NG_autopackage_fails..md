---
title: "Lincity-NG autopackage fails."
date: 2005-07-29
forum: Gaming &amp; Leisure
---

### Post by dud on 2005-07-29
Trying to install [http://lincity-ng.berlios.de/wiki/index.php/Main_Page](http://lincity-ng.berlios.de/wiki/index.php/Main_Page), by the autopackage over at [http://download.berlios.de/lincity-ng/lincity-ng-1.0.1.x86.package](http://download.berlios.de/lincity-ng/lincity-ng-1.0.1.x86.package) fails with the following:

> # Preparing: LinCity-NG
# Checking for required C library versions ... failed
# FAIL:
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: GLIBC_2.0.
#
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
#
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL:  Unable to prepare package LinCity-NG.
 

Some system information might be useful ;)
>  
uname -a
Linux shadowplay 2.6.10-5-amd64-generic #1 Fri May 20 14:04:49 UTC 2005 x86_64 GNU/Linux
 
>  
gcc -v
Reading specs from /usr/lib/gcc/x86_64-linux/3.4.4/specs
Configured with: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --libexecdir=/usr/lib --with-gxx-include-dir=/usr/include/c++/3.4 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --program-suffix=-3.4 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --disable-werror x86_64-linux
Thread model: posix
gcc version 3.4.4 20050209 (prerelease) (Debian 3.4.3-9ubuntu4)
 
>  
ldd --version
ldd (GNU libc) 2.3.2
Copyright (C) 2003 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
 
>  
package version
autopackage 1.0.5, (c) 2002-2005 the autopackage developers


---

