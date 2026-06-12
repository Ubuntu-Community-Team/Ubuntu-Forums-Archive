---
title: "Change the font"
date: 2007-01-26
forum: Desktop Environments
---

### Post by thomashenrydavies on 2007-01-26
Hi all

I've tried a few things, but I cannot seem to change the main font used by the unbuntu desktop. I've tried changing all the fonts in the Preferences, but the main font (used by apps for menus etc) never seems affected by what I do here. The deafult font is bloody massive, and I'd like much smaller fonts, so that I can get as much use per inch of desktop as I do in Windows XP.

Thanks
Tom

---

### Post by ynnhoj on 2007-01-26
off hand i can't recall how to change that through any of the settings applications, though you can manually edit either your ~/gtkrc-2.0 or ~/.gtkrc-2.0.mine file; here are mine:
.gtkrc-2.0:```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/usr/share/themes/Clearlooks/gtk-2.0/gtkrc"

include "/home/john/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

.gtkrc-2.0.mine```
style "user-font"
{
font_name = "dejavu sans 9"
}
widget_class "*" style "user-font"
gtk-font-name = "dejavu sans 9"
gtk-icon-theme-name = "yasis"
```

so, when i changed my gtk theme using gtk-theme-switch ('cause i'm using openbox, not gnome) ~/.gtkrc-2.0 was automatically generated, and then i created ~/.gtkrc-2.0.mine and set the fonts to dejavu sans 9 (you can ignore the last line about the icon theme name..).

and if for some reason, neither of those files exist in your home directory, you could just create .gtkrc-2.0 and copy the lines to set the font into it (though i'm sure you'll have that file).

---

