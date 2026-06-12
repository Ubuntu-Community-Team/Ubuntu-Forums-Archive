---
title: "[SOLVED] VirtualBox update howto"
date: 2008-10-25
forum: Desktop Environments
---

### Post by malty on 2008-10-25
I may have missed it, but not for the want of trying, I have searched VBox, Google and Ubuntu. Can anyone point me to a plain, simple, howto for the updating (or upgrade) of virtualBox, I am currently running 2.0.2 and want to update to 2.0.4. Running in Hardy.

---

### Post by ThaRabbit on 2008-10-25
First, uninstall your current VirtualBox. 
```
sudo aptitude remove virtualbox-2.0
```

Download the new package from:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Install (simply double clicking the .deb will start the installer)

*The installer will mention that an older version is available through the software channel, ignore this.*

Reboot, enjoy.

I had no trouble starting my made-in-virtualbox 2.0.2 XP machine in virtualbox 2.0.4


Alternatively, you can use the repositories.
Please check this website: 
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

For information on how to add the virtualbox repositories to Synaptic. You will then be able to update your virtualbox through Synaptic like any other app :)

---

