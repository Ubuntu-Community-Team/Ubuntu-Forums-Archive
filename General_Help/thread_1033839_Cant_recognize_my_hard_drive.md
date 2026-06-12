---
title: "Cant recognize my hard drive"
date: 2009-01-07
forum: General Help
---

### Post by arionadouble on 2009-01-07
how can i view my hardrive i could during my first install but i had 64bit and now have installed 32bit and cant seem to find away to access my harddrive

---

### Post by taurus on 2009-01-07
If you want to access a partition/harddrive, you first need to mount it.

What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by arionadouble on 2009-01-07
arion@ubuntu:~$ sudo fdisk -l
[sudo] password for arion: 
Sorry, try again.
[sudo] password for arion: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8028053

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29246   234918460    7  HPFS/NTFS
/dev/sda2           29247       30401     9277537+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x385f8db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS
arion@ubuntu:~$ sudo blkid
/dev/sda1: UUID="4C2881692881533E" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/loop0: UUID="57727d65-6f8a-4111-b421-bd55b8f8cb53" TYPE="ext3" 
/dev/sdb1: UUID="0830F6EC30F6DF9C" TYPE="ntfs" 
arion@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
arion@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.3G  3.3G  4.6G  42% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  324K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.9M 1010M   1% /dev
tmpfs                1012M  316K 1012M   1% /dev/shm
/dev/sda1             225G  133G   92G  60% /host
lrm                  1012M  2.0M 1011M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             373G  188G  185G  51% /media/disk
/dev/sda2             8.9G  8.0G  888M  91% /media/FACTORY_IMAGE
arion@ubuntu:~$

---

### Post by arionadouble on 2009-01-07
soo any ideas

---

