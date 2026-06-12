---
title: "A complex GRUB dual boot?"
date: 2009-06-21
forum: General Help
---

### Post by superjudge3 on 2009-06-21
Hey y'all. I'm using Ubuntu 9.04 and also have windows XP and windows 7 beta installed. I'm tired of having to chainload the 7 bootloader from an entry in grub. Is there any way I can get windows 7 and XP to show up as separate entries in GRUB so i can boot from ONE menu?

An explanation of why to do whatever steps you list would be very appreciated by this Ubuntu n00b.

---

### Post by blueridgedog on 2009-06-21
You can edit /boot/grub/menu.lst and add an entry for xp, if you know the drive and partition that it rests on.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Entropy_Sam on 2009-06-21
blueridgedog's answer should point you in the right direction.

Copy, paste and edit your Windows chainloading entry in menu.lst.

If you need help determining hard drive partitions as GRUB sees them, look at device.map in the same directory to see how sda, sdb, etc match up to hd0, hd1 etc. For partition numbers, you usually only need to subtract 1 from Linux's partition numbering scheme.

For example, if GRUB sees sda as hd0, then sda2 in Linux would probably be (hd0,1) in GRUB.

If you have any issues, post the output of **sudo fdisk -l** the contents of** menu.lst**, and the contents of **device.map **here and I or someone else will try to advise you. :-)

---

### Post by blueridgedog on 2009-06-21
Also, you can generally make an entry in menu.lst and tweak it as it goes...nothing like knowing your disks and partitions and being able to mentally form an image in your mind of what boots what.  Just don't change anything, copy your existing and working Windows 7 entry and edit the title and target.

---

