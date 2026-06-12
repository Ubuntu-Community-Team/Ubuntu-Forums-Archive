---
title: "[SOLVED] Lost desktop effects and options in KDE 4.1 and 3.5"
date: 2008-08-15
forum: Desktop Environments
---

### Post by gtmaneki on 2008-08-15
I think I may have messed up part of my X-windows or KDE configuration, and am hoping you guys have a suggestion to fix it.

**_My problems: _**

1. All at once, my KDE4 desktop effects stopped working.  

2. Additionally, when I select "shutdown" from the application launcher, the only option that then comes up is "logout," when before I could choose from "logout," "shutdown," and "reboot."

3. Finally, if I select "switch user" from the application launcher, I don't get a second login.  Instead, the screen goes black for a few seconds, and then takes me back to the KDE desktop.

I also see the second and third issues if I log into a KDE3.5 session instead of a KDE4 session on my computer.

**_The last thing I was doing: _**

I was following [endy's tutorial](http://ubuntuforums.org/showthread.php?t=51486&highlight=xgame) on Ubuntu Forums about running games in a new X server.  

**_Corrective action I've tried: _**

I followed the instructions to upgrade from KDE4 to KDE4.1.  I am now running KDE4.1, but still have the same issues.

In KDE4 and 4.1, I've tried unchecking and checking various desktop effects icons, and but no desktop effects have appeared.

**_System specs:_**

Kubuntu 8.04 64-bit
AMD X2 4400 processor
4 GB RAM
NVIDIA GeForce 6150 (integrated)

---

### Post by gtmaneki on 2008-08-28
I found out what the issue was: Before I tried Endy's How-To, I had installed the xserver-xgl package to help me with the Neverwinter Nights game because someone had recommended it, and this package screwed up my settings.  Removing this package restored everything to how it should be.

---

