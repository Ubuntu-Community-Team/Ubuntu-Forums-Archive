---
title: "Trying to mount second hard drive on /home"
date: 2009-06-04
forum: General Help
---

### Post by rvc on 2009-06-04
Ubuntu 8.04 (Linux PC - no Windows or dual boot etc)

Installed 2nd hard drive - recognized fine as sdb1 - configured single partition with gparted.

I want to have my home directories on the second disk. I have copied the complete /home/myname to it and can access these files through File Manager.

The drive shows up in "Places" and will mount temporarily in /media when selected. The mount command then returns following info:
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

I have tried to add the mount instruction to the fstab file so that it will mount automatically but have had near disasters and I am proceeding very carefully.  If I mount the drive from a Terminal session to /home/myname it is inaccessible from the Places menu.
I have also added the following line to the fstab file and then used mount-a command.
/dev/sdb1  /home/myname  ext3  rw,nosuid,nodev,uhelper=hal  0  0

The mount command then gives following info:
/dev/sdb1 on /home/rchidlow type ext3 (rw,nosuid,nodev,uhelper=hal)
which looks pretty much the same as when mounted by the system in /media.

However no Home Directories or files are accessible from the menu under Places/Home or Computer.
(I have been restoring the original fstab before shutting down.)

What else do I need to do?

---

### Post by logos34 on 2009-06-04
start over and try it this way:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

