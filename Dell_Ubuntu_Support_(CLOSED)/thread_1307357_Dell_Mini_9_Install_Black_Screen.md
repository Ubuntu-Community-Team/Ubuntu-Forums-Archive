---
title: "Dell Mini 9 Install Black Screen"
date: 2009-10-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Keairolas on 2009-10-31
I could not find any references to a similar problem as the one that I am having.

I am attempting to install the new 9.10 NBR onto my Dell Mini 9 with 16GB SSD (otherwise stock 8.04 dell-ubuntu).  However, after completing the following steps:

Downloading and creating a live boot usb
Rebooting to the install menu
Selecting install or test from USB

The screen displays a splash screen for a few moments and then hangs on a black page.

Waiting does nothing, and I'm not a linux guru.  Any help would be appreciated.

---

### Post by mueslibrown on 2009-10-31
I have exactly the same problem.  I did manage to update using the Update Manager from 9.04 to 9.10 but encountered errors during the clean up process.  It now takes about 2 minutes to boot and I usually get some failure message.

I do manage to eventually boot and can work normally but something doesn't appear to be right.  My 9.04 upgrade was a breeze compared to the move to 9.10

On a couple of occasions when I tried to boot from USB I got what appeared to be USB or drive/filesystem mount errors.  I tried different USB sticks as well as different ports in addition to downloading the ISO again.

I'm not a UNIX or Linux expert but am very computer literate having worked in IT for the past 15 yrs and with a Comp Sci undergrad degree.  In short I know my way round Windows PCs but linux is a black art for me (last time I used it was the Slackware dist, I think, back when I was at Uni in '94)

I'm about to go back to 9.04

Any ideas?  Other mini 9 owners seem to be working fine based on postings around the web ...

MB

---

### Post by Jackyboy86 on 2009-10-31
Had a similar problem - have you re-written the image to the USB drive?
Try loading Gparted (sudo gparted) in your current dist - and deleting the partition on your USB drive (NOT your hard drive!) then loading the usb writer.
It'll require you to format the USB drive, and then you can rewrite the image to it.
Give it a shot - it worked for me on my mini10.

---

### Post by Keairolas on 2009-10-31
Found a work around by creating a USB from within the 9.10 Desktop version.  I had originally been using the default one that comes within the ISO from a Windows machine.

Someone else with the problem confirm if this helps.

---

### Post by Jackyboy86 on 2009-10-31
Aye - as I said, the usb creator sometimes doesn't work according to plan!
It's not necessarily the windoze one - it happened to me on 9.04...

---

### Post by mueslibrown on 2009-10-31
I finally got things working - went back to a clean install of 9.04 after wiping the same usb stick and using the.img package for 9.04 to boot up.  Performed the 9.10 upgrade using Update Manager and after disabling a few applets it works.

The interface looks good but boot up is so slow and I also get usb errors on boot if my sdhc card is installed.  I think I may go back to 9.04 for now - it simply works for me.

Thx. for the help.

mb

---

### Post by mueslibrown on 2009-11-01
Well, I spoke too soon ... it was the final straw this morning. 'File system mount error' and I got booted into the command line shell so I couldn't even get into the desktop gui.  Going back to 9.04

---

### Post by shiningkenmonster on 2009-11-01
I get that when i do the "dd" command line to make a startup OS usb flash drive. something along like this:

```
 sudo dd if=/home/kenny/ubuntu-8.04.3-desktop-i386.iso of=/dev/sdc bs=1M
```

I have gotten a dark blank screen upon start-up via usb-flash drive, when i dd the command line on Moblin 2.0 beta and from Canonical's Ubuntu 8.04.3.

however, when i made a successful usb start up stick, I used Ubuntu 9.04's usb-creator. For some odd reason, the usb-creator on Ubuntu 8.04 has problems. there has been a bug report for it!

I've used Ubuntu 9.10 beta usb-creator and it just worked just fine with it!

i have also went to use my friend's Windows XP computer and downloaded "unetbootin" and uploaded the Ubuntu's iso image just fine. After restarting and uploading it on  Dell Mini, it has no blank screen and the installation has worked!

If you have Ubuntu 8.04, you are out of luck. The only work around is to use ImageWriter, but it only works with .img images. Which are Dell's Mini Ubuntu 8.04 and Dell's Ubuntu Moblin remix. Not Canonical's Ubuntu iso images. which are from ubuntu.com

---

### Post by mueslibrown on 2009-11-03
Hmmm ... well back on 9.04 and all working perfectly.  I'll try 9.10 in 6 months time ...

---

