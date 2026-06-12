---
title: "[SOLVED] How to Load KDE"
date: 2006-06-14
forum: Desktop Environments
---

### Post by dstein on 2006-06-14
I am running Ubuntu, and my system is set to boot to a terminal, and I proceed to load Gnome by styping startx. Because of this setup, when I logout, it goes back to the terminal rather than going back to Gnome login screen. Now here's my problem:

I followed the instructions on [http://psychocats.net/ubuntu/kde.html](http://psychocats.net/ubuntu/kde.html) to install KDE. Unforunately, since I do not get the login screen, I am unable to click options, then select session, then KDE. How would I go about loading KDE from the terminal. Typing startx loads Gnome, as this must still be the default. Thanks.

---

### Post by aysiu on 2006-06-14
Instead of typing *startx*, try this: ```
sudo /etc/init.d/gdm start
```

---

### Post by dstein on 2006-06-14
I will give this a shot, but before I do, how would I go about loading back Gnome when I want to. Also, why would I type "sude /etc/init.d/gdm start" to load KDE. I was under the impression that gdm was associated with Gnome. Did you intend to type kdm start? Thanks.

---

### Post by aysiu on 2006-06-14
KDM can load both KDE and Gnome.
So can GDM.

The difference is that GDM will ask you every time you switch between KDE and Gnome whether you want to make it the new default or switch for only that session.

KDE will just switch and keep Gnome or KDE the default until you switch again.

---

### Post by dstein on 2006-06-14
I should also mention that even though my computer still loads into Gnome, my startup and shutdown splash screens say "Kubuntu". This started immediately after installing kubuntu-desktop.

---

### Post by aysiu on 2006-06-14
[This](http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6) may help.

---

