---
title: "Need to use a LAN Win7 PC for data storage and retreival"
date: 2015-07-14
forum: Desktop Environments
---

### Post by Dave_Mann on 2015-07-14
Here is what I am trying (setting up a workstation desktop icon and accessing a Windows 7 computer on the LAN:

dave@MightyWurlitzer:~$ sudo mount -a

[sudo] password for dave: 

mount: mount point smb://misterfixit/z/Documents does not exist

Here is my fstab line:

/home/dave/Desktop smb://misterfixit/z/ bind defaults,bind 0 0

Is this a permissions problem or have I got this concept all wrong? 				

No complex stuff for me to do, just access to a several large folders on the RAID located on the remote LAN Windows 7 machine; and r/w them on my Ubuntu workstation.  Sort of like the Windows "desktop icons" where you click and go directly to any folder on the LAN if you have permissions.

---

