---
title: "Something like KNemo for gnome ?"
date: 2007-01-31
forum: Desktop Environments
---

### Post by rohandhruva on 2007-01-31
Hi,

I have a eth0 connection which is not always up. So, what I do is just remove "auto eth0" like in /etc/interfaces and manually use ifup or ifdown as needed. Now, when I use KDE, I use knemo. It is a program that shows "M$ Windows style" two monitors in the system tray. Also, it allows me to add commands when I right click on it, so that I add "Enable" and "Disable" to it, so that the ifup and ifdown commands get executed.

In gnome, I was able to find add the  the "Network Monitor" applet to the system tray, but I have to open a terminal and enter ifup when I need. Is there any app like KNemo for gnome ?

Thanks.

---

### Post by bitfoo on 2007-01-31
You'll want to install network-manager (and network-manager-gnome (ubuntu) or knetworkmanager (kubuntu)); after installing you can remove the network monitor applet from the tray.  The network manager will allow you to right click and disable and enable interfaces at will.

---

### Post by rohandhruva on 2007-01-31
Thank you. I will definitely try it :)

---

