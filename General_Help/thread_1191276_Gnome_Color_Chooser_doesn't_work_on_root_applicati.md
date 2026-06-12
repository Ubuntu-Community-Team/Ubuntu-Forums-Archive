---
title: "Gnome Color Chooser doesn't work on root applications?"
date: 2009-06-18
forum: General Help
---

### Post by Fzang on 2009-06-18
Gnome Color Chooser is such a nice tool... problem is, it doesn't work for root applications, and this looks pretty stupid.

Is there a way to make Gnome Color Chooser skin root applications as well?

---

### Post by JackTheDipper on 2009-06-19
If you're running globally installed Theme and Engine(s), you can just symlink your gtkrc file:
(sudo) ln -s /home/youruser/.gtkrc-2.0-gnome-color-chooser /root/.gtkrc-2.0

Good Luck!

---

