---
title: "Ubuntu and KDE-desktop"
date: 2005-05-17
forum: Desktop Environments
---

### Post by sevi on 2005-05-17
In Ubuntu Gnome-desktop there's for notebooks a battery-status symbol.

How can I get this symbol for KDE too? (Is it a "mini-program" or a system-tool?)

thanx for help,
sevi

---

### Post by Seth on 2005-05-17
[QUOTE=sevi]In Ubuntu Gnome-desktop there's for notebooks a battery-status symbol.

How can I get this symbol for KDE too? (Is it a "mini-program" or a system-tool?)

thanx for help,
sevi[/QUOTE]
 It's part of the KLaptop package :)

---

### Post by philipacamaniac on 2005-05-17
The klaptopdaemon package is included with Kubuntu.

Go to Control Center --> Power Control --> Laptop Battery.

Check the box next to "Show battery monitor" and then click the "Start Battery Monitor" if it isn't started already.

---

### Post by sevi on 2005-05-17
hm, thanx ;)

it works.
And how about the icon for network-access.. 
gnome has the icon with the two blinking monitors (you know what i'm talking about? ;))
KDE doesn't have an icon like this :(
How do i get it?

---

### Post by philipacamaniac on 2005-05-17
You need the knemo package.  

1. Make sure you have Universe repositories enabled (see [http://kudos.berlios.de/kf/kisimlar/swmgmt.html](http://kudos.berlios.de/kf/kisimlar/swmgmt.html))
2. K-Menu --> System --> Kynaptic
3. Hit the Update button, and then search for the knemo package

EDIT: Once it is installed, you have to configure it.
4. Restart KDE if you haven't already
5. KDE Control Center --> Internet & Network --> Network Monitor
6. Add a new interface (usually eth0)
7. Apply and restart KDE again

 \\:D/

---

