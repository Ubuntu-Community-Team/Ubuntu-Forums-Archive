---
title: "Hardrive owned by root"
date: 2009-01-16
forum: General Help
---

### Post by Katshaus on 2009-01-16
Hi,

I have 8.10 installed, with two hardrives - one dedicated to Ubuntu, and one partitioned with Windows & Ubuntu. I can't access the partition on the second drive, as it shows as being owned by root and privileges only for owner and group. There's nothing on ther yet but my first drive is nearly full and need the extra space - how do i change ownership of the drive?

ls -l shows this:

drwxrwx---  root  plugdev  (mb) (time) (date) sdb1

I am obviously a complete newbie to command line...

Cheers,
Katshaus

---

### Post by Ahadiel on 2009-01-16
How are you mounting it?

---

### Post by utnubuuser on 2009-01-16
And could you chmod it, or chown it?

---

### Post by Katshaus on 2009-01-16
Don't know much about mounting - I partitioned it during install, so it's mounted the default method that ubuntu uses during that process

I tried chmod and chown but it hasn't worked - maybe wrong syntax??

chmod u+r sda1

as super user

chown katshaus sda1

as root

---

### Post by iaculallad on 2009-01-16
> **Katshaus said:**
> Don't know much about mounting - I partitioned it during install, so it's mounted the default method that ubuntu uses during that process

I tried chmod and chown but it hasn't worked - maybe wrong syntax??

chmod u+r sda1

as super user

chown katshaus sda1

as root

Syntax should be:

```
sudo chown -R katshaus:katshaus /mount_point
sudo chmod -R 700 /mount_point
```

Did you create a mountpoint for your drive/partition?

---

### Post by Ahadiel on 2009-01-16
Paste the contents of */etc/fstab* and the output of *sudo fdisk -l*.

---

### Post by SnakeHips on 2009-01-16
If I read you right you want to access the files n stuff on the second drive from the first drive? 

posting the output of the following will help
```
mount
```

and here is a great guide to fstab

[http://ubuntuforums.org/showthread.php?t=1040938](http://ubuntuforums.org/showthread.php?t=1040938)

---

### Post by Katshaus on 2009-01-16
Output from sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b18a353

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            3649        9729    48845632+  83  Linux
/dev/sda3            2433        3648     9767520   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       30394   141741495   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)
katshaus@DaKatHaus:/$

---

### Post by Katshaus on 2009-01-16
sdb2 - wrong disk mentioned earlier

---

### Post by Katshaus on 2009-01-16
snakehips - yes that is precisely what I want to do. i'm still migrating from Windows

Output from mount

katshaus@DaKatHaus:/$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw,relatime)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /media/sdb2 type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/katshaus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=katshaus)
/dev/sdc1 on /media/BLACK_BUG type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by Katshaus on 2009-01-16
Contents of /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=58994de9-8f00-42c1-a384-af682d2a0cb8 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda2
UUID=cff72030-60d3-4bbd-9796-8f3c77d0f303 /home           ext3    defaults,relatime        0       2
# /dev/sdb1
UUID=AC50F33850F3083A /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=0beafe5c-a893-45dd-aa5c-78985c48f573 /media/sdb2     ext3    defaults,relatime        0       2
# /dev/sda3
UUID=8ac42d7b-5b3f-411b-8fb5-55eb229cc433 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
~

---

### Post by Katshaus on 2009-01-16
iaculallad - cheers - simple syntax problem. Thanks everyone!

---

