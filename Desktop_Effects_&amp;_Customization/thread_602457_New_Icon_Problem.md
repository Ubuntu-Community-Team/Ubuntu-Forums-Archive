---
title: "New Icon Problem"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by rollerdiscoman on 2007-11-04
Hello,
I'm not really new to Ubuntu, but some things I tend to have trouble on: I would like to install a new set of icons, but (from previous experience) whenever you install and activate a new icon theme, you disable some of the icons (for instance, the application and menu icons). 
Is there any way I can perhaps use some icons from Human, and some from my new theme?

If you need me to be a bit clearer, I can try.
-Thanks!

---

### Post by ayoli on 2007-11-04
> **rollerdiscoman said:**
> Hello,
I'm not really new to Ubuntu, but some things I tend to have trouble on: I would like to install a new set of icons, but (from previous experience) whenever you install and activate a new icon theme, you disable some of the icons (for instance, the application and menu icons). 
Is there any way I can perhaps use some icons from Human, and some from my new theme?

If you need me to be a bit clearer, I can try.
-Thanks!

You may try to add this line in [Icon Theme] section of the index.theme file of your icon theme:

```
Inherits=Human, Tango, gnome
```

---

