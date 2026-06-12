---
title: "Gtk Engines Help"
date: 2007-01-07
forum: Desktop Environments
---

### Post by Lucas0607 on 2007-01-07
Hey,

I'm a total noob to linux but I have managed to install beryl on edgy and it is stable...
I was browsing gnome look and found nice gtk2 themes but they say i need their engines installed and stuff... do all those compiling steps.

I've been researching aorund this forum for a resource or a howto change the panel, the overall look of everything... Starting with the engine I guess. Can anyone please make a little quick guide step by step on how to install these gtk themes and actually see the differences e.g. panels and windows wise. Thank you! :)

---

### Post by mikeym on 2007-01-07
I don't think you sould be compilling anything as a noob, just stick to downloading packages from the repositories using synaptic package manager of the command line "apt-get install whatever".

I haven't looked but I'm sure anything you'd want will be there.

---

### Post by 3rdalbum on 2007-01-07
Most of the theme engines are available from the repositories, anyway. (and most of the attractive and usable themes are included with Ubuntu, lol)

---

### Post by ayoli on 2007-01-07
```
aptitude search gtk2-engines
```
for gtk2
```
aptitude search gtk-engines
```
for gtk1.2
and here is a way to customize panel: [http://www.ubuntuforums.org/showthread.php?t=86638#5](http://www.ubuntuforums.org/showthread.php?t=86638#5)
or like i did with a background (included in gtkrc file of used theme or in a .gtkrc-2.0 in your home dir):
```
#panel stuff
style "theme-panel" 
{
  xthickness                    = 0
  ythickness                    = 0
  bg_pixmap[NORMAL]             = "panel-bg.png"
  fg[NORMAL]                    = "#ffffff" 
  fg[PRELIGHT]          = "#ffffff"
  fg[ACTIVE]                    = "#353535"
  fg[SELECTED]          = "#353535"

}
class "*Panel*"                 style "theme-panel"
widget "*PanelWidget*" style "theme-panel"
widget "*PanelApplet*" style "theme-panel"

```

a how-to for gtk theming: [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

---

