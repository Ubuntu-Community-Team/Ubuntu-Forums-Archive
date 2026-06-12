---
title: "GRUB taking over startup?"
date: 2009-01-04
forum: General Help
---

### Post by justin10ec on 2009-01-04
Hello, I was going to do a fresh install of Windows Vista, but before I did that I decided to see what Ubuntu 9.04 was like (the Alpha #2), it's installed, but now when I put my  CD in, it's like it never checks it, it goes straight into GRUB and loads Ubuntu...

HELP ME PLEASE!!!!

---

### Post by nemilar on 2009-01-04
Your BIOS determines where to boot from (hard disk or CD).  Go into setup and make sure CD-ROM is the first item in the boot order.

Optionally, there is probably a command "Press F[something] for boot menu" when you start up your computer.  Press that key and select the CD drive.

---

### Post by justin10ec on 2009-01-04
I have already checked that. The CD is number 1 on the list.

---

### Post by nemilar on 2009-01-04
Can you test the CD in another computer to make sure it is bootable?

---

### Post by justin10ec on 2009-01-04
It's bootable, I've used it before.... I just tried my Windows XP cd, it loads, but when I go to install XP, I see this message:

> Setup did not find any hard disk drives installed in your computer.

Wow, I got this for Christmas, and if it's messed up, I'm going to be in some deep trouble. =\

---

### Post by aleangelico on 2009-01-04
AS nemilar said, is a BIOS issue. The computer is booting from the HD device instead of booting from the CD. There are 2 options, the booting order is HD first, then CD, etc, or the CD is not bootable. GRUB cannot take over the boot order, because its not activated until the BIOS loads the HD boot sector loader.

.alex

---

### Post by justin10ec on 2009-01-04
I finally got the Vista DVD to load. I don't know why it randomly started working. I didn't do anything but try it for the 20000000th time.

It's now at the expanding files stage, so I am assuming everything is okay now.. 

Any ideas of what may have caused this?

---

### Post by nemilar on 2009-01-04
Hmm, this is an interesting symptom.  Not entirely sure how that would occur, except perhaps the Windows install can't see the ext partitions and thus doesn't recognize any hardware..

You may perhaps try this, assuming you don't need anything from the Ubuntu installation:

1. Burn a gparted live CD
2. Boot into the gparded liveCD and erase all the partitions, so that it is only free space left on the drive
3. Reboot into the Windows install CD

Gparted liveCD is available here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)


> **justin10ec said:**
> It's bootable, I've used it before.... I just tried my Windows XP cd, it loads, but when I go to install XP, I see this message:



Wow, I got this for Christmas, and if it's messed up, I'm going to be in some deep trouble. =\

---

