---
title: "Grub error 17"
date: 2009-06-18
forum: General Help
---

### Post by Orangeyness on 2009-06-18
Hi there, I'm new to Linux, and have recently installed ubuntu. It was working beautifully and I was quite impressed. How ever I tried to install Vista on one of my other hard drives and set up a dual boot. Vista installed failed, not detecting one of my drives and not finding any it deems suitable, even after I formatted one of them... Anyway I'm not really worried about that, my problem is ever since then I have been greeted by "grub error 17" when I attempt to boot. Now I am forced to boot from the live cd. I have tried editing my menu.lst, device.map and so on, but I haven't made much progress. 
 
Heres what fdisk -l say,
  
                                 > Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd55b35a
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS
 
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62d69df4
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488381440    7  HPFS/NTFS
 
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5261c5b0
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18662   149902483+  83 Linux
/dev/sdc2           18663       19457     6385837+   5  Extended
/dev/sdc5           18663       19457     6385806   82  Linux swap / Solaris
 
Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcf9c4c3
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19457   156288321    7  HPFS/NTFS                         My menu.lst file currently is, 
  
                                 > 
#Generic... + 

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=24b5580e-df2f-42e5-89$
initrd          /boot/initrd.img-2.6.28-11-generic
quiet
 
title           Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=24b5580e-df2f-42e5-89$
initrd          /boot/initrd.img-2.6.24-23-generic
 
title           Ubuntu 8.04.2, memtest86+
root            (hd2,0)                         Any Help? 
Thanks.

---

### Post by merlinus on 2009-06-18
This may help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by joseph8832@live.com on 2009-06-18
Hi,
some of the software unable to process some functions you have to ask the linux admin

---

