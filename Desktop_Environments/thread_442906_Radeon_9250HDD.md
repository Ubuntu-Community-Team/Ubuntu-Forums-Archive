---
title: "Radeon 9250/HDD"
date: 2007-05-14
forum: Desktop Environments
---

### Post by InfamousMyzt on 2007-05-14
I tried 6.10 of ubuntu, and when I did, no driver i found would support 3D. I need to be able to play games like WoW on my ubuntu, and i'm wondering if 7.04 has a better driver for it, or if 7.10 will have one. If not, I give up on linux, as it's taking a lot of time to do so little.

Also, if anyone can tell me why this happened, thanks....

I had 2 IDE hdd's set up. I did NOT have a master/slave setup, but i switched the masters out. One was a 80gb with ubuntu 6.10, and a 120gb with windows xp. After i setup ubuntu on the 80gb, windows wouldnt work on the other one, and now i think its completely shot. It wont work and it wont install windows anymore. I'm now scared to even try to put ubuntu on another drive, as it might endanger the 80gb which i had to put windows on. Anyone know why this happened? Or how to fix my 120 GB? (Not looking for a suggestion to do master/slave, because, I DON'T WANT TO.)

Thanks...It's been bugging me for a long time and I'd like to use ubuntu, but I don't see it being good enough for me.

---

### Post by InfamousMyzt on 2007-05-14
bump...

---

### Post by Ken_Lewis81 on 2007-05-14
Bump?!? You cheeky rascal!

I'm not sure what your hardware is like, so the stuf below about your disks is my best guess to help you -- take care while doing this so you don't lose your data!

I don't understand what you mean about haveing both disks as master - are you swapping cables or putting each as master on its own IDE connector?  If the former, you may have damaged the connectors.  If each is on its own IDE bus, then Windows will be stroppy if it's connected to IDE2 instead of IDE1.  Ubuntu is groovy and will run from nearly any bit of disk space you can give it.

Alternatively, Windows may have had the small program which sets everything going, called a boot-loader, on the disk you formatted with Ubuntu.  If you're to use the 120GB disk with Windows as a Master, then it will need to have the Windows boot-loader put on it.  You can find the Win98se Rescue Disc floppy-disc image around on the internet, which has the program you need on it.  If this is the case, boot from the Win98se rescue floppy, or make a CD with the floppy as the boot-image (most CD writing software permits a bootable project and allows you to supply a disk image for booting).  Then, when you have the "D:\>" or "E:\>" prompts, type "FSCK /mbr".  That might rescue Windows, if this is what's broken.

BTW, the Radeon driver for X.org has support for the 3D capabilities of your card.  It should have been installed automagically.  If not, a terminal window and the command "sudo dpkg-reconfigure xserver-xorg" will allow you to reconfigure the X Server to use the Radeon driver.

Take care.
Ken.

---

### Post by InfamousMyzt on 2007-05-14
It was the first one. Swapping cables.

---

### Post by InfamousMyzt on 2007-05-15
Also, the default driver was horribly laggy. And it thought my main was my internal intel card which i use for my second monitor, and I had to to a dpkg for xorg to reconfigure the driver myself.

---

### Post by InfamousMyzt on 2007-05-16
bump...

---

### Post by Ken_Lewis81 on 2007-05-16
I couldn't say what's going on with your 120GB disk.  Sorry.

Take care.
Ken.

---

