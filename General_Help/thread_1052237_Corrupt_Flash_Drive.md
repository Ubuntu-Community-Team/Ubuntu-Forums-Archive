---
title: "Corrupt Flash Drive"
date: 2009-01-27
forum: General Help
---

### Post by sidewalkcynic on 2009-01-27
I recently had to re-install upgrade to the Ubuntu 8.04 from 7.04.

I saved all my files to a 4Gb Attache USB memory stick. Things are okay as far as my small application files are concerned, the problem occurs in my Internet HTML, MHT, and PDF files - it was over 6000 files and about 1.2 Gb.

It seems that some of the files are now 1000's of Gigabytes large now, and are considered executable - and the flash disk is now marked a bootable. Anyway, I cannot copy the files back to my hard disk, and Windows XP cannot read the flash and asks if I want to format it. Any ideas?

> Disk /dev/sda: 10.0 GB, 10056130560 bytes
240 heads, 63 sectors/track, 1299 cylinders, total 19640880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65e032e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     6138719     3069328+   b  W95 FAT32
/dev/sda2         6138720    18960479     6410880   83  Linux
/dev/sda3        18960480    19640879      340200    5  Extended
/dev/sda5        18960543    19640879      340168+  82  Linux swap / Solaris

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7935999     3963968    c  W95 FAT32 (LBA)


---

### Post by taurus on 2009-01-27
What happens if you try to mount it with

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by sidewalkcynic on 2009-01-28
> :~$ sudo mkdir /media/sdb1
[sudo] password: 

:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000

mount: /dev/sdb1 already mounted or /media/sdb1 busy
mount: according to mtab, /dev/sdb1 is mounted on /media/disk

:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             6.1G  2.9G  2.9G  50% /
varrun                125M  104K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   64K  125M   1% /dev
devshm                125M   12K  125M   1% /dev/shm
lrm                   125M   39M   86M  32% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      6.1G  2.9G  2.9G  50% /home/lunaphiles/.gvfs
/dev/sdb1             3.8G  1.6G  2.0G  44% /media/disk
Can you make anything of it?

Durring my re-installation phase I attempted to make a bootable live USB. But that was on a different USB - I may have copied a couple of folders and files from it to the USB in question but it would not have been the liveCD files.

Anyway,for now, I am going to remove all the folders and files except for the directory I am trying to repair.

---

### Post by sidewalkcynic on 2009-01-28
So I did as I said above, and then when I run a property check on the directory in question:
> 3,718 items, totalling 4172253058 bytes
When it should be about 6,000 items.

And then my monitor goes through the roof, and I have to restart to get it back to normal???

---

### Post by sidewalkcynic on 2009-01-28
Well, I toggled the BOOT flag with fdisk /dev/s##

But I still have the problem of what seems to be recent mht files being seen as having several Gigabytes of information???

I'm trying to pull them out of the directory, and hopefully I can copy the rest back to my hard drive.

---

