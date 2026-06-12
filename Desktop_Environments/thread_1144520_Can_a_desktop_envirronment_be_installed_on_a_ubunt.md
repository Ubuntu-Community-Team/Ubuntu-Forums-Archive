---
title: "Can a desktop envirronment be installed on a ubuntu server query?"
date: 2009-04-30
forum: Desktop Environments
---

### Post by bergayse on 2009-04-30
Please can any one show me how to install a desktop envirronmet or GUI look and feel for ubuntu server? i'm not used to this cmd console thing and also new to ubuntu server.A help from any of you guys would be very much appreciated. Thank you very much in advance

---

### Post by PacSci on 2009-04-30
If you want a GUI on your server, just:

```
sudo apt-get install xubuntu-desktop
```

It will install the Xfce desktop environment on top of your server. (You can also use ubuntu-desktop for GNOME or kubuntu-desktop for KDE, but Xfce is probably the best choice for a server because it's the lightest.)

---

### Post by x1a4 on 2009-04-30
Hi,
You may not want to install any of the *-desktop packages like xubuntu-desktop.  They are meta packages which will install everything a Xubuntu, Ubuntu, Kubuntu etc system has, this includes a host of applications you most likely will not need, especially on a server.  Instead, install just the components you want.  

Some of the things you'll probably want/need are: 

 - Xorg

 - a display manager like GDM (best), KDM (resource hog) or the very light-weight (and ugly) XDM.  

- as this is a server you should look into a lighter GUI like IceWM, Xfce, LXDE or WindowMaker 

- D-Bus
- ALSA if you want sound

- a file manager like Thunar, XFE, EmelFM etc.

- Synaptic if you want to manage your packages using the GUI

Search the repositories for the packages you want.  Xfce package names begin with **xfce4**

---

