---
title: "compiling problems (aclocal)"
date: 2005-10-25
forum: Desktop Environments
---

### Post by luna6 on 2005-10-25
Hello I am trying to compile kcheckgmail and running into this problem, after I run the "make" command and have had this error for a few other programs as well. How do i fix this error?

make[2]: Entering directory `/SharedLocker/downloads/kcheckgmail-0.5.4/src'
 cd .. && /bin/sh /SharedLocker/downloads/kcheckgmail-0.5.4/admin/missing --run automake-1.9 --gnu  src/Makefile
configure.in:43: version mismatch.  This is Automake 1.9.5,
configure.in:43: but the definition used by this AM_INIT_AUTOMAKE
configure.in:43: comes from Automake 1.9.2.  You should recreate
configure.in:43: aclocal.m4 with aclocal and run automake again.
make[2]: *** [Makefile.in] Error 1
make[2]: Leaving directory `/SharedLocker/downloads/kcheckgmail-0.5.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/SharedLocker/downloads/kcheckgmail-0.5.4'
make: *** [all] Error 2

---

