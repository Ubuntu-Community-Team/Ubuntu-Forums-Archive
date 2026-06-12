---
title: "Persistent Install Questions (USB Stick)"
date: 2009-02-12
forum: General Help
---

### Post by Emarian on 2009-02-12
I've been reading over several different documents ([Like this](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)) on creating a persistent install of Ubuntu, but none of them seem to answer a few simple basic questions for a newer Ubuntu user; rather, they just describe the process:

1. Will this (the guide I linked to) work on any computer? For example, if I followed that guide and created the persistent install at home, could I take it to work or a friend's house, plug it in, and expect it to work (different hardware configurations)?

2. ALL changes will be saved? For example, if placed a file on my desktop, could I expect it to be there on reboot?

3. Drivers will be selected for each computer on boot? So that I will not have any issues with unique hardware (assuming that Ubuntu is natively compatible)?

---

### Post by C.S.Cameron on 2009-02-12
1)Some older computer BIOS will not boot flash dives. If you install restricted drivers, say for Nvidia the flash drive will have problems on computers with ATI or Intel graphics.
2)All changes should be saved if you do a full install similar to Method 1. (I would recommend installing the same as to HDD except to disable the computers internal drive first).
If you use the ISO image method using USB-creator or unetbootin you will not be able to update and save the kernel, most other changes should be saved though.
3)In my experience the drive should work on most other computers except as mentioned in question 1. It will not automatically detect the best screen resolution, dual monitors or drivers for obscure hardware.
An install using usb-creator or Unetbootin should work just like the Live CD only a bit faster.

---

