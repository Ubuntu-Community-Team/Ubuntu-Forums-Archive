---
title: "how to set default desktop as Gnome instead of KDE?"
date: 2006-11-17
forum: Desktop Environments
---

### Post by bricedebrignaisplage on 2006-11-17
I gave KDE a try and now it's my default session. I prefer Gnome. How can I set Gnome as default. I am tired of always having to select it in the session menu.
PS: now I have a KDE login screen...

Brice

---

### Post by bricedebrignaisplage on 2006-11-17
Some corrections:
The default session is not KDE but my previous session. It's just the login screen that has changed. So the question becomes: how to set the login window to Gnome's one? There is an item in the administration menu called 'login window' but it doesn't open anything ....

---

### Post by aysiu on 2006-11-17
KDM defaults to whatever you used last.
GDM will ask you if you want to make whatever you're selecting the default (if it is not already the default).

Sounds as if your display manager is messed up. If KDM isn't working out for you, you can use GDM instead. Have you tried this [terminal](http://www.psychocats.net/ubuntu/terminal) command? ```
sudo dpkg-reconfigure gdm
```

---

### Post by Encore1974 on 2008-05-13
Hi 

Thanks, that fixed my gnome. I have ubuntu 8 and i installed kde4 and it is horrible so i wanted to remove it completely but the default session was kde so gnome couldn't start. 

I removed kde4 completely with 

sudo apt-get remove --purge kdebase-bin-kde4
sudo apt-get autoremove --purge


Reconfiguring gnome using

sudo dpkg-reconfigure gdm

fixed gnome. 

Thanks

---

