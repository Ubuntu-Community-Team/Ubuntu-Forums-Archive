---
title: "Cant Mount HD"
date: 2009-02-25
forum: General Help
---

### Post by Vrekk on 2009-02-25
When I try to mount the Vista half of my Hd I get an error saying 

mount_point cannot contain the following characters: newline,G_DIR_SEPARATOR (usually /)

Any help? My files are saved there and i need to get to them asap while booted into ubuntu

---

### Post by taurus on 2009-02-25
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```
If ntfs partition is what you want to mount, install ntfs-config and use it to configure your ntfs partition.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by Vrekk on 2009-02-25
```
brett@brett-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d8c7d8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         131     1052226   82  Linux swap / Solaris
/dev/sda2             631       60800   483315525    f  W95 Ext'd (LBA)
/dev/sda3             132         630     4008217+  83  Linux
/dev/sda5           30385       60800   244316488+   7  HPFS/NTFS
/dev/sda6             631       29628   232926372   83  Linux
/dev/sda7           29629       30384     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order
brett@brett-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d89990a7-2081-49ad-b5d5-b02b8f2604a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=a3d52c7e-4aca-413b-82e0-bdc30393de91 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
brett@brett-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             219G  3.3G  205G   2% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  100K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1010M   1% /dev
tmpfs                1012M  104K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile
brett@brett-desktop:~$ 

```

It is an ntfs, but i have been able to mount it in the past, what changed?

---

### Post by taurus on 2009-02-25
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two entries at the end of it.

```

/dev/sda3   /media/sda3   ext3   defaults   0   2
/dev/sda5   /media/sda5   ntfs-3g   defaults,locale=en_US.UTF-8  0  0

```
Save it and then create two new mount points and mount them.

```
sudo mkdir /media/sda3 /media/sda5
sudo mount -a
df -h
```
p.s.  If you are running vista from /dev/sda5, make sure you shut it down cleanly.  Otherwise, Ubuntu would have a hard time to mount it without using the force option.

---

### Post by Vrekk on 2009-02-25
Thanks its working great now.
If I knew how to changed the title to [Solved] I would can someone fill me in real fast?

---

### Post by absolutezero1287 on 2009-02-26
It should be in "Thread Tools".

---

