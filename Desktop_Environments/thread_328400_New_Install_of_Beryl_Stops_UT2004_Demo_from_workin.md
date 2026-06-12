---
title: "New Install of Beryl Stops UT2004 Demo from working"
date: 2006-12-30
forum: Desktop Environments
---

### Post by grunge09 on 2006-12-30
I have Ubuntu Dapper LTS which I did the Internet upgrade to Edgy.   I installed Beryl today, right for now without opening terminal up and running UT2004 demo it runs fine.  BUT if I open terminal and run "beryl-manager" Then try to open UT2004 Demo All I get is the UT splash screen and kicked back out to the desktop.  

If I logout of Ubuntu and log back in beryl is off (I haven't figured out how to stop beryl from the command line yet and after visiting beryls site I am still as clueless)

My system:
AMD 4000+ Single Core Skt 939 Stock Cooling no overclocking
ECS Kn1 Extreme MB
Kingston ValueRam 1 GB RAM (2x512 sticks) 
WD 250GB SATA II 300 HD on SATA II channel on MB
Sapphire 850 XT PCI Express 256 MB DDR3 Video Card
Ubuntu Dapper LTS upgraded via Internet to Edgy 6.10 i386 version installed from ALT CD.
I am using onboard sound at the moment I just got a Creative Labs X-Fi sound card which I will be installing soon.

My question is:

1 Is there a terminal command to manually unload Beryl-manager so I cna play UT2004 demo?  I tried closing the Emerald icon in the top right and that does not stop beryl.

2. Is there a way Beryl and UT2004 demo can "just get along?"

---

### Post by Stemp on 2006-12-30
> 1 Is there a terminal command to manually unload Beryl-manager so I cna play UT2004 demo? I tried closing the Emerald icon in the top right and that does not stop beryl.

click on beryl manager, Windows manager --> Metacity or whatever you want

---

### Post by Shay Stephens on 2007-01-03
> **Stemp said:**
> click on beryl manager, Windows manager --> Metacity or whatever you want
I hate to be dense, but I can't find any of that.  I tried going to System - Preferences - Beryl Settings Manager, but that seems to be as close as I can get.  Am I in the wrong area?  Overlooking something?

---

### Post by Lord Illidan on 2007-01-03
It is that diamond in the taskbar.

---

### Post by Shay Stephens on 2007-01-03
Hmm, that seems to be the problem then, I don't have a task bar icon.  Is there any other way to get to it.  A terminal command maybe?

---

### Post by Shay Stephens on 2007-01-03
Ok, I think I got it.  I typed in beryl-manager in the terminal and now I have a red jewel in the taskbar.  :-)

edit: Yep, that did it, I can now turn it on and off at will :-)  thank you!

---

