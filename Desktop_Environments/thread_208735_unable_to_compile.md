---
title: "unable to compile"
date: 2006-07-04
forum: Desktop Environments
---

### Post by ubun_nv on 2006-07-04
i was unable to compile a driver even though i have all the development tools .can anyone able to compile a driver for me.i use default kernel.

link [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.18.00.07full/hsfmodem_7.18.00.07full_i386.deb.zip](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.18.00.07full/hsfmodem_7.18.00.07full_i386.deb.zip)

---

### Post by XAsmodeanX on 2006-07-04
Can you give an error message?  That would be very helpful in diagnosing the problem.

---

### Post by ape on 2006-07-04
what error message(s) are you getting?  I was able to compile the linuxant modem driver without problems.

---

### Post by ubun_nv on 2006-07-04
error message


(cd /lib/modules/2.6.15-23-386/build && make "CNXT_KERNELSRC=/lib/modules/2.6.15-23-386/build" "M=/usr/lib/hsfmodem/modules" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.15-23-386/build/.tmp_versions/hsfsoar.mod
(cd /lib/modules/2.6.15-23-386/build && make "CNXT_KERNELSRC=/lib/modules/2.6.15-23-386/build" "M=/usr/lib/hsfmodem/modules" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
In file included from /usr/lib/hsfmodem/modules/mod_mc97ali.c:32:
/usr/lib/hsfmodem/modules/cnxthwpci_common.c: In function 'cnxthwpci_probe':
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: implicit declaration of function 'pm_register'
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: assignment makes pointer from integer without a cast
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:137: warning: implicit declaration of function 'pm_unregister'
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
In file included from /usr/lib/hsfmodem/modules/mod_mc97ati.c:25:
/usr/lib/hsfmodem/modules/cnxthwpci_common.c: In function 'cnxthwpci_probe':
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: implicit declaration of function 'pm_register'
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: assignment makes pointer from integer without a cast
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:137: warning: implicit declaration of function 'pm_unregister'
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
In file included from /usr/lib/hsfmodem/modules/mod_mc97ich.c:37:
/usr/lib/hsfmodem/modules/cnxthwpci_common.c: In function 'cnxthwpci_probe':
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: implicit declaration of function 'pm_register'
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: assignment makes pointer from integer without a cast
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:137: warning: implicit declaration of function 'pm_unregister'
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
In file included from /usr/lib/hsfmodem/modules/mod_mc97sis.c:25:
/usr/lib/hsfmodem/modules/cnxthwpci_common.c: In function 'cnxthwpci_probe':
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: implicit declaration of function 'pm_register'
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: assignment makes pointer from integer without a cast
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:137: warning: implicit declaration of function 'pm_unregister'
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
In file included from /usr/lib/hsfmodem/modules/mod_mc97via.c:25:
/usr/lib/hsfmodem/modules/cnxthwpci_common.c: In function 'cnxthwpci_probe':
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: implicit declaration of function 'pm_register'
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:86: warning: assignment makes pointer from integer without a cast
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:137: warning: implicit declaration of function 'pm_unregister'
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
  CC [M]  /usr/lib/hsfmodem/modules/osresour.o
  CC [M]  /usr/lib/hsfmodem/modules/osstring.o
  CC [M]  /usr/lib/hsfmodem/modules/osmemory.o
  CC [M]  /usr/lib/hsfmodem/modules/osdiag.o
/usr/lib/hsfmodem/modules/osdiag.c: In function 'GetDiagInstance':
/usr/lib/hsfmodem/modules/osdiag.c:662: warning: implicit declaration of function 'class_simple_device_add'
/usr/lib/hsfmodem/modules/osdiag.c: In function 'PutDiagInstance':
/usr/lib/hsfmodem/modules/osdiag.c:767: warning: implicit declaration of function 'class_simple_device_remove'
/usr/lib/hsfmodem/modules/osdiag.c: In function 'OsDiagExit':
/usr/lib/hsfmodem/modules/osdiag.c:844: warning: implicit declaration of function 'class_simple_destroy'
/usr/lib/hsfmodem/modules/osdiag.c: In function 'OsDiagInit':
/usr/lib/hsfmodem/modules/osdiag.c:868: warning: implicit declaration of function 'class_simple_create'
/usr/lib/hsfmodem/modules/osdiag.c:868: warning: assignment makes pointer from integer without a cast
  CC [M]  /usr/lib/hsfmodem/modules/osusb.o
/usr/lib/hsfmodem/modules/osusb.c: In function 'AbortListUrbs':
/usr/lib/hsfmodem/modules/osusb.c:236: error: 'URB_ASYNC_UNLINK' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/osusb.c:236: error: (Each undeclared identifier is reported only once
/usr/lib/hsfmodem/modules/osusb.c:236: error: for each function it appears in.)
/usr/lib/hsfmodem/modules/osusb.c: In function 'FreeUrbList':
/usr/lib/hsfmodem/modules/osusb.c:257: error: 'URB_ASYNC_UNLINK' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/osusb.c: In function 'cnxthsf_OsUsbMakeNotifyRequest':
/usr/lib/hsfmodem/modules/osusb.c:1498: error: 'URB_ASYNC_UNLINK' undeclared (first use in this function)
make[2]: *** [/usr/lib/hsfmodem/modules/osusb.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
make: *** [all] Error 2

---

### Post by ubun_nv on 2006-07-04
anyone please compile the drivers.

---

### Post by ape on 2006-07-21
Just built them again with no errors.  Do you have the linux-source package installed?  The tree will live in /usr/src if you've installed it.  Looking at the hsfconfig file that actually does the building, they're definitely looking for the kernel source tree.

---

