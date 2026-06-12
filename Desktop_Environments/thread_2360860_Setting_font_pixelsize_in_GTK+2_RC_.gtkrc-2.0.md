---
title: "Setting font pixelsize in GTK+/2 RC .gtkrc-2.0"
date: 2017-05-09
forum: Desktop Environments
---

### Post by os2 on 2017-05-09
Does anyone know the option to set the font pixelsize (as opposed to size) for GTK apps?

.gtkrc-2.0 does this by default:

```

gtk-font-name="Sans 10"

```

But the value 10 defaults to font size.

---

### Post by os2 on 2017-05-09
The answer is it doesn't exist. No option:

[https://developer.gnome.org/gtk3/stable/GtkSettings.html#GtkSettings--gtk-font-name](https://developer.gnome.org/gtk3/stable/GtkSettings.html#GtkSettings--gtk-font-name)

GTK makes things more difficult than they already are.

---

