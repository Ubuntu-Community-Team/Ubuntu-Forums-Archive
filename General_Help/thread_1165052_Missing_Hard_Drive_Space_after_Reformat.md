---
title: "Missing Hard Drive Space after Reformat"
date: 2009-05-20
forum: General Help
---

### Post by davidmigl on 2009-05-20
I have a 1TB External hard drive. I just reformatted it as ext3 using gparted.

It's new name is 1000.2 GB Media. Gparted says its size is 931.51 GiB, 14.81 GiB used, leaving 916.70 GiB unused. If I right click on the drive and choose properties in nautilus, it says total capacity is 916.9 GB, with 46.8 Gb used and 870.1 Gb free.  Under "contents," it reports "1 item, with size 16.0 KB (some contents unreadable)."

```
sudo fdisk -l
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
```
(the previous wasn't the entire output, just the part relevant to this drive)

```
 df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            152371456  68651696  75979648  48% /
tmpfs                   254656         0    254656   0% /lib/init/rw
varrun                  254656       364    254292   1% /var/run
varlock                 254656         0    254656   0% /var/lock
udev                    254656       156    254500   1% /dev
tmpfs                   254656      1368    253288   1% /dev/shm
lrm                     254656      2392    252264   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdc1            244136352 215082528  29053824  89% /media/MyBook250
/dev/sdb1            961432072    204568 912389504   1% /media/Elements

```

I have the drive mounted to /media/Elements. I am running jaunty. There is a lost+found folder with no contents on the drive, but nothing else. Additionally, nobody but root seems to have permissions to write to the drive.

How can I get this 46.8 GB of space back?

Thanks for your help!

---

### Post by davidmigl on 2009-06-18
It appears that the ext3 and ext4 filesystems reserve a certain percentage of space for their journal. So that's where the space is going.

---

### Post by HermanAB on 2009-06-18
If you want more efficient use of disk space, use JFS or XFS.  Both are more efficient and faster than Ext3.  The main reason these are not popular is because of 'not invented here' syndrome.

---

