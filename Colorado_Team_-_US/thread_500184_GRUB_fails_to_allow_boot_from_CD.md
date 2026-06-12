---
title: "GRUB fails to allow boot from CD"
date: 2007-07-13
forum: Colorado Team - US
---

### Post by VoiceOvGod on 2007-07-13
(X- posted from Installations & Upgrades: [http://ubuntuforums.org/showthread.php?t=500156](http://ubuntuforums.org/showthread.php?t=500156))



I decided to throw FreeBSD on my Sacrificial Laptop last night, it currently has Ubuntu 6.10 and Kubuntu 7.04 installed.

When I tried to boot from the CD, it went to GRUB, even after attempting to force it to boot from the CD.

When in the desktop environment, it was not even acknowledging the CD drive.

I also tried booting from a USB drive, but same result.

I do not know if it is not detecting the USB drive in the desktop environment either.

Ideas?

---

### Post by FunnyLookinHat on 2007-07-13
Sounds like you have a hardware issue with your computer not recognizing the CD Drive at all...  check to make sure that the cables are still firmly plugged in from the mobo to the drive itself.  If all else fails, just buy a new CD drive (they're less than $15 these days and often with free shipping).

---

### Post by VoiceOvGod on 2007-07-13
It's one of those funky Sony Vaio laptops. So it's got an odd connector. It spins the disc and all that, it just won't boot from it.

---

### Post by ElEdwards on 2007-07-13
I had that problem about a week ago on my Presario laptop... but it turned out that I had goofed up:
I hadn't made an image of the ISO... I had just copied the ISO to the CD, which won't boot, of course.

Duh! :)

---

### Post by VoiceOvGod on 2007-07-13
I don't think its that.

I also tried a slackware ISO and KnoppixSTD.

The FreeBSD came with a Linux Magazine issue.

---

### Post by ElEdwards on 2007-07-13
OK :)  By the way, the "Duh" in my previous post was aimed at me and no one else :lolflag:

---

### Post by VoiceOvGod on 2007-07-13
I figured that ;)

I too am guilty of the "Duh" moments.

---

### Post by FunnyLookinHat on 2007-07-14
Does  your laptop support booting from a USB device by any chance?  You can write an image to a flash drive and make it bootable with a few quick tricks....  that could be your solution.

I'm still convinced you have a hardware issue with your cd-rom drive, since it won't detect it during boot and with Ubuntu booted up...

---

### Post by VoiceOvGod on 2007-07-14
I'm starting to agree with you on that.

I tried the USB while in the desktop environment. It loaded up.

What will I need to do to put an image onto a thumb drive?

---

### Post by FunnyLookinHat on 2007-07-19
Well...  using a USB device and booting from one are two separate things.  But you can give it a try anyways

To put an image on a USB drive I found a few helpful links:
 
[http://www.sandaru1.com/2007/07/02/how-to-convert-your-live-cd-iso-into-a-live-usb/](http://www.sandaru1.com/2007/07/02/how-to-convert-your-live-cd-iso-into-a-live-usb/)

[http://h18007.www1.hp.com/support/files/hpcpqdt/us/download/20306.html](http://h18007.www1.hp.com/support/files/hpcpqdt/us/download/20306.html)

[http://slax.linux-live.org/forum/viewtopic.php?t=5094](http://slax.linux-live.org/forum/viewtopic.php?t=5094)

---

### Post by VoiceOvGod on 2007-07-19
Cool!

Thanks!

But will it require sacrificing a USB stick?

I've got a feeling it won't, but I just want to make sure.

---

### Post by Marrz on 2008-04-23
Mine is doing the same thing, boot order is set for the CDROM before the HDD but it still loads straight to grub without allowing me to boot from a CD and I know it's not a hardware issue because when I boot into either Linux Mint or XP I can use the CDROM drive without any issues at all, it's something in the boot order that grub is doing wrong.

Doesn't matter too much to me since I can just back up all important data, do a partition magic in XP, wipe Linux, do a MBR restore and do it all over again, but still a nuisance.

---

### Post by Keen101 on 2008-04-24
I was not aware that GRUB had the ability to boot from CD's.

Forgive me, but I thought that work was done by the BIOS.

---

### Post by Marrz on 2008-04-24
It would seem that it does not have the ability to boot from a CD, what it does have is the ability to bypass the boot order set in the BIOS. I was eventually able to boot from a CD by removing my hard drive then reinserting it as the CD loaded. I was unable to reset the MBR in the XP recovery counsel as well. Since I backed up all important data and it is something of a test mule of a computer I'm reformatting it now.

---

