---
title: "Mount External Hard Drive via .xsession?"
date: 2008-12-11
forum: General Help
---

### Post by MCrittenden on 2008-12-11
I'm running XBMC (media center app if you're unfamiliar) via a dedicated username, and that user is running an xsession script, which only has ```
xbmc
```
That way, when I log in as that user, XBMC is the only thing that loads so I don't have any unneeded apps taking up resources. Problem is, I can't open an external hard drive full of music/movies when I do it that way, because the script doesn't mount it. 

How can I make it automount? Would it involve editing fstab or can I just throw a couple more lines into xsession? Here's the output of fdisk -l if you need it. Thanks!
```
Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000830c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7383    59303916   83  Linux
/dev/sda2            7384        7476      747022+   5  Extended
/dev/sda5            7384        7476      746991   82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28f12a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7296    58605088+   c  W95 FAT32 (LBA)

```

---

### Post by decoherence on 2008-12-11
I say do it with fstab. If you try doing it with a mount line in your .xsession you'll probably get told you need to be root.

Adding a line like this to fstab will likely do the trick

/dev/sdb1 /media/external vfat defaults 0 0

Make sure you already have the directory /media/external (this can be called whatever you like)

---

### Post by MCrittenden on 2008-12-11
Worked. Thanks!

---

