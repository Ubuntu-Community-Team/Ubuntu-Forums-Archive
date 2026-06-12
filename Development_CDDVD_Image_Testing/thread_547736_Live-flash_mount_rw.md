---
title: "Live-flash mount r/w"
date: 2007-09-10
forum: Development CD/DVD Image Testing
---

### Post by xanderfiss on 2007-09-10
I am working on a flash drive based off of the Feisty live-cd. It boots off of GRUB and for the most part everything works beautifully.

By default the flash drive fstype (FAT16) is automatically detected and the drive is mounted to /cdrom as read-only. I need to be able to access this partition as read/write, and I'm not sure which files I need to edit to make this happen.

What's really strange is that when running the OS (from both the CD and my flash drive) there is no listing for /cdrom in the mount table!  This prevents me from doing a 

mount -t vfat -o remount,rw /dev/sdxx /cdrom

I'm at my wits end trying to solve this, any ideas would be greatly appreciated.

Thanks!

Xander

---

### Post by xanderfiss on 2007-09-11
Okay! So I figured it out, in case anyone is curious, even though I didn't get any replies.

If you are using the Feisty live-CD to make a live-flash and you want that flash drive to be read/write, do the following.

`fdisk -l` and find out what device/partition your flash drive is, e.g. /dev/sdd1

`sudo nano /etc/mtab' and add the following line at the bottom:

/dev/sdd1 /cdrom vfat ro 0 0

This is descriptive of what it's currently doing, mounting the flash drive read-only into /cdrom as type vfat.  Then run:

`sudo mount -t vfat -o rw,remount /dev/sdd1 /cdrom`

and BOOM! you have r/w access.

---

