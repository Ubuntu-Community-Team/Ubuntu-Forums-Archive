---
title: "can't compile ov511 for philips toucam"
date: 2006-06-11
forum: Desktop Environments
---

### Post by cobralgato on 2006-06-11
hi!
i'm using dapper amd64
have a philips toucam PCVC810B
used synaptic and got ov511-src but it only works with up to 2.5 kernel...
then got the ov511 source and tried to make but got this error :

/usr/src/ov511-2.31$ make
    Building OVCam drivers for 2.6 kernel.
make -C /lib/modules/2.6.15-23-amd64-generic/build SUBDIRS=/usr/src/ov511-2.31 modules
make: *** /lib/modules/2.6.15-23-amd64-generic/build: No such file or directory.  Stop.
make: *** [default] Error 2


cant compile ..!   !!!      
if i try to use it with xawtv   i get :

xawtv
This is xawtv-3.94, running on Linux/x86_64 (2.6.15-23-amd64-generic)
WARNING: No DGA support available for this display.
can't open /dev/video0: Function not implemented
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Function not implemented
v4l2: open /dev/video0: Function not implemented
v4l: open /dev/video0: Function not implemented
no video grabber device available


and dmesg says :

[ 2388.461677] drivers/usb/media/ov511/ov511.c: No decompressor available
[ 2388.542007] drivers/usb/media/ov511/ov511.c: No decompressor available
[ 2388.622853] drivers/usb/media/ov511/ov511.c: No decompressor available
[ 2388.701853] drivers/usb/media/ov511/ov511.c: No decompressor available


lsusb :

Bus 002 Device 003: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam

and if i try :
webcam
reading config file: /home/mr/.webcamrc
v4l2: open /dev/video0: Function not implemented
v4l2: open /dev/video0: Function not implemented
v4l: open /dev/video0: Function not implemented
no grabber device available


how can i compile that ?


thanx

---

### Post by cobralgato on 2006-06-17
this ubuntu forum is getting too big ...  so many threads and users ... and no replies .... :-(

---

### Post by cobralgato on 2006-09-18
Done.

---

### Post by FRuMMaGe on 2007-09-05
> **cobralgato said:**
> Done.

I have this problem!  How did you fix it?

---

