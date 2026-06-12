---
title: "icon size craziness"
date: 2009-05-22
forum: Desktop Environments
---

### Post by chamb244 on 2009-05-22
I'm having a problem in Xubuntu 8.10 where for some icon themes (example: high contrast inverse) there is a weird relative sizing thing going on. Example in screenshot (where the high contrast icons are 4 times larger than the other icons).  This is especially annoying in context menus, which get all distorted to accommodate the huge icons.  I've tried adjusting all the icon theme settings but doesn't seem to affect this behavior.  Any suggestions?

---

### Post by ckonestroh on 2009-05-22
I'm taking it your a newbie....  Ok first off I use the same theme ,but your using the larger version.... There is a normal sized version of high contrast inverse and a larger version.... Your going to have to right click your desktop select change background > select tab themes and select smaller version.....

Tip Press super + N gives you contrast in colors mainly Websites instead of all the background pages being white they will black back ground...

Only reason I use High Contrast is I have bad I sight when reading text in white light for long times....


Good Luck....

You can also add more GTK themes in Gnome-look.org....


later

---

### Post by ckonestroh on 2009-05-22
Quick tip on downloading new GTK themes

[http://video.google.com/videosearch?q=gtk&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&sa=N&hl=en&tab=wv#q=gtk+themes&hl=en&emb=0&client=firefox-a]("http://video.google.com/videosearch?q=gtk&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&sa=N&hl=en&tab=wv#q=gtk+themes&hl=en&emb=0&client=firefox-a")

---

### Post by etnlIcarus on 2009-05-22
There's 2 reasons why icon sizes may be screwy:

- Not all gtk+ size hints are honoured (not a lot you can do here except try to match the honoured icons to the non-honoured ones eg:

[[IMG]http://img411.imageshack.us/img411/6290/screenshot1u.th.png[/IMG]](http://img411.imageshack.us/my.php?image=screenshot1u.png)

- Some icon themes are incomplete and, "inherit", their missing icons from another theme (usually the Gnome, Tango and Hicolor themes). Most of these fallback icons are fixed-size, while many of the icon themes you get off, lets say, gnome/xfce-look.org, will allow scaling.

You can either try to match the scaling icons to the fixed ones or you can copy the Gnome and Tango themes from /usr/share/icons/ to $HOME/.icons/, open up their index.theme files in your text editor and change all the, "Type=fixedsize", values as follows:

[[IMG]http://img29.imageshack.us/img29/7226/screenshot2p.th.png[/IMG]](http://img29.imageshack.us/my.php?image=screenshot2p.png)

---

### Post by Bohemenian on 2009-06-18
Thanks etnlIcarus! Really useful post, I'm one step closer to a stylized dekstop

---

