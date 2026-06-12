---
title: "Grub error 5 with new drive"
date: 2005-12-11
forum: General Help
---

### Post by ultima2k on 2005-12-11
Normally when I have used Ubuntu I have had three harddrives, one SATA (ubuntu, windoze) and two PATA as storage...

Resently got a Maxtor 200GB PATA back from RMA and set it up as master on the secondary IDE-controller with DVD as slave. Now I get "Grub error 5".

I can understand that the SATA-drive with ubuntu on it will become hd3, instead of hd2 because PATA-drives comes before SATA, but even after editing menu.lst with the right drive it doesn't work...

Any clue?

---

### Post by ultima2k on 2005-12-11
Problem solved...seems something was wrong with the NTFS-partition on the drive :S

---

### Post by bomb-24 on 2007-06-16
I recently installed ubuntu on a flash drive. I didnt want to disturb my xp installation at all. I used a 4 gig flash drive, went through the installation process and when it rebooted and went to the grub menu it stated: grub loading stage 1.5
                                       grub loading, please wait...
                                       ERROR 5
What can I do?? I am out of options. I cant boot my xp now, all I have is the live cd to run. Can someone please help me?

---

### Post by jmielke on 2007-06-26
I'm having the exact same issue but should note that I installed Ubuntu on a second (internal) hard drive.

Any feedback would be greatly appreciated as my next step is to delete both drives and start anew with a fresh installation of XP.  I'd rather not go this route because of the fact that I will lose all of my data.

---

### Post by Herman on 2007-06-26
Okay, well don't delete anything. Almost all boot loader problems are easily solved and even if they take a while it's better than losing data and settings etc. A little patience is better than a lot of work.

Try reading this link and see if it's any help at all, [Grub error   5]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#5_").

Please boot your live CD and post the output from 'sudo fdisk -lu' here,
```
 sudo fdisk -lu
``` Maybe we will be able to see what's wrong with your partition table. 
It might be something very simple and easy to fix or it might be a glitch that will be more of a challenge.  Probably we can fix it. If we can't, at least I can help you rescue your data. I would prefer if I can help you fix your partition table though. :D

I'll be back later to check on how you are getting along,
Regards, Herman :)

---

