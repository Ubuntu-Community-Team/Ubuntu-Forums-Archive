---
title: "ubuntu iso for dell inspiron 1525"
date: 2008-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ananthakumaran on 2008-08-22
hi i have a dell inspiron 1525 laptop and i bought it before dell offers support for ubuntu 

i want to install ubuntu 

all i need is the site where i can download the

iso image of ubuntu 8.04 for my laptop

advance thaks::guitar:

---

### Post by ajgreeny on 2008-08-22
If you only need a standard ubuntu iso, then go to [www.ubuntu.com](www.ubuntu.com).  If you want the edited version that Dell use you will need to ask Dell, I think.

---

### Post by Talon2 on 2008-08-22
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by TimDaniels on 2008-08-22
The .iso file for your laptop is downloadable from [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04), but be aware that it will wipe your entire hard disk, then put a couple Primary partitions on it for diagnostic utilities and a recovery image - neither of which you need since you have a utilities CD already, and the recovery image will soon be obsolete as you add data and apps and updates and then upgrade to the next iteration of Ubuntu.  But... they will take up 2 Primary partitions.  Plus, the .iso sets up a swap file in an Extended partition at the very end of the hard drive, and it uses _all_ the rest of the space for a single Primary partition containing Ubuntu.  IOW, it provides no flexibility at all.  It would be better to just download the standard 8.04 Ubuntu installation .iso from [www.Ubuntu.com](www.Ubuntu.com) .  As a plus, you would also be able to set up a dual-boot with Vista if you want.

*TimDaniels*

---

