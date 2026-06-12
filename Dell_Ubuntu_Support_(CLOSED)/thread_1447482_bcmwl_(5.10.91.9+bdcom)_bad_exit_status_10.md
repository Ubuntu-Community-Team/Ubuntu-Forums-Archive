---
title: "bcmwl (5.10.91.9+bdcom) bad exit status: 10"
date: 2010-04-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pcstalljr on 2010-04-05
Hey guys, i have a weird problem, well its only weird because i had it working 4 days ago before a system re-install.

ok so heres the deal, I got the urge to try ubuntu (again) about a week ago and upgraded to Linux kernel 2.6.33 so i can use the new b43 driver for th 14e4:4315 version of my Broadcom bcm4312 rev 01 wifi card (im on a dell studio 1555). and everything went fine! About 3 days later I decided to wipe it so i could put it on my larger partition of my drive, and i did the same install, but when i try to install the generic linux headers for Linux kernel 2.6.33 i get this error.

```
 *  bcmwl (5.10.91.9+bdcom)...
bcmwl (5.10.91.9+bdcom): Installing module.
.......(bad exit status: 10)

```

the compiler error is: (from /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/make.log)

```
DKMS make.log for bcmwl-5.10.91.9+bdcom for kernel 2.6.33-020633-generic (i686)
Sun Apr  4 23:06:43 MDT 2010
make: Entering directory `/usr/src/linux-headers-2.6.33-020633-generic'
  LD      /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_free’:
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.c:702: error: implicit declaration of function ‘schedule’
make[1]: *** [/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.33-020633-generic'
```

the thing that confuses me, is that i installed this same package 3 days before and it was working find. any ideas anyone?

---

