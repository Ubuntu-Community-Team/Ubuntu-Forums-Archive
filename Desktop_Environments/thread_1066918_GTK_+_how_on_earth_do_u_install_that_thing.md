---
title: "GTK + how on earth do u install that thing"
date: 2009-02-11
forum: Desktop Environments
---

### Post by prestigechaser on 2009-02-11
hi,
 i use ubuntu v8.10 for 4 months and i tried all different stuff with it. however one thing that i failed to d0 is fully install gtk + themes, wenever i install one this message comes up in the appearance preference window :

This theme will not look as intended because the required GTK+ theme engine '' is not installed.

I tried installing the gtk+ thing however many times i failed so please can anyone explain me in detail how to do so as the instructions in the package aren't clear enough for me.

---

### Post by kellemes on 2009-02-12
Does this help?
[http://ubuntuforums.org/showthread.php?t=1017246]("http://ubuntuforums.org/showthread.php?t=1017246")

---

### Post by mcduck on 2009-02-12
It's not actually missing anything, so everything works just fine without you doing anything about it.

If the warning really annoys you, you can open that theme's gtkrc file and edit every place where it says 'engine ""' to 'engine"pixmap"'. This will make the warning disappear, but has no effect on how the theme looks like.

(making theme definitions with no engine defined is a common trick when making GTK themes. The current version of Gnome's theme manager however doesn't understand that and complains about missing GTK engine that has no name. Changing those definitions to point to pixmap engine without actually defining any images for the pixmap engine to use has the same effect as using empty engine definition but doesn't confuse Gnome's theme manager.)

---

