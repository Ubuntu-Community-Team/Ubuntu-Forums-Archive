---
title: "USB drive error"
date: 2011-10-17
forum: Desktop Environments
---

### Post by scopeman on 2011-10-17
I have a USB thumb drive that does not work with 11.10.  lsusb sees the drive but fdisk doesn't.  The output of dmesg:

[ 7623.400034] usb 1-5: new high speed USB device number 23 using ehci_hcd
[ 7623.555485] usb 1-5: can't set config #1, error -71

I found a few posts about removing LAUNCH from the drive.  I did this and also formatted it using my XP machine.  I have an older full-speed drive that works fine.

---

