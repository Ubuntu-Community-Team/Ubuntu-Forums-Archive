---
title: "GTK font settings (text too small) in Kubuntu 14.04 (KDE 4.13)"
date: 2014-06-05
forum: Desktop Environments
---

### Post by Erik1984 on 2014-06-05
After I recently cleared my KDE settings (changing the name of the .kde folder) to get the defaults back it also seem to have changed the appearance of GTK fonts. As shown in the example below they appear much smaller than the 'normal' fonts. Compare in the screenshot the menu items of Kate and Leafpad. The same small GTK fonts also appear on Eclipse and LibreOffice for example. Certainly doesn't look like the Ubuntu font at 12 points. Yet that is what the settings indicate. Am I overlooking some settings? Are there other config files for GTK fonts in KDE?

~/.config/gtk-3.0/settings.ini

```

[Settings]
gtk-font-name=Ubuntu Regular 12
gtk-theme-name=oxygen-gtk
gtk-icon-theme-name=oxygen
gtk-fallback-icon-theme=unity-webapps
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-menu-images=0
gtk-button-images=0

```

The GTK system settings:

[ATTACH=CONFIG]253755[/ATTACH]

Example (Kate vs Leafpad):

[ATTACH=CONFIG]253754[/ATTACH]

---

### Post by Erik1984 on 2014-06-07
Found another config file ~/.gtkrc-2.0

```

 File created by KDE Gtk Config
# Configs for GTK2 programs

include "/usr/share/themes/oxygen-gtk/gtk-2.0/gtkrc"
style "user-font"
{
        font_name="Ubuntu Regular"
}
widget_class "*" style "user-font"
gtk-font-name="Ubuntu Regular 12"
gtk-theme-name="oxygen-gtk"
gtk-icon-theme-name="oxygen"
gtk-fallback-icon-theme="unity-webapps"
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-menu-images=0
gtk-button-images=0

```

Again with a font size of 12.

---

### Post by Erik1984 on 2014-06-09
Regarding GTK 2.0 I noticed that changing the font size does affect the application menu if the theme is set to Raleigh. This is not a solution for me as this theme looks horrible :P So if this is a bug it seems to be related to the oxygen-gtk theme.

---

### Post by Erik1984 on 2014-07-22
Okay... I changed the fonts to Oxygen and after a while (couldn't get used to it) back to the Ubuntu font. Now all fonts look as intended, also in GTK apps... SOLVED but I don't exactly understand why :P

[[IMG]http://i.imgur.com/isG9vJr.png[/IMG]](http://imgur.com/isG9vJr)

---

