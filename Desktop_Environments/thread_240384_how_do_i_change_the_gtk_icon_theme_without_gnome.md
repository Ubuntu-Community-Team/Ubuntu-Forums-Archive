---
title: "how do i change the gtk icon theme without gnome?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by lapsey on 2006-08-20
I am using a really simple lightweight IceWM installation, and, while installing **gtk-theme-switch** allows me to change the gtk widget appearance for things that use gtk (such as swing, python and mousepad)... I can't change the icon theme at all, and am stuck with the default hicolor gnome theme in those gtk apps.

After installing **tangerine-icon-theme** , i created and edited ~/.gtkrc.mine with the line 
```
gtk-icon-theme-name = "Tangerine"
```
(as per instructions i have read elsewhere), but nothing happened. Is this right, or are there other ways to do it?

I've been searching for far too long for a config tool and it's driving me potty ](*,)

---

### Post by croak77 on 2006-08-20
Try creating a ~/.gtkrc-2.0 with the same line.

---

### Post by ardchoille on 2006-08-20
I used this in other window managers:

Create ~/.gtkrc-2.0, if it doesn't exist, and add the following text to it:

```

include "/usr/share/themes/Bluecurve/gtk/gtkrc"

include "/home/USERNAME/.gtkrc.mine"

style "user-font"
{
        font_name="Sans Serif 12"
}
widget_class "*" style "user-font"

gtk-icon-theme-name = "Bluecurve"
gtk-theme-name = "Bluecurve"
gtk-font-name = "Sans Serif 12"

```

This will tell other window managers to use your GTK2 theme settings.

This information is geared toward using the Bluecurve theme, but this information can be helpful for other themes as well.

---

