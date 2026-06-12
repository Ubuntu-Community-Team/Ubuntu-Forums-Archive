---
title: "Gnome-network-manager not managing!"
date: 2009-06-12
forum: General Help
---

### Post by rbolio on 2009-06-12
Sooo after a venture with installing Ubuntu Studio 9.04 (comes without various things, such as gnome-network-manager) 

So after doing all the necessary updates and installing "gnome-network-manager" i reeboted (as instructed) and hey, it was in the notification area, but when I click on it to select a different network it says (in a blacked out , unclicable manner) 

"device not managed" 

If I right click it and press "edit connection"  the GUI comes up but it's practically worthless, for everything I do has no outcome.....

help please!....

Thanks for your time!

---

### Post by majamba on 2009-06-12
huh strange, that gui is only one that has been working for me
you could try wicd

try ifconfig
try iwconfig

---

### Post by cariboo on 2009-06-12
I had the same problem, what worked for me was to uninstall network-manager-gnome and install gnome-network-admin. To set up your network device go to System-->Administration--Network.

---

### Post by rbolio on 2009-06-12
I already have gnome-network-admin, however i con only acces wireless networks towhich i know the SSID (aka....no accessing hotspots and stuff)

also, it doesn't connect automatically to any wireless network....

---

### Post by rbolio on 2009-06-13
so....Any suggestions?

---

### Post by gradinaruvasile on 2009-06-13
What you have in your /etc/network/interfaces file?
If using networkmanager u should only have

auto lo
iface lo inet loopback

in it

---

### Post by rbolio on 2009-06-13
heres my /etc/network/Interface  outcome (or the gedit file :D)

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-essid linksys 01



iface eth0 inet dhcp

auto eth0

auto wlan0
```


However, I installed WICD and it worked!....is there anyway to put it in the notification area?? (you know as the normal connection manager is?)

heehhehe once more thanks for all your help! :D

---

