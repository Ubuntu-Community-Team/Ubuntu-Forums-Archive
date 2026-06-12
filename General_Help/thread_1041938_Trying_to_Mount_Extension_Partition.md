---
title: "Trying to Mount Extension Partition"
date: 2009-01-17
forum: General Help
---

### Post by Stillwellean on 2009-01-17
I know this will probably end in failure, but I have run into a huge problem.  

A bunch of my data (read: documents prepared for academic journal submission, we're talking 150+ hours of research and editing) were on my laptop.  Now my laptop starts up with:

GRUB stage 1.5

Error 22


Now, I know that means all i should have to do is follow the ubuntu recovering after a windows installation guide, overwriting the boot sector and re-installing GRUB.  But, the problem is, I can't get to old filesystem from my liveCD.  

sudo fdisk -l outputs this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6906069f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8192000    c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2            1020        3731    21768555    7  HPFS/NTFS
/dev/sda3            3732       60802   458416248    f  W95 Ext'd (LBA)
/dev/sda5           31421       60802   235998208    7  HPFS/NTFS


and the only partition i haven't been able to get to is /dev/sda3.  Yes, i know this is an extension partition. 

So, i tried mounting it, and after a while, i came up with this:
 mkdir /media/windows   -or something like this, i forget
 sudo mount -t vfat /dev/sda3 /media/windows -o force

now the error message i get is:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

so i check 

dmesg |tail
[ 1258.391083] wlan0: CTS protection enabled (BSSID=00:1f:33:29:ae:20)
[ 1260.561164] wlan0: CTS protection disabled (BSSID=00:1f:33:29:ae:20)
[ 1262.035153] wlan0: CTS protection enabled (BSSID=00:1f:33:29:ae:20)
[ 1263.468014] wlan0: CTS protection disabled (BSSID=00:1f:33:29:ae:20)
[ 1439.189005] FAT: bogus number of reserved sectors
[ 1439.189018] VFS: Can't find a valid FAT filesystem on dev sda3.
[ 1457.960584] FAT: bogus number of reserved sectors
[ 1457.960596] VFS: Can't find a valid FAT filesystem on dev sda3.
[ 1476.371790] wlan0: CTS protection enabled (BSSID=00:1f:33:29:ae:20)
[ 1477.749780] wlan0: CTS protection disabled (BSSID=00:1f:33:29:ae:20)

So, i guess what im asking is, does anyone know how i can get the data off of that extension? If the logical partition isn't around?

---

### Post by Yellow Pasque on 2009-01-17
The extended partition contains logical partition(s). You want to mount the logical partition (/dev/sda5 in this case), not the extended partition itself.

---

### Post by -kg- on 2009-01-17
> **Stillwellean said:**
> I know this will probably end in failure, but I have run into a huge problem.  

A bunch of my data (read: documents prepared for academic journal submission, we're talking 150+ hours of research and editing) were on my laptop.  Now my laptop starts up with:

GRUB stage 1.5

Error 22


Now, I know that means all i should have to do is follow the ubuntu recovering after a windows installation guide, overwriting the boot sector and re-installing GRUB.  But, the problem is, I can't get to old filesystem from my liveCD.  

sudo fdisk -l outputs this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6906069f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8192000    c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2            1020        3731    21768555    7  HPFS/NTFS
/dev/sda3            3732       60802   458416248    f  W95 Ext'd (LBA)
/dev/sda5           31421       60802   235998208    7  HPFS/NTFS


and the only partition i haven't been able to get to is /dev/sda3.  Yes, i know this is an extension partition. 

So, i tried mounting it, and after a while, i came up with this:
 mkdir /media/windows   -or something like this, i forget
 sudo mount -t vfat /dev/sda3 /media/windows -o force

now the error message i get is:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

so i check 

dmesg |tail
[ 1258.391083] wlan0: CTS protection enabled (BSSID=00:1f:33:29:ae:20)
[ 1260.561164] wlan0: CTS protection disabled (BSSID=00:1f:33:29:ae:20)
[ 1262.035153] wlan0: CTS protection enabled (BSSID=00:1f:33:29:ae:20)
[ 1263.468014] wlan0: CTS protection disabled (BSSID=00:1f:33:29:ae:20)
[ 1439.189005] FAT: bogus number of reserved sectors
[ 1439.189018] VFS: Can't find a valid FAT filesystem on dev sda3.
[ 1457.960584] FAT: bogus number of reserved sectors
[ 1457.960596] VFS: Can't find a valid FAT filesystem on dev sda3.
[ 1476.371790] wlan0: CTS protection enabled (BSSID=00:1f:33:29:ae:20)
[ 1477.749780] wlan0: CTS protection disabled (BSSID=00:1f:33:29:ae:20)

So, i guess what im asking is, does anyone know how i can get the data off of that extension? If the logical partition isn't around?

[QUOTE=Temüjin]The extended partition contains logical partition(s). You want to mount the logical partition (/dev/sda5 in this case), not the extended partition itself.[/QUOTE]

Temüjin is right, of course.  The only reason an extended partition exists is to overcome the 4 Primary partition rule in which one can create only 4 Primary partitions on a physical hard drive. (See [https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics"))

One thing confuses me, though.  Since you have GRUB controlling your booting, it would seem to me that you would have had Ubuntu already installed.  However, the "fdisk -l" output you posted only shows 1 FAT32 and 2 NTFS partitions.

Do you have another hard drive that Ubuntu is installed on, or was Ubuntu installed on that partition?  Were the files you are trying to recover created under Windows or Ubuntu, and if under Ubuntu, did you save them to one of the Windows partitions?

If your data files are on one of the Windows partitions, you should be able to mount that partition, find your data files, and save them to a location where you can recover them or transfer them to another computer.  I personally would try to repair GRUB and be able to get back to your files the normal way, though.

If you only have one hard drive in your computer, somehow you are missing the partitions that Ubuntu was installed to, and likely you will need to reinstall Ubuntu, in which process GRUB  will be reinstalled and you will once again have access to your files through either Ubuntu or your old Windows installation.

If you have two hard drives, the second of which contains your Ubuntu installation, then you need to repair or reinstall GRUB from that installation, which will accomplish the same thing.

I notice, though, that you have a bit of unallocated space within your extended partition, so we need to know the situation before recommending a course of action.

---

### Post by Stillwellean on 2009-01-17
OK, so it looks like one of my roommates tried to boot into the malfunctioning Vista boot loader when they started my computer. The reason I started using Linux in the first place. (reinstalling wouldn't work after i got a false positive for wga).

So, while I'm not really sure what went wrong, he told me that all that came up was a window with the word error in it really big and then he turned it back off.

What i understand that to mean is that I'm pretty much out of luck. 

there is a chunk of 212.11 GB that has become unallocated. I'm just going to bite the bullet and reinstall.  That'll teach me for not backing up more regularly.

Thanks for the help.

---

### Post by caljohnsmith on 2009-01-17
If you want to try and recover your data from the drive, I think there is a good chance we can do it with some tools like testdisk to recover the partition. It won't take that much effort, so if you want to try, how about posting the current partition table:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

