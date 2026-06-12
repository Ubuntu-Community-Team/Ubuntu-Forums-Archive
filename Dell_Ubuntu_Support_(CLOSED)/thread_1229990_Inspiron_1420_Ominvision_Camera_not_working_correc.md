---
title: "Inspiron 1420 Ominvision Camera not working correctly"
date: 2009-08-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mjwalfredo on 2009-08-02
I've gone 100% Ubuntu at home for a while now but I still can't get this darn built in webcam to work correctly.  When testing with gstreamer-properties and luvcview, I get greenish garbled video. I can't get any picture in Skype and Cheese even though the light comes on signaling the camera is working.

I am running Ubuntu 32-bit 9.04 and keep it up to date.  It seems like this thing is supposed to work right out of the box but I just can't get it and it's frustrating me.  Anyone have any solutions?

dmesg output when running sudo modprobe uvcvideo:

```
[31966.879862] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[31966.880607] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[31966.881882] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input38
[31966.916214] usbcore: registered new interface driver uvcvideo
[31966.916223] USB Video Class driver (v0.1.0)

```

---

