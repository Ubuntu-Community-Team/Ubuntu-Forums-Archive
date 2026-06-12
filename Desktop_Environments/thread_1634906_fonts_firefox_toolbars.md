---
title: "fonts /firefox toolbars"
date: 2010-12-01
forum: Desktop Environments
---

### Post by debili on 2010-12-01
the new ubuntu font family is great! however the way it's being displayed seems to differ between applications, or, at least firefox (see screenshot pls)
the top window is firefox, the bottom is nautilus, why the font is much "smoother" in nautilus?

---

### Post by gogolink on 2010-12-01
Do you have subpixel smoothing enabled under System > Preferences > Appearance > Fonts?

---

### Post by debili on 2010-12-02
yes i do actually

---

### Post by mcduck on 2010-12-02
> **debili said:**
> the new ubuntu font family is great! however the way it's being displayed seems to differ between applications, or, at least firefox (see screenshot pls)
the top window is firefox, the bottom is nautilus, why the font is much "smoother" in nautilus?

Firefox doesn't actually use GTK (the toolkit used to create the GUI for most of Gnome desktop's applications), so while it does fairly good job at picking up the theme you are using it's not perfect and implements some stuff in completely wrong way.

Also, if you are using any Firefox theme that could look ugly as well. Based on how they work I'd say they are mostly targeted for Windows users, at least they always look ugly and half-made on both my Linux and OSX machines.

---

