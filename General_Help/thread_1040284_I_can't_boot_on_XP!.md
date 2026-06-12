---
title: "I can't boot on XP!"
date: 2009-01-15
forum: General Help
---

### Post by Fixman on 2009-01-15
This is my fdisk:

```
 Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa110a110

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9400    75505468+  83  Linux
/dev/sda2            9401        9729     2642692+   5  Extended
/dev/sda5            9401        9729     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
22 heads, 20 sectors/track, 710413 cylinders
Units = cylinders of 440 * 512 = 225280 bytes
Disk identifier: 0xbfffe9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      710412   156290630    7  HPFS/NTFS

```

And this is /boot/grub/menu.lst
```
 splashimage=(hd0,0)/boot/grub/splashimages/matrix.xpm.gz
default saved
timeout 5
color cyan/blue white/green

title Ubuntu
root (hd0,0)
savedefault 0
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=a2c75bfd-dc90-4a34-92e8-4b52e2b9e3f6 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Windows
root (hd1,0)
savedefault 0
chainloader +1

```

This worked perfectly when I had Windows Vista installed, but now I deleted windows vista and installed windows XP on the second hard drive, and when I try to boot on Windows all it gives me is a text saying "Starting up..." (like if I booted on Ubuntu with chainloader +1). Can anyone help me on this?

---

### Post by logos34 on 2009-01-15
take out the '0':

> title Windows
root (hd1,0)
savedefault **[COLOR="Red"]0[/COLOR]**
chainloader +1

  Try this:

> title Windows
root (hd1,0)
[COLOR="Blue"]makeactive[/COLOR]
savedefault
chainloader +1

---

