---
title: "Restricting users..."
date: 2009-09-21
forum: Desktop Environments
---

### Post by questo on 2009-09-21
I've run into a problem, I'm installing a workstation to be put up at my school, and I've pretty much restricted the users so they can't really do much.. Which is good, but they can still change desktop settings, such as wallpapers, panels, themes, icons, fonts etc. This is very bad cause I know that someone will mess with the box and have inappropriate wallpapers etc etc.

So I'm asking you, the Ubuntu community to help me out!
// Q

---

### Post by Lars Noodén on 2009-09-21
KDE has a kiosk mode.

[http://enterprise.kde.org/articles/kiosk-lp.php](http://enterprise.kde.org/articles/kiosk-lp.php)
[http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)
[http://developer.kde.org/documentation/tutorials/kiosk/](http://developer.kde.org/documentation/tutorials/kiosk/)

Xfce also has a kiosk mode.

[http://www.xfce.org/documentation/4.2/manuals/xfce4-session](http://www.xfce.org/documentation/4.2/manuals/xfce4-session)
[http://www.xfce.org/documentation/4.2/api/libxfce4util/libxfce4util-Xfce-Kiosk-functions.html](http://www.xfce.org/documentation/4.2/api/libxfce4util/libxfce4util-Xfce-Kiosk-functions.html)
[http://wiki.xfce.org/howto/kiosk_mode](http://wiki.xfce.org/howto/kiosk_mode)

Also, if you make a parallel copy of the user directory, with settings and all, when it is just the way you like it, then you can have it restored at startup or shutdown using a script with rsync.

---

### Post by mcduck on 2009-09-21
> **questo said:**
> I've run into a problem, I'm installing a workstation to be put up at my school, and I've pretty much restricted the users so they can't really do much.. Which is good, but they can still change desktop settings, such as wallpapers, panels, themes, icons, fonts etc. This is very bad cause I know that someone will mess with the box and have inappropriate wallpapers etc etc.

So I'm asking you, the Ubuntu community to help me out!
// Q

Ability to change these settings can be disabled through Gconf. But you'll probably want to try Sabayon and Pessulus, Gnome's tools for editing user desktops and limiting user abilities, instead of doing it manually.

---

### Post by MechaMechanism on 2009-09-21
Have you looked at the program "polkit-gnome-authorization".  This program is in "System/Administration/Authorizations.  I don't have any experience with it, but it might be worth a look.  At first glance it seems to be what you are looking for.

---

