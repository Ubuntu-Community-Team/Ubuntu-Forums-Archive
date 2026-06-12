---
title: "Font problem in GNOME after KDE installation"
date: 2006-09-10
forum: Desktop Environments
---

### Post by abelthorne on 2006-09-10
Yesterday, I installed KDE in order to test it (via the *kubuntu-desktop* package). When returning in GNOME, I had problems with the fonts settings : whatever font I select in the preferences, they stay the same in GTK applications, the GNOME menubars and Nautilus.

I tried to uninstall KDE completely but it didn't change anything. I also tried to reconfigure the fonts settings with **sudo apt-get install --reinstall fontconfig** and **sudo dpkg-reconfigure fontconfig** still with no change.

Any idea ?

---

### Post by abhiomkar on 2006-09-10
Me too have same problem, the font doesn't change at all. Yesterday i did install kubuntu-desktop (using sudo apt-get install kubuntu-desktop). When i login to GNOME , i had the problem with font settings, whatever i select it remains **Sans**. The Application Font Doesn't Change.

Any Suggestions ?

---

### Post by abelthorne on 2006-09-10
This may be related to [this thread](http://ubuntuforums.org/showthread.php?t=229549) and [that bug](https://launchpad.net/distros/ubuntu/+source/gtk-qt-engine/+bug/36256). It seems that KDE (or Kubuntu) breaks something in GNOME that isn't easy to repair.

EDIT : just fixed the problem by removing the *~/.gtkrc-2.0* file and also another one written by KDE (name like *~/.gtkqt_rc*).

---

