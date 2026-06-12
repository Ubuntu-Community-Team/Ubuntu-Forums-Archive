---
title: "Hoary, Gnome, and Xinerama"
date: 2005-03-12
forum: Desktop Environments
---

### Post by terasurfer on 2005-03-12
Since upgrading to hoary, i've had no luck getting xinerama to work properly in Gnome.  I don't think the problem is with my Xorg configuration, since everything works as expected if I switch over to KDE.

In warty, I had to apply a patch to metacity (as desctibed [here](http://www.ubuntuforums.org/showthread.php?t=15298)), in order to get a more reasonable window placement.  This time, window placement is not working, and neither is window maximize to a single display.  Any ideas on how I can recover this functionality?

---

### Post by Burgundavia on 2005-03-12
Are you running ATI or nvidia?

---

### Post by terasurfer on 2005-03-12
nVidia

---

### Post by terasurfer on 2005-03-12
I was able to get things working properly again, by reverting to metacity 2.8.8 and applying a patch.  See [this thread](http://www.ubuntuforums.org/showthread.php?t=15298) for instructions.

---

