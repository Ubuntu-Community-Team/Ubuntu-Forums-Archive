---
title: "Trying to boot from external USB HD with a MacBook"
date: 2018-06-28
forum: Desktop Environments
---

### Post by chkneater on 2018-06-28
I'm using a Mac right now cause my tower crashed... I had it set up to boot from an external HD but when I started using the Mac it isn't recognizing any OS on the external USB HD, the Mac works fine except it's a Mac :-/  So my overall questions are: how to get the UUID in order to chroot (need help with that also) to that partition in the ext. HD and get Mac to recognize the Ubuntu install. I can get the Mac to boot there after that.  I don't think I'll have any GRUB issues.  One other thing, I did have a backup partiton on the USB HD for my data and set the partition as NSFT so windows and this Mac could at least have the data, which it does read fine.  1 of 2 things are happening: the Ubuntu image was accidentally wiped OR I need to use the terminal and do work.  I've not messed with Ubuntu in a while, but I quite prefer it over the Mac OS and am familiar with some commands, so I think this should be an easy fix.  All help is appreciated.

---

### Post by sudodus on 2018-06-28
- Please specify your tower computer (brand name and model of the computer or motherboard, if you built it yourself).

- Is there an internal drive in the tower computer with some other operating system, for example Windows? Can you disconnect the internal drive?

- How is the external hard disk drive connected? USB or eSATA or some other way?

- Can you read files from the external hard disk drive, when connected to another computer (for example your Mac?

- Which version of Ubuntu is it?

- Please describe with as many details as possible what you think caused the problem to boot from the external hard disk drive. What happened/did you do just before it stopped working?

[hr][/hr]
- Can you create a USB boot drive or DVD boot disk with Ubuntu, and boot your tower computer boot from it?

In that case select 'Try Ubuntu' and you will be able to run some commands in a terminal window to help analyze the problem, and after that some other commands to solve the problem.

---

### Post by chkneater on 2018-06-28
Perhaps I mistated slightly: Tower crashed, gone; I HAD been running and booting the tower with an EXTERNAL USB HD with version 10.04 I believe.  There were no other drives in THAT one...  I am NOW using a MacBook Pro and want to boot from the USB HD AGAIN, the Mac is 10.6.8 and recognizes the Ext. HD as MyBook 1140.  It even mounts it and recognizes the NFTS partition that I put along side Ubuntu but is not recognizing Ubuntu.

What I need is to check all the EXTERNAL USB partitions which should be three for me: Ubuntu, Swap and the NFTS to make sure Ubuntu is still installed.  Then I need to get Mac to recognize it and set the Mac to boot from it in the System Preferences.  I did not have any GRUB issues before so that should be OK after chrooting and updating the GRUB.  Does that sound better?

Also the tower crashed because of motherboard issues preventing startup and didn't harm the EXT. HD I am using.

Rundown: I have MacBooK Pro ver. 10.6.8 that I want to boot from the EXT. HD, MyBook 1140 that should have three partitions (Ubuntu 10.04, Swap, and NFTS); I need to check for Ubuntu and get Mac to see Ubuntu, then set Mac to boot from the MyBook and pray for no Grub issues

---

### Post by chkneater on 2018-06-28
I should say that the Mac disk utility is now showing all three partitions; however the part. with Ubuntu and the swap both say unbootable and neither will mount, but the NTFS mounts fine... so how do I make the Ubuntu Part. bootable and get all three to mount?

---

### Post by sudodus on 2018-06-28
I know very little about Mac computers and Mac operating systems, and cannot help you much in order to make it read your Ubuntu partition (which I would guess has a linux ext4 file system (maybe an older ext3 file system).

The only tip would be to **try to boot your Mac from a USB pendrive or DVD disk made bootable** with a light Ubuntu community flavour from a current iso file (I suggest a community flavour with a lighter desktop environment  **Lubuntu** or **Xubuntu**, version **16.04.1** LTS or version **18.04** LTS).

Read the whole conversation in this link to a thread that is marked as SOLVED,

[Advice on installing Ubuntu on older Macbook with OSX 10.6.8 ](https://ubuntuforums.org/showthread.php?t=2359438)

When booted from such a live Ubuntu system, I am rather sure that you will be able to access Ubuntu's linux file system in your external hard disk drive.

[hr][/hr]
Please notice that Ubuntu version 10.04 LTS, good old Lucid Lynx, passed end of life in April 2015, more than three years ago. It is a good idea to save the personal files you can find there (documents, pictures etc). But you should not run it, because there will be no updates/upgrades, and it will be vulnerable to attacks via the internet.

After saving the files, you can try to install a current system (from a Lubuntu or Xubuntu boot drive) into the external drive. I know how to do it in a standard PC computer, but there might be difficulties in a Mac computer, that I don't know. You may get better help if you start another and very specific thread in the Ubuntu Mac forum,

[ Apple Hardware Users](https://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by chkneater on 2018-06-28
I use the NTFS partion and save most things there already.  And yeah I know that it is older, but I did not know about the forum for Apple. I'm not tryint to INSTALL on the Mac cuz I want to be able to use the external drive on other computers (newer!) the previous owner who gifted me this (burdened me) Mac dinged it up bad and the ONLY cd drive is busted so I can't fix it in Live mode, tho I think it's more to do with the Mac than my drive now that I can see all the partitins, just can't access them...yet...

---

### Post by yancek on 2018-06-28
How old is this Mac?  Macs have been using UEFI for a number of years, is your Ubuntu on the usb a UEFI system, does it have an EFI partition.  I'm not familiar with Macs but I believe there is an 'Option' key you need to tap to access boot options, use the keyboard arrow keys to navigate.  You might take a look at the link below which explains booting from a usb on a Mac.  This particular instance is an EFI usb, not sure how it will work if you have a Legacy Ubuntu.

 [https://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/](https://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/)

---

