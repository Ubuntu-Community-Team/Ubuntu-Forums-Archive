---
title: "Is this a bug in Intrepid/Gnome top panel transparancy"
date: 2009-01-24
forum: General Help
---

### Post by Peter09 on 2009-01-24
Hi.
Just changed my wall paper on my dual monitor desktop. I decided to have my top panel as nearly transparent. 
I notice that the Ubuntu Menu area and the user switcher have a lower highlight - not the same as the rest of the panel. Is this a bug or is there a place where I can change this?

---

### Post by AlexBellisBrown on 2009-01-24
I think its noramlly a bug caused by the GTK theme that is used in Appearences. I dont know of any way to fix it....

EDIT: Actually ive just remembered i saw a similar thread not to long ago, it was solved by editing the themes file in gedit or something.... i cant remember exactly but ill look for the thread and post it here. :)

---

### Post by Peter09 on 2009-01-24
Thanks - I'll have a look around as well.

---

### Post by AlexBellisBrown on 2009-01-24
This is what was posted, its rather complicated, but its really not that hard to understand...


> **mcduck said:**
> Open the themes gtkrc file (you'll find it somewhere in /home/*username*/.themes/*nameofthetheme*) in text editor, and comment out the line 10 (include "panel.rc") by adding a "#" to the beginning of that line. That should pretty much remove all the changes that theme makes to your panels.

Depending on your theme/panel background/wallpaper you might also need to define new colors for text in your panels. You can do that by creating a file called ".gtkrc-2.0" in your home directory and pasting the following code there. (You can change the colors to whatever fits your desktop. Log out and back again to see the changes.)
```
style "panel"
{
fg[NORMAL] = "#000000"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"

style "panel-clock"
{
  fg[NORMAL] = "#000000"
}
widget "*.clock-applet-button.*" style "panel-clock"
```

---

