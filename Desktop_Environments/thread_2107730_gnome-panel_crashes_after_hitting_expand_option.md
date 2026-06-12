---
title: "gnome-panel crashes after hitting expand option"
date: 2013-01-22
forum: Desktop Environments
---

### Post by psifunk on 2013-01-22
So, all I wanted was to have the change keyboard layout option found in classic gnome. I am using ubuntu 12.04, its a fresh installation and I am trying real hard to give unity a chance. I followed some instructions for a simple idea. 

Run gnome-panel in terminal
Delete the top panel.
Add the change layout applet in the bottom panel nad remove all other applets in that panel as they are not needed in unity.
Right click the panel, go to properties and unclick expand, so that the panel does not overlap unity on the left.

Everything was going fine up to the point i unclicked expand. Gnome panel immediately crashed and would not run again. I did apt-get purge gnome-panel and then reinstalled it. Nothing changed. The output looks like

```
marios@mrLap:~$ gnome-panel 

(gnome-panel:2457): Gtk-CRITICAL **: _gtk_style_properties_set_property_by_property: assertion `_gtk_css_value_holds (value, _gtk_css_style_property_get_computed_type (style_prop))' failed

```

repeated say 30 times. Any clues on what to do to get gnome-panel back in life? Alternative ideas for the keyboard layout? I use a french keyboard with which i can also write english but my native language is greek so i absolutely need to change to greek layout from time to time. I used to do that by adding the keyboard layout applet in the old gnome panel and then the applets properties allowed me to choose a key combination for that action. thanks for any help

---

### Post by psifunk on 2013-01-22
I found how to change the layout but the gnom-panel problem is still there and i would love to solve that

---

