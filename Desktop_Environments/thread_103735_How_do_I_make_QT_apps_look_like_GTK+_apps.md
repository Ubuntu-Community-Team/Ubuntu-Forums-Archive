---
title: "How do I make QT apps look like GTK+ apps?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by The Warlock on 2005-12-14
Is there a way to make a QT app (in my case, amaroK) fit in with my GTK+ gnome desktop? I know that the other way (GTK apps looking like QT) can be done, but how about this?

---

### Post by shevek on 2005-12-14
You can try with qt3-qtconfig package. After installing it, you must run in the terminal qtconfig and select the same font that Gnome apps are using (by default is sans, but you can check it in System->Preferences->Typography or something similar (in spanish is tipografía))

---

### Post by The Warlock on 2005-12-14
[QUOTE=shevek]You can try with qt3-qtconfig package. After installing it, you must run in the terminal qtconfig and select the same font that Gnome apps are using (by default is sans, but you can check it in System->Preferences->Typography or something similar (in spanish is tipografía))[/QUOTE]
That works great for font, but how about color, widgets, icons, etc?

---

### Post by miscz on 2005-12-14
The easiest way would be installing kdebase, it comes with kcontrol utility which is KDE's control center. You can set up every part of look and feel there - style, colors, icons, fonts, etc. For something that fits Clearlooks-based theme (like Human) look for Klearlooks or QtCurve on kde-look.org. They may need some tweaking like matching colours and some details but it's a lot easier in KDE than Gnome, you don't have to edit theme because KDE keeps styles and colours separated. For icons try Gnome-mix (also can be found on kde-look.org), the only problem with this icon theme is that it includes some Gorilla icons which don't look really good.

---

### Post by 23meg on 2005-12-14
By doing a forum search..

[http://www.ubuntuforums.org/showthread.php?t=56630](http://www.ubuntuforums.org/showthread.php?t=56630)

---

### Post by endersshadow on 2005-12-14
Luckily for you, someone wrote a HowTo just for this, and it works very well:

[http://doc.gwos.org/index.php/Gnomeish_QT_apps](http://doc.gwos.org/index.php/Gnomeish_QT_apps)

---

### Post by miscz on 2005-12-15
I don't know how somebody can consider Polymer theme gnomeish. Unlike Clearlooks it looks shiny, artificial and toy-like. No color tweaks will make it fit into Gnome. It may look good on Skype screenshot but the scrollbars are just ugly.

[edit]
Klearlooks + Gnome-mix
[[IMG]http://img255.imageshack.us/img255/5921/zrzutekranu5uo.th.jpg[/IMG]](http://img255.imageshack.us/my.php?image=zrzutekranu5uo.jpg)

---

### Post by 23meg on 2005-12-15
It's as gnomeish as they get.

clearlooks gperfection2 + blended doublesmallround + polymer + gnome-mix

[[IMG]http://img365.imageshack.us/img365/4320/amarokpolymer7ib.png[/IMG]](http://imageshack.us)

---

### Post by freddoo on 2006-02-04
hello; gtk3-config is installed, but not new entry appear in my preferences, why?

---

