---
title: "Change icon theme while in fluxbox"
date: 2007-11-16
forum: Desktop Environments
---

### Post by mike868y on 2007-11-16
I'm using fluxbox, how would i change the icon theme of the icons that appear in thunar?

---

### Post by urukrama on 2007-11-16
If you have gnome installed, you can add "gnome-settings-daemon" to your autostart file; if you have xfce installed, use "xfce-mcs-settings". The gtk apps will then use the theme and icons specified in the theme manager of gnome or xfce. To change it run "gnome-control-centre" or "xfce-setting-show".

Or you can use the .gtkrc-2.0 anf .gtkrc-2.0.mine files in your home directory. Create them if they don't exist. This is what they should look like:

**.gtkrc-2.0**
> # -- THEME AUTO-WRITTEN DO NOT EDIT
include "/path/to/theme/gtkrc"

include "/home/USERNAME/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT

(If you use gtk theme switch or something like it, it will write the path to your theme's gtkrc file here automatically. You'll need to specify the icon theme in the gtkrc-2.0.mine file as the gtkrc-2.0 file is overwritten when you change themes with swithc or the like.

**.gtkrc-2.0.mine**
> style "Sans"
{
font_name = "Sans 10"
}
widget_class "*" style "Sans"
gtk-font-name = "Sans 10"

gtk-icon-theme-name = "*iconthemename*"

Change the font to whatever font you like.

Hope this helps.

---

### Post by TeaSwigger on 2007-11-17
And if you have Kubuntu / KDE, you can change the icons by running:

```
kcmshell icons
```

---

