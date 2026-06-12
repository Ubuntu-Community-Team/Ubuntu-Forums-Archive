---
title: "KDE has taken over my gnome desktop"
date: 2005-11-26
forum: Desktop Environments
---

### Post by robstoffers on 2005-11-26
Hi,

I installed the kubuntu-desktop package so my wife can use KDE rather then Gnome, however it seems to have taken over my fonts and caused Gnome to use gtk1 style widgets for everything instead of the normal gtk2 widgets. I'm guessing there is a config file somewhere where the type of widgets to use is set, so my question is "how can I get everything looking normal on my Gnome desktop?".

I've tried qt-config without much luck either..


Thanks,

---

### Post by dodongo on 2005-11-27
[ttp://ubuntuforums.org/showthread.php?t=58787]("http://ubuntuforums.org/showthread.php?t=58787")

This may be a thread that helps you?  That awful goofy "gkt-qt" theme engine, or whatever it's called (the one that makes your GNOME themes look like KDE/QT themes) was the culprit in my situation.

As to why your widgets look funky, I can't say, but I did spend an afternoon hunting the bastard that screwed up my fonts in GNOME.  Check that thread and see if my results lead you in anything resembling the proper direction.

---

### Post by manicka on 2005-11-27
Yes, the gtk-qt engine will be the culpritt. Remove it and it's config file as well in your home directory. Can't remeber what it's called off the top of my head but it was fairly easy to find.

---

### Post by robstoffers on 2005-11-28
[QUOTE=manicka]Yes, the gtk-qt engine will be the culpritt. Remove it and it's config file as well in your home directory. Can't remeber what it's called off the top of my head but it was fairly easy to find.[/QUOTE]

Yep, that and removing both its config file and the .gtkrc-2.0 from my home directory solved the widgets and font problems (and de-kdeified my desktop). However, now I don't have a "desktop", ie no icons on the desktop and nor can I make any. I also can't right click on the desktop and get a menu. I tried running nautilus maunally but its not creating the desktop either, any suggestions?

Cheers,

---

