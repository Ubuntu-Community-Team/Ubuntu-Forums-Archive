---
title: "Problems compiling Glibc"
date: 2008-12-04
forum: General Help
---

### Post by dianming on 2008-12-04
Hey everyone,

   I've been using Linux for a few years now, having gone through all the major distributions (openSuSE, Red Hat, Fedora, and now mostly Ubuntu), and I'm trying to expand a little more by building some packages from source.

    I've run into a funny error, though, when trying to compile glibc 2.8.x or 2.9.x(Latest). The config runs flawlessly, but when I run the make command I get this error well into the compile:

../misc/syslog.c: In function ‘__vsyslog_chk’:
../misc/syslog.c:123: sorry, unimplemented: inlining failed in call to ‘syslog’: function body not available
../misc/syslog.c:155: sorry, unimplemented: called from here
make[2]: *** [/mnt/adm/sources/glibc-build/misc/syslog.o] Error 1
make[2]: Leaving directory `/mnt/adm/sources/glibc-src/misc'
make[1]: *** [misc/subdir_lib] Error 2
make[1]: Leaving directory `/mnt/adm/sources/glibc-src'
make: *** [all] Error 2

    So `_vsyslog_chk' isn't implemented? Is it a deprecated function? 

    I'm running Ibex 8.10 with all the updates, an Intel Dual-Core 6300 @ 1.86 GHz, 1.8 GB ram. 

    Anything I can do to get around this?

---

### Post by binbash on 2008-12-04
what was your configure prefix?

---

### Post by dianming on 2008-12-04
I'm following the Linux From Source manual, so it's at /mnt/adm/tools. Would that change anything?

---

### Post by thotmos on 2009-02-02
Hi dianming, have you resolved your problem? I'm having the same trouble.

---

### Post by frischi on 2009-02-16
try adding -D_FORTIFY_SOURCE to your CFLAGS I always use some optimisation too
sry for that -U_FORTIFY_SOURCE of course not -D_FORTIFY_SOURCE

```
export CFLAGS="-O2 -D_FORTIFY_SOURCE" <- Wrong
export CFLAGS="-O2 -U_FORTIFY_SOURCE" <- Right"
```

that's at least what i got from the glibc [mailing-list]("http://sourceware.org/ml/libc-help/2009-02/msg00023.html") and it worked for me.

I'm not exactly sure what fortify does. Here's what Ubuntu says about it
> First enabled in Ubuntu 8.10. Provides compile-time best-practices errors for certain libc functions, and provides run-time checks of buffer lengths and memory regions. Only activated when compiled with -O2 or higher. Most problems are related to common unsafe uses of certain libc functions.
from: [https://wiki.ubuntu.com/CompilerFlags]("https://wiki.ubuntu.com/CompilerFlags")

They use D_FORTIFY_SOURCE=2 instead of only D_FORTIFY_SOURCE. I don't know if there is a big difference.

---

### Post by pakje on 2009-02-22
Hi, I got it fixed by using the following flags

CFLAGS=-O2 -U_FORTIFY_SOURCE -march=i486 -mtune=native -fno-stack-protector

---

### Post by tomdkat on 2009-07-11
Thanks for the info on the compiler flags as they solved my build problems too!  :)

I ended up going with:

$ CFLAGS="-O2 -U_FORTIFY_SOURCE -fno-stack-protector" ../glibc-2.10.1/configure --prefix=/usr
....
$ make

and everything compiled without issue.  :)

Thanks!

Peace...

---

### Post by ryadav on 2009-07-16
$ uname -a
Linux K32x2 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Trying to build LFS, I am getting a different error for glic 2.10.1, I've tried the provided suggestions and it doesn't work. I get the following error by make:

mawk: scripts/gen-sorted.awk: line 19: syntax error at or near ]
mawk: scripts/gen-sorted.awk: line 19: runaway regular expression /, "", subd ...
make[1]: Leaving directory `/mnt/custom_linux/sources/glibc-2.10.1'
make[1]: Entering directory `/mnt/custom_linux/sources/glibc-2.10.1'
mawk -f scripts/gen-sorted.awk \
               -v subdirs='csu assert ctype locale intl catgets math setjmp signal stdlib stdio-common libio malloc string wcsmbs time dirent grp pwd posix io termios resource misc socket sysvipc gmon gnulib iconv iconvdata wctype manual shadow gshadow po argp crypt nss localedata timezone rt conform debug  dlfcn elf' \
               -v srcpfx='' \
               nptl/sysdeps/pthread/Subdirs sysdeps/unix/inet/Subdirs sysdeps/unix/Subdirs assert/Depend intl/Depend catgets/Depend stdlib/Depend stdio-common/Depend libio/Depend malloc/Depend string/Depend wcsmbs/Depend time/Depend posix/Depend iconvdata/Depend nss/Depend localedata/Depend rt/Depend debug/Depend > /mnt/custom_linux/sources/build/sysd-sorted-tmp
mawk: scripts/gen-sorted.awk: line 19: regular expression compile failed (bad class -- [], [^] or [)
/[^
mawk: scripts/gen-sorted.awk: line 19: syntax error at or near ]
mawk: scripts/gen-sorted.awk: line 19: runaway regular expression /, "", subd ...
rm -f /mnt/custom_linux/sources/build/stamp.o; > /mnt/custom_linux/sources/build/stamp.o
rm -f /mnt/custom_linux/sources/build/stamp.os; > /mnt/custom_linux/sources/build/stamp.os
rm -f /mnt/custom_linux/sources/build/stamp.oS; > /mnt/custom_linux/sources/build/stamp.oS
cd /mnt/custom_linux/sources/build && /mnt/custom_linux/tools/bin/../lib/gcc/i686-lfs-linux-gnu/4.4.0/../../../../i686-lfs-linux-gnu/bin/ar cruv libc.a `cat stamp.o`
: /mnt/custom_linux/sources/build/libc.a
cd /mnt/custom_linux/sources/build && /mnt/custom_linux/tools/bin/../lib/gcc/i686-lfs-linux-gnu/4.4.0/../../../../i686-lfs-linux-gnu/bin/ar cruv libc_pic.a `cat stamp.os`
: /mnt/custom_linux/sources/build/libc_pic.a
cd /mnt/custom_linux/sources/build && /mnt/custom_linux/tools/bin/../lib/gcc/i686-lfs-linux-gnu/4.4.0/../../../../i686-lfs-linux-gnu/bin/ar cruv libc_nonshared.a `cat stamp.oS`
: /mnt/custom_linux/sources/build/libc_nonshared.a
make[1]: *** No rule to make target `/mnt/custom_linux/sources/build/Versions.all', needed by `/mnt/custom_linux/sources/build/abi-versions.h'.  Stop.
make[1]: Leaving directory `/mnt/custom_linux/sources/glibc-2.10.1'
make: *** [all] Error 2

--
Kind Regards,
Rajinder Yadav

---

### Post by ryadav on 2009-07-16
It seems I was missing a few build essentials, got that corrected.

---

