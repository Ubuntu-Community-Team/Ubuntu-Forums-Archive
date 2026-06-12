---
title: "Installing Ubuntu problems [Newbie]"
date: 2009-04-21
forum: General Help
---

### Post by Andrew852 on 2009-04-21
Hi I'm Andrew, let me start from the beginning.

A few days ago after loving the videos and pictures of Ubuntu that I had seen, I decided to download it and burn it to a CD, I managed to do that.  I booted the Live CD (as im on right now.) and I have 3 hardrives, two internal one external.  I put Ubuntu onto a 6 GB internal hardrive I have.  The installation went amazing and when in Ubuntu I can see and view the hard drive which has the ubuntu files on them.  Now here is my problem:

When not booting with the Live CD in, It boots up immediatly with Windows XP (which is on my other interal hardrive) giving me no choice to choose and Windows no longer reads the 6 GB drive, Only ubuntu can read it.  Which I assume because of that is the reason it wont let me boot ubuntu on start up.

My system specs are:

OS: Windows XP Professional
Computer type: HP desktop
RAM: 512 MB
(and as I said before) 3 Hardrives two internal one external.  The hardrive that cant be read on windows and has ubuntu on it is a Maxtor and its connetion type is SCSI.

Please help and thank you for reading
~Andrew

---

### Post by jsowoc on 2009-04-21
Dear Andrew,

Let me describe what is happening, for future reference.

When you turn on your computer, your BIOS has a setting for which is considered the "1st device" to boot from. It usually is a floppy or CD drive. Next, if no CD/floppy is found, it proceeds down the list until it gets to the hard drive. There should be another sub-menu for what order the hard drives should be booted from.

Are you able to get into your BIOS (usually F1 or F2 or DEL during the "hp" splash screen) and set the order in which your hard drives should be read during startup? If not (because the other drive is SCSI, and some motherboards don't like to boot from those), the next step would be to tell Windows where to look for the SCSI drive.

Let me know if you are able to change the boot order.

Jan

---

### Post by Andrew852 on 2009-04-21
Thank you!  Changing the order worked :).  I'm loving ubuntu!

~Andrew

---

