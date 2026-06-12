---
title: "Nvidia Module on Custom Kernel Error"
date: 2007-03-16
forum: Desktop Environments
---

### Post by avairos on 2007-03-16
I just compiled a custom kernel, inputting the coretemp.ko module (probably unrelated, heh).  On trying to use NVIDIA's installation script to configure the module, I get this error:

  ```

FATAL: modpost: GPL-incompatible module nvidia.ko uses GPL-only symbol 'para
   virt_ops'
   make[3]: *** [__modpost] Error 1
   make[2]: *** [modules] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

Any help? :)

---

### Post by Mysth-R on 2007-03-29
hello,
I've got the same error.

Have you find a solution ?
Mysth-R

---

### Post by stmiller on 2007-03-31
Looks like that nvidia driver does not work with the latest kernel. Nvidia needs to make an updated driver. Apparently only leaving in VESA and no rivafb and nvidiafb in the kernel config, AND turning off virtualization makes it work, according to this forum:

[http://linuxforum.ru/index.php?showtopic=37512&pid=370386&st=0&#entry370386](http://linuxforum.ru/index.php?showtopic=37512&pid=370386&st=0&#entry370386)

Edit: I tried this, but it did not fix it for me. :(

I did see this in my nvidia-installer.log

> 
   NVIDIA: calling KBUILD...
   make CC=cc KBUILD_OUTPUT=/lib/modules/2.6.20.4/build KBUILD_VERBOSE=1 -C /li
   b/modules/2.6.20.4/source SUBDIRS=/tmp/selfgz7190/NVIDIA-Linux-x86-1.0-9755-
   pkg1/usr/src/nv modules
   make -C /lib/modules/2.6.20.4/build \
   	KBUILD_SRC=/usr/src/linux-2.6.20.4 \
   	KBUILD_EXTMOD="/tmp/selfgz7190/NVIDIA-Linux-x86-1.0-9755-pkg1/usr/src/nv" -
   f /usr/src/linux-2.6.20.4/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;



So I'll try the make oldconfig .... suggestion and see if that works.

---

### Post by brent.stephens on 2007-04-01
1. Go to your source location and run *make menuconfig*
2. Under "Processor type and features" turn "Paravirtualization Support" OFF
3. Exit and save the config.
4. Run *make prepare*
5. Re-run the NVIDIA Installer
6. Profit.

---

### Post by wheaties_box on 2007-04-22
turning off paravirtualization worked for me

---

### Post by 5-HT on 2007-04-27
> **wheaties_box said:**
> turning off paravirtualization worked for me

Worked for me as well. Thanks everyone!

---

### Post by Tyl3r on 2007-05-07
Thanks a lot, I fixed my problem too! :D

---

### Post by zerwas on 2007-05-12
Turning off Paravirtualization also works with kernel 2.6.21. Thank you very much brent.stephens :-)

---

