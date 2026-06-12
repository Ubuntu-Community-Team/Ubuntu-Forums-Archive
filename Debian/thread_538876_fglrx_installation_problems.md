---
title: "fglrx installation problems"
date: 2007-08-30
forum: Debian
---

### Post by super.rad on 2007-08-30
Im trying to install the fglrx driver on lenny using the following guide [http://forums.debian.net/viewtopic.php?t=17776](http://forums.debian.net/viewtopic.php?t=17776) but when i get to
```
m-a a-i fglrx
```
it says
```
Build of the package fglrx-kernel-src failed
```
and it saves a logfile which says
```
dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
		cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
	fi
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \
		mv /usr/src/modules/fglrx/debian/postinst /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.21-2-486.postinst; \
	fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /lib/modules/2.6.21-2-486/build SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.21-2-486'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c: In function '__ke_pci_find_device':
/usr/src/modules/fglrx/firegl_public.c:1886: warning: 'pci_find_device' is deprecated (declared at include/linux/pci.h:470)
/usr/src/modules/fglrx/firegl_public.c: In function '__ke_request_irq':
/usr/src/modules/fglrx/firegl_public.c:2829: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:5306: warning: 'kmem_cache_t' is deprecated
/usr/src/modules/fglrx/firegl_public.c:484: warning: 'firegl_smp_func_parameter_wrap' defined but not used
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol 'paravirt_ops'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.21-2-486'
make: *** [build] Error 2
```
If someone could tell me what im doing wrong/missing i can finally get the driver installed?

---

### Post by shae on 2007-09-08
It appears that the kernel in Lenny is compiled with paravirtualization support.  This is known to cause problems with compiling the fglrx kernel module.  Make sure you are using the latest drivers from AMD/ATI (the ones from the site).  If the problem persists, you may have to recompile your kernel without paravirtualization.

---

### Post by super.rad on 2007-09-13
thanks but i ended up moving to sid and it had a newer kernel so tried again and it worked fine

---

### Post by angryfirelord on 2007-09-13
This is an issue with kernels 2.6.19 through 2.6.21 on the i386. AMD64 doesn't suffer from this.

---

