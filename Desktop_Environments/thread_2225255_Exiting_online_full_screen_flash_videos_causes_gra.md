---
title: "Exiting online full screen flash videos causes graphic freeze"
date: 2014-05-20
forum: Desktop Environments
---

### Post by bradleypariah on 2014-05-20
UbuntuGnome 14.04 64-bit 
AMD dual core 2.7GHz
4GB DDR2 RAM
Radeon HD5850 1GB DDR3
I built the CCC from scratch, plus I have used the AMD drivers found in Software Update.  

Problem exists in both Chrome and Firefox.
To check if it was Gnome's fault, I downloaded KDE and Cinnamon.  Problem persists in all environments.

No problems until I upgraded from 13.10.
Now anytime I watch flash videos online (which is all the time, everyday), every_single_time I enter fullscreen, I cannot exit.
Pressing the escape key freezes the video, locking it in place.  
Alt-tab yields zero results.
Hot corner is ignored.
The mouse still moves, and while wandering around the screen, the icon changes from "pointer" to "selection", as if I'm pointing at icons or buttons on the screen, but I obviously can't see them.
The only way out is to control+alt+delete and press enter, then log back in.

Oddly enough, using pipelight for Netflix, if I simply use F11 to fullscreen Firefox itself, and *not* press the fullscreen button in Netflix, I can leave fullscreen anytime I want.
If I press Netflix' fullscreen button, and attempt to exit later, freeze.
Unfortunately, Netflix is not my only source of video.  I don't pay for cable, so the internet is my TV.
Problem exists on Fox, Comedy Central, Crackle, Hulu, Project South Park... you name it.  *Everywhere*.

---

### Post by kansasnoob on 2014-05-20
I've been using Ubuntu Trusty + [Flashback w/Metacity]("http://ubuntuforums.org/showthread.php?t=2220264") to stream videos on this hardware:

> AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

No issue so far, but I haven't tried a different DE.

---

### Post by kansasnoob on 2014-05-20
I just happened to think that I had a test installation of Ubuntu GNOME Trusty amd64 installed on different hardware:

> Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

So I tried streaming Bones on Hulu and I had no problem exiting fullscreen.

So I wonder how you're managing the screensaver while using flash?

Aside from that I'd suspect something related to the graphics driver in use but I know less than nothing about Radeon :(

---

### Post by bradleypariah on 2014-06-01
My fix was surgery with a chainsaw, I'm afraid.
I backed up my themes, icons, and home directories.  Then I just wiped the computer and installed Ubuntu 14.04 (rather than Ubuntu Gnome) from scratch.
After restoring my personal stuff and the necessary drivers, I added the Gnome PPA and just installed it on top of Ubuntu, keeping LightDM.
All my full-screen flash woes are gone.
I wish I could help a future Linux user in need with what caused the problem, but I'm sorry, I didn't care enough to find out.
I was sick of my computer freezing after watching a single episode of something.
The problem had been going on for weeks and I wasn't getting anywhere with it.  I appreciate everyone's help just the same.
As far as I'm concerned, it's fixed.

---

