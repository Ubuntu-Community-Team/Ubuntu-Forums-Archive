---
title: "Howto Gnome Panel bold fonts and yellow color fonts"
date: 2009-04-26
forum: Desktop Environments
---

### Post by brdokoky on 2009-04-26
When I replaced gnome panel to dark one ,I could not read my fonts in panel. That I found this how to change color and bold fonts. Still working in ubuntu 9.10 
Just open up your home folder and make sure you can view all hidden files, look for the file .gtkrc-2.0

If the file isnt there open up your text editor and create one, put this into that file:

[B]style "modpanel"
{
font_name = "Bold"
fg[NORMAL] = "#ECE703"
}
widget "*PanelWidget*" style "modpanel"
widget "*PanelApplet*" style "modpanel"
widget "*fast-user-switch-applet*" style "modpanel"
[/B]
Thats it! Just save the file. And into the terminal put :

killall gnome-panel 


Now you got readable fonts in gnome panel.

Have fun with it!

---

### Post by Maleeq on 2009-11-03
Thanks...works fine for me

---

