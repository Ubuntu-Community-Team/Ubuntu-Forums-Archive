---
title: "is there a global menu bar option available for xfce ?"
date: 2011-01-24
forum: Desktop Environments
---

### Post by rvchari on 2011-01-24
i ve been using xfce for the past couple of days and i am awed by the speed and efficieny in comparision to gnome / kde...

now, i ve been using gnome all thru and i had tweaked it to the best possible way complete with a global menu et all... is global menu bar option available in sfce desktop environment ?

---

### Post by hhh on 2011-01-24
Are you talking about this?...
[http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/)

I haven't used it, but it looks like it's a panel applet...
[http://code.google.com/p/gnome2-globalmenu/wiki/Installation](http://code.google.com/p/gnome2-globalmenu/wiki/Installation)

If that is the case, you can install xfce4-xfapplet-plugin which allows the use of gnome-applets on xfce. Install it from Synaptic or via a terminal...```
sudo apt-get install xfce4-xfapplet-plugin
```

Install gnome2-globalmenu, then add a new item to your panel and choose XfApplet and choose gnome2-globalmenu. The globalmenu FAQ has a note for Xfce users (see number 10)...
[http://code.google.com/p/gnome2-globalmenu/wiki/FAQ](http://code.google.com/p/gnome2-globalmenu/wiki/FAQ)

It seems there are some bugs open for using globalmenu with Xfce, you might find help there at Google Code or at this Ubuntu forum...
[http://ubuntuforums.org/showthread.php?t=241868](http://ubuntuforums.org/showthread.php?t=241868)

BTW, you can install the rest of the Gnome panel applets via the package gnome-applets. HTH

---

### Post by rvchari on 2011-01-24
i did that, some bug is there, xterm and nautilus menu remains on window :(

---

