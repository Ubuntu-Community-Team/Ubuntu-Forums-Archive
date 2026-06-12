---
title: "Mounting Windows partition"
date: 2008-04-27
forum: Desktop Environments
---

### Post by dhigger on 2008-04-27
I dual-boot Hardy with Vista.

In Ubuntu's Places menu, there are the usual Nautilus bookmarks (Documents, Videos, etc), followed by Computer, CD/DVD Creator, and then - in my case - "Recovery".

"Recovery" is my Windows *recovery partition* (at /dev/sda1), *not* the Windows Vista OS partition (at /dev/sda2).

Now, I know that the Windows Vista OS partition (sda2) is properly mounted at /windows. But **how do I get Ubuntu to ignore the Windows Recovery partition (sda1) and automatically mount the Windows Vista OS partition (sda2) in my Places menu?**

---

### Post by iwallet on 2008-05-08
> **mriedel said:**
> apt-get install ntfs-config, then run Applications -> System Tools -> NTFS Configuration Utility

Alternatively you could add a line similar to "/dev/XXX /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0" to /etc/fstab. The aforementioned tool does that (and a few other things) for you.

try this!

---

