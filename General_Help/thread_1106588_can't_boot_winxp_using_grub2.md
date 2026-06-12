---
title: "can't boot winxp using grub2"
date: 2009-03-25
forum: General Help
---

### Post by abjdiat on 2009-03-25
I have 2 sata hdds,,500g each
i installed winxp on the first partition (hda,0)one and ubuntu8.10 on the other(hdb,4),,
i chose grub2 to be installed on the same drive where winxp is, but now i can't boot to winxp, everytime i click winxp in booting menu nothing happens, no error messages,
menu.lst
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1f551356-1e03-4f70-afab-25c988f06bbe
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1f551356-1e03-4f70-afab-25c988f06bbe ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1f551356-1e03-4f70-afab-25c988f06bbe
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1f551356-1e03-4f70-afab-25c988f06bbe ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1f551356-1e03-4f70-afab-25c988f06bbe
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1
```

here is my hdds partitions..
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x771e2e19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16588   133242086    7  HPFS/NTFS
/dev/sda2           16589       60784   355004370    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022b41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       34968   280880428+   7  HPFS/NTFS
/dev/sdb2           48054       60801   102398310   83  Linux
/dev/sdb3           34969       48053   105105262+   5  Extended
/dev/sdb5           34969       47515   100783746   83  Linux
/dev/sdb6           47516       48053     4321453+  82  Linux swap / Solaris
```
I hope you could help , thanx in advance

---

### Post by abjdiat on 2009-03-25
i tried to edit menu.lst, i changed 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```
to 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1

```
win xp booting now, but I got NTLDR messing message,.
I figured out what I did wrong, which is missing with windows MBR, instead of installing grub boot loader on the second hdd
is there anyway I can fix this, thanx in advance..

---

