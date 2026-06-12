---
title: "Can't mount file"
date: 2009-02-05
forum: General Help
---

### Post by bermu on 2009-02-05
Hi,

I'm a newbie, I just installed Ubuntu, the installation went well but I do have problem with my usb compact flash driver. 
I can see it has been detected but when I try to open I get message "Can't mount file ". 

Please help.

---

### Post by WelterPelter on 2009-02-05
Do you know the usb's formatting scheme?

---

### Post by taurus on 2009-02-05
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by bermu on 2009-02-05
Thanks guys,

I just tried to open files created in windows (NTFS) files and I'm able to open but the one I have problem is files created in unix, No I don't know the usb's formatting scheme.

I will do sudo fdisk -l and will post the output.

---

### Post by bermu on 2009-02-05
Here is the output

acmc@ac-desktop:/$ sudo fdisk -l
[sudo] password for ac:

Disk 
/dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63a363a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39439543+   7  HPFS/NTFS
/dev/sda2            4911        9525    37069987+  83  Linux
/dev/sda3            9526        9729     1638630    5  Extended
/dev/sda5            9526        9729     1638598+   b  W95 FAT32
acmc@ac-desktop:/$

---

### Post by taurus on 2009-02-05
Are you having problem mounting /dev/sda2?

---

### Post by bermu on 2009-02-05
taurus,

When I try to mount /dev/sda2, I get messgage " /dev/sda2 is already mounted.

---

### Post by taurus on 2009-02-05
See where it has been mounted to, mount point.  You need to access the mount point, not the device itself.

```
df -h
```

---

### Post by bermu on 2009-02-05
Sorry,

This is what I get when I try to mount /dev/sda2:

" Can't find /dev/sda2 in /etc/fsatb or etc/mtab

---

### Post by taurus on 2009-02-05
If /dev/sda2 has not been mounted, try to mount it with

```
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2 /media/sda2
ls -la /media/sda2
```

---

### Post by bermu on 2009-02-05
Ok, I will do it right now

---

### Post by bermu on 2009-02-05
Here is it,

ac@ac-desktop:/$ sudo fdisk -l
[sudo] password for acmc:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63a363a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39439543+   7  HPFS/NTFS
/dev/sda2            4911        9525    37069987+  83  Linux
/dev/sda3            9526        9729     1638630    5  Extended
/dev/sda5            9526        9729     1638598+   b  W95 FAT32
ac@ac-desktop:/$ 

ac@ac-desktop:/$ sudo mount -t ext3/dev/media/sda2
ac@ac-desktop:/$ ls -la /media/sda2
total 8
drwxr-xr-x 2 root root 4096 2009-02-05 13:53 .
drwxr-xr-x 7 root root 4096 2009-02-05 13:53 ..
acmc@acmc-desktop:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun                502M   84K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   80K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   34M  468M   7% /lib/modules/2.6.22-14-generic/volatile

---

### Post by taurus on 2009-02-05
> **bermu said:**
> Here is it,

ac@ac-desktop:/$ sudo fdisk -l
[sudo] password for acmc:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63a363a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39439543+   7  HPFS/NTFS
/dev/sda2            4911        9525    37069987+  83  Linux
/dev/sda3            9526        9729     1638630    5  Extended
/dev/sda5            9526        9729     1638598+   b  W95 FAT32
ac@ac-desktop:/$ 

ac@ac-desktop:/$ **[COLOR="Red"]sudo mount -t ext3/dev/media/sda2[/COLOR]**  :confused:
ac@ac-desktop:/$ ls -la /media/sda2
total 8
drwxr-xr-x 2 root root 4096 2009-02-05 13:53 .
drwxr-xr-x 7 root root 4096 2009-02-05 13:53 ..
acmc@acmc-desktop:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun                502M   84K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   80K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   34M  468M   7% /lib/modules/2.6.22-14-generic/volatile

```
**sudo mount -t ext3 /dev/sda2 /media/sda2**
ls -la /media/sda2
```

---

### Post by bermu on 2009-02-05
Sorry, here is it:

acmc@acmc-desktop:/media$ sudo mount -t ext3 /dev/sda2 /media/sda2
acmc@acmc-desktop:/media$ ls -la /media/sda2
total 96
drwxr-xr-x  21 root root  4096 2009-02-03 15:54 .
drwxr-xr-x   7 root root  4096 2009-02-05 14:31 ..
drwxr-xr-x   2 root root  4096 2008-04-24 18:13 bin
drwxr-xr-x   3 root root  4096 2008-04-24 18:13 boot
lrwxrwxrwx   1 root root    11 2008-04-24 18:03 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2007-10-15 16:28 dev
drwxr-xr-x 111 root root  4096 2009-02-05 15:10 etc
drwxr-xr-x   3 root root  4096 2008-04-24 18:11 home
drwxr-xr-x   2 root root  4096 2007-10-15 16:17 initrd
lrwxrwxrwx   1 root root    33 2008-04-24 18:13 initrd.img -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root root  4096 2008-04-24 18:13 lib
drwx------   2 root root 16384 2008-04-24 18:03 lost+found
drwxr-xr-x   7 root root  4096 2009-02-05 14:31 media
drwxr-xr-x   2 root root  4096 2007-10-15 16:17 opt
drwxr-xr-x   2 root root  4096 2007-10-08 03:47 proc
drwxr-xr-x   3 root root  4096 2009-02-03 15:54 Recycled
drwxr-xr-x   6 root root  4096 2009-01-26 16:43 root
drwxr-xr-x   2 root root  4096 2008-04-24 18:13 sbin
drwxr-xr-x   2 root root  4096 2007-10-15 16:17 srv
drwxr-xr-x   2 root root  4096 2007-10-04 04:17 sys
drwxrwxrwt  11 root root  4096 2009-02-05 14:30 tmp
drwxr-xr-x  11 root root  4096 2007-10-15 16:19 usr
drwxr-xr-x  15 root root  4096 2007-10-15 16:31 var
lrwxrwxrwx   1 root root    30 2008-04-24 18:13 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
acmc@acmc-desktop:/media$ 

"""""""""""""""""""

Another thing is: when I plug my external flash drive and do " sudo fdisk -l" , I get this (Disk /dev/sdc doesn't contain a valid partition table) see below.

acmc@acmc-desktop:/$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63a363a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39439543+   7  HPFS/NTFS
/dev/sda2            4911        9525    37069987+  83  Linux
/dev/sda3            9526        9729     1638630    5  Extended
/dev/sda5            9526        9729     1638598+   b  W95 FAT32

Disk /dev/sdc: 512 MB, 512483328 bytes
16 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 992 * 512 = 507904 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdf: 4127 MB, 4127195136 bytes
16 heads, 32 sectors/track, 15744 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xe35e0fb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       15744     4030448    c  W95 FAT32 (LBA)
acmc@acmc-desktop:/$

---

### Post by taurus on 2009-02-05
> 
Disk /dev/sdc: 512 MB, 512483328 bytes
16 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 992 * 512 = 507904 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table


You need to create a partition, /dev/sdc1, and put a filesystem (formatting) on it before you can use it.

---

### Post by bermu on 2009-02-05
Thanks, how do I create a partition and put a filesystem (formatting) on it?.

---

### Post by bermu on 2009-02-05
If I formatt it, I'm going to loose all the data and I don't want to happen this, all I want is to be able to read.

---

### Post by bermu on 2009-02-05
Hi,anyone can help me how to create a partition, /dev/sdc1, and put a filesystem (formatting) on it .

---

### Post by taurus on 2009-02-05
If you create a partition and format your /dev/sdc1, all data will be gone.  So, why not just connect it to a window machine and backup whatever you have on that drive, if you think windows can read it?

---

### Post by bermu on 2009-02-05
Thank you very much for your help but I'm ineterseted in why I'm unable to read it with Ubuntu. As I mentioned before the files that I want to read were created in Unix(Solaris), could that be the the issue?, I don't know what the format scheme of the flash is. Is it a way to find out what the flash format scheme?, also I can't read in windows either. But I can read NTFS/FAT files in Ubuntu.

---

