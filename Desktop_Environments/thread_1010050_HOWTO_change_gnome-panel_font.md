---
title: "HOWTO: change gnome-panel font"
date: 2008-12-13
forum: Desktop Environments
---

### Post by Onyx_47 on 2008-12-13
The easiest way to change the font in gnome-panel is to go to System > Preferences > Apperance, the to "Fonts" tab and change "Application Font". However, this doesn't always work. If you install gtk2.x theme by copying it to /usr/share/themes changing the font will fail as you don't have permission to write to that location. But you can easily change this manualy.

First, in terminal do:
```
sudo gedit /usr/share/<theme>/gtk-2.0/gtkrc
```
where <theme> is the name of gtk2.x theme you're using.

In this file find a section that looks something like this:
```
### font for menus and panel ###
style "extrabold" {
font_name = "FreeSans 7"
}
```
change the font and size to ones you want and save the file.

You can also change colors and size of elements here. One line I found very useful is near the top and looks something like this:

```
gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-button=16,16:gtk-large-toolbar=16,16"
```

On my 1280x800 laptop display System > Preferences menu was originaly so long it required me to scrool throught it. Changing icon size to 16,16 instead of 24,24 and shrinking the font made it compact enough for my screen ;)

If you want to play around with settings but you're not sure what will happen and you want your theme backed up you can do:

```
sudo cp /usr/share/themes/<theme>/gtk-2.0/gtkrc /usr/share/themes/<theme>/gtk-2.0/gtkrc-backup
```
to back up theme's gtkrc file.

And to restore from backup:
```
sudo mv /usr/share/themes/<theme>/gtk-2.0/gtkrc-backup /usr/share/themes/<theme>/gtk-2.0/gtkrc
```

Before settings take effect you'll have to restart gnome-panel:

```
killall gnome-panel
```

If for some reason gnome-panel doesn't start by itself:
```
gnome-panel &
```

Enjoy :)

---

