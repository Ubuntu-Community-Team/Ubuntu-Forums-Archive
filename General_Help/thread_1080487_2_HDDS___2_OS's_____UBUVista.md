---
title: "2 HDDS   2 OS's     UBU/Vista"
date: 2009-02-25
forum: General Help
---

### Post by kevil99 on 2009-02-25
Ok i wanna save my self the trouble and time of having to disconnect and reconnect my sata and power cables back and forth to use both vista and ubuntu.

I have two 160g sata HDDs
evga 780i mobo


What i want to do is to plug all cables needed to both HDDs and close the case.
Then easily select on bootup which ever OS i wanna use.


Someone point out a simple way of doing this for me please

---

### Post by blueridgedog on 2009-02-25
I did it as follows:

Install each drive, one on SATA 1 and the other on SATA 2.  Tell your bios to boot from SATA 1.

Install Vista first onto the first drive.

Install Ubuntu on the second (with each drive in, so it will install GRUB onto the first drive).  

Upon rebooting, you will have a menu to boot either Ubuntu or Vista.

---

### Post by kevil99 on 2009-02-25
ok so this will require formatting both hdds and reinstalling the os's.
Im cool with that. ill just wait till ubu 9.04 rolls out in april 23rd

---

### Post by blueridgedog on 2009-02-25
Well, if you already have vista installed, you can proceed as I mentioned with the install to the second drive.  Ubuntu will install grub and will boot each OS.  If you have each os installed and want to setup booting, then you can install grub on the primary drive and configure it to boot each OS.

This thread goes over installing grub from a live CD:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once installed and booting Ubuntu, you can then configure it to boot the first hard drive.  It will entail editing grub.comf and putting in an entry for your first hard drive:

title Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

Once edited, you will reinstall grub with 

grub-install --no-floppy /dev/sda

I encourage you to do some web research ahead of time as the process is delicate and can render your system unbootable.  I generally do as you mentioned and install as I need.  I have only manually installed grub once due to moving drives around.

---

