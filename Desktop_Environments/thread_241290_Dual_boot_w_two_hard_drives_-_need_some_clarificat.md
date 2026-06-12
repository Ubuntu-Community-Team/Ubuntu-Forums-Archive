---
title: "Dual boot w/ two hard drives - need some clarification"
date: 2006-08-22
forum: Desktop Environments
---

### Post by nemesisrobot on 2006-08-22
I did do a search, and I found some guides on dual-booting with two hard drives like confused57's ([http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot+windows+hard+drives](http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot+windows+hard+drives)) but most of the guides assume that both drives are sharing the same IDE channel with one set as master and the other as slave.  

In my case though, I have two hard drives, one which is an SATA drive (Windows installation) and an IDE drive (Ubuntu), both set at master on their channels.  In my BIOS, the IDE drive is booted before the SATA drive.  How would I go about installing Ubuntu on the IDE drive?  Do I just go ahead and install Ubuntu on the IDE drive without changing any settings?

Thank you.

---

### Post by FuriousLettuce on 2006-08-22
When you attempt to install Ubuntu, you will be given the option of which hard drive you would like to use. Most likely, your SATA hard drive will be referred to as 'sda', and your IDE hard drive will be referred to as 'hda'. Make sure you double check the sizes of the drives, to make sure they match the known sizes of each respective drive. 

Other than that, it should be fine.

Good luck!

---

### Post by nemesisrobot on 2006-08-22
great.  One more thing, after I'm done with the installation, would i still need to make this change

title Windows
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

to GRUB?

---

### Post by FuriousLettuce on 2006-08-22
GRUB should automatically pick up your Windows installation. Only make those changes if your GRUB installation doesn't see your windows installation [in which case, if you need to use windows to find a fix, temporarily set the BIOS to boot the windows disk first].

---

