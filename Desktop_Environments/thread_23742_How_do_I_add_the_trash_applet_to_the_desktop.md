---
title: "How do I add the trash applet to the desktop?"
date: 2005-04-03
forum: Desktop Environments
---

### Post by digby on 2005-04-03
How do I add the trash applet to the desktop?  I have it on my kicker, but I don't really like that, and it won't let me do the intuitive thing and simply drag it.

---

### Post by Buffalo Soldier on 2005-04-03
Applications -> System Tools -> Configuration Editor.

/apps/nautilus/desktop/trash_icon_visible (check mark)

---

### Post by digby on 2005-04-04
I guess I should have specified... this is for KDE.

---

### Post by Buffalo Soldier on 2005-04-04
And I guess I should have read which section you've posted under :) my bad, sorry.

---

### Post by Klin'Targ on 2005-04-05
The trash item is on the desktop by default, but its hidden. To show it, go to ~/Desktop in a terminal and edit the trash.desktop file. Change "Hidden=true" to "Hidden=false" and restart kde. There really should be an easier/friendlier way to do this.

---

### Post by digby on 2005-04-05
Ah!  No wonder I didn't find it looking through the control center.  Thanks!

---

### Post by ykpaiha on 2005-04-05
My way :most probably not the best but it worked (as i could find any hided trash desktop::)
go to /usr/share/apps/systemview
and ther you ''ll find the icons you need, just copy them on your desktop
Easy and staright forward. :-({|=

---

