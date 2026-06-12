---
title: "Wine help"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by Korialstrasz on 2007-05-13
I'm a complete nub with linux, just got it yesterday, i know i shouldn't technically be messing with Wine and Beryl but I have been. I've gotten Beryl to run fine and successfully have been able to install Warcraft 3 (just as a test), however i've hit a road block with Wine, in that when i run Warcraft it is very very laggy and this shouldn't be the case with my system:

AMD 64 4400+ 2.2ghz dual core
2 7800 GTX 256 mb video cards (this might be a problem since i don't know if ubuntu supports SLI)
4 Gbs of RAM
250 GBs for Linux (500 for windows but that'll change)
if you need any other specs i'll edit it later.

The sound is working perfectly, I actually was able to run a cinematic however after it ran it crashed.

My main question is what caused this laggy behavior (Beryl wasn't running) and is there a way to play the game off of the hard drive or am i stuck using the CD?

---

### Post by bukwirm on 2007-05-13
Google for "Warcraft 3 no cd crack" - there's probably one somewhere.

> **Korialstrasz said:**
> i know i shouldn't technically be messing with Wine and Beryl but I have been.

You should! That's one of the great things about Linux - you can mess with it however you want! (However, you can also completely trash your system any way you want).

---

### Post by ahaslam on 2007-05-13
Many Windows app's, especially games require a few tweaks (registry and/or configs) to run well under Wine. I don't have your particular game, hopefully someone can advise.

Wine is under heavy development and you may find improvements with a new version, see here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

You can create an iso of the disc & mount it as required. Here's a couple of useful commands:

Make iso from disc:
*dd if=/dev/sr0 of=/tmp/cdimage.iso *
Mount iso: 
*mount -t iso9660 -o loop /path/to/.iso /mnt/*

---

### Post by AndrewRiedi on 2007-05-13
> **Korialstrasz said:**
> I'm a complete nub with linux, just got it yesterday, i know i shouldn't technically be messing with Wine and Beryl but I have been. I've gotten Beryl to run fine and successfully have been able to install Warcraft 3 (just as a test), however i've hit a road block with Wine, in that when i run Warcraft it is very very laggy and this shouldn't be the case with my system:

AMD 64 4400+ 2.2ghz dual core
2 7800 GTX 256 mb video cards (this might be a problem since i don't know if ubuntu supports SLI)
4 Gbs of RAM
250 GBs for Linux (500 for windows but that'll change)
if you need any other specs i'll edit it later.

The sound is working perfectly, I actually was able to run a cinematic however after it ran it crashed.

My main question is what caused this laggy behavior (Beryl wasn't running) and is there a way to play the game off of the hard drive or am i stuck using the CD?

Ubuntu is a Linux distro with a recent Xorg.  So yes, it supports SLI.  However, you will have to set it up in your /etc/X11/xorg.conf file.  The xorg developers are working hard to make it autodetect stuff like this so you won't have to edit such a file in the future.  (I hear the code will make it into Xorg 7.3, but not sure)

Also, although Linux and Ubuntu support dual core and 64-bit, Wine does not currently support either one of these features of your cpu.  (I believe Linux was the first OS to support 64-bit, not 100% sure on that though.)  I would go look at the [Wine Wiki]("http://wiki.winehq.org/UsefulRegistryKeys") for information on making your game render using the opengl rendering engine.  Gdi is more accurate, but a lot slower.  The other option is to wait until the end of summer when the DIB engine will (hopefully) be in Wine which will speed up the GDI renderer a *lot*.

---

### Post by Korialstrasz on 2007-05-13
How exactly do you edit the xorg.conf file, again i'm completely new to this i'm looking at a read only view of the file and i think i understand the code but what do i have to change and how do i do it?

---

### Post by Nythain on 2007-05-13
in terminal
gksudo gedit /etc/X11/xorg.conf
that will open up your xorg.conf in a text editor with root privelages so you can save any changes you make

---

### Post by AndrewRiedi on 2007-05-13
**BE VERY CAREFUL BEFORE EDITING SUCH A FILE.**

Editing this file can make it so you cannot get into your computer without more advanced knowledge if you mess up.  I will see if I can write some instructions later, in the mean time you may want to back stuff up just in case it goes wrong.  Like I said, the Xorg developers are working on getting rid of the file for reasons like these and others.

---

