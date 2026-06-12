---
title: "Missing &quot;Desktop&quot; bar in Ubuntu 11.10"
date: 2011-11-09
forum: Desktop Environments
---

### Post by gordonaw on 2011-11-09
I apologize in advanced if this has been solved in another thread, or if I'm posting in the wrong thread.
 
I'm new to Ubuntu and Linux. I've installed Ubuntu 11.10 in VMWare Player 4.0. The Global Menu Bar is functional across the various apps (Terminal, Home, Libre). However it will not show the "Desktop" menu bar. I can only see a version of it if I open Home (which at the top shows Home). When there are no apps running if I move my mouse to the top of my screen "Desktop" should appear in the top bar and give me File Edit View GO Bookmarks and Help. However it's just blank except for the items on the right (sound, time, my user account, the gear icon, etc.). On my laptop which also has Ubuntu 11.10 I do see the "Desktop" menu bar. 
 
I've tried installing CCSM and disabling and reenabling the Unity plug-in. I've also removed the Global Menu Bar packages and reinstalled them. Neither has helped me gain access to this menu bar. I'm not sure where to go next.
 
Also I was wondering where to go to look at and/or configure the display drivers that Ubunu sees in this virtual environment. I have no xorg.conf file in my X11 folder. Reaon why is a couple times the top bar turned light grey, like after restoring it from sleep mode, and the gear icon disappears as well as icons in the system prefences screen. A reboot fixes it but I also had this problem on another laptop that was using NVidia drivers. Just wondering what causes this and how I can fix it.
 
Thanks!
 
Andrew

---

### Post by randywilharm on 2011-11-09
> **gordonaw said:**
> I apologize in advanced if this has been solved in another thread, or if I'm posting in the wrong thread.
 
I'm new to Ubuntu and Linux. I've installed Ubuntu 11.10 in VMWare Player 4.0. The Global Menu Bar is functional across the various apps (Terminal, Home, Libre). However it will not show the "Desktop" menu bar. I can only see a version of it if I open Home (which at the top shows Home). When there are no apps running if I move my mouse to the top of my screen "Desktop" should appear in the top bar and give me File Edit View GO Bookmarks and Help. However it's just blank except for the items on the right (sound, time, my user account, the gear icon, etc.). On my laptop which also has Ubuntu 11.10 I do see the "Desktop" menu bar. 
 
I've tried installing CCSM and disabling and reenabling the Unity plug-in. I've also removed the Global Menu Bar packages and reinstalled them. Neither has helped me gain access to this menu bar. I'm not sure where to go next.
 
Also I was wondering where to go to look at and/or configure the display drivers that Ubunu sees in this virtual environment. I have no xorg.conf file in my X11 folder. Reaon why is a couple times the top bar turned light grey, like after restoring it from sleep mode, and the gear icon disappears as well as icons in the system prefences screen. A reboot fixes it but I also had this problem on another laptop that was using NVidia drivers. Just wondering what causes this and how I can fix it.
 
Thanks!
 
Andrew


Try resetting the Xorg server:

sudo dpkg-reconfigure -phigh xserver-xorg

.

---

### Post by Mark Phelps on 2011-11-10
If that doesn't work, you're most likely going to have to uninstall compiz and unity, clean up the remainder, and reinstall compiz and unity.  All I did was OPEN ccsm -- and the same thing happened to me.

Steps are included in the link below: 

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by azkraja on 2011-11-10
I am facing same problem, i have re-installed OS 3 time due to this bug, Unity Bar has disappeared suddenly and works temporarily after "unity --rest" during resetting terminal shows in many lines that it should not be happened, file a bug report.
I am also new to Ubuntu and fed up from this bug, After disappearing this bar, we can login to Ubuntu 2D are as a guest user, but it works again only a day or two. 
Experts please let us know why this happened? it might be some of our mistake or its a really bug.

---

