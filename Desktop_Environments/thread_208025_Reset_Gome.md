---
title: "Reset Gome"
date: 2006-07-02
forum: Desktop Environments
---

### Post by acorn22 on 2006-07-02
Is there a way to reset Gnome? I messed with the taskbars and what not and I just want it back to the way it was. Is there an option someplace for this?

---

### Post by aysiu on 2006-07-02
Yes. Paste these commands in the terminal: ```
mv ~/.gnome ~/.gnome.old
mv ~/.gnome2 ~/.gnome2.old
mv ~/.gconf ~/.gconf.old
mv ~/.gconfd ~/.gconfd.old
mv ~/.metacity ~/.metacity.old
mv ~/.nautilus ~/.nautilus.old
``` You may have to log out and log back in again for the changes to take effect.

---

### Post by acorn22 on 2006-07-02
Thanks

---

