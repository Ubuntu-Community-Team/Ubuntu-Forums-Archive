---
title: "Edgy update broke Xorg"
date: 2006-12-17
forum: Desktop Environments
---

### Post by masterkale on 2006-12-17
My machine is in a very poor state right now. I updated from Dapper to Edgy using the command line (the apt-get dist-upgrade) I rebooted once and it worked fine.

 I then installed some updates, rebooted again and now X wont start. I get the "no screens found". So I try the suggested dpkg-reconfigure xserver-xorg and I get the error that xserver-xorg is "broken or not fully installed." Also whenever I do the apt-get update I get the error to use "dpkg --configure -a to correct the problem." And when I run that I get a message saying that the process was halted because there were too many errors. Also, all the text output right above that error is about xserver-xorg.

So did I really screw this thing up or is it somehow fixable?

---

### Post by dbbolton on 2006-12-17
boot the recovery mode and do

sudo nano /etc/X11/xorg.conf


and  you can manually edit it there.

---

### Post by obsidion on 2006-12-17
> **dbbolton said:**
> boot the recovery mode and do

sudo nano /etc/X11/xorg.conf


and  you can manually edit it there.

Surely if xorg is not installed correctly as seems to be the case editing the xorg.conf won't fix it.

Try sudo apt-get install -f and see if you can get the system back to something like working.
You might need to alternate between that and apt-get update, apt-get dist-upgrade, and dpke-reconfigure -a  a few times till you get it working normally again

---

