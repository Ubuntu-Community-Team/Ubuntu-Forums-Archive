---
title: "qtcurve gtk+ evolution icons missing"
date: 2009-11-05
forum: Desktop Environments
---

### Post by cdntx1010 on 2009-11-05
I recently upgraded to Kubuntu 9.10 and found that several evolution icons are missing from the qtcurve widget style for kde.  If I switch to Raleigh all of the icons appear.  Here is my .gtkrc-2.0-kde4

```
# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/QtCurve/gtk-2.0/gtkrc"

style "user-font"
{
        font_name="DejaVu Sans"
}
widget_class "*" style "user-font"

gtk-theme-name="QtCurve"
gtk-font-name="DejaVu Sans 8"
```

Is there anything I can install to fix these icons.  It's not a big deal but it's annoying to look at.

---

