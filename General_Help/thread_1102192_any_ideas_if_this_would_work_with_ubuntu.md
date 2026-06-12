---
title: "any ideas if this would work with ubuntu?"
date: 2009-03-21
forum: General Help
---

### Post by sdowney717 on 2009-03-21
[http://cgi.ebay.com/12M-USB-12-MEGA-PIXEL-Webcam-Driverless-PC-Video-Camera_W0QQitemZ220381239406QQcmdZViewItemQQptZPCA_Video_Conferencing_Webcams?hash=item220381239406&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1308|301%3A0|293%3A1|294%3A50](http://cgi.ebay.com/12M-USB-12-MEGA-PIXEL-Webcam-Driverless-PC-Video-Camera_W0QQitemZ220381239406QQcmdZViewItemQQptZPCA_Video_Conferencing_Webcams?hash=item220381239406&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1308|301%3A0|293%3A1|294%3A50)

Or what is a great web cam with a great picture to look for?

---

### Post by linuxuser21 on 2009-03-21
It should.  I don't see why it wouldn't.

---

### Post by sdowney717 on 2009-03-21
I have struggled with a logitech quickcam which does not work 

scott@scott-desktop:~/libv4l-0.5.0$ lsusb
Bus 004 Device 014: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
[152836.636035] usb 4-1: new full speed USB device using uhci_hcd and address 32
[152836.815948] usb 4-1: configuration #1 chosen from 1 choice
[152836.819793] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[152836.819805] quickcam: Kernel:2.6.27-11-generic bus:4 class:FF subclass:FF vendor:046D product:0850
[152836.865712] quickcam: Sensor VV6410 detected
[152836.867906] quickcam: Registered device: /dev/video1
[152837.858361] hub 4-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[152837.858378] usb 4-1: USB disconnect, address 32
[152837.890033] 32:2:1: usb_set_interface failed
[152838.132088] usb 4-1: new full speed USB device using uhci_hcd and address 33
[152838.346246] usb 4-1: configuration #1 chosen from 1 choice
[152838.349544] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[152838.349555] quickcam: Kernel:2.6.27-11-generic bus:4 class:FF subclass:FF vendor:046D product:0850
[152838.389444] quickcam: Sensor VV6410 detected
[152838.391639] quickcam: Registered device: /dev/video1

```

---

### Post by sdowney717 on 2009-03-21
even though it is recognized, no programs can use the webcam

---

### Post by Monsieur Gonzalez on 2009-03-21
Hard to tell without more info on maker, model, sensor type... you could try and contact the seller. Or take a look at the [wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras") and make sure you buy a supported camera and save yourself some trouble.

---

### Post by Monsieur Gonzalez on 2009-03-21
Sdowney, your webcam seems to require some additional work, take a look [here]("http://qce-ga.sourceforge.net/") .

---

### Post by sdowney717 on 2009-03-21
errors, any thoughts

```
scott@scott-desktop:~/qc-usb-0.6.6$ sudo make all
make -C "/lib/modules/2.6.27-11-generic/build" SUBDIRS="/home/scott/qc-usb-0.6.6" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/scott/qc-usb-0.6.6/.tmp_versions ; rm -f /home/scott/qc-usb-0.6.6/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/scott/qc-usb-0.6.6
  gcc -Wp,-MD,/home/scott/qc-usb-0.6.6/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAVE_UTSRELEASE_H=1 -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/scott/qc-usb-0.6.6/.tmp_qc-driver.o /home/scott/qc-usb-0.6.6/qc-driver.c
In file included from /home/scott/qc-usb-0.6.6/qc-driver.c:47:
/home/scott/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:60,
                 from include/linux/videodev.h:16,
                 from /home/scott/qc-usb-0.6.6/quickcam.h:95,
                 from /home/scott/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/scott/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/scott/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/scott/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/scott/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/scott/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/scott/qc-usb-0.6.6/qc-driver.c: In function ‘qc_v4l_ioctl’:
/home/scott/qc-usb-0.6.6/qc-driver.c:2529: error: ‘struct video_device’ has no member named ‘type’
/home/scott/qc-usb-0.6.6/qc-driver.c: At top level:
/home/scott/qc-usb-0.6.6/qc-driver.c:3008: error: unknown field ‘type’ specified in initializer
/home/scott/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/scott/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/scott/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [quickcam.ko] Error 2
scott@scott-desktop:~/qc-usb-0.6.6$ 

```

---

