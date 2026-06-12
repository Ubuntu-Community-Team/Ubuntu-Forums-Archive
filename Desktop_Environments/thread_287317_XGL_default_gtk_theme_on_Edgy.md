---
title: "XGL default gtk theme on Edgy"
date: 2006-10-28
forum: Desktop Environments
---

### Post by illegalbuds on 2006-10-28
I installed Ubuntu Edgy 6.10 today. After installing xserver-xgl and other beryl packages, I ran into one problem. I have the latest (8.29.6) ATI driver and XGL seems to load okay with my video card, but my Gnome theme is gone.

This is my desktop with regular Xorg and Gnome
[[IMG]http://img234.imageshack.us/img234/7957/noxglzd6.th.png[/IMG]](http://img234.imageshack.us/my.php?image=noxglzd6.png)

This is my desktop with XGL and Gnome loaded
[[IMG]http://img55.imageshack.us/img55/6798/xglxy1.th.png[/IMG]](http://img55.imageshack.us/my.php?image=xglxy1.png)

Any ideas? Does Edgy (or my ATI card) require AIGLX (not XGL)?

**Note:** I had Dapper with XGL/Beryl on my system working perfectly before trying Edgy. Also, Beryl loads great and replaces Metacity perfectly, but it just looks dumb with my eyecandy Beryl and old default GTK look.

---

### Post by Starlight on 2006-10-30
I have exactly the same problem... I hope it can be  fixed somehow... I don't like that plain gray theme. I tried changing the theme in System/Preferences/Theme, but it doesn't work.

---

### Post by Starlight on 2006-10-30
I found out how to fix it :) Just add gnome-settings-daemon to System/Preferences/Sessions/Startup Programs. :)

---

### Post by illegalbuds on 2006-10-30
Hey thanks man! That worked for me too :-)

---

### Post by gnlnx on 2006-11-05
Thanks Starlight...that worked for me too.

---

### Post by caspian on 2006-11-17
You're awesome, Starlight... thanks!

---

