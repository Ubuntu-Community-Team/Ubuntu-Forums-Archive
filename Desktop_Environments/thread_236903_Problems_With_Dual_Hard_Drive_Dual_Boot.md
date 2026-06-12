---
title: "Problems With Dual Hard Drive Dual Boot"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Chemicalice9 on 2006-08-15
To summarize, I can't boot Ubuntu, which is on a secondary slave hard disk, but can boot Windows which is on the primary hard disk.  I have tried SBM to no avail.  In detail, here inlies the problem:

  Two nights ago windows crashed, and the reinstall disk could not be found.  I loaded up my trusty knoppix Live Cd and went through a long process of formatting the hard disk so that I could use it to install the Ubuntu .iso on.
  After getting Ubuntu up and running on that hard disk, I altered settings for hours, installed programs, etc.  I really wish to not have to reinstall and go through all the settings again.
  Now the fun really starts.  My father wanted Windows Xp on the computer.   I figured easy, install it to my extra hard drive and use BIOS to go to Ubuntu when I want it.  
  After messing around with jumpers and ribbon cables, I found that it would allow me to install windows on the new drive with jumpers on both drives on cable select, having the new drive on the cable first.
  After installing Windows with no problems I had to face the dilemma of a Boot Manager.  I installed SBM to a floppy disk, put it in the drive and restarted.
  In SMB, I could not see all of the partions on the second hard disk (which was the only one in when Ubuntu was installed).  I tried to load from the partions it showed, but was greeted by a GRUB error and it took me to a page to select the kernel.  None of them worked.  I was told that the aprtion could not be found.
  My dilemma is, how do I setup my system so that Windows XP starts automatically, but when I need it, I can use Ubuntu off of the second hard disk.

---

### Post by mority on 2006-08-15
To answer your last question: Install grub into the master boot record of the primary master and add a menu entry for Windows and a menu entry for Ubuntu.

To install grub, boot the Ubuntu 6.06 CD into the live system, start a terminal and follow theses instructions: [http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

Maybe you will have to mount the / directory of your already installed Ubuntu and adjust /boot/grub/menu.lst. There you can make the Windows installation default, too. You will finde the necessary information to edit menu.lst here:
[http://www.gnu.org/software/grub/manual/grub.html/men#Configuration](http://www.gnu.org/software/grub/manual/grub.html/men#Configuration)

---

