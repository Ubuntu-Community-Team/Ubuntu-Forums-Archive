---
title: "Raid"
date: 2009-05-19
forum: General Help
---

### Post by RedSingularity on 2009-05-19
Anyone have a good HOWTO on setting up RAID arrays in ubuntu?  And also i wanted to ask, is this something that has to be done with a fresh install or can it be done when a system is already installed?  



---THANKS

---

### Post by Cheesemill on 2009-05-19
There's a great guide for setting up a software RAID5 using Ubuntu here:
[http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)

Cheesemill

---

### Post by fjgaude on 2009-05-21
Here's one:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

---

### Post by djrakun on 2009-05-22
has anyone had problems with ubuntu recognizing a hardware based RAID5 array?

from a friend of mine:

I need to install ubuntu on a Compaq Proliant DL 380 sever which has the RAID controller built in with three 9.1 Gig SCSI drive and 18.1 Gig SCSI drive installed.  Using all default for the installation of Ubuntu 9.0.2 Server version, it does not recognize the three 9.1Gig drive but it installs everything on the 18.1G drive.  What do you suggest to make ubuntu recognize and utilize the three 9.1G drives?

It sounds like parted doesn't recognize the drives at all, maybe the hardware drivers are not supported?

---

