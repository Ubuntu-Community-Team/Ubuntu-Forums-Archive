---
title: "gnome-keyring-daemon taking 100% cpu"
date: 2006-06-17
forum: Desktop Environments
---

### Post by jkusar on 2006-06-17
Hello all,

I have Ubuntu Dapper installed on my Dell 700m laptop.  Everything worked great for a while, but now, when I try to connect to a wireless network, gnome-keyring-daemon starts taking 100% of the cpu and basically brings the computer to a halt.  It takes about 2 minutes before it finally finishes whatever it's doing.  I have a broadcom 4306 network card.  I've tried using both the bcm43xx driver and ndiswrapper with the Windoze drivers with the same results.

Has anyone else experienced this?  Any suggestions?

Thanks!
--Jason

---

### Post by BungaMan on 2006-09-12
I got the same since about a week.  I first have to type in the pass phrase for my WPA network.  Then it asks to set a password for the gnome keyring and wham 100% CPU and the size in memory goes up to around 350MB.  Now that I know this in advance I start up system monitor.  When the daemon grows excessivly I kill it.  After that everything runs as normal.  Even my wifi connection runs perfect.

---

### Post by gpierce on 2006-10-14
I have the exact same problem. Gnome-keyring-daemon grows to over 1.8GB on my laptop before it dies. Also, it can't seem to remember my network keys. I thought I was alone with this problem. Hope someone speaks up soon about a solution. My laptop crawls when I am prompted to type a passphrase to store the key.

---

### Post by za0 on 2006-11-04
Hi People,

same sh*t here. I am runnung Dapper (6.06). Well I tried to solve it by compiling the newest version of keyrings - but it did solve problem. Well - bullsh*t - thats all I can say.

There is no solution, is it?

---

### Post by Slasher Fun on 2006-11-17
Same problem with me, so just see there how to fix it :
[https://launchpad.net/products/gnome-keyring/+bug/60765](https://launchpad.net/products/gnome-keyring/+bug/60765)

You can also delete the supposed-to-be-corrupted keyring file named default.keyring in the folder ~/.gnome2/keyrings

---

