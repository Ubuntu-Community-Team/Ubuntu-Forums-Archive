---
title: "wmii: How to access the Internet"
date: 2009-01-28
forum: Desktop Environments
---

### Post by johnnyxxxcakes on 2009-01-28
I just recently installed wmii onto my distribution from Synaptic, and I've logged out and logged into the wmii session. I'm learning about the commands and how to use this lightweight window manager and whatnot, but my one problem is that when I open up Firefox, I have no Internet connection, does anybody know what I should do to enable the internet on wmii?

---

### Post by AopicieR on 2009-01-28
Hi,

that certainly depends on how you are connected to the internet. Via WLan or Ethernet? How do you connect to the Internet in your default window manager? 
The most natural way would be to look for a terminal solution to establish the connection. For example if you use WLan you could use wpasupplicant. If you have been using a graphical solution like the gnome or the kde network manager, it should also be possible to just start it in wmii.

Good luck getting used to wmii, I've been using it for about a month now and I'm very pleased with it.

---

### Post by johnnyxxxcakes on 2009-01-28
> **tantris said:**
> Hi,

that certainly depends on how you are connected to the internet. Via WLan or Ethernet? How do you connect to the Internet in your default window manager? 
The most natural way would be to look for a terminal solution to establish the connection. For example if you use WLan you could use wpasupplicant. If you have been using a graphical solution like the gnome or the kde network manager, it should also be possible to just start it in wmii.

Good luck getting used to wmii, I've been using it for about a month now and I'm very pleased with it.

I connect through WiFi via the NetworkManager applet on GNOME. Sometimes the connection is made when I tried Xmonad, but not wmii, or it works the other way around.

---

### Post by AopicieR on 2009-01-31
What happens if you just start the network-manager-gnome in wmii?
For the natural solution: Did you have a look at [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) ? After following the steps there you will probably have to set up the WPA supplicant as described in [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

