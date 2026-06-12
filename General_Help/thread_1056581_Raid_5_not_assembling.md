---
title: "Raid 5 not assembling ??"
date: 2009-01-31
forum: General Help
---

### Post by oiad on 2009-01-31
I have recently moved a 4 disk raid 5 from one system to another.  The system that it is in now was recently installed with 8.10 x64.  The array is acting very strange.  When I boot up the machine 4 out of 5 times the array isn't working and only lists only one drive is present.  When I do a fdisk -l or mdadm --examine all of the disks show with the correct info.
The 1 out of 5 boots it is assembled correctly.  I booted into the 8.10 live cd and if I do an apt-get mdadm and scan for arrays it automatically assembles with no problems.

Anyone have any ideas on what is causing the difference from the live cd to the installed system?

---

### Post by oiad on 2009-02-09
Well I figured out how to avoid this problem.  I had done the install on the x64 alt cd due to another raid that is on the same system.  This bug seems to be related to installing with the Alt cd.  I reinstalled a couple of times with the Alt cd to replicate the problem and it is something in the mdadm that was on the cd.

I installed with the normal x64 disk then did an apt-get mdadm and rebuild the array.  I haven't any problems since.  
=

---

### Post by fjgaude on 2009-02-09
Great! Thanks for letting us know.

---

