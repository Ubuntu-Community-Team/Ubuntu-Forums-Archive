---
title: "xfce4 weather applet font colours"
date: 2012-08-25
forum: Desktop Environments
---

### Post by gdesilva on 2012-08-25
I am running the xfce4 weather applet but due to the desktop theme I am running, the updates can be hardly seen.

Is there a way to change the font color in weather applet?

Thanks

---

### Post by gdesilva on 2012-09-02
For the benefit of anyone else who may come across the same probelm...I had to workaround the problem by selecting a different theme. I was using SiO2 as my theme which gives me a dark panel and the animated text has a similar color and hence the problem. However, I found that if I changed to another theme such as greybird the text color changes to white to make the text visible. Not the ideal solution but some consolation!

---

### Post by SantaFe on 2012-09-02
Or you could just right click on the panel, pick panel then Panel Preferences.  Choose which panel it is (If you have more than one) and click on the Appearance tab.  Then in the Style option click & choose Solid Color.  Then click on the colored box & play around with the color wheel till you find a color you like that shows the black text well. ;)

Note: might need to restart if the panel looks messed up.  There are always some plugins that want to hold on to the old panel theme sometimes. :popcorn:

---

### Post by jawz101 on 2013-01-05
got this from another forum.  in your .gtkrc for the theme you're using in /usr/share/themes/... add this:

```
#--------------------------------------------------------

style "panel-color" {  
  fg[ACTIVE]        = "#111111"
  bg[NORMAL]        = "#edeff2"
  bg[PRELIGHT]      = "#213d60"
  bg[ACTIVE]        = "#042230"
  text[NORMAL]      = "#ffffff"			# color for the text in the weather applet
}

widget "*PanelWidget*"	style "panel-color"
widget "*PanelApplet*"	style "panel-color"
widget "*Panel*"	style "panel-color"	# Changes the selected Background around the trash applet
widget_class "*Panel*"	style "panel-color"	# Used to change the weather applet in Xfce text color also background in the panel selected, active, etc. buttons
#class "*Panel*" style "panel-color"
#class "*Tray*" style "panel-color"
#class "*tray*" style "panel-color"

#--------------------------------------------------------
```

I put in a request on the xfce4 wiki to request a global-wide font color setting for panel plugins since I always have trouble with dark themes or transparent panels with a dark wallpaper

---

