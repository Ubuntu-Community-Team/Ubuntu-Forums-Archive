---
title: "mkdosfs help required"
date: 2006-01-29
forum: Desktop Environments
---

### Post by SmokingGun on 2006-01-29
I am trying to format my 2GB SD card through a USB card reader. 
Using: 
mkdosfs -F 32 /dev/sde1
gives the message:
mkdosfs: /dev/sde1 contains a mounted file system
So i unmount the drive an then the same command gives:
/dev/sde1: No such file or directory

What can i do?:confused:

---

### Post by claes on 2006-01-29
You need to unmount the usb device in linux. Linux doesn't let you format a drive that "are in use". You could try this command before you format the usb device.

sudo umount /dev/hde1 

Then try to format the device again.

Claes

---

