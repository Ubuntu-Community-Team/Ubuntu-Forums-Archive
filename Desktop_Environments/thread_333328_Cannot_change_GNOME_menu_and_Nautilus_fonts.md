---
title: "Cannot change GNOME menu and Nautilus fonts"
date: 2007-01-07
forum: Desktop Environments
---

### Post by digTro on 2007-01-07
How do I change the fonts for GNOME menus and the fonts used in the File Browser? I tried changing the fonts in System->Preferences->Font , but it is not working. The font changes are working for other applications (like Firefox menus).

---

### Post by ecoxmit on 2007-01-08
i am having exactly the same problem.. anyone has any ideas?

---

### Post by digTro on 2007-01-13
The issue is fixed. The problem was, earlier I had installed kde-desktop and changed some font settings there. It created a file .gtkrc-2.0 in my home folder with the following contents:
```
# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

style "user-font"
{
        font_name="DejaVu Sans 9"
}
widget_class "*" style "user-font"

gtk-theme-name="Qt"
gtk-font-name="DejaVu Sans 9"

```

I think that's why GNOME fonts were always fixed. Anyway, now I deleted the file and my font problem is gone.

---

