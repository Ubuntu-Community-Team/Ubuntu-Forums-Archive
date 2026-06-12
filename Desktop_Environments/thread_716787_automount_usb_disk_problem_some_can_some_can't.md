---
title: "automount usb disk problem: some can some can't"
date: 2008-03-06
forum: Desktop Environments
---

### Post by zl2k on 2008-03-06
hi, there
I have newly installed ubuntu 7.10 i386 desktop. I can automount my usb flashdrive (4G) with writable authority. But the system can't automount my external usb disk (250G, with 3 partitions in ext3). Both can be automount on another machine which is running debian etch. 
How can I fix the problem? Thanks for help.
zl2k

---

### Post by taurus on 2008-03-06
Can you mount them by hand from a terminal?  

Post

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Rytron on 2008-03-06
If above did not work try connecting external hdd and then starting up Ubuntu.

---

### Post by LuisGMarine on 2008-03-06
Also post the output of your /etc/fstab:
```

cat /etc/fstab 
```

or

```
sudo gedit /etc/fstab
```

post the results of either command.

Usually USB drives have a hardtime mounting out of the box, usually for some reason the mount point is never created so you have to do it manually, and change the permissions on it to allow you write to it.  

Don't worry easy fix, the quicker you post those commands the quicker we can get your drive working.  

Cheers!

---

### Post by zl2k on 2008-03-06
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=19f8ccee-7524-400a-8f6a-cfadab20536e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3d7ad245-fd7e-4c15-a070-52ce0231aad5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

If I plug in the usb disk and restart, then I can see them after reboot and writable.

In debian, I can see them writable for the first plug in after boot up. But it will fade away after a while (30min?) if not touching it. If I re-plug it in, I can not see it any more. Again, the usb flashdrive never have this trouble.

zl2k

---

### Post by LuisGMarine on 2008-03-06
I might be stupid but I don't think I see it on your /etc/fstab.  I see your main HDD which is /dev/sda*  that one has your linux partition, along with the swap.  Then you have sdc , which is your CDROM, but there is no trace of your USB drive.  If it was on your fstab it would be under /dev/sdb or something of that sort.

Hook up the drive and run this command, sorry I should of had you run this one before:

```
sudo fdisk -l
```

---

### Post by zl2k on 2008-03-06
sorry, here it is.

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c9ae4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29665   238284081   83  Linux
/dev/sda2           29666       30394     5855692+   5  Extended
/dev/sda5           29666       30394     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000beeca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13417   107772021   83  Linux
/dev/sdb2           13418       26165   102398310   83  Linux
/dev/sdb3           26166       38913   102398310   83  Linux

---

### Post by taurus on 2008-03-06
So you want to mount /dev/sdb1, /dev/sdb2, & /dev/sdb3.

```
sudo mkdir /media/sdb1 /media/sdb2 /media/sdb3
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo mount -t ext3 /dev/sdb2 /media/sdb2
sudo mount -t ext3 /dev/sdb3 /media/sdb3
```
And if you want to write to those without using sudo/gksudo, then you can change the ownership of the moun points from root to your login name.  

_Assuming_ your login name is** john**, do

```
sudo chown -R **john**:**john** /media/sdb1 
sudo chown -R **john**:**john** /media/sdb2
sudo chown -R **john**:**john** /media/sdb3
ls -la /media
```

---

### Post by LuisGMarine on 2008-03-06
> **taurus said:**
> So you want to mount /dev/sdb1, /dev/sdb2, & /dev/sdb3.

```
sudo mkdir /media/sdb1 /media/sdb2 /media/sdb3
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo mount -t ext3 /dev/sdb2 /media/sdb2
sudo mount -t ext3 /dev/sdb3 /media/sdb3
```
And if you want to write to those without using sudo/gksudo, then you can change the ownership of the moun points from root to your login name.  

_Assuming_ your login name is** john**, do

```
sudo chown -R **john**:**john** /media/sdb1 
sudo chown -R **john**:**john** /media/sdb2
sudo chown -R **john**:**john** /media/sdb3
ls -la /media
```

+1 :guitar:

---

### Post by zl2k on 2008-03-07
Thank you. Now at least I can mount it manually. 
zl2k

---

### Post by LuisGMarine on 2008-03-07
you don't sound satisfied, read this guide on how to add it to your fstab so you can mount those partitions automatically when you boot your machine:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28mount%29)

---

