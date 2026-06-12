---
title: "cannot mount volume   (ntfs"
date: 2008-12-11
forum: General Help
---

### Post by wightangel on 2008-12-11
i have ubuntu but i cant open my partition
wgat can i do ?
i have photo to view the proplem


[http://rapidshare.com/files/172426324/m](http://rapidshare.com/files/172426324/m)  >>>> the link

---

### Post by albandy on 2008-12-11
Did you have a system crash in windows? This NTFS partition is marked as being in use, so you should enter windows and do a chkdsk, or do a forced mounting in linux (can be dangerous).

---

### Post by Agent Smith on 2008-12-11
Is this a partition on your drive or an external drive? If its external i found the easiest way is to plug it into my Windows pc and use :safely remove hardware.

---

### Post by wightangel on 2008-12-11
> **wightangel said:**
> i have ubuntu but i cant open my partition
wgat can i do ?
i have photo to view the proplem


[http://rapidshare.com/files/172426324/m](http://rapidshare.com/files/172426324/m)  >>>> the link

put i dont have windows now

---

### Post by taurus on 2008-12-11
Install ntfsprogs and use ntfsfix to fix your ntfs filesystem.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
Assuming /dev/sda1 is your ntfs partition.

---

### Post by jerome1232 on 2008-12-11
If you don't have access to a Windows pc then you can force a mount or use ntfsfix to clean the log files so that you may mount it.

```
# using ntfsfix

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdxx    # replace /dev/sdxx with the real device path for your drive

# or forcing a mount

sudo mount /dev/sdxx /mnt -o force
```

---

### Post by wightangel on 2008-12-11
> **wightangel said:**
> i have ubuntu but i cant open my partition
wgat can i do ?
i have photo to view the proplem


[http://rapidshare.com/files/172426324/m](http://rapidshare.com/files/172426324/m)  >>>> the link

the log file is removed put the partition disappeared !!!

---

### Post by taurus on 2008-12-11
Post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by wightangel on 2008-12-11
> **taurus said:**
> Post the output of this command from a terminal.

```
sudo fdisk -l
```

that's output of this command :
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe215e215

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         730     5858968+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             893        4866    31911564    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3             730         893     1307880   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by albinootje on 2008-12-11
> the log file is removed put the partition disappeared !!!

Is it not visible in your "places" now ?
Try to mount it manually for testing :
sudo mount /dev/sda2 /mnt -t ntfs

After that check the content of /mnt

---

### Post by wightangel on 2008-12-11
> **albinootje said:**
> > the log file is removed put the partition disappeared !!!

Is it not visible in your "places" now ?
Try to mount it manually for testing :
sudo mount /dev/sda2 /mnt -t ntfs

After that check the content of /mnt

thank you 
my folders in mnt 
but not in palces
is it ok?

---

### Post by taurus on 2008-12-11
```
sudo umount /dev/sda2
sudo mkdir /media/sda2
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
```

---

### Post by wightangel on 2008-12-11
> **taurus said:**
> ```
sudo umount /dev/sda2
sudo mkdir /media/sda2
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
```

its ok now

thanxxxxxxxxxxxxxxxxxxxxx

---

### Post by taurus on 2008-12-11
Since you don't have windows on that machine (or at least not on that harddrive), I am not sure why you would use ntfs filesystem for /dev/sda2?  Should format it to ext3 instead of using ntfs unless you have a good reason to use ntfs filesystem.

---

