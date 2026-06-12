---
title: "Dual Boot 2 hard drives"
date: 2009-01-24
forum: General Help
---

### Post by geome on 2009-01-24
Hello, I'm still rough on the edges for using linux, I just installed mythbuntu on one of my hard drives (set as master) and have a loaded copy of winxp pro on the other hard drive (set as slave). Both on the same IDE cable. 
What I want to do is boot into grub and be able to choose which one to go to. (rather than unplug the drive and boot into the other). This is what my menu.lst file looks like (uncommented), can someone please help me to get this to work. Both OS systems work great now, I just need a way to get a way to boot without disconnecting the cables. Thanks.


default		1
timeout		10

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c657be3a-f17f-4eef-8dcf-209168413cc2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c657be3a-f17f-4eef-8dcf-209168413cc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		c657be3a-f17f-4eef-8dcf-209168413cc2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c657be3a-f17f-4eef-8dcf-209168413cc2 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c657be3a-f17f-4eef-8dcf-209168413cc2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c657be3a-f17f-4eef-8dcf-209168413cc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c657be3a-f17f-4eef-8dcf-209168413cc2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c657be3a-f17f-4eef-8dcf-209168413cc2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c657be3a-f17f-4eef-8dcf-209168413cc2
kernel		/boot/memtest86+.bin
quiet

---

### Post by mikewhatever on 2009-01-24
Can you also post the output of <sudo fdisk -l>. We need to know which partition Windows is installed on, then, it should be fairly easy to add an entry to the menu.lst.

---

### Post by geome on 2009-01-24
Hi Mikewhatever, 
I was wondering why I could only find 8.3 gigs of free space for my disk drive when installing mythbuntu (was able to put the icon on the desktop whoo) I think when I was playing with gparted, the partitions on my first drive did not delete as I thought they did, anyway is there a way to fix this too, or do I have to scrub the drive and start new, or should I post this as a new thread? Plus tring to get winxp to boot on second HD. Thanks again for the Help!

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cd12cd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460       30515   233392320    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584       30515   232396258+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa567a567

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5235    42050106    7  HPFS/NTFS
/dev/sdb2            5236       30401   202145895    7  HPFS/NTFS

---

### Post by mikewhatever on 2009-01-24
Are you saying the root partition is sda6, and sda1 is the partition you wanted to delete?

As for adding Windows, try the following at the very end of menu.lst.

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows 
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

On the second thought, you may need to find out on which partition is GRUB installed, first <sudo grub>, then 
<grub> find /boot/grub/stage1>.

---

### Post by geome on 2009-01-25
Thanks!!!
I ended up wiping the drive completely, re-installing mythbuntu, and then adding this at the end. Works like a charm.

---

