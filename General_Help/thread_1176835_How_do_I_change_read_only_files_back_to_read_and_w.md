---
title: "How do I change read only files back to read and write"
date: 2009-06-02
forum: General Help
---

### Post by ozguitarplayer on 2009-06-02
Hi,
I don't know how it happened but now I can 'read only' files that are on another partition on the same hard drive as my Ubuntu operating system.
How do I change it back to read and write?

---

### Post by albinootje on 2009-06-02
> **ozguitarplayer said:**
> Hi,
I don't know how it happened but now I can 'read only' files that are on another partition on the same hard drive as my Ubuntu operating system.
How do I change it back to read and write?

It depends on whether the whole filesystem is mounted read only or not.
Which file system is that partition having ? ext2,ext3,fat32,ntfs ?

Can you post the output of :
```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by ozguitarplayer on 2009-06-02
Hi albinoote,
The file system is ext3, and it is both sda3 & sda4 that I can now only read and not write to.
Here is the output of the commands you wanted;  

nigel@LapUbu:~$ sudo fdisk -l
[sudo] password for nigel: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c110b3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         777     6241221   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda3            1566        4679    25013205   83  Linux
/dev/sda4   *         778        1565     6329610   83  Linux
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4026 MB, 4026531328 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         490     3932128    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(488, 254, 63) logical=(489, 135, 29)
nigel@LapUbu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ec68c7e-b6ab-43f9-abd0-34ff1f26b149 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=faf7ca58-e53d-4452-b68c-eca087b328b7 none   swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
nigel@LapUbu:~$

---

### Post by MichaelSammels on 2009-06-02
Another way in which this can be done is by installing the Storage Device Manager:

```
sudo apt-get install pysdm
```
```
sudo pysdm
```

---

### Post by albinootje on 2009-06-02
> **ozguitarplayer said:**
> 
The file system is ext3, and it is both sda3 & sda4 that I can now only read and not write to.

Okay, thanks for the info. 
It sounds like you're trying to write as normal user to those ext3 partitions.
Can you create a new directory on it like this e.g. (assuming you have /dev/sda3 mounted on /media/sda3, and assuming that you are using the user account that was created during the Ubuntu installation, which has uid 1000) :
```

sudo mkdir /media/sda3/test
sudo chown 1000:1000 /media/sda3/test

```
After this, try to read and write in /media/sda3/test/

---

### Post by ozguitarplayer on 2009-06-02
all sorted, thanks very much

---

