---
title: "Dapper missing thunderbird icon"
date: 2006-05-30
forum: Desktop Environments
---

### Post by scottmuz on 2006-05-30
I have no icon in the KDE panel 
when thunderbird is running 
just a big X in Kubuntu (see screenshot)

Is anyone else seeing this problem?

Any ideas now to solve?

---

### Post by zsazs on 2006-06-01
I also have this problem.

---

### Post by ivomans on 2006-06-01
Not only in the taskbar, also in the window-titlebar it only shows an X.

---

### Post by Kikoolol on 2006-07-02
I got the same issue too, after upgrading to dapper.

Any idea here ? :p 

KKl

EDIT : solved ! The icon was missing in the chrome directory. Just do the following :
"sudo cp /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm"

---

### Post by jgcamp99 on 2006-07-02
Try Ximian Evolution, it comes w/ Ubuntu, I prefer Evolutions integrated approach to Thunderbird & Sunbird as separate applications to do the same thing.

---

### Post by ivomans on 2006-07-03
[QUOTE=Kikoolol]solved ! The icon was missing in the chrome directory. Just do the following :
"sudo cp /usr/share/pixmaps/mozilla-thunderbird.xpm /usr/lib/mozilla-thunderbird/chrome/icons/default/default.xpm"[/QUOTE]

Thanks for the tip! Issue solved for me.

---

