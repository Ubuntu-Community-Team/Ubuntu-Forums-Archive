---
title: "Ubuntu on Vostro 1000 - NEWB ALERT."
date: 2010-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by regcheeseman on 2010-06-11
Hi all, go easy on me it's my first post here....
 
I was given a sickly Vostro 1000, one BIOS update later and it's fine apart from being crippled by Vista. 
I already have a couple of windows machines in the house and fancy a play with some Linux.
I downloaded a Ubuntu release (9.something?) onto a USB drive and have a play and all seems good.
 
The drive on the laptop is a mess so I used a quick XP install to reformat drive and give me a safety net OS.
 
Now the Ubuntu release won't boot, coming up with various mount failures, not recognising devices, I did a quick google with the error messages and to be honest, it looked too daunting for me.
 
I figured it may be the XP install - so I wiped the drive, still no boot.
 
So I downloaded Xubuntu 10.4 onto another drive and ran it from there fine. :)
 
Now I decided to install it properly and it seemed fine apart from the lack of wireless. Back to the trusty XP desktop machine and google the problem and there is loads of help but it all involves downloading - Catch 22. How can I download on my Xubuntu laptop without a wireless connection?
I used the XP box to download a few bits and pieces, including a large Dell sourced exe file for ubuntu fixes onto a pen drive.
Aha the pendrive doesn't work on Xubuntu, I can mount it manually but see nothing on it, tried a SD card and it's the same problem.
 
OK, up into the loft and find an ethernet cable in the darkest recesses, but it appears that my ethernet port is dead too. :(
 
Another tack - reboot Xubuntu but run it from the USB pen, hurrah! I can see my downloaded driver files - but I do not know how to put them into my installed version of Xubuntu. 
 
Ah well, I'll just install them into the USB live version of Xubuntu and see if they actually work.....
 
nope. Xubuntu seems to recognise them as windows files and fails to do anything with them.
I try to use terminal to force it too accept the broadcom driver file BCM34xxx or something similar and it doesn't like that.
 
 
So there it is.... no ethernet, no wireless, no removable storage - not much use at all - PLEASE someone help or I'll reach for the XP install disk and end it all.... ;)

---

### Post by regcheeseman on 2010-06-16
Nobody?
 
Did I do something wrong?
 
Bye , Bye Ubuntu

---

### Post by mikewhatever on 2010-06-16
Let me restate the problem:
[you have a Vostro 1000, Ubuntu 10.04 installed, there is no cdrom, wireless doesn't work, ethernet unavailable, need installing a wireless driver].
Is that more or less correct?

---

### Post by regcheeseman on 2010-06-16
Yes that's about it..
 
The packaged drivers don't seem to help
 
Ethernet port dead
 
USB devices recognised but not browseable
 
No wireless activity
 
 
I've found various solutions (yes I have been searching!) but they all require importing data from one medium or another which I can't do.

---

### Post by mikewhatever on 2010-06-17
I am curious what are the files you downloaded and where from. Keep in mind that .exe files are Windows executables and do not work in Ubuntu. You need to check the model of the card firs (lspci | grep -i network). Broadcom is very common for Dell notebooks, and if that's the case, the file you need it bcmwl-kernel-source.
[http://packages.ubuntu.com/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/lucid/bcmwl-kernel-source)
There are links for 32 and 64 bit at the bottom of the page
When downloaded, you can put the file on the pen drive, boot from it, mount the Ubuntu partition and copy the file over. Then boot Ubuntu and double click the file.
This is a long shot and I rather doubt it would work because of dependencies, but you can try.

---

