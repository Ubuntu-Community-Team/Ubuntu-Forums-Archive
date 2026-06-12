---
title: "Eclipse messing up in KDE"
date: 2008-04-26
forum: Desktop Environments
---

### Post by unbuntued on 2008-04-26
I switched to the KDE environment, but still using numerous GTK applications.

I'm not able to run Eclipse IDE with gtk-qt-engine installed.
Removing gtk-qt-engine though makes the GTK applications (firefox, pidgin, etc.) interface look like crap.

Is there a way to set ONLY Eclipse IDE not to use qtk-qt-engine or yet better some workaround to get it working correctly?

---

### Post by marmida on 2008-09-30
This thread is stale, but I thought I'd bump it for the sake of documentation for other people that find it when searching.

I had this problem and then came across this thread: [http://ubuntuforums.org/archive/index.php/t-544032.html](http://ubuntuforums.org/archive/index.php/t-544032.html)

In my case in particular, the problem was triggered by the bundling of 32-bit Eclipse in the all-in-one PDT package I was running, which could not load the 64-bit gtk-qt-engine.

Switching to 64-bit Eclipse allowed it to launch, from which point I just had to deal with the Update Manager to find everything I needed.

---

