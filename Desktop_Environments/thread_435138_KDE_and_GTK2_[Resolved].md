---
title: "KDE and GTK2 [Resolved]"
date: 2007-05-06
forum: Desktop Environments
---

### Post by MadMonkey234 on 2007-05-06
Hi,

Until now, GTK2 (mainly Firefox 2) used KDE colors. However, I wanted video playback in my Kubuntu setup, so I decided to install from MPlayer by compiling it from the sources. To do that, I had to install some dev packages, including libgtk2.0-dev. After I installed this package, the colors in Firefox became wrong... Now, the background color of all Firefox windows is not the good one. How can I fix this?

Thanks!

P.S.: MPlayer works fine though :)

---

### Post by aysiu on 2007-05-06
That's weird. Firefox isn't actually a GTK application, but maybe [this](http://ubuntuforums.org/showpost.php?p=2537051&postcount=209) might help.

It's written for IceWM, but it should apply to any situation where you don't have Gnome installed.

---

### Post by MadMonkey234 on 2007-05-06
Alright I got it. At first I tried reinstalling the gtk2-engines-qt package in adept but it didn't help. Then I downloaded the .package file on the qt engine website and it fixed it!

Thanks for your help

---

