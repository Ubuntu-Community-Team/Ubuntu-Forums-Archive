---
title: "double boot problem"
date: 2009-02-17
forum: General Help
---

### Post by oknos on 2009-02-17
Hi there, i have installed ubuntu interpid on a HP laptop with preinstalled vista.
I have mounted the windows partition as /windows so i can access my files. The double boot works just fine but the thing is that i can't access the windows partition. Ubuntu recognizes it but when i open the windows file its blank. Sometimes though it works fine without me doing anything. 

if anyone could help i'd appreciate it

thanks in advance.

---

### Post by oknos on 2009-02-17
pleeeeease help!!!  :(

---

### Post by taurus on 2009-02-17
Did you install Ubuntu on it own partition (not wubi)?  How did you mount your ntfs partition?

Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by oknos on 2009-02-17
this is what i get```
doriangray@doriangray-laptop:~$ sudo fdisk -l
[sudo] password for doriangray: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82fa82fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27241   218807568    7  HPFS/NTFS
/dev/sda2           29281       30401     9004432+   7  HPFS/NTFS
/dev/sda3           27242       28942    13663282+  83  Linux
/dev/sda4           28943       29280     2714985    5  Extended
/dev/sda5           28943       29280     2714953+  82  Linux swap / Solaris

Partition table entries are not in disk order
doriangray@doriangray-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=81153571-7dfb-4987-bd2b-61e00a7e8ab1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=39C47A23095BF56C /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=b9f9be78-1105-4525-b0da-637f423a45cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
doriangray@doriangray-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              13G  3,0G  9,3G  25% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  100K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2,8M 1009M   1% /dev
tmpfs                1012M  228K 1012M   1% /dev/shm
lrm                  1012M  2,0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1             209G  191G   19G  92% /windows

```

---

### Post by taurus on 2009-02-17
> **oknos said:**
> this is what i get```
doriangray@doriangray-laptop:~$ sudo fdisk -l
[sudo] password for doriangray: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82fa82fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27241   218807568    7  HPFS/NTFS
/dev/sda2           29281       30401     9004432+   7  HPFS/NTFS
/dev/sda3           27242       28942    13663282+  83  Linux
/dev/sda4           28943       29280     2714985    5  Extended
/dev/sda5           28943       29280     2714953+  82  Linux swap / Solaris

Partition table entries are not in disk order
doriangray@doriangray-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=81153571-7dfb-4987-bd2b-61e00a7e8ab1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
**UUID=39C47A23095BF56C /windows        ntfs    defaults,umask=007,gid=46 0       1**
# /dev/sda5
UUID=b9f9be78-1105-4525-b0da-637f423a45cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
doriangray@doriangray-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              13G  3,0G  9,3G  25% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  100K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2,8M 1009M   1% /dev
tmpfs                1012M  228K 1012M   1% /dev/shm
lrm                  1012M  2,0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1             209G  191G   19G  92% /windows

```

I would replace the entry in /etc/fstab for windows partition, /dev/sda1, from what you have now to this.

```
UUID=39C47A23095BF56C   /windows   ntfs-3g   defaults,locale=en_US.UTF-8   0   0
```
Assuming you are in the US.  Save it and reboot.

---

### Post by oknos on 2009-02-17
That solved my problem. Thanks a lot taurus :D. If by any chance anything unexpected comes up I will refresh the thread.

---

### Post by taurus on 2009-02-17
By the way, I guess you don't want to also mount the other ntfs partition, /dev/sda2?

---

