---
title: "Disk boot failure error"
date: 2005-12-07
forum: General Help
---

### Post by Fatstink on 2005-12-07
Ok, I got a problem and about a thousand ways I've tried to fix it....I'm putting it out to the forums hoping that someone has had this problem before:

Problem:
I installed linux and windows on to a 300GB hard drive. This hard drive is now completely ruined (I'm guessing that this was a faulty HD because I ran a seagate utility and got an error for every part). So we installed a 4.3GB (yes...) and got a boot failure. Now I put a 40GB in, it passes all the seagate utility tests, and now it gives me "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

Solution:
Thats why i'm posting

What I've Tried:
3 different systems reformatting and installing and getting the same error.
Note: It has been through loads of reformats...
I have cleared the CMOS and have been doing about everything I have thought of.

Note:
I have noticed that the memory controller and input device do not have a IRQ Value assigned. IRQ value is assigned to NA.

Any input is very much appreciated.

---

### Post by tonysathre on 2005-12-07
not having interrupt request numbers set might be the cause, im fairly certain that all things need DMAs, IRQs and the like to talk to the CPU, i dont know what the values should be tho, also do any of your input devices work because they dont have these specified?

---

### Post by Fatstink on 2005-12-08
I have my BIOS set to Hard Disk, Removable, CD, when I boot I get to lines that say Boot from CD and then it prints "Disk boot failure, input system disk and press enter"

---

### Post by tonysathre on 2005-12-09
i had this problem just last night, i fixed it by unplugging my floppy drive.
another thing was my data cable to my CD ROM was unplugged, maybe check and make sure everything is securely fastened

after rereading your original post it sounds like the same disk is failing on multiple systems, try varifying the checksum value of your ISO image, and try redownloading a new image file and burn it at a very slow speed

---

### Post by Princey on 2005-12-11
[QUOTE=Fatstink]I have my BIOS set to Hard Disk, Removable, CD, when I boot I get to lines that say Boot from CD and then it prints "Disk boot failure, input system disk and press enter"[/QUOTE]

Have you tried checking the jumper what it's set to? All hard drives have the options of setting to Master, Slave, or Cable Select. It seems to me that there could be a conflict with the CD Rom and Hard drive being set to both and giving that error message. Just a thought.

---

### Post by Fatstink on 2005-12-12
I have done all of the above.  I think flat out that I have a bad hard drive and motherboard, maybe even a bad powersupply.  All are under warranty so hopefully I can get it fixed soon.  Thanks for the help.

---

### Post by tonysathre on 2005-12-12
now that i think of it it wasnt the floopy that i unplugged it was the CD ROM - the jumpers were both set to master and were conflicting each other

good luck

---

