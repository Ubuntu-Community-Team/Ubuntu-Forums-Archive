---
title: "formatting flash drive"
date: 2009-08-19
forum: Desktop Environments
---

### Post by num on 2009-08-19
Hello,

I got Ubuntu 8.04 LTS and I wiped a 2.0 GB Flash Drive using KillDisk (using the Guttman algorithm) on a Windows XP computer, I formatted it FAT16 and FAT32 (tried both) but it won't mount on Ubuntu. I tried erasing and reformatting with FAT but it won't mount that. What is going on?

---

### Post by SoftwareExplorer on 2009-08-20
What if you do Applications->Add/Remove and search for Gparted. Put a check my gnome partition editor and apply chenges. Then go to System->Administration->Partition editor. What if you format it with that program? Then does it mount?

---

### Post by riazrahaman on 2009-08-20
assuming that you have sudo access on your machine.

Before inserting the flash drive do

$> sudo dmesg -c

Then insert the flash drive and do dmesg.

Copy paste the output here.

If you see something like /dev/sdd, then do the below

1. mkdir sd any where, for example /home/abc/sd
2. sudo mount /dev/sdd /home/abc/sd _OR_ sudo mount /dev/sdd1 /home/abc/sd

---

### Post by Bucky Ball on 2009-08-20
> **riazrahaman said:**
> assuming that you have sudo access on your machine.

Before inserting the flash drive do

$> sudo dmesg -c

Then insert the flash drive and do dmesg.

Copy paste the output here.

If you see something like /dev/sdd, then do the below

1. mkdir sd **any where,** for example /home/abc/sd
2. sudo mount /dev/sdd /home/abc/sd _OR_ sudo mount /dev/sdd1 /home/abc/sd

All good advice but rather than anywhere, I would put it where it is supposed to be:

```
sudo mkdir /media/name_of_your_sd_mountpoint_here
```Then type:

```
sudo mount -a
```

I would definitely attempt to format the drive with Partition Editor (Gparted) first and see if that works.

---

### Post by num on 2009-08-20
I can format it ext3 and it will mount but FAT it will not mount :(

---

### Post by num on 2009-08-21
anyone?

---

### Post by SoftwareExplorer on 2009-08-21
What if you use ntfs? windows can read it and so can Linux.

---

### Post by Bucky Ball on 2009-08-21
If you have it formatted in FAT (not sure why you're keen on this as it is not the best), make sure it appears in:

```
sudo blkid
``` If it is not there, skip to the end of this post. If it is, take note of its 'sd*' and UUID number. Then:

```
sudo mkdir /media/name_of_your_sd_mountpoint_here
```... This can be any name. Open your fstab file:

```
sudo nano /etc/fstab
```You should have the correct UUID number for the device from the results of 'sudo blkid' so; add something like this line at the bottom with the correct details:

```
# /dev/**sd**** (this line only to identify drive, commented out with a # so not read by machine)
**UUID=4893-E3A6**     /media/**mount_point_you_just_made**    vfat    defaults,umask=0002,gid=46 0 0

```In bold are the bits you need to change. Finally;

```
sudo mount -a
```If the device is showing up in 'sudo blkid', then it is mountable. As mentioned in a previous post, NTFS might be a better choice. If you go that way, ntfs-3g mounts and adds things to fstab very easily. System->Admin->Synaptic, search for and install 'ntfs-3g'. It will then be in your drop down menu. Run it and it will identify and present NTFS devices and ask what you want to do with them. 

Hope this is of some help. :)

---

