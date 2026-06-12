---
title: "Root access"
date: 2006-01-10
forum: Desktop Environments
---

### Post by UnknownPg on 2006-01-10
is there anyway i can make my current user account access everything without logging into root. the reason i ask is because i try to access my windows partition from sda1 and it says i dont have the nesecessary permissions

---

### Post by aysiu on 2006-01-10
That's a mounting issue. See the fourth link of my signature (below).

---

### Post by UnknownPg on 2006-01-10
i did your link and it says there is no mount at 0

---

### Post by aysiu on 2006-01-10
[QUOTE=UnknownPg]i did your link and it says there is no mount at 0[/QUOTE] Okay, which part were you at when that error appeared, and what was the exact error?

---

### Post by UnknownPg on 2006-01-10
i changed it so it basically matches this

> proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0

 but i have my own letters now and then i did sudo mount -a and it gives me

mount: mount point 0 does not exist

---

### Post by aysiu on 2006-01-10
[QUOTE=UnknownPg]
 but i have my own letters now and then i did sudo mount -a and it gives me[/QUOTE] Did you follow all the other instructions, too, or just change /etc/fstab? What are your own letters (those are the ones that count)?

The only way I can help is if you post the output of these three commands: ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by UnknownPg on 2006-01-10
for fdisk -l
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11211    90044294    7  HPFS/NTFS
/dev/sda2           11212       19457    66235995    5  Extended
/dev/sda5           19333       19457     1004031   82  Linux swap / Solaris
/dev/sda6   *       11212       19332    65231869+  83  Linux

Partition table entries are not in disk order


for cat /etc/fstab
> ryan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /windows        ntfs   nls=utf8,umask=0222
0       0
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
ryan@ubuntu:~$


for df -h 

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              62G  4.1G   55G   7% /
tmpfs                 506M     0  506M   0% /dev/shm
tmpfs                 506M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda1              84G   48G   37G  57% /windows


---

### Post by soulestream on 2006-01-10
> /dev/sda1 /windows ntfs nls=utf8,umask=0222
0 0


that all should be on one line


soule

---

### Post by aysiu on 2006-01-10
[QUOTE=soulestream]that all should be on one line


soule[/QUOTE] Agreed. After that, type ```
sudo umount /windows
sudo mount -a
```

---

