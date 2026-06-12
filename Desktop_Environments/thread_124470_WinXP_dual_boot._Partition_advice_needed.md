---
title: "WinXP dual boot. Partition advice needed"
date: 2006-02-01
forum: Desktop Environments
---

### Post by MikeyMuchos on 2006-02-01
Hi, 
third time lucky yesterday, installing Ubuntu from DVD to dual boot with an existing Win XP system. There were  no process halting errors as before. Then last night I tried to jiggle the partitions around a little to give more to Ubuntu from WinXP. It seemed to go OK but when I tried to reboot I got a Grub error which brought things to a dead stop. In the end I reformatted the whole drive and brought back yesterday's XP from some drive images.

This time I've tried to set up the finished partition structure before the installation of Ubuntu. I've made a 1.5GB swap, a 14GB Ext3 and a 12GB FAT32 Sharing partition to the East of the 2 NTFS WinXP partitons.

If I now install Ubuntu from the DVD, will the guided partitioning part of the process recognise the partitions specially prepared for the occasion, or will I need to opt for a more user defined method of partitioning duringt the install?
TIA
Mikey

---

### Post by lha on 2006-02-01
You'll have to select 'manually edit partition table' in installer. Then select mount points for your partitions you want to use with Ubuntu.

---

### Post by MikeyMuchos on 2006-02-01
Thanks for the tip. Will manual edit be pretty intuitive for a Linux newbie or do I need to read up big time on the terminology first? I just want to avoid getting into that ireversible position which leads to reformatting and reinstallation, again.:) 
Regards,
Mikey

---

### Post by lha on 2006-02-01
[QUOTE=MikeyMuchos]Thanks for the tip. Will manual edit be pretty intuitive for a Linux newbie or do I need to read up big time on the terminology first? I just want to avoid getting into that ireversible position which leads to reformatting and reinstallation, again.:) 
Regards,
Mikey[/QUOTE]

I'm not the one you should be asking if it is intuitive.. :) Well, I can say it's not too hard. It really depends on how afraid you are of computers. If you want to prepare yourself for the partitioner. take a look [here]("http://users.bigpond.net.au/hermanzone/p3.htm"). It's a page with detailed how to install Ubuntu with Windows already installed. A large portion of it is irrelevant to you (resizing ntfs partition and creating partitions), but it does show you  how partitioner works.

---

### Post by MikeyMuchos on 2006-02-01
Thanks very much. The link you give is just what I need.:D  My fear of computers isn't great but I do get a bit awed at the prospect of spending hours reformatting and reinstalling and then having to do it all again soon after.

---

