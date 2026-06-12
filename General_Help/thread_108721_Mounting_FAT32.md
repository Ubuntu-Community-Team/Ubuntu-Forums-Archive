---
title: "Mounting FAT32"
date: 2005-12-26
forum: General Help
---

### Post by tig4 on 2005-12-26
So i did formatted a HD with PartitionMagic in Windows, now in Ubuntu when i use:

sudo mount -t vfat /dev/hdd1 /drv/storage

it throws an error:

mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

am i trying to mount the wrong type of drive?

mount -l returns:

/dev/hdb1 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-k7/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /drv/windows type ntfs (rw,nls=utf8,umask=0222)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


doesnt look like its even recognizing the drive.

---

### Post by kenweill on 2005-12-26
Try
sudo fdisk -l

Then post your results.

---

### Post by tig4 on 2005-12-26
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7169    57584961   83  Linux
/dev/hdb2            7170        7476     2465977+   f  W95 Ext'd (LBA)
/dev/hdb5            7170        7476     2465946   82  Linux swap / Solaris

Disk /dev/hdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               2       14946   120045712+   f  W95 Ext'd (LBA)
/dev/hdd5               2       14946   120045681    b  W95 FAT32

---

### Post by tig4 on 2005-12-26
Just got it:

It was hdd5.

Thanks so much

---

### Post by kenweill on 2005-12-26
K.
No probs.
Just post your questions whenever you have problems.

---

