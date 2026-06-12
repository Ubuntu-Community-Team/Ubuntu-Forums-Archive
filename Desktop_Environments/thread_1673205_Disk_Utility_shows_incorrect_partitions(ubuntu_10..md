---
title: "Disk Utility shows incorrect partitions(ubuntu 10.04)"
date: 2011-01-22
forum: Desktop Environments
---

### Post by imkaushal on 2011-01-22
This is the result of  ```
sudo fdisk -l
```:
```
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c0a0a3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528       13054    52428127+   7  HPFS/NTFS
/dev/sda3           13055       60801   383527457+   5  Extended
/dev/sda4           16971       31580   117354793+   7  HPFS/NTFS
/dev/sda5           13055       16803    30112768   83  Linux
/dev/sda6           16804       16970     1340416   82  Linux swap / Solaris
/dev/sda7           31581       46190   117354793+   7  HPFS/NTFS
/dev/sda8           46191       60801   117362826    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2cf32cf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2433    19543041    7  HPFS/NTFS
/dev/sdb2            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sdb5            2434        6081    29302528+   b  W95 FAT32
/dev/sdb6            6082        9729    29302528+   7  HPFS/NTFS

```the 80GB HDD(sdb) is correct....
but 500GB HDD(sda) shows weird info....it used to show correct info initially...
but two weeks ago something went wrong and i had to reinstall GRUB.

this is the result of ```
df
```after mounting all the available partitions:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             29639756   4632612  23501508  17% /
none                   1024068       312   1023756   1% /dev
none                   1028572       344   1028228   1% /dev/shm
none                   1028572        80   1028492   1% /var/run
none                   1028572         0   1028572   0% /var/lock
none                   1028572         0   1028572   0% /lib/init/rw
/dev/sr0               3993166   3993166         0 100% /media/THE_SECRET
/dev/sdb1             19543040  17234696   2308344  89% /media/Windowswala
/dev/sdb5             29288208  10341360  18946848  36% /media/2C73-135A
/dev/sdb6             29302528  21203140   8099388  73% /media/B200B41A00B3E40F
/dev/sda1             52428092    271368  52156724   1% /media/C_WIN7
/dev/sda2             52428124  10861760  41566364  21% /media/d_win
/dev/sda4            117354792  41423880  75930912  36% /media/LG1
/dev/sda7            117354792  97970508  19384284  84% /media/LG2
/dev/sda8            117362824  83097000  34265824  71% /media/LG3

```A Screenshot of the Disk Utility is attached.

How can I remove the wrong partition info?:mad::confused:](*,)

Thanks in advance!!!

---

### Post by aldee96 on 2011-01-22
bump
same probs with me

---

### Post by imkaushal on 2011-01-23
please help us somebody......8-[

---

### Post by imkaushal on 2011-01-24
:twisted: :icon_frown: :shock: :shock: 8-[ !!!!!

Please Help.....

---

### Post by imkaushal on 2011-01-25
This is ridiculous....
 
Why is no one helping out??? :o
 
Please help me.....

---

