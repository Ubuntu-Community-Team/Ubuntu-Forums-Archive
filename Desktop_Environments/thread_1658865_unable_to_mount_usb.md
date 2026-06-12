---
title: "unable to mount usb"
date: 2011-01-03
forum: Desktop Environments
---

### Post by peterthewolf on 2011-01-03
When I plug usb stick or hard drive in Maverick does not display it.

If I go into system/administration/disk utility the usb drive is shown correctly and is at /dev/sdb1 but if I try to mount then I get this message.

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

What can I do.

---

### Post by regala on 2011-01-03
> **peterthewolf said:**
> 

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

What can I do.

well. what do you mean by
> but if I try to mount

the error message seems quite obvious, you try to mount the wront block device... /dev/sda1 is not /dev/sdb1

br

---

### Post by peterthewolf on 2011-01-03
I mean that I press the mount button in disk utility.

Further oddity is that with maverick live cd there is no problem, but it comes back when installed to HD.

---

### Post by OnlyJamieO on 2011-01-06
I have experienced the same problem.  I reformatted the USB flash to FAT.  The ubuntu 10.10 system recognises the drive is connected (it is visible in Disk Utilities, and I formatted the drive from that application), but when I click the Mount Volume button, this message pops up:

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

I says its already mounted on, although it is not visible anywhere but Disk Utilities
I installed the Gnome Format application, and that won't even open.  

Any advice?

Thank you

---

### Post by fagulhaspt on 2011-01-06
> **peterthewolf said:**
> When I plug usb stick or hard drive in Maverick does not display it.

If I go into system/administration/disk utility the usb drive is shown correctly and is at /dev/sdb1 but if I try to mount then I get this message.

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

What can I do.

As noteb by "regala", it seems it tries to mount /dev/sd**a**1 (which is you harddrive) instead of the usb drive /dev/sd**b**1.

The following is not a complete solution, but a workaround in case you need it - you can manually mount the usb-drive writting in a console:

```
mkdir usb-drive
sudo mount -o uid=$(id -u) /dev/sdb1 usb-drive

```

And you can access the directory "usb-drive" and read/write into it :)

---

### Post by ccicali on 2011-08-02
Hello,
i'm having this issue too...
When i insert an usb mass storage device, it does not mount automatically, so i go to disk utility, select the device, click on mount and get this message: 

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

Obviously /dev/sda1 is my internal hdd primary partition, why it confuse this partition with my usb stick?
Very odd!

thank you
Cristiano

---

