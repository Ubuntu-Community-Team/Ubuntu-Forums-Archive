---
title: "Reducing icon-size in gnome-menu"
date: 2005-12-09
forum: Desktop Environments
---

### Post by bytter on 2005-12-09
Is there anyway to reduce the icon-size in the gnome-menu and gnome-panel? The thing is that I prefer to use a more reduced font-size than 10pt (because of monitor size), but icons stay much larger than text (not to mention the while item size). Any solutions?

Thx!

---

### Post by blueplazma on 2005-12-09
In the panel, if you right-click and select properties, you can adjust the size of the panel.

---

### Post by bytter on 2005-12-13
[QUOTE=blueplazma]In the panel, if you right-click and select properties, you can adjust the size of the panel.[/QUOTE]

Thx, I know that... I phrased my question wrongly though...
Problem is that the icons are only adjusted in the gnome-panel, not in the menus...

---

### Post by 23meg on 2005-12-13
They're theme dependent, meaning that you'd probably have to use smaller icons in your icon theme.

---

### Post by bb002 on 2005-12-13
You could turn off icon in menus altogether "System -> Preferences -> Menus & toolbars" and uncheck "Show icons in menus". It isn't what you asked for but it is the best I can come up with.

---

### Post by Almighty Ju on 2006-12-20
if you edit the file home/.themes/<your theme in use>/gtk2.0/gtkrc and add the line gtk-icon-sizes = "panel-menu=24,24" at the top it should work. Change 24 to whatever size you want. If it doesnt work maybe its not the theme in use?

Is there anyway to stop the icons in the gnome panel from automatically changing size depending on the panels size? ive tried adding gtk-icon-sizes = panel=24,24" to my themes gtkrc file but it has no effect, anyone have any ideas?

Ju

---

