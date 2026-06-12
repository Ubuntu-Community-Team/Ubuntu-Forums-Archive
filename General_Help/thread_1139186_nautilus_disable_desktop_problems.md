---
title: "nautilus disable desktop problems"
date: 2009-04-26
forum: General Help
---

### Post by AnimalCrosser5 on 2009-04-26
I disabled show desktop in nautilus so I could use compiz-fusion's multi-wallpapers to work, but it disabled my right click menu on the desktop.

(it also removes icons, which I don't want, anyone know how to fix this one, too?)

I re-enabled it, but nothing reverted back to the way it was before. How can I remove the wallpaper "covering" the ones drawn by compiz, but still have the right click menu and icons?

---

### Post by Tim Sharitt on 2009-04-26
Show desktop must be enabled for icons and menus to work. 

Another option may be to disable draw_background in / > desktop > gnome > background with gconf-editor (Hit Alt-F2, enter gconf-editor).

I'm not sure that will work, but it may be worth a shot. :)

---

### Post by AnimalCrosser5 on 2009-04-26
I'll try that, if I can get the menu/icons working again. Thanks.

---

### Post by Tim Sharitt on 2009-04-26
To get the desktop back, you can enable / > apps > nautilus > preferences > show_desktop in gconf-editor. You may need to restart nautilus for it to take effect (or just log out and log back in).

---

### Post by AnimalCrosser5 on 2009-04-26
Thanks, my menu is back, but disabling the draw bg option just gives me a black background, it still overs the compiz BGs.

---

