---
title: "[SOLVED] Panel Disappeared"
date: 2008-07-23
forum: Desktop Environments
---

### Post by COLiNx86 on 2008-07-23
I was messing with conky and then I logged out and logged back in and my panel was gone. I tried ctrl alt backspace but it didn't work. I tryed compiz --replace but it didn't work either.
Any Ideas on how i could get my panel back?

---

### Post by tamoneya on 2008-07-23
are you talking about your conky panel or are you talking about gnome-panel(the things on the top and bottom)

conky panel missing: alt-f2 and type```
conky ~/.conkyrc
```

gnome-panel missing: alt-f2 and type```
gnome-panel
```.  If you cant get alt-f2 to work you can hit ctrl-alt-F1 to go to tty1 and reconfigure ubuntu-desktop:```
sudo dpkg-reconfigure ubuntu-desktop
```
Then hit ctrl-alt-F7 to return to gdm.

---

### Post by COLiNx86 on 2008-07-24
[LEFT]Thanks, but I solved it. some how I must of accidentally uninstalled ubuntu-desktop
[/LEFT]

---

### Post by tamoneya on 2008-07-24
glad to hear it is working for you.  Can you mark the thread solved in the thread options menu?
Thanks

---

