---
title: "gnome-panel transparency"
date: 2009-08-01
forum: Desktop Environments
---

### Post by DrFugly on 2009-08-01
Hello everyone! Trying to get some help here,

  I've updated my shiki-brave theme but my gnome-panel transparency got all screwed up. Before the entire top bar was completely transparent, but now it's only transparent where this 'nothing'. See the screenshot for a better idea. There should be no black what-so-ever on the gnome-panel.

Thank you,
  --Sandro

---

### Post by 67GTA on 2009-08-02
The Shiki themes have a default panel image included that will try to override your panel settings. You have to edit /usr/share/themes/Shiki-Brave/gtk-2.0/gtkrc and comment out (#) the lines pertaining to the panel. Then reselect the theme again to reset it.

---

### Post by vinutux on 2009-08-02
Select another theme/setback to default themes fix your prob

---

### Post by DrFugly on 2009-08-03
> **67GTA said:**
> The Shiki themes have a default panel image included that will try to override your panel settings. You have to edit /usr/share/themes/Shiki-Brave/gtk-2.0/gtkrc and comment out (#) the lines pertaining to the panel. Then reselect the theme again to reset it.
Thanks man, you were right.

In the gtkrc file it says to go into the panel.rc file to edit the panel properties. Then sure enough in panel.rc all I had to do was comment out the following line:
bg_pixmap[NORMAL]       = "/Panels/panel-bg-dark.png" # Disable for normal panel backgrounds.

(For all others who may want to do this)

Thank you!

---

