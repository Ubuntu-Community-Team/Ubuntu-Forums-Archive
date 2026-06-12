---
title: "Need fresh copt of GNOME"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Singee15 on 2005-11-04
I am using breezy and started out with GNOME then just for fun decided to install KDE just to try it, so i used kde for a day and changed some desktop setting to get it looked nice and decided that I just like GNOME better, so I went back into GNOME and it was all messed up. Fonts, colors, menus, basically what seems to be too much to go through and repair.

Is there a way to get a new copy of GNOME and make sure that KDE is gone?

Thanks

---

### Post by Xian on 2005-11-04
You can get rid of KDE by removing the kdelibs package and listed deps. As far as a "new" Gnome, the only thing I can recommend is that you remove the hidden Gnome pref folders (.gnome, .gnome2, etc.) in your home directory, and let them auto-repopulate the next time you login, which is to say your desktop will be reset to the default look.

---

