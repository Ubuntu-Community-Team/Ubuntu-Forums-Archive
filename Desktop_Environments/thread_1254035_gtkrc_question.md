---
title: "gtkrc question"
date: 2009-08-30
forum: Desktop Environments
---

### Post by Sim-I-Am :} on 2009-08-30
Just a quick question; I'm using a GTK/Emerald/Aurora theme called Filosofia, by Lassekongo83, and love it. My only qualm is that the drop-down menu's (aka right-click menu, or drop-down from file/edit/tools etc.) background color is blank white, which doesn't fit with the theme (grey, black). How do I change this? I've searched through the gtkrc, panel.rc and menubar.rc for the theme, but to no avail, and it's not a pixmap. The color I'd like to change it to is #D4D4D5.
Any help will be greatly appreciated.

~Sim-I-Am

---

### Post by Giant Speck on 2009-08-31
> **Sim-I-Am :} said:**
> Just a quick question; I'm using a GTK/Emerald/Aurora theme called Filosofia, by Lassekongo83, and love it. My only qualm is that the drop-down menu's (aka right-click menu, or drop-down from file/edit/tools etc.) background color is blank white, which doesn't fit with the theme (grey, black). How do I change this? I've searched through the gtkrc, panel.rc and menubar.rc for the theme, but to no avail, and it's not a pixmap. The color I'd like to change it to is #D4D4D5.
Any help will be greatly appreciated.

~Sim-I-Am


Go into .gtkrc and look for this:

> style "theme-menu" = "theme-default"
{
  xthickness = 0
  ythickness = 0
  bg[NORMAL] = [COLOR=Red]**shade (1.5,@bg_color)**[/COLOR]
  #xthickness = 0
 # ythickness = 0
  #bg[NORMAL] = shade (1.15,@bg_color)
}


Change [COLOR=Red]**shade (1.5,@bg_color) **[/COLOR]to "#D4D4D5".  Include the quotation marks.

---

### Post by Sim-I-Am :} on 2009-08-31
Ok, that worked, but only for the dropdown menu from the App/Places/System menu. I use 'killall gnome-panel' to refresh after saving gtkrc, but is there some other way to refresh right clck menus?

---

