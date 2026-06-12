---
title: "an Atypical dvd issue"
date: 2011-07-10
forum: Desktop Environments
---

### Post by covenist5 on 2011-07-10
Okay, first off, I've successfully set up many ubuntu systems that successfully play dvds.  This is a fairly unique problem, seeing as every potential solution I've tried has failed.  Here it is:  The folder linked to the device is /dev/cdrom1 and permissions are lrwxrwxrwx I've tried "sudo chown 'username:username /dev/cdrom1 -R" "sudo chmod 777 -R /dev/cdrom1"

no dice (and yes, libdvdread4 has been installed, and installcss.sh has been run installing libdvdcss2.)  I also have the gstreamer good/bad/ugly installed.

when viewed with nautilus, the folder has a lock in the corner.  I've tried changing permissions using "sudo nautilus" and right clicking on the folder selecting properties, etc... as well as using "gksudo nautilus"  etc...  
no dice.
I've tried using regionset to make sure that wasn't the issue. it was not

I also tried "sudo adduser 'username' disc" and appearently 'disc' isn't a group, so no help there.  

Hitting a brick wall here. I've pulled out the giant ubuntu book, and continue to hit brick walls.  Any suggestions would be greatly appreciated.

---

### Post by wildmanne39 on 2011-07-10
> **covenist5 said:**
> Okay, first off, I've successfully set up many ubuntu systems that successfully play dvds.  This is a fairly unique problem, seeing as every potential solution I've tried has failed.  Here it is:  The folder linked to the device is /dev/cdrom1 and permissions are lrwxrwxrwx I've tried "sudo chown 'username:username /dev/cdrom1 -R" "sudo chmod 777 -R /dev/cdrom1"

no dice (and yes, libdvdread4 has been installed, and installcss.sh has been run installing libdvdcss2.)  I also have the gstreamer good/bad/ugly installed.

when viewed with nautilus, the folder has a lock in the corner.  I've tried changing permissions using "sudo nautilus" and right clicking on the folder selecting properties, etc... as well as using "gksudo nautilus"  etc...  
no dice.
I've tried using regionset to make sure that wasn't the issue. it was not

I also tried "sudo adduser 'username' disc" and appearently 'disc' isn't a group, so no help there.  

Hitting a brick wall here. I've pulled out the giant ubuntu book, and continue to hit brick walls.  Any suggestions would be greatly appreciated.Hi, that is because the syntax of the command is wrong, it should look something like this.
```
sudo chown -R username:username /media/storage

```
to get the last part of what it should be instead of /media/storage like mine is hover your mouse over the drive in file manager and it will display what you need to type at the end so it will change ownership to you. It will be /media your file name.

---

