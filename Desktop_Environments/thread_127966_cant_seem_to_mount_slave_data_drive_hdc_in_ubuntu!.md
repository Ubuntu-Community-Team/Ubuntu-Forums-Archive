---
title: "cant seem to mount slave data drive hdc in ubuntu!"
date: 2006-02-10
forum: Desktop Environments
---

### Post by ttallos on 2006-02-10
I cant seem to mount hdc in ubuntu... when I type fdisk -l as root

I get the following hda hda1 etc...etc...etc
hdc hdc1 fat32 etc...etc...

then I try to type as root /dev/hdc access denied
/dev/hdc1 access denied
/mnt/hdc no such file or partition
/mnt/hdc1 no such file or partition

It would seem easy to slave in a drive and get the data off of it.

---

### Post by soulestream on 2006-02-10
have you actually mounted it?

you need to 

sudo mkdir /mnt/mountnameyourwant

if the drive is formatted fat32 

sudo mount -t vfat /dev/hdc1 /mnt/mountnameyourwant

then go to the directory

or you can enter it in /etc/fstab

soule

---

