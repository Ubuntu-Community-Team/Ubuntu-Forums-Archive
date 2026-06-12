---
title: "SATA HDD won't successfully format"
date: 2009-04-19
forum: General Help
---

### Post by Hellstudios on 2009-04-19
Hi, I recently got a 160GB sata HDD that was External, so I decided "hey! I'll take out the enclosure and hook it up to be internal!"  Every thing went fine until I decided to install my OSes on there. so I boot up from my CD drive with ubuntu 8.10, choose to format it to NTFS (I dual boot, you see.) and be on my merry old way, but an error came up, so I try again, and Notice that the drive has disappeared! So I reboot again with my CD drive, try to format it ext2 thinking "screw windows. I'll worry about that later" and the same error comes up and the drive disappears again!

computer specs:
celeron D processor
(I believe) it's an ASUS mobo
1gb RAM
256mb ati radeon xpress video card

The Error:

**EDIT: the screen shot seemed to lag and i didn't get the error.... darn it. ill post it in a minute.**
[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/error.png[/IMG]



P.S. my computer only recognises the first 149GB of the drive, could this have to do with anything?


Thanks, Hellstudios

---

### Post by Hellstudios on 2009-04-19
Here it is:

[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/error-1.png[/IMG]

---

### Post by Hellstudios on 2009-04-19
Bump, only 2 people have seen this????

---

### Post by codeseer on 2009-04-19
Normal SATA HD? Non-SSD? Version of GParted?

---

### Post by matrixblue on 2009-04-19
Try creating a new partition table (Device > Create Partition Table). This will erase the existing partition structure of the disk. Create a brand new partition and try again.

---

### Post by Hellstudios on 2009-04-19
> **codeseer said:**
> Normal SATA HD? Non-SSD? Version of GParted?

the version of gparted that comes with the 8.10 live CD. 



and it's a normal HDD.

---

### Post by Hellstudios on 2009-04-19
Didn't work, got the same error.



This is making me pull my hair out.

---

### Post by Hellstudios on 2009-04-19
OK, nevermind, I'll just go back to my old desk star, if my WD SATA HDD won't even format I could imagine the problems I will have with it as my main drive.

it seems that all SATA hard drives hate me and my computer..

---

