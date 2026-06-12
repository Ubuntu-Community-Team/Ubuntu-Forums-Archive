---
title: "GRUB hands on &quot;starting up...&quot; when booting XP!"
date: 2009-03-24
forum: General Help
---

### Post by Fixman on 2009-03-24
I have two hard disks: one with Ubuntu and in the other I just installed Windows XP. Since I can't install XP on a hard drive that isn't the primary one (dammit microsoft), I set the second hard drive as the primary drive and installed XP.

XP worked like charm (after I had to download and install the network, display, sound, and a long list of other drivers), but when I set again my first hard drive as primary hard drive (the one with Ubuntu on it), Ubuntu works perfectly, but when I try to boot XP from GRUB, it just hangs on "Starting Up..."

So, here are my two menu.lst entries and my fdisk:

```
 title Ubuntu
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=4c479c1d-1907-4c81-8177-21fc18c1f6ba ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic
savedefault

title Windows
root (hd1,0)
chainloader +1
savedefault 0 
```

```
 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfffe9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa110a110

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS 
```

I already tried re-setuping GRUB (is it called in that way?) and setting rootnoverify on the Windows entry. Is there another solution?

EDIT: [http://ubuntuforums.org/showpost.php?p=6536346&postcount=1](http://ubuntuforums.org/showpost.php?p=6536346&postcount=1)

Thanks mhgsys anyway.

---

### Post by tchoklat on 2009-03-24
[I]title Windows 95/98/NT/2000 
root (hd1,0) 
makeactive 
chainloader +1[/I]

---

### Post by mhgsys on 2009-03-24
try 

```

title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


```
 
when xp is set as your secondary disk
this will fool the "damn microsoft" to be primary, because that what it wants to be

EDIT: I just saw your edit btw, 
maybe it's easier to just reply instead of editing,
anyway, nice that it's solved.
please edit your thread and place [solved]

---

