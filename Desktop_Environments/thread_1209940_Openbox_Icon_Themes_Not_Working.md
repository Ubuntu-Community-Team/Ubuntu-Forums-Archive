---
title: "Openbox Icon Themes Not Working"
date: 2009-07-10
forum: Desktop Environments
---

### Post by tyke on 2009-07-10
Hi all.

I'm using openbox by itself, and I'm trying to change the icon theme, but it just seems to be ignoring whatever settings I try to specify.

This is my gtkrc-2.0

```
include "/usr/share/themes/Human/gtk-2.0/gtkrc"
include "/home/tyk3/.gtkrc.mine"
```

and this is my gtkrc.mine

```
style "Sans"
{
font_name = "Sans 10"
}
widget_class "*" style "Sans" 

gtk-font-name = "Sans 10"
gtk-icon-theme-name = "Tangerine"
gtk-toolbar-style = GTK_TOOLBAR_ICONS
```

But I still only get the default Gnome icons. It doesn't seem to matter which icon sets I specify either. I thought it might be problem with the custom icon set I was trying to use, but it seems to ignore the defaults included with Ubunut. Human doesn't work either.

Lxappearance isn't working properly either. All the theme names are listed, but when you click on one the preview doesn't alter from the default gnome theme. Selecting a different theme and clciking "Apply" makes the screen flicker as though a new theme is being applied, but nothing changes.

Anyone have any ideas?

Anyone

---

### Post by tyke on 2009-07-11
bump

---

### Post by ~sHyLoCk~ on 2009-07-11
Try the opposite. Here's my gtkrc-2.0:

```
# Auto-written by gtk2_prefs. Do not edit.

gtk-theme-name = "xfzenbl"
style "user-font"
{
	font_name="Sans 10"
}
widget_class "*" style "user-font"
include "/home/shy/.gtkrc.mine"

```

And gtkrc.mine:
```
gtk-icon-theme-name = "areab"
```

Make sure you put your icon folder in /usr/share/icons
And theme folder in /usr/share/themes

---

