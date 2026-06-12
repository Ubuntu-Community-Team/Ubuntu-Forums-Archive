---
title: "How do I uninstall Ubuntu?"
date: 2006-07-23
forum: Desktop Environments
---

### Post by Diafel on 2006-07-23
No, it's not because I hate it, it's because I'm having a problem booting in. For some reason at startup, it stops at a black screen with a movable mouse cursor. 

Can I simply delete the partition? I'm worried that maybe by deleting GRUB as well I won't be able to boot into Windows again.

---

### Post by Indras on 2006-07-23
By default grub installs in the master boot record of your hard drive, which is the first few bytes of the hard drive space.  If you clear the MBR and set it back to all zeroes, it should then skip the MBR and boot the first operating system it comes to.

Uninstalling Ubuntu is as simple as resetting the MBR and deleting the partitions it is installed in.  To reset the MBR, get an old Windows boot floppy, or Windows 95 or 98 install disk (which are bootable and have the 'boot to MS-DOS' option) and type in:

```
FDISK /MBR
```

Judging from the way you phrased your question, I assume you already know how to delete a partition.

(oh, and there's lots of other ways to reset your MBR, just google it)

---

### Post by greenstar on 2006-07-23
My answer is based on the presumtion that you're not planning on reinstalling Ubuntu (This seemed to be the implication of your post). I hope that you will give it another shot, but that's your choice.

You can delete the partition and

A. Leave grub on the MBR. If you do this, you'll want to edit /boot/grub/menu.lst to make Windows boot by default, and you can hide the grub menu while you're at it. You can even comment out the Ubuntu entry so grub doesn't see it.

OR

2. You can use your Windows CD to reinstall the NT bootloader onto the MBR. 

Hope this helps,
Greenstar

---

### Post by Indras on 2006-07-23
> **greenstar said:**
> A. Leave grub on the MBR. If you do this, you'll want to edit /boot/grub/menu.lst to make Windows boot by default, and you can hide the grub menu while you're at it. You can even comment out the Ubuntu entry so grub doesn't see it.

Keep in mind that if your /boot folder is in your main Ubuntu partition, it will be deleted with the rest of the information, so Grub will not load.

---

### Post by greenstar on 2006-07-23
> **Indras said:**
> Keep in mind that if your /boot folder is in your main Ubuntu partition, it will be deleted with the rest of the information, so Grub will not load.

You're right. That completely slipped my mind. 

OK, so better pull out the Windows CD. Or reinstall Ubuntu, formatting right over the old Ubuntu partitions with the new ones.

Greenstar

---

