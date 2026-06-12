---
title: "New user needs help with installation problem"
date: 2010-12-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cricketeer on 2010-12-06
Hi,
 
I'm pretty new to Ubuntu (and Linux in general) and could use some help.  I'm trying to install Ubuntu on a new computer and failing.  Does anyone know if Ubuntu has problems booting to a SCSI drive?  Alternatively, does anyone know if Ubuntu has problems booting to a solid state drive?

---

### Post by snowpine on 2010-12-06
Welcome to the forums!

Some advice to get the best results from this forum: Tell us as many details as possible about your hardware, the exact steps you have taken so far, where exactly the error occurs, if there are any specific error messages, etc. "I tried but it failed" just isn't enough info for us to help you in any meaningful way.

My understanding is that Ubuntu runs great on SSD drives but has some trouble with SCSI. (Since I don't have any SCSI hardware personally, I am only mentioning what I've read from other users.)

---

### Post by sp-1070 on 2010-12-06
Download unetbootin select wich ubuntu you want put an usb in let it download and extrackt wait till its done,
insert in computer and do the things you do
done

---

### Post by cricketeer on 2010-12-06
Thanks snowpine, for the welcome and the good advice.
 
I have a multicore 64-bit Dell Precision T7500 with a solid state SCSI drive and a traditional SCSI drive.  I would ideally like to load Bio-Linux 6 onto this machine as my goal is bioinformatics.  Bio-Linux 6 is based on Ubuntu 10.04 (to the best of my knowledge they simply distribute Ubuntu 10.04 with software and databases pre-instsalled for dummies like me).  
 
The machine was shipped with RedHat Enterprise Linux Desktop 64bit, and that worked fine.  However, after downloading and burning LiveCDs of Bio-Linux 6 and Ubuntu 10.04 I found that the machine would not boot from either of these LiveCDs.  After several re-downloads and re-burns failed to produce a successful boot, I attempted to boot to a 32-bit bioinformatics distribution of Ubuntu.  This one successfully booted.  I then tried 64-bit Windows and it successfully installed.  Finally I wondered if a 32-bit machine (the one I was downloading and burning with) was not able to  successfully burn the image of a 64-bit OS.  I subsequently downloaded Ubuntu 10.10 on the 64-bit machine and burned a LiveCD.  
 
Hallelujah, it booted.  Unfortunately, although it ran the LiveCD just fine after I installed Ubuntu 10.10 it wouldn't reboot into the OS.  Specifically, after the standard boot screen came up the monitor went blank and went to sleep as it wasn't getting any information.  
 
The thing that triggered my question regarding solid state drives was that during the installation of Ubuntu 10.10, the default hard drive that Ubuntu wanted to install on was the traditional drive...even though the solid state drive was listed as drive A.  I changed that default and installed on drive A - the solid state drive.  
 
I just re-installing on the traditional motorized drive.  This one got further along in the boot process.  I got to the screen that listed verisions of the OS e.g., Ubuntu Generic, Ubuntu Generic Recovery Mode, etc.  I chose the default, Ubuntu Generic, something quickly flashed on the screen then it went black.  
 
Does anyone have any idea of what's going on and/or how to fix it?  Is there additional information that I can give that would be helpful?

---

### Post by cricketeer on 2010-12-06
sp-1070,
 
Thanks for the suggestion.  I don't think the CD is the problem.  See my post above which contains more information.  I did test the LiveCD on a Mac and it worked fine.

---

### Post by snowpine on 2010-12-06
Thanks for providing the extra details, hopefully it will help the community find a quick answer for you! :) Your success with the Live CD suggests there is hope.

A good next step is, from the GRUB boot screen, select Ubuntu Recovery Mode. This should boot your system into text-only mode, so you can further troubleshoot the problem. 

My guess is that your computer has an ATI or Nvidia graphics card, and it is a "simple" matter of installing the correct graphics driver. For some reason Ubuntu includes these drivers on the Live CD, but you have to activate them yourself on an installed system. Some legal reason I suppose...

Unfortunately I don't have Nvidia or ATI on any of my computers, so I am not the guy to help you. :(

---

### Post by cricketeer on 2010-12-06
Thanks for the suggestion snowpine!
 
I tried booting into Ubuntu Generic Recovery Mode, but that didn't work.  A lot of text scrolled by on the screen before the screen went black.

---

### Post by snowpine on 2010-12-06
It was the best "educated guess" I could come up with, sorry it didn't work... with the details you have provided, I'm sure someone else will respond soon... hang in there! :)

---

