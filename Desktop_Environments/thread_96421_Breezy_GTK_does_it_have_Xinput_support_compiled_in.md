---
title: "Breezy GTK: does it have Xinput support compiled in?"
date: 2005-11-28
forum: Desktop Environments
---

### Post by jejones3141 on 2005-11-28
[This thread]("http://www.ubuntuforums.org/showthread.php?p=528463&posted=1") gives rise to the question in the title, because in trying to find out why, after following the Linux Wacom project's instructions up to the point of configuring GIMP, GIMP says "No extended input devices". [This thread]("http://gug.sunsite.dk/forum/?threadid=2315") in the GUG forum says that GTK lacking Xinput support is one possible cause of that response from GIMP. So, how can I tell whether GTK for Breezy has Xinput support?

---

### Post by jejones3141 on 2005-12-30
Answer: I can tell by having xorg.conf use the right device, /dev/input/wacom.

---

