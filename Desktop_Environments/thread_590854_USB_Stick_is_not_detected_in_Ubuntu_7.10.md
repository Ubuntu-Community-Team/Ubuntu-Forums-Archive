---
title: "USB Stick is not detected in Ubuntu 7.10"
date: 2007-10-25
forum: Desktop Environments
---

### Post by gaiterin on 2007-10-25
Hello.
I bought a laptop.
On Windows Vista read perfectly my 2 USB sticks (Generic and Kingston 1GB).
Ubuntu 7.10 reads the generic (and mount perfectly), but the Kingston not. The led Flashes a every 1.5 seconds, and do not read and do not mount.

Making lsusb does not appear the usb unit.

Other computer with Ubuntu 7.04, reads both memories perfectly.

Is it a problem of Ubuntu 7.10?

Thanks!
Marcos.

---

### Post by vanadium on 2007-10-25
Does your USB appear in the output of

sudo fdisk -l

(with -l of "list")? If not, then indeed the hardware is not recognized. If it does, then there is a problem with the partition on it, and you will need to check the partition for errors.

---

### Post by gaiterin on 2007-10-25
Hi!
But can I check the partition for errors?
Thanks very much ;)

---

### Post by gaiterin on 2007-11-07
The bug is this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746)

A temporal solution: Before insert the usb stick:
sudo modprobe -r ehci_hcd

---

