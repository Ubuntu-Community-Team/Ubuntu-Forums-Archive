---
title: "Need help with fstab file update"
date: 2009-03-22
forum: Desktop Environments
---

### Post by gcryall on 2009-03-22
I am a newbie so bear with me if this seems like I should have know it.

I want to modify the /etc/fstab file to mount a drive that happens to be in one of those docking devices (i.e. you can swap out the drive that resides in the docking station).  It is mounted as IDE.

This docking drive is not the boot drive and does not get mounted automatically at startup.  I want to modify the /etc/fstab file to remedy this situation since I want to do some automatic backups to that drive.  However I cant figure out what to use ad the file system name.

My problem is that I dont understand the differences between the /etc/fstab file and what the Linux fdsik command shows.

Here are my listings.

geo@Linux-Desktop:~$ sudo fdisk -l
[sudo] password for geo: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009317c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb014a86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    b  W95 FAT32

This appears to show /dev/sda as the boot drive

However when I go to the /etc/fstab file, it shows the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=be48bb68-c2a9-445a-98f4-becf85cb8898 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=dda3fc67-9d2e-4236-9b54-e8d6f4076e9f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Which shows /dev/sdb as the boot drive.

So  the crux of it is that I dont want to specify the wrong file system name in the /etc/fstab file and mess the system up.

Can anyone help me with this problem or offer any direction.  It would be greatly appreciated.

---

### Post by gcryall on 2009-03-22
By the way, dont pay any attention to the system information on th bottom.  This problem relates to a new desktop I am using with Intrepid 8.10

---

### Post by dacorr on 2009-03-22
Fdisk is a partition editor it will handle all partions on all drives connected to the host it is running on. Allowing you to alter the disk partions.

Fstab displays mounted partions for the Linux operating system
mtab handles USB devices connectied to the OS

Dac

---

