---
title: "Ubuntu r Kubuntu?&amp; Wireless Prob?"
date: 2009-11-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by karumudi7 on 2009-11-24
Hello Frnds, Today I got Ubuntu & Kubuntu 9.10. I hav two queries:
1> Which one is the best, I run the live CD of both I was impressed with KUBUNTU.. Is there any difference between Ubuntu & Kubunttu other than Desktop?

2>I noticed that in 9.04,My wirelesscard was automatically recognised and there was a problem with Graphics, Now in 9.10 the Graphics card was finely workind and Broadcom Drivers are not recognised, which are for networking!

DELL Latitude D530
Please solve my two problems, I would like to install 9.10
Thanks!

---

### Post by karumudi7 on 2009-11-24
Anybody there? plz solve my prob..!

---

### Post by teward on 2009-11-24
Ubuntu vs. Kububtu:  No difference other than the desktop interface; Kubuntu uses KDE and Ubuntu uses Gnome.

As for your drivers problems, I can't be of much help, however someone else can.

---

### Post by bobcollard on 2009-11-25
> **karumudi7 said:**
> Hello Frnds, Today I got Ubuntu & Kubuntu 9.10. I hav two queries:
1> Which one is the best, I run the live CD of both I was impressed with KUBUNTU.. Is there any difference between Ubuntu & Kubunttu other than Desktop?

2>I noticed that in 9.04,My wirelesscard was automatically recognised and there was a problem with Graphics, Now in 9.10 the Graphics card was finely workind and Broadcom Drivers are not recognised, which are for networking!

DELL Latitude D530
Please solve my two problems, I would like to install 9.10
Thanks!



If you have room on your hard drive, start with Ubuntu, get the drivers, choose which you need and install it.  For Broadcom Drivers you can get them using an ethernet cable and in Terminal type the following: *sudo apt-get install b43-fwcutter*
You'll find them in system hardware drivers.  Then if you still want KDE after updating your system and restarting you can get the kubuntu desktop either through synaptic or using terminal by typing 
[I]sudo apt-get install kubuntu-desktop
[/I]Then you will have a choice of Gnome or KDE desktops at login[I].
[/I]

---

