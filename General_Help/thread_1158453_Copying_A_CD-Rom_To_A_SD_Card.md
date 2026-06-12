---
title: "Copying A CD-Rom To A SD Card"
date: 2009-05-13
forum: General Help
---

### Post by s1mp13m4n on 2009-05-13
Hello everyone.  My wife is in college and needs to use a cd that came with one of her textbooks.  Her laptop is a netbook Acer Aspire One that does not have a dvd drive.  I have both Ubuntu 9.04 and WinXP on my computer.  How can I make a legal copy of that cd so it can be loaded on to a SD card and then installed on her netbook?  The program will not run without the cd installed in the drive, so it does a check for the disc.  What should I try next?  The program will run on my Linux box through Wine, yet it still will not run without the disc in the drive.  How do I make the cd think it is mounted inti a drive so my wife can use it on her Netbook that does not have a dvd drive in it?

---

### Post by perrti-y02 on 2009-05-13
What OS is the netbook running?

---

### Post by perrti-y02 on 2009-05-13
As a bit of a more helpful post you can create an iso image of a disk and then mount it somehow as if it were a cd.

on the linux machine put the cd into the drive and type

```
dd if=/dev/scd0 of=/home/insertnamehere/cdname.iso
```

for /dev/scd0 put the name of the block device for your dvd drive.

This may take a while if it is a DVD. After this I can be of no help, I don't know how you mount an iso but i know it can be done.

---

### Post by The Cog on 2009-05-13
I presume that the program is a wondows program. 

You can get CD emulators for windows that take an image of a CD and make wondows programd think the CD is in the drive (I saw one on a magazine cover once). Or you could run XP in VirtualBox and mount an image of the CD in the virtual drive.

To make an image file of a CD in Linux use this command:
sudo dd if=/dev/cdrom of=my-cd.iso

Edit:
LOL - Snap!

---

### Post by s1mp13m4n on 2009-05-13
The netbook is running WinXP Home on it.

---

### Post by s1mp13m4n on 2009-05-13
In Windows I have tried Daemontools and PowerISO with an ISO image that I made from Linux using K3b and it does not work.  I made the ISO image and placed it on the SD card and tried running it using PowerISO and Daemontools in Windows but it will not work.  It still looks for the cd, so I wonder if it is copy protected.  My next bet might be CloneCD in Windows and see what happens.

---

### Post by s1mp13m4n on 2009-05-13
I got it working by doing what "The Cog" posted.  I used this command: sudo dd if=/dev/cdrom of=my-cd.iso and it made the file for me.  I them cut and pasted it on the SD card, then I mounted it in WinXP useing PowerISO and now my wife has her study tool for her nursing class.  Thank you very much for that help.

---

