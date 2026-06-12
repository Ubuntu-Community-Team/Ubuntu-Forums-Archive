---
title: "Volume dialog?"
date: 2008-10-16
forum: Desktop Environments
---

### Post by Sam Lars on 2008-10-16
In Gnome, when I change the brightness or volume through keyboard shortcuts, little boxes pop up to show what the current level is.
In XFCE, the brightness one pops up, but I get nothing for the volume.  How could I get that back?

---

### Post by p_quarles on 2008-10-17
I'm not familiar with Xfce's administration tools, but I believe it does have a hotkey configuration tool. To use such things, you'll need to use xev:
[http://ubuntuforums.org/showpost.php?p=1047785&postcount=2](http://ubuntuforums.org/showpost.php?p=1047785&postcount=2)

Xmodmap is optional in some cases, as many window manager are capable of binding raw keycodes to commands.

---

### Post by Sam Lars on 2008-10-17
Thanks for the info.  The volume buttons already work, they adjust the volume, it's just that no box shows up with them.  Will binding it in this way fix that?

Edit:I can't find
xmodmap /etc/X11/Xmodmap

---

