---
title: "[SOLVED] parallels vm installation error"
date: 2009-01-01
forum: General Help
---

### Post by thingy87654321 on 2009-01-01
i bought a keycode, downloaded parallels in .deb format

ran the parallels-config command and i said has to be root
so i used the sudo parallels-config command and i got this


     Compiling Parallels Workstation 2.2 drivers...


Can not compile and/or link drivers. Read /usr/lib/parallels/doc/INSTALL
and follow instructions specified in this document.

Compilation log is available at /usr/lib/parallels/comp.log.6720.error
chris@chris-laptop:~$ 
(i cut out the licence agreement because it was way to long)
so i went to the error  log file and this is what was in it

cd drivers && make KSRC=/lib/modules/2.6.24-19-generic/build clean && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_virtualnic'
make[1]: Leaving directory `/usr/lib/parallels/drivers'
cd wrapper && make clean && cd ..
make[1]: Entering directory `/usr/lib/parallels/wrapper'
rm -f parallels-wrapper
make[1]: Leaving directory `/usr/lib/parallels/wrapper'
cd drivers && make KSRC=/lib/modules/2.6.24-19-generic/build all && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_virtualnic'
cd drv_main/ && make KSRC=/lib/modules/2.6.24-19-generic/build && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/lib/parallels/drivers/drv_main SRCROOT=/usr/lib/parallels/drivers/drv_main modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/lib/parallels/drivers/drv_main/vmmain.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/vmproc.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/device.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/dwrap.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/intgate.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/ioctls.o
In file included from /usr/lib/parallels/drivers/drv_main/ioctls.c:33:
/usr/lib/parallels/drivers/drv_main/../hypervisor/vtx_init.h:80: warning: function declaration isn’t a prototype
In file included from /usr/lib/parallels/drivers/drv_main/ioctls.c:34:
/usr/lib/parallels/drivers/drv_main/../hypervisor/svm_init.h:66: warning: function declaration isn’t a prototype
/usr/lib/parallels/drivers/drv_main/ioctls.c: In function ‘vmMainIoctl’:
/usr/lib/parallels/drivers/drv_main/ioctls.c:170: warning: assignment makes integer from pointer without a cast
  CC [M]  /usr/lib/parallels/drivers/drv_main/monexport.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/manager.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/pages.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/collector.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/monmem.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/wset.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/bma.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/logging.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/timer.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/idata.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/utils.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/md5.o
  LD [M]  /usr/lib/parallels/drivers/drv_main/vm-main.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "hypervisorPresentInSystem" [/usr/lib/parallels/drivers/drv_main/vm-main.ko] undefined!
WARNING: "appDecCounter" [/usr/lib/parallels/drivers/drv_main/vm-main.ko] undefined!
WARNING: "appIncCounter" [/usr/lib/parallels/drivers/drv_main/vm-main.ko] undefined!
  CC      /usr/lib/parallels/drivers/drv_main/vm-main.mod.o
  LD [M]  /usr/lib/parallels/drivers/drv_main/vm-main.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/lib/parallels/drivers/hypervisor SRCROOT=/usr/lib/parallels/drivers/hypervisor modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/lib/parallels/drivers/hypervisor/hypmain.o
  CC [M]  /usr/lib/parallels/drivers/hypervisor/hdevice.o
In file included from /usr/lib/parallels/drivers/hypervisor/hdevice.c:34:
/usr/lib/parallels/drivers/hypervisor/vtx_init.h:80: warning: function declaration isn’t a prototype
In file included from /usr/lib/parallels/drivers/hypervisor/hdevice.c:35:
/usr/lib/parallels/drivers/hypervisor/svm_init.h:66: warning: function declaration isn’t a prototype
  CC [M]  /usr/lib/parallels/drivers/hypervisor/hioctls.o
In file included from /usr/lib/parallels/drivers/hypervisor/hioctls.c:29:
/usr/lib/parallels/drivers/hypervisor/vtx_init.h:80: warning: function declaration isn’t a prototype
/usr/lib/parallels/drivers/hypervisor/hioctls.c: In function ‘hypIoctl’:
/usr/lib/parallels/drivers/hypervisor/hioctls.c:59: warning: unused variable ‘iVtxSupport’
  CC [M]  /usr/lib/parallels/drivers/hypervisor/hypvmstate.o
/usr/lib/parallels/drivers/hypervisor/hypvmstate.c: In function ‘hypVMStateAllocate’:
/usr/lib/parallels/drivers/hypervisor/hypvmstate.c:82: warning: passing argument 1 of ‘mmEnableExecution’ makes integer from pointer without a cast
  CC [M]  /usr/lib/parallels/drivers/hypervisor/logging.o
  CC [M]  /usr/lib/parallels/drivers/hypervisor/pages.o
  CC [M]  /usr/lib/parallels/drivers/hypervisor/utils.o
  CC [M]  /usr/lib/parallels/drivers/hypervisor/md5.o
  CC [M]  /usr/lib/parallels/drivers/hypervisor/vtx_init.o
In file included from /usr/lib/parallels/drivers/hypervisor/vtx_init.c:30:
/usr/lib/parallels/drivers/hypervisor/vtx_init.h:80: warning: function declaration isn’t a prototype
  CC [M]  /usr/lib/parallels/drivers/hypervisor/svm_init.o
In file included from /usr/lib/parallels/drivers/hypervisor/svm_init.c:30:
/usr/lib/parallels/drivers/hypervisor/svm_init.h:66: warning: function declaration isn’t a prototype
  LD [M]  /usr/lib/parallels/drivers/hypervisor/hypervisor.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /usr/lib/parallels/drivers/hypervisor/.interrupt.o.cmd for /usr/lib/parallels/drivers/hypervisor/interrupt.o
  CC      /usr/lib/parallels/drivers/hypervisor/hypervisor.mod.o
  LD [M]  /usr/lib/parallels/drivers/hypervisor/hypervisor.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/lib/parallels/drivers/drv_net/linux SRCROOT=/usr/lib/parallels/drivers/drv_net/linux modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/lib/parallels/drivers/drv_net/linux/prlnet.o
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c: In function ‘hw_bind’:
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1051: warning: passing argument 1 of ‘dev_get_by_name’ from incompatible pointer type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1051: error: too few arguments to function ‘dev_get_by_name’
make[4]: *** [/usr/lib/parallels/drivers/drv_net/linux/prlnet.o] Error 1
make[3]: *** [_module_/usr/lib/parallels/drivers/drv_net/linux] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
make[1]: *** [vmbridge] Error 2
make[1]: Leaving directory `/usr/lib/parallels/drivers'
make: *** [build] Error 2

if anyone could help, i will thank you, even if the idea does not work:D

---

### Post by thingy87654321 on 2009-01-02
i did something and my screen blinked and the config thingy started in the terminal asked for the password and it complied correctly:D

---

