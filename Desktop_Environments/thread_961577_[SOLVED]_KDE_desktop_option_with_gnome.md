---
title: "[SOLVED] KDE desktop option with gnome"
date: 2008-10-28
forum: Desktop Environments
---

### Post by Kevbert on 2008-10-28
I'm currently running Ubuntu Hardy and would like to have the option to use KDE4.1 from the log-in screen.  What files do I need to install to get this ? (and can I do this via Synaptic ?)

---

### Post by snowpine on 2008-10-28
You can install KDE 3 from Synaptic either as kdebase or kubuntu-desktop (if you want all the apps and themes). For KDE 4, I think you'll need to install it from the .deb's at kde.org...

---

### Post by Kevbert on 2008-10-28
Thanks (yet again) snowpine.:)

---

### Post by snowpine on 2008-10-28
You're welcome. One of these days I will get around to trying KDE...
This might sound shallow, but really the only reason I haven't is I can't stand how all the application start with 'K'! :)

---

### Post by maybeway36 on 2008-10-28
I think you can install the metapackage
```
kubuntu-kde4-desktop
```
from Synaptic.

---

### Post by Xiong Chiamiov on 2008-10-29
It [looks like]("http://packages.ubuntu.com/search?keywords=kde4&searchon=names&suite=hardy&section=all") there is a kde4 package, as well as a kde4-core package, which will install only what is necessary to run KDE, rather than including Kate, Amarok, K3B, etc.

---

### Post by ronocdh on 2008-10-29
> **Xiong Chiamiov said:**
> It [looks like]("http://packages.ubuntu.com/search?keywords=kde4&searchon=names&suite=hardy&section=all") there is a kde4 package, as well as a kde4-core package, which will install only what is necessary to run KDE, rather than including Kate, Amarok, K3B, etc.
This is correct. Searching for "KDE4" in Synaptic will give you everything you need, OP. The great thing about this is that KDE4.1 will install separately from KDE 3.x (and of course you'll still have GNOME, too).

I applaud your willingness to experiment with DEs!

---

### Post by snowpine on 2008-10-29
I stand corrected; thanks for the info people!

---

### Post by Kevbert on 2008-10-29
Thanks to everyone. Unfortunately the Synaptic Package is KDE 4.0 which looks a little unfinished, duplicate icons, missing icons with question marks and only the Kicker menus. Apt updater seems to be for 3.5 and not 4 (as per early Intrepid Alpha releases).  I even got a Segfault the first time I tried it, so I may wait until they release 4.1.2 in the Ubuntu repos for Hardy.

---

