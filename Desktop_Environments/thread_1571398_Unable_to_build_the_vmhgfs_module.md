---
title: "Unable to build the vmhgfs module"
date: 2010-09-09
forum: Desktop Environments
---

### Post by dink123 on 2010-09-09
hi
i am using Ubuntu 8.10 inside VMWare Workstation 6.
i need to use folder sharing feature with my host OS XP2 but when i tried installing VMWareTools i cant build several modules including vmhgfs and vmblock.


```
Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.

make: Entering directory `/tmp/vmware-config9/vmhgfs-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config9/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-config9/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/vmware-config9/vmhgfs-only/bdhandler.o
/tmp/vmware-config9/vmhgfs-only/bdhandler.c:15:27: error: asm/semaphore.h: No such file or directory
make[2]: *** [/tmp/vmware-config9/vmhgfs-only/bdhandler.o] Error 1
make[1]: *** [_module_/tmp/vmware-config9/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config9/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]
```


How can i resolve this?? i am spending hours googling this. Pls help

---

### Post by dink123 on 2010-09-10
someone please help me here?

---

