---
title: "Hauppauge tv-card issues"
date: 2006-01-12
forum: General Help
---

### Post by TLE on 2006-01-12
Hey
I'm trying to get some television watching and capturing to work but I'm having some problems with it. But first things first, I have some difficulty identifying exactly what card it is that I have, and it is sort of hard to find help without it. I run a dual boot so I looked in the Windows and it has my card registerede as a WinTV PVR PCI II (26xxx).
So what I can't figure out is, that migth mean that my card is a WinTV PVR PCI II, but if I look at this page on the hauppauge homepage [http://www.hauppauge.com/pages/support/support.html](http://www.hauppauge.com/pages/support/support.html) it says that cards with numbers (26xxx) is a WinTV-PVR-150 card. Can anyvody help me clear this up, so I can start searching for help
Regards TLE

[Edit] I meant to include, that when I say that i found the number WinTV PVR PCI II (26xxx) in Windows XP I mean that I found it in the device maneger

---

### Post by dbeckham32 on 2006-01-12
What does your dmesg tell you? Reboot your machine and run this command in the terminal:

dmesg > ~/dmesg_dump.txt


Somewhere in the resulting text file you should be able to see the name of your Hauppauge TV card. Mine reads "Hauppauge WinTV PVR 250" or words to that effect.

Also, have you installed the driver yet? If not, you'll need the IVTV driver from [http://www.ivtvdriver.org/index.php/Main_Page](http://www.ivtvdriver.org/index.php/Main_Page).

Let me know how it goes. It can be a bit tricky to install the driver.

---

### Post by TLE on 2006-01-12
Thanks, I found the line
[4294701.313000] ivtv0: Initialized WinTV PVR 150, card #0
so now I KNOW what kind of card I have. That was actually what I had already guessed on, so I have already tried this how to
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
(posted in this thread [http://www.ubuntuforums.org/showthread.php?t=106713&highlight=pvr-150](http://www.ubuntuforums.org/showthread.php?t=106713&highlight=pvr-150) ) for the WinTV PVR 150 on how to install the drivers. I followed it down through 1-5 but no further since I don't think mythtv is for me. But It does not work so before I went any further I wanted to make sure that I hadn't already messed it up by installing the wrong drivers. So now that I know, I'm going to start seraching the forum for the error massages. If I don't find anything I'll post here again.

Thanks

---

