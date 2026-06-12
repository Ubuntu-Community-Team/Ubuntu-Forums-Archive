---
title: "USB Drive /dev/sd* not created - Xubuntu 11.04"
date: 2011-07-19
forum: Desktop Environments
---

### Post by Pimpn8ezy on 2011-07-19
I've solved this problem, but it took longer than I would have liked and in the end the solution was easy.  I thought it best to still post to hopefully help others.

The Problem:
I installed Xubuntu on an older laptop.  Everything seemed fine - except that usb drives would not mount.  It turns out that /dev/sd* devices (/dev/sdb /dev/sbc etc.) were not being created when I plugged in a usb drive.  Drives would be mounted if a usb drive was present at boot time, the existing drive and any other drives added.

The Solution:
the module usb_storage was not being loaded unless a usb drive was present at boot.  Adding 'usb_storage' to the /etc/modules file fixed everything.

I hope this helps. :)
Ben

---

