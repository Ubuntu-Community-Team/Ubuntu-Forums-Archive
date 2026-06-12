---
title: "Gnome color chooser not work!"
date: 2010-03-08
forum: Desktop Environments
---

### Post by miksuli on 2010-03-08
I want switch my gnome panel font color but when I use Gnome color chooser and klick apply nothing happen? I also try edit gtk2.0 and add there these lines:
style "modpanel"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "modpanel"
widget "*PanelApplet*" style "modpanel"
widget "*fast-user-switch-applet*" style "modpanel"
and reloaded panel but nothing happened. :o
Sorro for poor english!

---

### Post by inobe on 2010-03-08
welcome to ubuntu forums.

you can change font colors by right clicking desktop and hitting settings, click them tab, at bottom hit properties and hit fonts, there are several fonts you can change color to, menu, window etc..

---

### Post by miksuli on 2010-03-10
Can´t find. Do you mean "Change desktop wallpaper"?

---

### Post by mcduck on 2010-03-10
> **miksuli said:**
> I want switch my gnome panel font color but when I use Gnome color chooser and klick apply nothing happen? I also try edit gtk2.0 and add there these lines:
style "modpanel"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "modpanel"
widget "*PanelApplet*" style "modpanel"
widget "*fast-user-switch-applet*" style "modpanel"
and reloaded panel but nothing happened. :o
Sorro for poor english!

The codes look OK, but what's the exact file where you are adding them? Into a theme's rc file or into the config file in your home directory? In the later case the file is actually called **.gtkrc-2.0**, and you need to log out and back again before any changes in that file take effect.

I don't know about gnome-color-chooser, though, never used it myself... ;)

---

### Post by stinkeye on 2010-03-10
Don't know what's going wrong but for your info gnome-color-chooser 
writes a line to your ***~/.gtkrc-2.0*** file
```
include ".gtkrc-2.0-gnome-color-chooser"
```

Which then reads the   ***~/.gtkrc-2.0-gnome-color-chooser*** file.

If I only  change the panel foreground color with gnome-color-chooser my ***~/.gtkrc-2.0-gnome-color-chooser*** file looks like this: 
```
pixmap_path "/home/glen/.gnome-color-chooser/images/"

style "gnome-color-chooser-panel"
{
  fg[NORMAL] = "#B9CDD5"
}
class "PanelTopLevel.*" style "gnome-color-chooser-panel"
widget_class "*PanelApplet*" style "gnome-color-chooser-panel"
widget_class "*PanelWidget*" style "gnome-color-chooser-panel"
widget "*fast-user-switch-applet*" style "gnome-color-chooser-panel"
```

---

### Post by miksuli on 2010-03-10
I checked those files and everything is alright. ; /

---

### Post by miksuli on 2010-03-12
Gtkc-2.0 file:

include “/home/autocrosser/.gnome2/panel-fontrc”style “desktop-icon”
{
NautilusIconContainer::frame_text = 1
text[NORMAL] = “#000000&#8243;
NautilusIconContainer::normal_alpha = 70
}
class “GtkWidget” style “desktop-icon”

#NautilusIconContainer::dark_info_color=”#888888&#8243;
#NautilusIconContainer::light_info_color=”#bbbbbb”
#NautilusIconContainer::highlight_alpha=200

style “my_color”
{
fg[NORMAL] = “#ffffff“
}
widget “*PanelWidget*” style “my_color”
widget “*PanelApplet*” style “my_color”
widget_class “*MenuItem*” style “my_color”
widget_class “*ToolItem*” style “my_color”
widget_class “*SeparatorMenuitem*” style “my_color”
widget_class “*SeparatorToolitem*” style “my_color”
widget_class “*ImageMenuitem*” style “my_color”
widget_class “*RadioMenuitem*” style “my_color”
widget_class “*CheckMenuitem*” style “my_color”
widget_class “*TearoffMenuitem*” style “my_color”
include ".gtkrc-2.0-gnome-color-chooser"

gtkrc-2.0-gnome-color-chooser file:

pixmap_path "/home/miksu/.gnome-color-chooser/images/"

style "gnome-color-chooser-panel"
{
  bg[NORMAL] = "#FFFFFF"
  bg[PRELIGHT] = "#FFFFFF"
  fg[NORMAL] = "#FFFFFF"
  fg[PRELIGHT] = "#FFFFFF"
  font_name = "Lastwaerk regular, 10"
}
class "PanelTopLevel.*" style "gnome-color-chooser-panel"
widget_class "*PanelApplet*" style "gnome-color-chooser-panel"
widget_class "*PanelWidget*" style "gnome-color-chooser-panel"
widget "*fast-user-switch-applet*" style "gnome-color-chooser-panel"

Any help?

---

### Post by stinkeye on 2010-03-12
I would make a backup of my ~/.gtkrc-2.0
and then delete the original.
Then try gnome-color-chooser again,to change the color of the panel.
The change should be instant.
If that doesn't work try changing the panel color when using a different theme.

---

### Post by miksuli on 2010-03-12
Thanks thats work! I make copy of my gtkrc2.0 file and deleted original and then used gnome-color again.

---

### Post by stinkeye on 2010-03-12
Yes ,I thought It might.You had a lot of stuff in there.
Mine contains only one line.
```
include ".gtkrc-2.0-gnome-color-chooser"
```

---

