---
title: "EXTRA_CFLAGS error"
date: 2009-06-15
forum: General Help
---

### Post by InvisibleMan on 2009-06-15
While compiling, ("make install" from an Intel driver download), the following error occurred:

make -C /lib/modules/2.6.28-11-server/build SUBDIRS=/home/operator/drivers/e100-3.5.17/src modules
make[1]: Entering directory '/usr/src/linux-headers-2.6.28-11-server'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/operator/drivers/e100-3.5.17/src/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/operatorr/drivers/e100-3.5.17/src] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-2.6.28-11-server'
make: *** [default] Error 2

I've googled a bit and searched the forums, but nothing matches this exactly. Any ideas, anyone?

---

