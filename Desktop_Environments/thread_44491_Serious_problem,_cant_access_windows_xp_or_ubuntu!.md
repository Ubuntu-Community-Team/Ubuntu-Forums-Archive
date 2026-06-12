---
title: "Serious problem, cant access windows xp or ubuntu!"
date: 2005-06-26
forum: Desktop Environments
---

### Post by kylester5 on 2005-06-26
Alright, I have ben on windows xp forever and wanted to try out ubuntu linux, i made the partitions i needed (root,home,boot,swap) and went through the install proccess and it was all fine and dandy, then at the very end it said the grub boot loader failed to install, so i tried to install grub again and it still failed, so i tried the LILO boot loader and it failed. After i rebooted it took me into windows xp and it was still fine, but i couldnt access linux so i tried it again. And after installing i wanted to take the cd out so it wouldnt goto the ubuntu install page or whatever.  So i removed the cd on the page where it says  Ubuntu in big letters and asks you to press enter to install it. THen i rebooted and now every time i boot up it gets to the point where it should start loading XP, but instead it says please insert system disk or something along these lines. So i put in the ubuntu cd and it just went to the screen where it asks you to press enter to install. So i rebooted, and took the cd out in the BIOS. And it just says something like "please insert system disk" every single time i try to boot up! I really need to access windows cause i have a BUNCH of files that are important. And now I am on the Knoppix Live cd but i cant back up my stuff and reformat cause i only have one cd rom drive,  and Im pretty sure taking out the cd while its running would be a bad idea so i cant put a blank cd in and back up my stuff then reformat.

So what can i do now? I REALLY, REALLY need to get into windows cause i have important school files and stuff on there

---

### Post by rachii on 2005-06-26
sounds like you killed the windows boot loader...try installing ubuntu, and installing grub overtop of the mbr, it should auto detect the windows install and allow you to boot either windows or linux.

look around for ubuntu/windows dual booting howto's also.  i've done it in linux, but not wiht ubuntu in particular

---

### Post by improverrr on 2005-06-26
[QUOTE=kylester5]Alright, I have ben on windows xp forever and wanted to try out ubuntu linux, i made the partitions i needed (root,home,boot,swap) and went through the install proccess and it was all fine and dandy, then at the very end it said the grub boot loader failed to install, so i tried to install grub again and it still failed, so i tried the LILO boot loader and it failed. After i rebooted it took me into windows xp and it was still fine, but i couldnt access linux so i tried it again. And after installing i wanted to take the cd out so it wouldnt goto the ubuntu install page or whatever.  So i removed the cd on the page where it says  Ubuntu in big letters and asks you to press enter to install it. THen i rebooted and now every time i boot up it gets to the point where it should start loading XP, but instead it says please insert system disk or something along these lines. So i put in the ubuntu cd and it just went to the screen where it asks you to press enter to install. So i rebooted, and took the cd out in the BIOS. And it just says something like "please insert system disk" every single time i try to boot up! I really need to access windows cause i have a BUNCH of files that are important. And now I am on the Knoppix Live cd but i cant back up my stuff and reformat cause i only have one cd rom drive,  and Im pretty sure taking out the cd while its running would be a bad idea so i cant put a blank cd in and back up my stuff then reformat.

So what can i do now? I REALLY, REALLY need to get into windows cause i have important school files and stuff on there[/QUOTE]


this is what I would do, from a windows boot disk, run FDISK /MBR this will build a new boot loader for windows.  You will now be able to boot windows.  The go in and delete all of the Linux partitions.  Leave them unpartitioned.  The boot from Ubuntu disk again, and when it comes to building partitions, tell it to use the largest free space and finish the install.  Not a big deal.  

Hope this helps!

---

### Post by kylester5 on 2005-06-26
Is there a way to FDISK /MBR without making a boot disk? Because i do not have a floppy disk

---

### Post by improverrr on 2005-06-26
[QUOTE=kylester5]Is there a way to FDISK /MBR without making a boot disk? Because i do not have a floppy disk[/QUOTE]

download hirens ultimate boot cd.  Great tool.  Has a tons of useful tools with it.

[http://62.253.162.19/hiren.thanki/bootcd.html](http://62.253.162.19/hiren.thanki/bootcd.html)

edited:

or try this one...

[http://www.mrbass.org/ubcd/](http://www.mrbass.org/ubcd/)

---

### Post by kylester5 on 2005-06-26
THANKS A TON improverrr! You saved my HDD, thx a lot!

---

