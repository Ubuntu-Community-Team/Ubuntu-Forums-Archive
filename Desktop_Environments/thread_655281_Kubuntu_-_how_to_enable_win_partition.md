---
title: "Kubuntu - how to enable win partition"
date: 2008-01-01
forum: Desktop Environments
---

### Post by Sain on 2008-01-01
Ok, I've just started using Kubuntu (used Gnome before), and for some reason it does not see windows partition.

When I enter disk & filesystems properties in system settings it shows that win partition is disabled, although when I try to modify it, says "enabled at startup".

How can I access Win partition?

---

### Post by taurus on 2008-01-01
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Sain on 2008-01-01
Sure.


```
sudo fdisk -l


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d9e98b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5354    43005942    7  HPFS/NTFS
/dev/sda2            5355        6723    10996492+   5  Extended
/dev/sda3            6724       14593    63215775    c  W95 FAT32 (LBA)
/dev/sda5            6629        6723      763056   82  Linux swap / Solaris
/dev/sda6            5355        6628    10233342   83  Linux

Partition table entries are not in disk order

```
```
cat /etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=3afa7527-90b6-44fc-b259-53f03b7be30c / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
LABEL=Windows /media/win ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda3
LABEL=DOCS /media/docs vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda5
UUID=4d0caa74-84ca-11dc-8235-a1976958ae8d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0


```

```
df -h


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.7G  4.2G  5.0G  46% /
varrun               1014M  140K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   76K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   17M  998M   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              61G   40G   21G  67% /media/docs

```

---

### Post by taurus on 2008-01-01
Can you edit your /etc/fstab

```
kdesu kwrite /etc/fstab
```
and replace these

```

[COLOR="Blue"]LABEL=Windows[/COLOR] /media/win ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1

```
with

```

**/dev/sda1** /media/win ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1

```
Save it and then run

```
sudo mount -a
df -h
```

If /media/win still doesn't show up from the last command, try to see if you can mount it by hand from a terminal with

```
sudo mount -t ntfs /dev/sda1 /media/win
```

It will probably complain about how you didn't shutdown your windows partition cleanly.

---

### Post by Sain on 2008-01-01
Thanks, it's fine now!

I edited fstab and then  force-mounted the partition. It worked, but drive didn't show up in storage media. Computer restart did the trick for that aswell...

---

