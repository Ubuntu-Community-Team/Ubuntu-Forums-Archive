---
title: "PerlMagick on ubuntu"
date: 2006-01-04
forum: Desktop Environments
---

### Post by bobinski on 2006-01-04
Although I am new to ubuntu I have (a very long time ago) used PerlMagick on Windows.  I started with the default installation and added ImageMagick.  There didn't seem to be a package for PerlMagick so I downloaded the source file and extracted PerlMagick from that.  I then tried to do :-

perl Makefile.PL
make

It first of all couldn't find the comand cc so I installed gcc but now fail to find header files.  Even after installing linux-headers etc I'm getting the failure :-

In file included from Magick.xs:60:
/usr/lib/perl/5.8/CORE/perl.h:382:24: error: sys/types.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:413:19: error: ctype.h: No such file or directory
...

I don't see where these files should be or which package should include them.

Any help welcomed.

---

### Post by schilcha on 2006-01-04
[QUOTE=bobinski]
/usr/lib/perl/5.8/CORE/perl.h:382:24: error: sys/types.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:413:19: error: ctype.h: No such file or directory
[/QUOTE]

On my system the package "libc6-dev" suppliedt /usr/include/sys/types.h and /usr/include/ctype.h. I guess this is what you need.

---

### Post by bobinski on 2006-01-05
Excellent, that is indeed the package required.  Thanks.

---

