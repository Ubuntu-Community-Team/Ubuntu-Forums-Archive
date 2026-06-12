---
title: "Grub Problem from USB Hard Drive"
date: 2009-05-29
forum: General Help
---

### Post by ChrisB111 on 2009-05-29
I have intrepid installed on my external hard drive, it was working fine, I installed Grub to my external hard drive to avoid overwriting my computers main bootloader. 

When installing jaunty to another partition on my external hard drive I told it to install grub to my external hard drive as I had done with intrepid. 

Jaunty boots fine but the installer detected my other ubuntu system and added an entry for it in the grub menu list. This I think was pointing at the wrong partition. When I tried to boot off this entry I got the error "22 Not Such Partition". Using the grub root and find commands I worked out my intrepid partition is (hd0,4) not (hd1,4). I tried booting as such and got the error "29 Disk write error".

I have included some hopefully useful info.

Thanks,

Chris

Ubuntu Jaunty Grub Boot Lines:```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d636c229-b86a-4eda-a642-126a870fb315
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d636c229-b86a-4eda-a642-126a870fb315 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```
Ubuntu Intrepid Grub Boot Lines:```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb5)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b63e8267-57cd-4184-aa62-cdac5bbef56a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot
```

fdisk output```
chris@chris-desktop:~$ sudo fdisk -l
[sudo] password for chris:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe655fbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ebf41fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6438    51713203+   7  HPFS/NTFS
/dev/sdb2            6439       19457   104575117+   5  Extended
/dev/sdb5           13004       19273    50363743+  83  Linux
/dev/sdb6           19274       19457     1477948+  82  Linux swap / Solaris
/dev/sdb7            6439       12817    51239254+  83  Linux
/dev/sdb8           12818       13003     1494013+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by wireonfire on 2009-05-29
[http://www.gnu.org/software/grub/manual/grub.html#makeactive](http://www.gnu.org/software/grub/manual/grub.html#makeactive)

29 : Disk write errorThis error is returned if there is a disk write error when trying to write to a particular disk. This would generally only occur during an install of set active partition command. 

Is the partition primary?  Doesn't look like it is (since sdb2 is extended).  You can only makeactive on primary partition.

---

### Post by ChrisB111 on 2009-05-30
> **wireonfire said:**
> 
Is the partition primary?  Doesn't look like it is (since sdb2 is extended).  You can only makeactive on primary partition.

Don't quite understand where/what this makeactive thing is but, what's the solution. Can I boot my other ubuntu system somehow?

Chris

---

### Post by ChrisB111 on 2009-05-31
I have found the solution, removing the savedefault command did the trick. I think because the savedefault command accesses the grub menu.lst and you used the root command to access another partition you get a disk write error (29).

Chris

---

