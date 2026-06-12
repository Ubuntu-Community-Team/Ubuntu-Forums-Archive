---
title: "My success story with World of Warcraft in linux."
date: 2005-03-30
forum: Gaming &amp; Leisure
---

### Post by askreet on 2005-03-30
I didnt see too many posts on the net about WoW in linux so I figured I'd post exactly what I did in hopes it may help someone else.

My system:
Albartron PX865 PE Pro I motherboard
2.8E Processor
1 GB PC-3200 DDR memory
eVGA 6800GT Video Card (AGP, 256MB)
SBLive! Sound Card
NEC DVD-RW 
80 GB Seagate SATA

What I did:

Clean UbuntuLinux Hoary installation.
Upgraded to 686-smp kernel.
Installed all nvidia driver as per the BinaryDriverHowTo wiki entry.
Installed the latest Point2Play using the .deb file and dpkg -i <filename> method.
Using Point2Play I installed the MS Core Fonts package and Cedega 4.3.0
Using Point2Play I installed World of Warcraft.

CAUTION: I had a number of problems where P2P's Eject Monitoring was causing it not to read the CD on the insertion of the next disc. In order to avoid this DISABLE auto eject funationality and use the Right-Click > Eject on the desktop icon of the CD-ROM drive. This seemed to work flawlessly. Also allow ample time for the CD-ROM to be auto-mounted by the operating system.

Other than that the game and patching went in pretty smoothly. Don't try to download the patcher manually just use the built in patcher, i had a few issues trying to circumvent the built in method.

With my hardware spec (pretty high end?) I get decent performace at 1280x1024... not nearly as good as windows. In windows I can max out everything and maintain a good 30-60 fps.. In linux I need to keep it lower, but I'd much rather avoid having to reboot to play a game.

Also, there is a glitch that I've noticed where footprints in snow flicker and cause huge fps drops... If anyone figures out a solution please post it here so that I and other WoW players can reap the benefits.

Hope this helps someone stuggling to get it to work..

- Skreet

---

### Post by rcbaxter on 2005-04-16
How I got it working:

First, some hardware specs for background purposes.  I'm running Ubuntu Hoary 5.04 on a P4 2.8, Abit DuraMAX AA8 motherboard, 512 DDR2 RAM, with an Nvidia GeForce 6600 PCI Express video card.  I had previously installed nvidia-glx using Synaptic.

1.  Installed Cedega 4.3

2.  Copied the first WoW installation CD to Desktop\cd1

3.  $cedega WoW.exe from within cd1 to start the WoW installer.

4.  Installed WoW just as if in Windows.  *(Swapping CDs worked fine for me)

5.  Downloaded the WoW updates from     [http://www.blizzhackers.com/viewtopic.php?t=261409](http://www.blizzhackers.com/viewtopic.php?t=261409) and manually installed them.

6.  $cedega WoW.exe from within the Wine WoW installation directory.

7.  WoW updated itself to the latest 1.31 build.

From this point, everything has been working great.  I hope this helps some of you.  If you need help, let me know.

---

