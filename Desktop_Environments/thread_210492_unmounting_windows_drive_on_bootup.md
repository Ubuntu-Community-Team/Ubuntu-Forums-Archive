---
title: "unmounting windows drive on bootup"
date: 2006-07-07
forum: Desktop Environments
---

### Post by nokiax on 2006-07-07
hi,

my windows drive keeps mounting everytime I boot to linux, can someone tell me how to stop this....... thanks

---

### Post by Athropos on 2006-07-07
Type this in a terminal:

> 
sudo gedit /etc/fstab


Then find the line about your Windows drive (you may refer to the mount point to find it, it may look like /media/windows) and either put a '#' character in front of it or add ',noauto' to the options columns.

---

### Post by DaveNF2G on 2006-07-13
Hmm. I have the opposite problem.  Every time I boot my system to Linux, I have to mount the Windows drives manually.  How do I make them "stay" mounted for the next session?

---

### Post by aysiu on 2006-07-13
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by DaveNF2G on 2006-07-17
I've seen that. I have **two** Windows FAT32 drives (C and D in Windows 98SE).  I'm not certain what part of those instructions to modify in order to mount **both** drives correctly.

---

### Post by DaveNF2G on 2006-07-21
Never mind.  I figured it out.  

The Ubuntu location of the hard drives can be determined by going to System->Administration->Disks and looking at the right hand window information for each drive.

---

