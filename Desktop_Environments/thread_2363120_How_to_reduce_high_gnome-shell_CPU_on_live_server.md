---
title: "How to reduce high gnome-shell CPU on live server"
date: 2017-06-06
forum: Desktop Environments
---

### Post by teledyn on 2017-06-06
The cause is very likely the lack of graphics hardware in the virtualized EC2 servers, but here's my problem: the server runs a *production* GUI app in a nomachine session, so reboots are to be avoided, and with the upgrade to Ubuntu 17.04 (and the deprecation of the Unity desktop) I installed ubuntu-gnome-desktop, but the default configuration now consumes huge CPU resources, which, on a production server, is also to be avoided.

So here's my problem: how do I modify the gnome/Xsession environment so as to simplify the gnome-desktop as much as possible, and preferably without having to reboot the machine -- note that because desktop access is via nomachine (nxclient) I can't simply log out and log in under a simpler desktop manager.

Any and all strategies are welcome :)

---

### Post by TheFu on 2017-06-07
Use LXDE or xfce4 desktops.  If you want something even lite-r, use straight openbox.

Avoid KDE, GNOME, Unity. Those are all heavy GUIs.

---

