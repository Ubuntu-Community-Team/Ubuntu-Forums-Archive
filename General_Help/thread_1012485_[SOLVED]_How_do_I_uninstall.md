---
title: "[SOLVED] How do I uninstall?"
date: 2008-12-15
forum: General Help
---

### Post by s13vin4t0r on 2008-12-15
I have Ubuntu Hardy Heron.

I am dual booting it with Windows Vista.

How do I uninstall Ubuntu and erase the partition it is on?

Thanks! ):P

---

### Post by caljohnsmith on 2008-12-16
Assuming you are using Grub in your HDD's MBR (Master Boot Record) to handle your dual-booting, the first thing would be to replace Grub with a Windows MBR. If you have a Vista Install CD, boot that, go to the command line and run:
```
bootrec /fixmbr
```
Or if you don't have a Vista Install CD, boot your Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
And that will install a Windows equivalent MBR into drive sda. After that, you should be able to boot directly into Vista, so you could use Vista's Disk Management to delete your Ubuntu partitions and turn them into NTFS data partitions for example. Anyway, that's the general idea, but let me know how it goes.

---

### Post by s13vin4t0r on 2008-12-17
So this stops me being able to boot Ubuntu? Nice.

I'll try this a little later.

Thanks a bunch man!! :D

---

