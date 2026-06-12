---
title: "Help mounting a second hard drive"
date: 2009-05-04
forum: General Help
---

### Post by DFord425 on 2009-05-04
Im trying to mount a second hard drive that i formated with ext4. I tried using this how-to [http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3&page=2](http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3&page=2) but it doesnt work, im not sure if its bc im using 9.04 or for another reason. When i run this command:
```
sudo mount -a
```
I get this error
```
dford@Cobra:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Can anyone help me?

---

### Post by taurus on 2009-05-04
Post the outputs of these commands?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by DFord425 on 2009-05-04
> **taurus said:**
> Post the outputs of these commands?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

```

dford@Cobra:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006801

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    5  Extended
/dev/sda5               1      121601   976759969+  83  Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18657   149862321   83  Linux
/dev/sdb2           18658       19452     6385837+   5  Extended
/dev/sdb5           18658       19452     6385806   82  Linux swap / Solaris

```
```
dford@Cobra:~$ sudo blkid
/dev/sdb1: UUID="a3905aa2-485c-4093-a114-b30e9fae714a" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="d5e7d080-e839-48eb-b25d-f862eadeb605" 
/dev/sda5: LABEL="Multimedia" UUID="95436974-85a1-444c-bdf1-e03561b452b3" TYPE="ext4" 

```
```
dford@Cobra:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=a3905aa2-485c-4093-a114-b30e9fae714a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d5e7d080-e839-48eb-b25d-f862eadeb605 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda5 	/Multimedia 	ext3 defaults 0 0

```
```
dford@Cobra:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             141G   41G   93G  31% /
tmpfs                 3.9G     0  3.9G   0% /lib/init/rw
varrun                3.9G  104K  3.9G   1% /var/run
varlock               3.9G     0  3.9G   0% /var/lock
udev                  3.9G  152K  3.9G   1% /dev
tmpfs                 3.9G  108K  3.9G   1% /dev/shm
lrm                   3.9G  2.7M  3.9G   1% /lib/modules/2.6.28-11-generic/volatile
/home/dford/.Private  141G   41G   93G  31% /home/dfor

```

---

### Post by DFord425 on 2009-05-04
i think i see my problem, i have it listed as ext3 in fstab.

---

