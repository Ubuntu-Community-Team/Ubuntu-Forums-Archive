---
title: "VMware 7 module compile failure"
date: 2011-12-02
forum: Desktop Environments
---

### Post by MakOwner on 2011-12-02
I'm currently running VMWare Workstation 7.1.5 on Ubuntu 10.10.
I'm trying to move away from the horror of Unity by going to Kubuntu or Xubuntu. So, installed Kubuntu and Xubuntu 11.10 on a second workstation to make sure everything worked.  

Both distros exhibit this same issue - VMware 7 installs but on first run attempts to compile the needed modules and fails with this error.


I have searched here in the forums and can't find anything.
VMware says this is fixed in 7.1.5, which I'm trying to install.

Anyone have any ideas?  This is 64bit if it makes any difference.


```

Dec 02 08:47:31.464: app-140053974779680| Extracting the sources of the vmmon module.
Dec 02 08:47:31.486: app-140053974779680| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.0.0-13-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6.1
Dec 02 08:47:32.675: app-140053974779680| Failed to compile module vmmon!
root@dale:/tmp/vmware-root# /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.0.0-13-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6.1
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/3.0.0-13-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-13-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:788:59: error: ‘SPIN_LOCK_UNLOCKED’ undeclared here (not in a function)
make[2]: *** [/tmp/vmware-root/modules/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-13-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
root@dale:/tmp/vmware-root# 

```

---

### Post by BC59 on 2011-12-02
I think the solution is here:

[http://www.vi-toolkit.com/wiki/index.php/Build_host_vmware_kernel_modules](http://www.vi-toolkit.com/wiki/index.php/Build_host_vmware_kernel_modules)

---

### Post by collisionystm on 2011-12-02
> Using 2.6.x kernel build system.

> /usr/src/linux-headers-3.0.0-13-generic

try out some scripts from here. Just scroll down to 
**VMware patches**


[https://wiki.archlinux.org/index.php/VMware](https://wiki.archlinux.org/index.php/VMware)

---

### Post by MakOwner on 2011-12-05
> **collisionystm said:**
> try out some scripts from here. Just scroll down to 
**VMware patches**


[https://wiki.archlinux.org/index.php/VMware](https://wiki.archlinux.org/index.php/VMware)

I'm on the 3.0 kernel, but I see messages stating I'm 
"Using the 2.6.x kernel build system" and I'm assuming that's the cause of the errors I see when attempting these various fixes.

If my assumption is correct, how do I get the running kernel in sync with the build system?

---

### Post by Raberra on 2011-12-29
[http://weltall.heliohost.org/wordpress/2011/08/10/vmware-workstation-7-1-4-fix-for-linux-3-1/](http://weltall.heliohost.org/wordpress/2011/08/10/vmware-workstation-7-1-4-fix-for-linux-3-1/)

Seems to work for linux-headers-3.0.0-14-generic but vmware will give you a warning:

"This version of the Linux kernel is newer than the newest series with which VMware Workstation is supported.  It may or may not work.  Would you like to continue?"

---

