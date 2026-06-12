---
title: "NTFS partition unreadable?"
date: 2009-05-06
forum: General Help
---

### Post by dajhull on 2009-05-06
Hi, I wonder if anyone can give me some advice...

I intalled Ubuntu 9.04 recently to dual boot with Vista. By mistake (I think) I set it to boot from the Windows partition. On booting up, Grub gave Windows as an option, but would boot it -- it just cycled back to the Grub boot menu.

Today I reinstalled 8.10 because 9.04 doesn't seem to work with my wireless, and I was hoping that reinstalling might allow Vista to boot again.

Unfortunately now Grub doesn't even detect Vista is there, and Gparted says the NTFS partition is unreadable. 

This is my output from fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08f3c280

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        5885    45732422    7  HPFS/NTFS
/dev/sda3            5886       19457   109017090    5  Extended
/dev/sda5            5886       19380   108398556   83  Linux
/dev/sda6           19381       19457      618471   82  Linux swap / Solaris

```

Have I corrupted the Vista partition? Any suggestions about how to fix this would be really appreciated!

---

### Post by kirsis on 2009-05-06
You could try changing the /boot/grub/menu.lst file

The entry for windows will probably say something like

root (hdx,y)
chainloader +1
boot

If you change root to rootnoverify (like this: rootnoverify (hdx,y)), grub will not attempt to read the partition and will jump straight to the windows bootloader. If this is successful, maybe Windows will check and repair its filesystem itself.

Though, this is just speculation.

---

