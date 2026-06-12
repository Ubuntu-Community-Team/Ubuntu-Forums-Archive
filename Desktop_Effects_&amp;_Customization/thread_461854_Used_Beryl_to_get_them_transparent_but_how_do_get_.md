---
title: "Used Beryl to get them transparent but how do get my menus colored?"
date: 2007-06-02
forum: Desktop Effects &amp; Customization
---

### Post by RudolfMDLT on 2007-06-02
Hi,

I have edited my .gtkrc-2.0 and it looks like this:

> include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
[COLOR="Red"]fg[NORMAL] = " #F026CB"
}
widget "*PanelWidget*" style "#D58A90"
widget "*PanelApplet*" style "#D58A90"[/COLOR]
widget_class "*MenuItem*" style "000000"
widget_class "*ToolItem*" style "000000"
widget_class "*SeparatorMenuitem*" style "000000"
widget_class "*SeparatorToolitem*" style "000000"
widget_class "*ImageMenuitem*" style "000000"
widget_class "*RadioMenuitem*" style "000000"
widget_class "*CheckMenuitem*" style "000000"
widget_class "*TearoffMenuitem*" style "000000"

The settings in red are the ones that I changed -  but they are not working and I have restarted X.... any ideas will be much appreciated!

Thanks,
Rudolf

---

### Post by RudolfMDLT on 2007-06-02
bump

---

