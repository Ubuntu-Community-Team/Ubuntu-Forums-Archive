---
title: "Help...ubuntu Is Doing Scary Things!!!"
date: 2005-12-08
forum: General Help
---

### Post by codyrinas on 2005-12-08
I just got my new Ububtu CDs and went ahead to put it into my computer...it installed okay, minus this one thing that didnt install under 'additional components'...could be my problem.   the problem is that when it installs completely, it comes up with this screen that looks like a command line that asks me to log in...so i log in, and when I do, it gives me something that looks like a command line.  What to do with this command line I do not know, I reinstalled it about 7 times, then gave up.  

The computer I am using has

A Via Chipset for the AMD Athlon XP/Duron CPU (VIA KTxxx)
An AMD Athlon XP 2600+ at 2150 MHz
256 MB DDR 266 RAM
32MB embedded Graphics
AOpen 16x speed DVD+-RW DL drive
Optorite 52/32/52 Speed CDRW drive
Seagate 2.05 GB hard disk ( I have a 40 GB HDD but i hve an insatllation of windows on there and do not want to corrupt it by having the GRUB loader interfere with NTLOADER)

If it is a hardware issue, or lack of HDD space PLZ LET ME KNOW, and also I would like to know how to create a dual boot system for windows and Ubuntu PLZZZ!!!!! ](*,) :confused:

---

### Post by nelposto on 2005-12-08
[QUOTE=codyrinas]the problem is that when it installs completely, it comes up with this screen that looks like a command line that asks me to log in...so i log in, and when I do, it gives me something that looks like a command line.  [/QUOTE]

First off, after logging in and getting the command line, try  'startx', which should hopefully start the X windows manager.

If this doesn't work, and even if it does, chances are you either downloaded the image badly, or the CD you burnt it to/have it on isn't perfectly burnt (hence the failing during install - I had the same issue).

Try redownloading the image and burning at a slower speed.

---

### Post by linbetwin on 2005-12-08
If you installed Ubuntu on 2.05 GB, I'm afraid that's not enough space. 3GB+ should be okay.

You could try to type "startx" at that command line after you login, but I don't think it will work.

---

### Post by taurus on 2005-12-08
Did you install desktop or server?

---

### Post by codyrinas on 2005-12-08
i should also mention that I got my cds from shipit.ubuntu.com or whatever, and i tried 3 different CDS

---

### Post by codyrinas on 2005-12-08
i installed desktop

---

### Post by linbetwin on 2005-12-08
On 2.05 GB?

---

### Post by codyrinas on 2005-12-08
yes on 2.05GB

---

### Post by taurus on 2005-12-08
Maybe it didn't have enough space to install addtional components as the error message said!!!

---

### Post by codyrinas on 2005-12-08
yea im going to see ig i can get my hands on a bigger HDD

---

### Post by Gurgeh on 2005-12-17
Good god man! 2.5gbs?!?! Throw it in the bin lol I use a 10gb hard drive as a coffee mat (slightly bust at the minute admittedly) but anyways, yeah its blatently not getting all the files on there.

Plus ur right not to trust GRUB on ur primary drive, I lost XP and was ass fisted into the deep end of ubuntu, but i'm lovin it! Time to make a decision :)

---

### Post by codyrinas on 2005-12-17
so wat about a Dualboot from the same HDD?? how would I do that? From 2 HDDs?
which is better?

---

### Post by Gurgeh on 2005-12-18
Naaah won't make a difference but you'll either need to blank the harddrive and start again or purchase (bit**cough**torrent) a copy of partition manager and explosively partition your harddrive (explosively means while data is still on it btw) then when you install ubuntu it'll sit in the unused space and hopefully GRUB will take ur windows MBR into account. So to summarise:

- Get a graphical partition manager
- Make sure at least half ur harddrive is free and defrag it
- slice it in half with the partition manager
- Run ubuntu installer in expert and pay attention to the partition and GRUB bootloader stages.

Follow those steps and u should be fine....

---

