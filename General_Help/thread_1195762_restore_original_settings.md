---
title: "restore original settings"
date: 2009-06-24
forum: General Help
---

### Post by abelito8 on 2009-06-24
I am running a kubuntu 9.04 and have installed all the three desktop environments (KDE, Gnome, Xfce). My favourite turned out to be xfce but I did something last time I used it and now it does not show the horizontal bar anymore (with the clock and all the widgets)...it disappeared after last login

I think the easiest thing is to restore the original settings (and I do not know how to do it), but any other suggestion is welcome

thank you

---

### Post by wojox on 2009-06-24
Try deleting the directory called ~/.config/xfce4/panel which will then force xfce4-panel to draw up a fresh one.

---

### Post by yeats on 2009-06-24
If I'm not mistaken,  all of those sorts of settings would be stored in a hidden directory within your home folder (perhaps .xfce (?)).  Gnome and KDE settings are stored this way I know.  Perhaps renaming that folder to something like .xfce.backup, then logging out and back into xfce would do the trick.

EDIT: wojox and I posted at the same time - follow his suggestion :-)

---

