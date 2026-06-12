---
title: "How do I set an option to load either Gnome or KDE at boot up"
date: 2006-07-27
forum: Desktop Environments
---

### Post by Galactus on 2006-07-27
I heard the guys on the Ubuntu Podcast mention that it was possible to download KDE desktop and at boot up have the option to boot into either a KDE or Gnome environment. 

Is this possible and if so what do I need to get from the repository (i.e. KDE desktop?) and how do I set it up?

Thanks

---

### Post by reacocard on 2006-07-27
```
sudo apt-get install kubuntu-desktop
```

then kde will also be available as an option in Options -> Sessions at the login screen.

---

### Post by ozorba on 2006-07-27
First of all you need to install ubuntu-desktop and kubuntu-desktop. using either synaptic or apt-get.

sudo apt-get install ubuntu-desktop  (for GNOME)
sudo apt-get install kubuntu-desktop (for KDE)

When you get graphical interface and type in your login name and password just press F10 and select the session. Then when you press enter it tells you if you want the selected session to be the default (permanent) one.

Alternatively, there is a file that you can modify in /etc directory. But  the first option is much nicer...

--

---

### Post by aysiu on 2006-07-27
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

