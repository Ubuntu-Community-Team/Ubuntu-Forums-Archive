---
title: "Problems with file permissions... I think"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Dillius on 2005-10-28
I made a 70 gig partition of FAT 32 to act as a transfer between my linux install and my windows install. Windows is able to place things on it fine, but whenever I try to copy to it in linux, it is giving me errors in which "Operation is not permitted". The command I am attempting to use is

sudo chown -R dillius:dillius storage/

dillius of course, being my name on the system.

Anyone know why this isn't working? Or just have an easier way for me to get write permissions?

---

### Post by stuporglue on 2005-10-28
> but whenever I try to copy to it in linux...
sudo chown -R dillius:dillius storage/


Problem 1 is that's not a copy command. That changes the owner and group of the file to be you. 

Problem 2 is probably that FAT32 doesn't support permissions. Move the files to a non-FAT partition and try applying the permissions again.

---

### Post by aysiu on 2005-10-28
Follow these instructions:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

It's very likely that your FAT32 drive is not /dev/hda1, though. To find out what location it is, type this command in ```
sudo fdisk -l
``` My FAT32 partition is located at /dev/hda5, for example.

---

