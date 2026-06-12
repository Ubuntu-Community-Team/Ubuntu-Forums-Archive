---
title: "Error 12: Invalid Device Requested"
date: 2009-05-25
forum: General Help
---

### Post by naszaklasa on 2009-05-25
Hi,

I have had Ubuntu installed while having XP on the other partition. Thus, I was able to dual boot using Grub. I have installed Windows 7 to try it out over XP, and my Grub was gone so I was unable to log into Ubuntu. Thus, I restored the Grub using live CD. The problem is that now when I click on Windows boot in Grub, I get the Error 12.

The Windows partition has ~38.8GB.


Here are the outputs:
```

desktop:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x47cbac59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065   122881184    61432560    f  W95 Ext'd (LBA)
/dev/sda2   *   122881185   266245244    71682030    7  HPFS/NTFS
/dev/sda3       266245245   409609304    71682030    7  HPFS/NTFS
/dev/sda4       409609305   625137344   107764020    7  HPFS/NTFS
/dev/sda5           16128   122881184    61432528+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb393b393

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    75746474    37873206    7  HPFS/NTFS
/dev/sdb2   *    75746475    82156409     3204967+  82  Linux swap / Solaris
/dev/sdb3        82156410   143364059    30603825    f  W95 Ext'd (LBA)
/dev/sdb4       143364123   312576704    84606291    7  HPFS/NTFS
/dev/sdb5        82156473   143364059    30603793+  83  Linux

```


```

-desktop:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=    16065, size=122865120, Id= f
/dev/sda2 : start=122881185, size=143364060, Id= 7, bootable
/dev/sda3 : start=266245245, size=143364060, Id= 7
/dev/sda4 : start=409609305, size=215528040, Id= 7
/dev/sda5 : start=    16128, size=122865057, Id= 7
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 75746412, Id= 7
/dev/sdb2 : start= 75746475, size=  6409935, Id=82, bootable
/dev/sdb3 : start= 82156410, size= 61207650, Id= f
/dev/sdb4 : start=143364123, size=169212582, Id= 7
/dev/sdb5 : start= 82156473, size= 61207587, Id=83


```



```

-desktop:~$ sudo pico /boot/grub/menu.lst
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            1ecbc713-380a-4c59-af43-1e5bd31531b9
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=1ecbc713-380a-4c59-af43-1e5bd31531b9 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            1ecbc713-380a-4c59-af43-1e5bd31531b9
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=1ecbc713-380a-4c59-af43-1e5bd31531b9 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            1ecbc713-380a-4c59-af43-1e5bd31531b9
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows 7
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


```

---

### Post by naszaklasa on 2009-05-25
I have been playing with it for the past couple hours and I'm about to give up :(

---

