---
title: "Cannot configure alsa"
date: 2006-10-07
forum: Desktop Environments
---

### Post by PerH on 2006-10-07
Hi I'm currently trying to compile a new kernel. Before I did the compilation I thought I should install a newer version of the alsa driver. So I downloaded the latest release from the homepage and got this error while doing the configuring:

```

per@pers:/tmp/alsa-driver-1.0.13$ ./configure --with-kernel=/usr/src/linux-2.6.18-ck
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /tmp/alsa-driver-1.0.13
checking cross compile...
checking for directory with kernel source... /usr/src/linux-2.6.18-ck
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux-2.6.18-ck/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.17-ck1/source).
per@pers:/tmp/alsa-driver-1.0.13$

```

How do I solve this?

---

