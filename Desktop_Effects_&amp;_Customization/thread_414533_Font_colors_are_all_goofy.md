---
title: "Font colors are all goofy"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by Pilot-Doofy on 2007-04-19
I followed this tutorial here:
[http://ubuntuforums.org/showthread.php?p=2024839](http://ubuntuforums.org/showthread.php?p=2024839)

It worked as far as changing the font color for my "taskbar" as Windows calls it. However, now a lot of my text is white. For example, I can't see what I'm typing right now, ti's just white. Here is the code I put in the gedit file:

include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#FFFFFF"
NautilusIconContainer::normal_alpha = 40
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "blackFont"
{
fg[NORMAL] = "#000000"
}

style "whiteFont"
{
fg[NORMAL] = "#FFFFFF"
}

widget "*PanelWidget*" style "whiteFont"
#widget "*PanelApplet*" style "whiteFont"


My question is how do I change only the "taskbar" font color and the clock app font color? I don't want to change anything else!

In addition, I was wondering if you could point me to any good tutorials on making themes for Ubuntu. I'm currently doing a Vista transformation pack because Vista looks good. :)

---

