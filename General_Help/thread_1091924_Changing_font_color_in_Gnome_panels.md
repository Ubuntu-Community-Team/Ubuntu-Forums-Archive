---
title: "Changing font color in Gnome panels"
date: 2009-03-09
forum: General Help
---

### Post by Tribulation on 2009-03-09
My panels are transparent so I can barely read anything on my panels when I use dark backgrounds (which is quite often). So I created a .gtkrc-2.0 file in my home directory and pasted in

```
style "panel-clock"
{
  fg[NORMAL] = "#FFFFFF"
}
widget "*.clock-applet-button.*" style "panel-clock"
```

to change my clock font to white. I decided that I could like to read everything else in the panel, so after some more searching I found this code to paste in that file

```
include "panel-fontrc"style "desktop-icon"

{
    NautilusIconContainer::frame_text = 0
    text[NORMAL] = "#000000"
    NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
    fg[NORMAL] = "#ffffff"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "my_color"
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"
```

However, that unfortunately changed all my font white, even in my sub menus and in Firefox, so I removed that and for now, I just have the first part for my clock in. What I ask is, what would I put in to change the font color of my panels, but nothing else?

---

### Post by rbmorse on 2009-03-09
This is not original to me, but I can't remember where I stole it:

Open the terminal and type:

gedit .gtkrc-2.0

Insert the following into this file

--------- cut here --------

style "panel" 
{ 
# fg[NORMAL] = "#ffffff" 
# fg[PRELIGHT] = "#000000" 
# fg[ACTIVE] = "#ffffff" 
# fg[SELECTED] = "#000000" 
# fg[INSENSITIVE] = "#8A857C" 
# bg[NORMAL] = "#000000" 
# bg[PRELIGHT] = "#dfdfdf" 
# bg[ACTIVE] = "#D0D0D0" 
# bg[SELECTED] = "#D8BB75" 
# bg[INSENSITIVE] = "#EFEFEF" 
# base[NORMAL] = "#ffffff" 
# base[PRELIGHT] = "#EFEFEF" 
# base[ACTIVE] = "#D0D0D0" 
# base[SELECTED] = "#DAB566" 
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
-------- cut here --------

Next, uncomment the part that says:

# fg[NORMAL] = &#8220;#ffffff&#8221;

So it looks like:

fg[NORMAL] = &#8220;#ffffff&#8221;

Save this file. It will be saved as .gtkrc-2.0 in your home directory. You do not need to do save as, unless your terminal is opened in another directory besides your home directory.

Note: you will not see this file in normal view. The &#8220;.&#8221; in front of the filename makes the file hidden. You can see all of your hidden files in Nautilus by selecting view -> show hidden files.

To explain, the #ffffff represents the color white. You can change this to whatever color you want. Gcolor2 is a great color chooser for Gnome. Ubuntu users will find this in universe:

sudo apt-get install gcolor2

The change desktop background dialog will also work to select this color notation, if you do not want to install gcolor2.

All we need to change is:

fg[NORMAL] = &#8220;#ffffff&#8221;

to allow our Gnome panel to have a different text color besides black (#000000), which is the default. The rest of the lines in this are out of the scope of this solution. However, they are useful for other things which will not be discussed for this post.

The last step is to refresh the Gnome panel:

killall gnome-panel

---

### Post by Tribulation on 2009-03-09
Hey, thanks a lot for that. Works perfect.

---

