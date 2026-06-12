---
title: "help a newbie!  After installing Kubuntu 7.04 laptop keeps rebooting"
date: 2007-07-06
forum: Dell  Ubuntu Support
---

### Post by talekhinezh on 2007-07-06
Hi, im pretty new to this stuff so help is appreciated!

I installed Kubuntu 7.04 on my Dell Latitude D505 Laptop yesterday.  Everything seemed to work fine.  Whenever I rebooted my laptop a screen would come up asking which OS I wanted to use.  This morning though, my computer just keeps rebooting over and over again.  I dont know why this would happen now since it worked fine yesterday.  It does this after "Grub loading Stage 1.5".  Help please?  Thanks.

---

### Post by ridgeland on 2007-07-06
What do you see after the 1.5?
Do you get any Grub menu at all?
Also have you upgraded the kernel?  Lots of System Upgrades?

---

### Post by talekhinezh on 2007-07-08
There is no Grub menu at all.  Immediately after 1.5 the computer reboots.  And i havent upgraded the kernel.  I just installed kubuntu 7.05 and booted and it was working. Next morning though, it wont go into the GRUB screen and the dell boot screen just keeps reloading.  I think that the boot loader is corrupt or something since there is no GRUB screen at all.  Thanks.

---

### Post by ridgeland on 2007-07-08
I would use the brute force method and reinstall.
Sometimes a couple of hours to reinstall is faster than debugging.
But first do a little research for GRUB in Google-Linux (or Linux) and the forums.  Try Google like "Linux Grub Repair Ubuntu"  Forum searches for "GRUB" and "GRUB rescue", "GRUB repair" etc.

I know a little about GRUB.  There are two pieces.  The first is space constrained by the MBR "Master Boot Record" and does little more than point to the second piece.  That handoff seems to be dying for some reason.  I think the second piece should be /boot/stage2 on the Kubuntu partition, which loads the menu from /boot/grub/menu.lst

I've changed my setup by issuing 
grub> setup (hd0) (hd0,4) 
to tell grub where the second part is (5th partition, count 0,1,2 not 1,2,3).
This command is issued by stopping the Grub menu and getting to the "grub>" prompt.  Without a Grub menu I don't know how you would do this.

You may be able to boot the install CD as a rescue CD.  There are also System Repair CDs you can download as an iso.  I use SysRescueCD, I haven't done GRUB repair.

---

