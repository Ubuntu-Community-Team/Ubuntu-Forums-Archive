---
title: "Cant enable desktop effects in KDE, works fine in GNOME"
date: 2010-11-06
forum: Desktop Environments
---

### Post by P4man on 2010-11-06
Hi,

Every year or so I give KDE another try (I really want to like it). So I installed kubuntu-desktop on top of my ubuntu install and tried it. In a KDE session I get terrible flickering and the interace is really laggy and buggy.

Turns out I cant enable desktop effects, it says "due to technical reasons"' but none are given. Compiz works fine on gnome.

Im using the 10.9 catalyst drivers from jockey on (k)ubuntu 10.10 with a radeon 4870. Anything obvious Im missing?

---

### Post by mister_playboy on 2010-11-06
To clarify, are you running Compiz or KWin as the compositor in Kubuntu?

---

### Post by P4man on 2010-11-06
Neither I think? How do I check or change?

---

### Post by mrcreativity on 2010-11-06
I'm experiencing the exact same thing. I know i haven't enabled kwin or compiz by myself. No idea if it's enabled by default. Any suggestions?

---

### Post by mister_playboy on 2010-11-06
I haven't installed Compiz on my Kubuntu (although I've thought about it since KWin performance is so crappy), so I don't know how they interact if you have both.

If the box at System > System Settings > Desktop Effects > General > Enable Desktop Effects is checked, then I assume KWin is in charge on your KDE desktop

You might want to try checking the box at System > System Settings > Desktop Effects > Advanced > Disable Functionality Checks and restarting X.

I have KWin effects working on an Intel 965, but they become slower and slower over the course of a few hours until they disable themselves... :P

---

### Post by P4man on 2010-11-06
I cant access those settings, they are all greyed out. 

[[IMG]http://img5.imagebanana.com/img/ey4o5pum/thumb/DesktopEffectsSystemSettings_014.png[/IMG]](http://www.imagebanana.com/view/ey4o5pum/DesktopEffectsSystemSettings_014.png)

I just removed the proprietary ATI driver, and the problem is still exactly the same. Well, it seems faster and less buggy, but still no desktop effects.

Compiz isnt running btw

---

### Post by P4man on 2010-11-06
Tried starting Kwin from a terminal, perhaps this helps:
```

kwin --replace
kwin(3910) KWin::CompositingPrefs::detectDriverAndVersion: GL vendor is "Advanced Micro Devices, Inc." 
kwin(3910) KWin::CompositingPrefs::detectDriverAndVersion: GL renderer is "Mesa DRI R600 (RV770 9440) 20090101  TCL DRI2" 
kwin(3910) KWin::CompositingPrefs::detectDriverAndVersion: GL version is "2.1 Mesa 7.9-devel" 
kwin(3910) KWin::CompositingPrefs::detectDriverAndVersion: Detected driver "radeon" , version "20090101" 
kwin(3910) KWin::Workspace::setupCompositing: **KWin has detected that your OpenGL library is unsafe to use, falling back to XRender. **
kwin(3910): Failed to initialize compositing, compositing disabled 
kwin(3910): Consult http://techbase.kde.org/Projects/KWin/4.0-release-notes#Setting_up 
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

```

That is with the opensource drivers. I suspect it was the same with the proprietary ones, Ill check in a minute.

---

### Post by mrcreativity on 2010-11-06
Since I have an ATI card, this worked for me:

[http://matthieu.yiptong.ca/2010/09/28/enable-desktop-effects-in-kubuntu-10-10-using-radeon-driver/](http://matthieu.yiptong.ca/2010/09/28/enable-desktop-effects-in-kubuntu-10-10-using-radeon-driver/)

---

### Post by mister_playboy on 2010-11-06
Googling for that error message came up with this thread: [http://www.pclinuxos.com/forum/index.php?topic=78790.0](http://www.pclinuxos.com/forum/index.php?topic=78790.0)

Some people getting this message on Intel 945 graphics had success deleting kwin's config file and letting it rebuild.  Maybe best to back it up, too.

```
mv ~/.kde/share/config/kwinrc ~/.kde/share/config/kwinrc1
```

---

### Post by P4man on 2010-11-06
> **mrcreativity said:**
> Since I have an ATI card, this worked for me:

[http://matthieu.yiptong.ca/2010/09/28/enable-desktop-effects-in-kubuntu-10-10-using-radeon-driver/](http://matthieu.yiptong.ca/2010/09/28/enable-desktop-effects-in-kubuntu-10-10-using-radeon-driver/)

I had just found the same link, and indeed it works for me as well. Strange that both radeon and fglx are affected by this, that basically means 100% of ATI users.

---

### Post by paulo.bartos on 2010-11-12
> **P4man said:**
> Tried starting Kwin from a terminal, perhaps this helps:
```

kwin --replace
kwin(3910) KWin::CompositingPrefs::detectDriverAndVersion: GL vendor is "Advanced Micro Devices, Inc." 
kwin(3910) KWin::CompositingPrefs::detectDriverAndVersion: GL renderer is "Mesa DRI R600 (RV770 9440) 20090101  TCL DRI2" 
kwin(3910) KWin::CompositingPrefs::detectDriverAndVersion: GL version is "2.1 Mesa 7.9-devel" 
kwin(3910) KWin::CompositingPrefs::detectDriverAndVersion: Detected driver "radeon" , version "20090101" 
kwin(3910) KWin::Workspace::setupCompositing: **KWin has detected that your OpenGL library is unsafe to use, falling back to XRender. **
kwin(3910): Failed to initialize compositing, compositing disabled 
kwin(3910): Consult http://techbase.kde.org/Projects/KWin/4.0-release-notes#Setting_up 
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

```

That is with the opensource drivers. I suspect it was the same with the proprietary ones, Ill check in a minute.

I had the exact same problem as P4man, as I have an old and discountinued ATI card. I need to use de opensource driver. 

Doing as mister_playboy said and 

mv ~/.kde/share/config/kwinrc ~/.kde/share/config/kwinrc1

and i was able to activate and configure My desktop efects once again.

Thanks for everyones help!!!  :P:P:P:P:P

---

