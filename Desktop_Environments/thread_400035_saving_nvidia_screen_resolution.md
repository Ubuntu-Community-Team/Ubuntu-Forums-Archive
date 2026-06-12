---
title: "saving nvidia screen resolution"
date: 2007-04-03
forum: Desktop Environments
---

### Post by howlingmadhowie on 2007-04-03
the resolution i was setting in nvidia-settings was being applied for the gdm login screen but not for gnome.

the solution was to go to:

$HOME/.gconf/desktop/gnome/screen/default/0

and edit %gconf.xml to include the desired resolution.

maybe this problem is x86-64 specific, i dunno.

---

### Post by swegner on 2007-12-09
I've also been having this problem.  I'm hesitant to simply change the setting in %gconf.xml.  Does anybody know where this is set, whether through some GUI config, or automatically somewhere?

I am also using x86-64, with the restricted nvidia-glx-new driver on gutsy.

---

