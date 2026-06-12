---
title: "[SOLVED] Ubuntu + KDE"
date: 2008-02-29
forum: Desktop Environments
---

### Post by Damanther on 2008-02-29
I have a fresh Ubuntu 64 bit install and it works well. I wanted to try the KDE desktop and so I installed the kde 3.5 stuff, WITHOUT installing kubuntu-desktop.

Which means that when I start up, I still get the gdm greeter/ login display, and my session chooser points to KDE by default, and I can switch it to gnome and all still works well.

My question is, it seems odd to startup with gdm if I'm basically going to use kde 99% of the time. Is there a way to switch the startup to use the kdm greeter instead of the gdm greeter without just installing kubuntu-desktop??

Not overly important and the only reason I ask is because I found a new kdm login greeter that I would like to use, but I can't use it since gdm is the greeter that gets launched on startup.

Damanther

---

### Post by benerivo on 2008-02-29
You would need to install kdm. During the kdm installation you should be asked which login manager you want to use as the default.

EDIT - If you have trouble changing the default login manager, then try```
sudo dpkg-reconfigure kdm
```

---

