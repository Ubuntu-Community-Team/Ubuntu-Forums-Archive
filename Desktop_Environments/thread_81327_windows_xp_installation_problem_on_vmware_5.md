---
title: "windows xp installation problem on vmware 5"
date: 2005-10-24
forum: Desktop Environments
---

### Post by ggv6 on 2005-10-24
Hi

I installed vmware 5.0 following instruction on ubuntu documentation. Vmware is now running fine but having problem installing windows XP (tested it with w98). 

The installation starts I create the new partition and format it to ntfs (also tried FAT32). It then moves to start copying files to the disk but I get a message saying that the setup cannot access the files in the CD-ROM drive and asking to press enter to retry or F3 to exit (which is crazy cause the installation up to that point was running from the cd-rom).
I also tried using an iso from the hard disk mounted to cd-rom using virtual machine settings but still having the same problem.

Is there something I 'm doing wrong?

I there a way that I could copy the files on the virtual disk used by the virtual machine and start the installation from there?

Has anyone managed to install windows XP on vmware 5.0 using  Ubuntu 5.10?

Any help would be appreciated

---

### Post by Appolusionist on 2005-10-25
I had no problems with installing Windows XP as a Guest OS on Vmware 5/Ubuntu 5.10 combo. You did not give any details on hardware so really can't be too much help. You may have to look at installing 3rd party drivers for your disk controller. I would suggest that you look at VMware's [Discussion Forums]("http://www.vmware.com/community/index.jspa") and [Knowledgebase]("http://www.vmware.com/support/kb/enduser/std_alp.php"). And of I am assuming that your cd is not damaged.
 
I also suggest just making an ISO out of your cd and editing your VM profiles so it will read it directly from the ISO until the install has been completed.

---

