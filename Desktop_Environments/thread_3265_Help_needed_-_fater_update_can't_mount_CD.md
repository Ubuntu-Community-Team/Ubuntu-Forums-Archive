---
title: "Help needed - fater update can't mount CD"
date: 2004-11-04
forum: Desktop Environments
---

### Post by Guy on 2004-11-04
Hello

i am running ubuntu on a P4 1500MHZ
until now i had no problems mounting the cdrom. few days ago i updated the system 
( apt-get update & apt-upgrade ) 
after all the packages are installed now i can't mount the cdrom or DiskOnKey.

root@canada:~ # mount /media/cdrom
mount: can't find /media/cdrom in /etc/fstab or /etc/mtab

and with the gui i get "mount: mount point /media/cdrom0 does not exist"

so .. please Help !

Thank you for your time

Guy

---

### Post by Guy on 2004-11-05
no one ??

please, help !!

---

### Post by Johan on 2004-11-05
What does your /etc/fstab look like?

---

### Post by diebels on 2004-11-05
Strange thing, my cdroms didn't automount either. When I ran the removamble media thing in gnome-control-center it said "hald" was not running. So I tried ```
dpkg-reconfigure hal hal-device-manager
``` Still didn't work. Looked in /media directory, and my cdrom0 and cdrom1 directory was gone. So I did ```
mkdir /media/cdrom0
mkdir /media/cdrom1
```Now it seems to work. Not sure where the bug is. You could try this.

---

### Post by thattoo on 2005-03-04
This thread turned up in a Google search when I was looking for something remotely related.  It's a little late to be of much help in this case, and I'm not familiar with Ubuntu anyway; but this problem does look familiar, and I suppose someone else might run into it.

While setting up Debian after a new installation a few months ago, I was asked whether I wanted the cd drive to be handled by discover.  My answer was a yes, and I started getting the same error message that was mentioned in this thread, about a nonexistent mount point at /media/cdrom0.

What had happened was that discover had deleted the mount point by mistake after a reboot, and it would've happened again with the next reboot, had I not either gone back to answer that yes-or-no question with a no, or upgraded discover to fix the bug.

---

