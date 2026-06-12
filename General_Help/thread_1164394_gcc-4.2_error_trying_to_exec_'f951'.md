---
title: "gcc-4.2: error trying to exec 'f951':"
date: 2009-05-19
forum: General Help
---

### Post by walli on 2009-05-19
Hi forum.

I'm trying to compile a fortrun file. I get following error message after typing: gcc-4.2 scopy.f:
gcc-4.2: error trying to exec 'f951': execvp: No such file or directory

The fortrun file is ok, because I compiled it on other systems before.
My gcc version: gcc-4.2 -v:
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

The work-arounds in thread: 			 			[g77 won't compile]("http://ubuntuforums.org/showthread.php?t=882382&highlight=file+directory+execvp%3A") : [http://ubuntuforums.org/showthread.php?t=882382&highlight=file+directory+execvp%3A](http://ubuntuforums.org/showthread.php?t=882382&highlight=file+directory+execvp%3A) doesn't work.

Thanks for your help
walli

---

### Post by walli on 2009-05-19
> **walli said:**
> Hi forum.

I'm trying to compile a fortrun file. I get following error message after typing: gcc-4.2 scopy.f:
gcc-4.2: error trying to exec 'f951': execvp: No such file or directory

The fortrun file is ok, because I compiled it on other systems before.
My gcc version: gcc-4.2 -v:
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

The work-arounds in thread:                          [g77 won't compile]("http://ubuntuforums.org/showthread.php?t=882382&highlight=file+directory+execvp%3A") : [http://ubuntuforums.org/showthread.php?t=882382&highlight=file+directory+execvp%3A](http://ubuntuforums.org/showthread.php?t=882382&highlight=file+directory+execvp%3A) doesn't work.

Thanks for your help
walli

Hi all again.

I downloaded gcc-4.4.0 source package from [http://gcc.gnu.org/](http://gcc.gnu.org/)  and build it on ny machine. It works now. But I  hope there is a more conviniend solution for this problem.

Best regards
walli
[U]
[/U]

---

### Post by alex.kvasov on 2011-03-16
Hi, everybody!

I also tried to compile fortran file using gcc. I used
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5).
And I got the following message:
gcc: error trying to exec 'f951': execvp: No such file or directory
I've spent some time to understand what is insufficient for gcc to compile fortran file...
So one has to install gfortran (it was gfortran-4.4 for my case). After this compilation becomes to work fine.

I hope it helps somebody sometimes.

---

### Post by andyheld on 2012-01-31
Suprisingly it did!
Thanks.

---

### Post by oldos2er on 2012-01-31
Closed, necromancy.

---

