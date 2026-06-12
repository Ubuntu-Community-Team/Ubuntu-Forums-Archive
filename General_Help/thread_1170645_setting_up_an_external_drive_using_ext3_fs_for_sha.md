---
title: "setting up an external drive using ext3 fs for sharing"
date: 2009-05-26
forum: General Help
---

### Post by jrz on 2009-05-26
I've been trying to find a "How To" on formatting and setting up an external drive which can be shared between several systems, all running Ubuntu, and several different users all having full permissions.

Using Gparted I've been able to format the drive as ext3, and it mounted displaying an icon on the Desktop, but after unmounting the drive I've been unable to get it to display an icon on the Desktop again. I can see the drive at /media/disk and fdisk -l and df -h give the following output.

sudo fdisk -l
[sudo] password for joe: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3eed1473

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            1276       19966   150135457+  83  Linux
/dev/sda3           19967       38657   150135457+  83  Linux
/dev/sda4           38658       38913     2056320   82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc55b20f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   83  Linux

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.7G  5.3G  4.0G  58% /
tmpfs                1002M     0 1002M   0% /lib/init/rw
varrun               1002M  328K 1002M   1% /var/run
varlock              1002M     0 1002M   0% /var/lock
udev                 1002M  168K 1002M   1% /dev
tmpfs                1002M  612K 1002M   1% /dev/shm
lrm                  1002M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda3             141G  121G   14G  90% /backup
/dev/sda2             141G  129G  5.8G  96% /home
/dev/sdf1             459G  199M  435G   1% /media/disk

So far I'm unable to write to the drive, and can only view it. If there is a "How To" on making an ext3 fs drive work, I've been unable to find it. Just for curiosity, I formatted the drive as ntfs, and then it mounts displaying an icon each time and is readable and writable. When formatted as ext3 it no longer mounts displaying an icon, and I can't write to the drive.

---

