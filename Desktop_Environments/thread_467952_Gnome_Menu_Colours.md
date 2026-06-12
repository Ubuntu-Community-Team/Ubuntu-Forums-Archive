---
title: "Gnome Menu Colours"
date: 2007-06-08
forum: Desktop Environments
---

### Post by Alex Tennant on 2007-06-08
I've been fiddling around with my gtkrc-2.0 today and I've managed to edit everything to my satisfaction except for one thing. I can't seem to find the setting to change the colour of the menu once it is selected. (IE. Behind where it says Applications/Places/System) I assume it is customisable, since I've not had any problems customising anything else on the panel.

If anyone could help me that would be great, the contents of my gtkrc-2.0 file are as follows, in case it's relevant.

```
gtk-menu-popup-delay=0
style "panel"
{
fg[NORMAL] = "#ffffff"
fg[PRELIGHT] = "#ffffff"
fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
bg[PRELIGHT] = "#555555"
bg[ACTIVE] = "#2a2a2a"
bg[SELECTED] = "#EEEEEE"
# bg[INSENSITIVE] = "#FFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = “#DAB566&#8243;
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
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

---

### Post by dizee on 2007-06-08
Not sure about the config files, but if you go to System > Preferences > Theme, then click the customise box and go to Colours, the "selected items" colours are what you're looking for I think.

---

### Post by juniah on 2007-11-04
What if the theme you have is unchangable?

---

