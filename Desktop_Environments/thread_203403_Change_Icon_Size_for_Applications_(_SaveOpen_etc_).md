---
title: "Change Icon Size for Applications ( Save/Open etc )"
date: 2006-06-25
forum: Desktop Environments
---

### Post by v8YKxgHe on 2006-06-25
Hey, 

Is there anyway to force applications to use smaller icons for things like New/Save/Open/Print. They really do take up room, for example if you look at a typical Windows application the Button/Icons are compact yet still easily useable. Compare this to Linux/Ubuntu and they are huge, they take up a lot of desktop space. 

I'd like it if I could shrink the icons by about...50-60% so that the applications will become smaller. 

Thanks,

---

### Post by ayoli on 2006-06-25
you can add  is line to your ~/.gtkrc-2.0 (create it if not existing) or to the gtkrc of the theme you're using (in /usr/share/theme/yourtheme/gtk-2.0/gtkrc or ~/.themes/yourtheme/gtk-2.0/gtkrc):
```
gtk-icon-sizes = "gtk-large-toolbar=18,18:panel-menu=16,16:gtk-menu=14,14"
```
use the sizes you need instead of 18,16,14 here.
edit: maybe you'll have to switch to another theme, then switch back to your theme to apply to open apps.
regards.

---

### Post by v8YKxgHe on 2006-06-25
Hum, I don't see any difference with any value - even 2.

---

### Post by ayoli on 2006-06-25
i've missed something, if you use .gtkrc in your home name must be .gtkrc-2.0
regards

---

