---
title: "after converting fat to ext4, suddenly there's less space"
date: 2009-05-10
forum: General Help
---

### Post by supersonicdarky on 2009-05-10
It wasn't an actual conversion. The process I followed was:
1. resize fat
2. create ext4
3. move some data
4. resize fat
5. resize ext4
6. continue doing 3 through 5 until no more data left
7. delete fat
8. resize ext4

Now after step 8, I suddenly lost 100gb of space (drive is 465gb).
```
kernel@fission ~ $ df -h /dev/sdb2
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             364G  341G  4.2G  99% /media/ext
kernel@fission ~ $ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f72a1c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1       60801   488384001   83  Linux
```
and according to gparted, the disk size is 465gb, but only 23gb free.

My guess is that since this is a somewhat old drive, there were bad blocks and gparted automatically added them to the ignore list. Is there a way I can check that? However I highly doubt that the drive would have 100gb of bad blocks. Any other opinions/suggestions are welcome.

2.6.29.2 amd64
Sidux (Debian sid)
Drive is external, connected though usb.

---

### Post by danwood76 on 2009-05-10
Ext4 will use more space when compared to fat32.
It reserves a certain amount for system use I think.

---

### Post by supersonicdarky on 2009-05-10
But 100gb? =/ And that still doesnt explain the difference between gparted and df. (unless the hidden stuff is ignored by gparted)

---

### Post by danwood76 on 2009-05-10
If you look at the df output there is actually 23GB free so gparted agrees with it.
I think its reserved about 20 GB for its needs, use a file browser to see the size of the files you have on the drive.

---

