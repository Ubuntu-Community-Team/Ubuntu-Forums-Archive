---
title: "internal harddrive not showing up"
date: 2008-01-11
forum: Desktop Environments
---

### Post by iyavin on 2008-01-11
Hi, I have an internal hard drive which I use to backup my system. I mount it on /mnt/backup. Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4 -- converted during upgrade to edgy
UUID=829b1d3b-0cd9-42c6-93a9-37161357cd14 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=4974100a-a926-4617-9ce2-2f57413a0b1d none swap sw 0 0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/sda5 -- converted during upgrade to edgy
UUID=3428-8DC7 /mnt/dual vfat iocharset=utf8,umask=000 0 0
# /dev/sdb1 -- converted during upgrade to edgy
UUID=814c854f-2a30-4aca-b2e6-783ed2e7e484 /mnt/backup ext3 defaults 0 0

It is indeed mounted on /mnt/backup and I can access without a problem. However, it doesn't seem to be visible to gparted or even fdisk -l  or df -lh (the result of these commands is shown below). My problem is that I would like to see how much free space I have left on that hard drive. There is probably some easy solution, but I can't figure it out. Any help is appreciated.

fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    7  HPFS/NTFS
/dev/sda2            6080       12980    55432282+   f  W95 Ext'd (LBA)
/dev/sda3           18975       19457     3879697+  12  Compaq diagnostics
/dev/sda4           12981       18974    48146805   83  Linux
/dev/sda5            6080        9903    30716248+   b  W95 FAT32
/dev/sda6            9904       12722    22643586    7  HPFS/NTFS
/dev/sda7           12723       12980     2072353+  82  Linux swap / Solaris

Partition table entries are not in disk order


df -lh

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              46G   24G   20G  56% /
varrun               1009M  112K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   80K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   35M  974M   4% /lib/modules/2.6.22-14-386/volatile
/dev/sda5              30G   20G  9.7G  68% /mnt/dual

---

### Post by dabang on 2008-01-11
Maybe it's too easy, but did you select /dev/sdb in gparted? Also, when running fdisk or cfdisk you need to point it to the right disk:

```
fdisk /dev/sdb
```

Just a guess.

---

### Post by iyavin on 2008-01-11
mmm... I don't think that's it. When I try

 sudo fdisk /dev/sdb1

or

  sudo fdisk /dev/sdb

it just replies back:

Unable to open /dev/sdb1
etc.

Any other ideas?

---

### Post by dabang on 2008-01-11
Hm, according to the comment in your /etc/fstab, it's /dev/sdb. You can't do
sudo fsdisk /dev/sdb1
because that would be a partition, you need to choose the whole disk with 
sudo fdisk /dev/sdb
If that doesn't work...

But maybe try
sudo cfdisk /dev/sdb

From man fdisk:
There  are  several  *fdisk programs around.  Each has its problems and
       strengths.  Try them in the  order  cfdisk,  fdisk,  sfdisk.   (Indeed,
       cfdisk  is a beautiful program that has strict requirements on the par&#8208;
       tition tables it accepts, and produces high quality  partition  tables.
       Use  it  if you can.  fdisk is a buggy program that does fuzzy things -
       usually it happens to produce reasonable results. Its single  advantage
       is  that it has some support for BSD disk labels and other non-DOS par&#8208;
       tition tables.  Avoid it if you can.  sfdisk is for hackers only -  the
       user  interface is terrible, but it is more correct than fdisk and more
       powerful than both fdisk and cfdisk.  Moreover, it can be  used  nonin&#8208;
       teractively.)

---

### Post by iyavin on 2008-01-11
sorry, maybe it wasn't clear from my last posting: I indeed tried both commands:

sudo fdisk /dev/sdb1

as well as 

sudo fdisk /dev/sdb

both gave the response quoted above with the respective sdb1 and sdb.
Looking in the folder /dev maybe this is not a surprise, because there is no mention of sdb or sdb1 anywhere. Now I am even more confused.

---

### Post by iyavin on 2008-02-04
Any other idea, anyone?

---

