---
title: "trouble automaounting extra drive after upgrading to 7.10"
date: 2007-10-22
forum: Desktop Environments
---

### Post by sjoseph on 2007-10-22
After upgrading, I am not able to get sdc5 to automount. I can mount manually. You'll not that the UUID is different in fstab, but when i change it to the one below, i can't even mount manually. any help would be appreciated.

here are result for blkid:
/dev/sda1: UUID="8C4E-3E1E" TYPE="vfat" 
/dev/sdb1: UUID="13762edf-2616-47d1-8ce1-50ede4736428" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="940552e4-73af-4788-aa36-cae4f40fb47e" 
/dev/sdc5: UUID="9731-6BB5" TYPE="vfat" 

and here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=13762edf-2616-47d1-8ce1-50ede4736428 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=940552e4-73af-4788-aa36-cae4f40fb47e none            swap    sw              0       0
# /dev/sdc5
UUID=13762edf-2616-47d1-8ce1-50ede4736428 /media/sdc5 vfat defaults 0 0

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by sjoseph on 2007-10-23
by the way, i struggled with the same issue in Feisty, with your help i found that the UUID was listed wrong in fstab. when i corrected that the drive automounted. now in 7.10, it appears the issue is the same, but when i correct the UUID in fstab, it not doesn't automount, when i try to mount it manually, i get 'you don't have the permission to mount this drive'.

---

### Post by sjoseph on 2007-10-23
no ideas anyone!!!! must i beg...

---

### Post by sjoseph on 2007-10-25
still no thoughts...

---

### Post by taurus on 2007-10-25
> **sjoseph said:**
> After upgrading, I am not able to get sdc5 to automount. I can mount manually. You'll not that the UUID is different in fstab, but when i change it to the one below, i can't even mount manually. any help would be appreciated.

here are result for blkid:
/dev/sda1: UUID="8C4E-3E1E" TYPE="vfat" 
/dev/sdb1: UUID="13762edf-2616-47d1-8ce1-50ede4736428" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="940552e4-73af-4788-aa36-cae4f40fb47e" 
/dev/sdc5: UUID="9731-6BB5" TYPE="vfat" 

and here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=13762edf-2616-47d1-8ce1-50ede4736428 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=940552e4-73af-4788-aa36-cae4f40fb47e none            swap    sw              0       0
# /dev/sdc5
**[COLOR="Blue"]UUID=13762edf-2616-47d1-8ce1-50ede4736428 /media/sdc5 vfat defaults 0 0[/COLOR]**

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the UUID for /dev/sdc5 with the actual device, /dev/sdc5.

```
/dev/sdc5   /media/sdc5    vfat     iocharset=utf8,umask=000   0   0
```
Save it and reboot.

---

### Post by sjoseph on 2007-10-26
thanks for the idea, still no automount, and this way, without the UUID, i can't even mount manually (when i try to through nautilus).

---

### Post by taurus on 2007-10-26
Post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by der_joachim on 2007-10-26
If you have more than one cores or processors, chances are that your /etc/init.d/rc contains the following line:
```

CONCURRENCY=shell

```

It is a tweak to better use the multiple cores or processors while booting ep IIRC. Change it back to
```

CONCURRENCY=none

```

and HAL will be functional again, thus re-enabling automounting.

---

### Post by sjoseph on 2007-10-26
Disk /dev/sda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x053a053a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2494    20033023+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19270f6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9541    76638051   83  Linux
/dev/sdb2            9542        9729     1510110    5  Extended
/dev/sdb5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
4 heads, 17 sectors/track, 5745911 cylinders
Units = cylinders of 68 * 512 = 34816 bytes
Disk identifier: 0x47f5f614

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2     5745911   195360940    f  W95 Ext'd (LBA)
/dev/sdc5               2     5745911   195360931+   b  W95 FAT32

---

### Post by sjoseph on 2007-10-26
thanks again, but the CONCURRENCY=none in that file..

---

### Post by taurus on 2007-10-26
What happens if you try to mount it by hand from a terminal?

```
sudo mount -t vfat /dev/sdc5 /media/sdc5
df -h
```

---

### Post by sjoseph on 2007-10-28
When i do that, it mounts...

sjoseph@sjoseph-desktop:~$ sudo mount -t vfat /dev/sdc5 /media/sdc5
[sudo] password for sjoseph:
sjoseph@sjoseph-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              72G  3.7G   65G   6% /
varrun                252M   88K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  100K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile

---

### Post by sjoseph on 2007-10-28
Oh Boy, I hate being a newbie..Turns out that I needed to have a directory created in /media folder for the sdc5 to mount..is this true..because now it's working...

---

### Post by sjoseph on 2007-10-29
So now I have a new problem with that drive, it is automounting as sdc5, but now I can't write to it, it won't allow me access. the fstab line is

/dev/sdc5 	/media/sdc5 vfat defaults 0 0

and it's mounting in the media file, but only the root has permissions, and in terminal it won't let me chown to myself. what now...

---

