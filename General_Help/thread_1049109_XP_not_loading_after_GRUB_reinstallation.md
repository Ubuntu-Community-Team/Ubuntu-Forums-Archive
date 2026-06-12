---
title: "XP not loading after GRUB reinstallation"
date: 2009-01-24
forum: General Help
---

### Post by Kukabarra on 2009-01-24
Hello all.

I've installed XP on my ubuntu machine, GRUB went down as always, I've reinstalled it. After the reinstallation only ubuntu is loading, and there's no entry for WinXP in /boot/grub/menu.lst. What is wrong?

> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40e440e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686   83  Linux
/dev/sda2   *        5100       11785    53705295    7  HPFS/NTFS
/dev/sda3           11786       12161     3020220    5  Extended
/dev/sda5           11786       12161     3020188+  82  Linux swap / Solaris


---

### Post by Elfy on 2009-01-24
TRy adding this - back up and edit the file with

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.2401
gksudo gedit /boot/grub/menu.lst
```

```
title 		--Xp--
root		(hd0,1)
makeactive
chainloader	+1
```

---

