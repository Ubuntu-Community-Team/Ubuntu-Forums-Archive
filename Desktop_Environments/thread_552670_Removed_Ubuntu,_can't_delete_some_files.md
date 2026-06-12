---
title: "Removed Ubuntu, can't delete some files"
date: 2007-09-16
forum: Desktop Environments
---

### Post by eeefresh on 2007-09-16
For reasons I won't go into here, I have decided to remove Ubuntu from my desktop PC.  Please don't preach at me...I loved Ubuntu, but right now I prefer to stick with XP.

So here's how I had my PC set up before:

**1 HD with four partitions**
- sda1 (XP)
- sda2 (Ubuntu)
- sda3 (swap)
- sda4 (files shared between both OSs, ext3 format)

I set up Ubuntu to use sda4 as the home folder and had also configured sda4 to be my "My Documents" folder in XP (when I set up my system, I used Ext2 IFS on XP to allow it to read the sda4 partition in ext3 format).  So all of my non-OS files were on the sda4 partition, and frankly I was proud of myself for getting all this configured correctly! :)

However, I recently uninstalled Ubuntu.  I still have the sda4 partition with all my files.  Again, I am using Ext2 IFS with XP, so I can still access everything.  However, I still have a few Ubuntu remnants that I can't seem to delete.  For instance, there is a "lost+found" folder that is taking up almost 1 GB of space, but I can't seem to delete it in XP.

I thought about booting to a Live CD and seeing if that would allow me to remove the files, but it wasn't showing sda4 and I couldn't figure out how to mount it.  Assuming I can even get it mounted using the Live CD, will it let me delete those files?

---

### Post by pay on 2007-09-16
Boot up your liveCD and mount it with```
sudo mount /dev/sda4 /ubuntu/Desktop
```Then you should be able to delete the files.

---

### Post by eeefresh on 2007-09-17
Thanks for the response.  Terminal gave me this when I entered it:

mount: mount point /ubuntu/desktop does not exist

---

### Post by eeefresh on 2007-09-17
Okay, I think I succeeded in mounting it.  I can now see the lost+found folder, but it won't let me delete it.

---

### Post by maybeway36 on 2007-09-18
lost+found is on every ext3 partition, it's for internal fuctions of some sort. There's no need to get rid of it.

---

