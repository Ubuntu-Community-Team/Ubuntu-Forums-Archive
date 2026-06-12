---
title: "Cannot Change GTK Theme from default theme - Ubuntu Gnome"
date: 2014-04-10
forum: Desktop Environments
---

### Post by daveandclaire75 on 2014-04-10
Hi 
I am experiencing issues in Ubuntu Gnome 13.10.
I cannot change the GTK and Window Themes from the default versions.
[LIST]
[*]Gnome-Tweak Tool is installed
[*]The themes are located in either /usr/share/themes or.local/share/themes
[*]I have the appropriate GTK 3 and 2 theme engines installed
[/LIST]

When I try to change them in Gnome-Tweak Tool the majority of themes do not appear in the drop down menu, and those that do allow me to change the GTK theme but not the window theme

I have tried changing the theme in Dconf Tool however when I do this I experience the following:
[LIST]
[*]No window theme appears at all
[*]I am unable to make any further changes to the themes
[*]The only solution to this issue has been for me to do a complete re-install
[/LIST]

Appreciate any guidance:)

---

### Post by vasa1 on 2014-04-10
> **daveandclaire75 said:**
> ...
[*]The themes are located in ... or **.local/share/themes**
...
I don't have a solution but aren't user-specific themes to be in **~/.themes**?

---

### Post by ibjsb4 on 2014-04-10
I am on lxde at the moment (at you vasa1 :)) and do not have dconf in front of me, but look here:


org -> gnome -> desktop -> interface and select gtk-color-scheme

---

### Post by Frogs Hair on 2014-04-10
I have had to change file permissions with a number of my manually installed themes on the 13.10 release . Check for Gnome 3.8 compatibility also. To change permissions right click on the theme folder and enter properties. gksudo nautilus will be required make changes .

---

