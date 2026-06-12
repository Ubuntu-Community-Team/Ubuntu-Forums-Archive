---
title: "External Drive Permission Problem"
date: 2006-04-21
forum: Desktop Environments
---

### Post by bmadaras on 2006-04-21
I have a Western Digital external drive where I keep most of my media, I have been trying to share this with some of my friends using proftpd, but I have run into a permission problem.  For some reason when the drive is auto mounted in /media/WD it only has user level permissions.  I tried chmod -R 755 WD to give the group read permissions but nothing seems to happen, ls -al still gives me rwx------ as the permissions.  
I also tried to edit the permissions through the UI, by checking off Read for the group level, but as soon as I put the check there it disappears again.


I have tried added this line to fstab, which I found in another thread:
/dev/sda1      /media/usbdisk  auto    users,gid=users,umask=0002,defaults

After a reboot to test the changes I get this error when trying to access /media/usbdisk

Warning: device /dev/sda1 is already handled by /etc/fstab, supplied label is ignored
mount: only root can mount /dev/sda1 on /media/usbdisk
Error: could not execute pmount

Any ideas of how to give the external drive group level permissions would be greatly appreciated.:-k

---

### Post by Ramses de Norre on 2006-04-22
You'll need to set other mount options in fstab, what's the filesystem on the drive?

---

### Post by bmadaras on 2006-04-22
The filesystem is fat32, is there anyway to change the automounting settings or would that be over the head of a person that just started using linux 3 months ago.

---

### Post by stansaraczewski on 2006-04-22
I had the same problem last weekend - do a search on my name to see how it was repaired.

---

### Post by bmadaras on 2006-04-22
I think my problem is actually a little different, my user has full permissions to read, write and execute on the usb hard drive. I can basically do whatever I want to it, those are the permissions it gets automatically mounted with.  The odd thing is when auto mounted it has no group permissions, and I can not seem to give it group permissions.

I want other users to be able to read but not write or delete, so I created another user and added it to my users group.  I was then going to give my users group permissions to only read.

---

### Post by aysiu on 2006-04-22
If you want group permissions, don't use FAT32. FAT32 doesn't support permissions.

---

### Post by bmadaras on 2006-04-22
Thank you very much, that would never occured to me that some older filesystems do not have permissions setup like that.  I will be looking up another FS to use that will work with windows and linux, any suggestions would be appreciated

---

### Post by Ramses de Norre on 2006-04-22
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
This is a driver you can install in win so it can read/write on ext2 and ext3 filesystems.

---

