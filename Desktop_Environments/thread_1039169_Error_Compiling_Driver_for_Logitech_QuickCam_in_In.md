---
title: "Error Compiling Driver for Logitech QuickCam in Intrepid"
date: 2009-01-14
forum: Desktop Environments
---

### Post by sharathpaps on 2009-01-14
I have a Logitech Quickcam Express which I want to use in Intrepid. I am trying to install qc-usb driver 0.6.6 as per the instructions given over [here]("http://qce-ga.sourceforge.net/")

The webcam is recognised as an usb device because the output of lsusb is 

```
Bus 005 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:0003 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

On compiling the driver I get the following error :

```
sharath@Desktop:~/Driver$ cd qc-usb-0.6.6
sharath@Desktop:~/Driver/qc-usb-0.6.6$ make all
make -C "/lib/modules/2.6.27-9-generic/build" SUBDIRS="/home/sharath/Driver/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/sharath/Driver/qc-usb-0.6.6/.tmp_versions ; rm -f /home/sharath/Driver/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/sharath/Driver/qc-usb-0.6.6
  gcc -Wp,-MD,/home/sharath/Driver/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-9-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/sharath/Driver/qc-usb-0.6.6/.tmp_qc-driver.o /home/sharath/Driver/qc-usb-0.6.6/qc-driver.c
In file included from /home/sharath/Driver/qc-usb-0.6.6/qc-driver.c:47:
/home/sharath/Driver/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:60,
                 from include/linux/videodev.h:16,
                 from /home/sharath/Driver/qc-usb-0.6.6/quickcam.h:95,
                 from /home/sharath/Driver/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c:2529: error: ‘struct video_device’ has no member named ‘type’
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c: At top level:
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c:3008: error: unknown field ‘type’ specified in initializer
/home/sharath/Driver/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/sharath/Driver/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/sharath/Driver/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [quickcam.ko] Error 2

```

Ekiga, Cheese, Easycam2, Skype all fail to detect the device.

What am I doing wrong?

Thank You

---

### Post by Progenitor101 on 2009-01-15
I installed the same driver through synaptic and no chat program detects my logitec webcam either. It used to work with Hardy but since installing Intrepid, it doesn't. (using KDE)

---

