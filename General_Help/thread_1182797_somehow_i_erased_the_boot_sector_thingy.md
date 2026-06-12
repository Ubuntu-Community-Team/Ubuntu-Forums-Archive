---
title: "somehow i erased the boot sector thingy"
date: 2009-06-09
forum: General Help
---

### Post by beaubeau on 2009-06-09
Okay here is the skinny.  I recently turned my cousin on to Ubuntu and she loves it.  She was out the door to buy a new computer when i showed here that the hardware is fine (great in fact) but its the software.  Windows was full of bugs and viruses so i set her up with a dual boot.  No problem.  But then when she went home suddenly windows would not open.  She and her husband need it for itunes and such.  So, she brought it back and indeed windows would not open.  So i used the recovery partition to try to get XP back online.  However this created a larger problem in that it erased the computers ability to recognize the dual boot or any OS for that matter.  After the BIOS splash page nothing happens.  I mean nothing.  
Booting up with a live USB shows that both xp and ubuntu partitions are in tact however i can't get the computer to boot them.  

Any help?  I'm sitting by the computer and i'll copy and paste any information about the computer requested to help fix this problem.

---

### Post by michy99 on 2009-06-09
Try this and see if it works:

[http://ubuntuforums.org/archive/index.php/t-965672.html](http://ubuntuforums.org/archive/index.php/t-965672.html)

---

### Post by alwaysbutter on 2009-06-09
I would start by looking into Super Grub Disk.

---

### Post by CaptainEvilStomper on 2009-06-09
Try this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Also, make sure the boot partition (or the Ubuntu partition if you didn't create a separate boot partition) is on the same hard drive as the Windows partition. For example, if you have Windows on sda1 and Grub is installed on sda2, Windows will refuse to boot.

---

### Post by beaubeau on 2009-06-09
Michy99 thanks so much!  That completely solved my problem and worked with out a hitch.  Now i'll try to see if XP will open.  If it doesn't i'll try to convince my cousin to live with it and work through Wine.  
Thank you everyone.  I'm so grateful to have had this problem addressed so quickly!

---

