---
title: "clock font color"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by d_xtremw on 2007-06-25
HELP.. ive changed the colors of all my fonts and they're okay. all except for my clock font. its black on a black background. all the text on the panel is white but the clock font is black. does anyone know how to change just the clock font color?

---

### Post by ivesjd on 2007-06-25
I'd be interested to know how as well. Mine is default now though. Have never tried to change it. I'll go try now.

---

### Post by d_xtremw on 2007-06-25
aight thanx let me know if u get anythin

---

### Post by andrewsomething on 2007-06-28
I was just trying to find out the same thing. Apparently there is no way to do this through the GUI. The folks at Gnome know that is a problem and are working on ideas to change that. But you can change the font colors by creating a configuration file in you home directory.

```
gedit .gtkrc-2.0 
```

Paste and save.
.
```

style "panel"
{
  fg[NORMAL]               = "#ffffff"
#  fg[PRELIGHT]            = "#000000"
#  fg[ACTIVE]               = "#ffffff"
#  fg[SELECTED]            = "#000000"
#  fg[INSENSITIVE]            = "#8A857C"

#  bg[NORMAL]               = "#000000"
#  bg[PRELIGHT]            = "#dfdfdf"
#  bg[ACTIVE]               = "#D0D0D0"
#  bg[SELECTED]            = "#D8BB75"
#  bg[INSENSITIVE]            = "#EFEFEF"

# base[NORMAL]            = "#ffffff"
#  base[PRELIGHT]            = "#EFEFEF"
#  base[ACTIVE]            = "#D0D0D0"
#  base[SELECTED]            = "#DAB566"
#  base[INSENSITIVE]         = "#E8E8E8"

#  text[NORMAL]            = "#161616"
#  text[PRELIGHT]            = "#000000"
#  text[ACTIVE]               = "#000000"
#  text[SELECTED]            = "#ffffff"
#  text[INSENSITIVE]            = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel" 
```

Restart the Gnome Panel with:  killall gnome-panel 

To go back to black text, comment out "  fg[NORMAL]   = "#ffffff""

I'm not sure what each field will do. I haven't played around with it much. I found this searching the Gnome forums. If you want there seems to be a lot of customization ability there....

---

### Post by ELY_M on 2007-10-14
how can you change only that clock panel to different background and font?

---

