---
title: "usbvision and wintv usb"
date: 2005-12-28
forum: General Help
---

### Post by philipgm on 2005-12-28
I've finally managed to get usbvision installed on my system. The device is correctly identified, model number and revision, but I don't seem to be able to tune anything dmesg gives this:

/home/philip/usbvision/src/usbvision.c: usbvision_probe: Hauppauge WinTv-USB Model 40205 Rev B298 found
/home/philip/usbvision/src/usbvision.c: USBVision[1]: registered USBVision Video device /dev/video1 [v4l]
/home/philip/usbvision/src/usbvision.c: USBVision[1]: registered USBVision VBI device /dev/vbi2 [v4l] (Not Working Yet!)
tuner 2-0061: chip found @ 0xc2 (usbvision #1)
tuner 2-0061: Tuner has no way to set tv freq
tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))

This is all on a vanilla 2.6.14.4 kernel that I built today.

Any ideas, suggestions?

---

### Post by suomiro on 2006-11-09
I have the same problem. Can anyone say what is the problem and how to fix it?

Thanks!

---

