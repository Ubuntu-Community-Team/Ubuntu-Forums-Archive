---
title: "Can't get past KDM login screen"
date: 2007-05-14
forum: Desktop Environments
---

### Post by cewan on 2007-05-14
I have a big problem with Kubuntu 7.04 on my laptop. I had it all installed and everything working fine, but yesterday when I rebooted I couldn't log in anymore. I can't think of anything special that I did install in Kubuntu that would cause this.

The problem is: I boot up.The KDM login screen appears. I enter my name and password and press enter. It starts to load, then the screen goes blank (black) and then returns to the login screen again.

I read somewhere that this behaviour can be caused by the partition being full, so I checked the disk space, and yes my partition was full. So I cleared out some stuff and now I have a little more than 1Gb free (the total partition is around 20Gb). I rebooted and tried to login, but the problem had not gone away!

I can also mention that if I go into console mode (Ctrl+Alt+F2), I can login, but that does not really help getting KDE running again...

Anyone knows how to solve this issue?

BR

---

### Post by thayerw on 2007-05-24
Assuming you haven't fixed this yet... make sure you delete the ~/.Trash directory too, which is where files are moved to when they are simply deleted from the computer:

---

