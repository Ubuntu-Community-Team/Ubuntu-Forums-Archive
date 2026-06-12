---
title: "How To: Change the panel's font color"
date: 2006-10-09
forum: Desktop Environments
---

### Post by eszajdecki on 2006-10-09
I would like to know how to change the color of the font on a panel. I want to make the panel color dark and the font a different color then black. How do I do this?

---

### Post by tuxrtfm on 2006-10-21
Open up terminal, in your home folder type "gedit .gtkrc-2.0" and add the following code.
Change the hex color code to what you want
(right click on your desktop and select change desktop background, then select pick a color if you need a simple way to get hex code for colors)

Hemm, The Panel code doesnt seem to be working, hopefully someone can help. :redface: 
However the Desktop and Nautilus code works great #-o
For the Panel 
```
style "desktop-icon"
{
NautilusIconContainer::normal_alpha = 0
text[NORMAL] = "#000000"
NautilusIconContainer::frame_text = 1
}
class "GtkWidget" style "desktop-icon"

style "panel"
{
fg[NORMAL]               = "#ffffff"
fg[PRELIGHT]            = "#000000"
fg[ACTIVE]               = "#ffffff"
fg[SELECTED]            = "#000000"
fg[INSENSITIVE]            = "#8A857C"

bg[NORMAL]               = "#000000"
bg[PRELIGHT]            = "#dfdfdf"
bg[ACTIVE]               = "#D0D0D0"
bg[SELECTED]            = "#D8BB75"
bg[INSENSITIVE]            = "#EFEFEF"

base[NORMAL]            = "#ffffff"
base[PRELIGHT]            = "#EFEFEF"
base[ACTIVE]            = "#D0D0D0"
base[SELECTED]            = "#DAB566"
base[INSENSITIVE]         = "#E8E8E8"

text[NORMAL]            = "#161616"
text[PRELIGHT]            = "#000000"
text[ACTIVE]               = "#000000"
text[SELECTED]            = "#ffffff"
text[INSENSITIVE]            = "#8A857C"
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

For the Desktop and Nautilus
```
style "desktop-icon"
{
NautilusIconContainer::normal_alpha = 0
text[NORMAL] = "#000000"
NautilusIconContainer::frame_text = 1
}
class "GtkWidget" style "desktop-icon"
```

Good Luck
TuxRTFM

---

