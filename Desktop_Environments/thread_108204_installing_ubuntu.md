---
title: "installing ubuntu"
date: 2005-12-25
forum: Desktop Environments
---

### Post by keheikev on 2005-12-25
Hi,
I put the ubuntu iso disk into the cdrom, System is amd 2100+ with 500mb ram with two hard drives partitioned in windows like this master drive c is all fat 32 and partitioned into c, d, e, f , g drives and drive I is one master (?not sure on this its been awhile) is in ntfs format. How do I direct the install to the g drive without harming  the data on c,d,f or I, drives btw will backup all data to dvd as latest is about 90 days old.
Keheikev
moderator annexcafe.com.annexcafe.general.linux2linux
:KS :KS

---

### Post by sciurus on 2005-12-25
It's probably the partition with the largest number on drive hda. However just to be sure, 
1) Boot an Ubuntu livecd.
2) Open a  terminal and run ```
for i in `ls /dev/hd* | grep -e "hd\w$"`; do sudo fdisk -l $i; done
```. THis will show you all your paritions.
3) Create a folder to use as a mountpoint.
4) Attempt to mount the partition you think might be G: using the command ```
sudo mount -t vfat /dev/hda*?* /*mountpoint*

```
5) Check the contents to make sure it's the right partition. If it's not, umount it and try another.

In the ubuntu installer, delete this partition, and create an EXT3 (or whatever filesystem you prefer) partition and a swap partition in its place. That should preserve all data except on G:, but no promises.

---

### Post by keheikev on 2005-12-28
Thank you I will do that I am not sure if the live cd is what comes with the ubuntu distrubution. At least now my knoppix is working (dirty cd disk). Is ext3 the latest and greatest filesystem to come along for linux?
Keheikev

---

