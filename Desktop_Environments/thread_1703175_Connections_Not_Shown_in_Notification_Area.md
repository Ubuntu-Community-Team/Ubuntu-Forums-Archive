---
title: "Connections Not Shown in Notification Area"
date: 2011-03-08
forum: Desktop Environments
---

### Post by ThatOne on 2011-03-08
Some background information..

My dad has an older netbook that I installed Ubuntu 10.10 to, but he complained that it was too clunky.

So I did what any good son would do and **installed GNOME and Ubuntu themes on top of the minimal version of Ubuntu 10.10.**

It does run much faster, but I have a small problem with the Notification Area:

nm-applet IS running.
Notification Area is added to my panel, and in view
I have two interfaces, one wired, one wireless, both function correctly (both manually configured with gedit)

Neither one of the aforementioned interfaces are being displayed in the Notification Area, and my dad is not familiar with Ubuntu or any of the commands, so this is really a must-have for him.

Thanks.

---

### Post by Krytarik on 2011-03-09
> **ThatOne said:**
> (both manually configured with gedit)
That maybe the reason why NM can't handle them! Do a backup of the config files, then check them via "System -> Preferences -> Network Connections" and save them from there.

---

### Post by ThatOne on 2011-03-09
Thanks for the information.


After randomly playing around, I flipped my wifi switch off and back on, and then the connection was there.

Irritated to know that was the problem, but glad it's fixed.

Thanks.

---

