---
title: "Create custom themes for applications."
date: 2008-07-12
forum: Desktop Environments
---

### Post by artrbinfo on 2008-07-12
Hello!
 Is it possible to make custom themes, for example for F-spot. I want to create another metacity for it. Is it possible, and how to set specific metacity to apps?
 Thank you!

---

### Post by sayakb on 2008-07-12
All apps using GTK themes will have the same theme you select in the Appearance Properties window. So I don't think (or I don't know) whether it can be done.. ;)

---

### Post by Spaceman9 on 2008-07-12
The F-Spot web site [http://f-spot.org/Main_Page](http://f-spot.org/Main_Page) doesn't seem to have anything about making themes for it.

Check out these on metacity themes.

Metacity Wiki [http://en.wikipedia.org/wiki/Metacity](http://en.wikipedia.org/wiki/Metacity)

Gnome metacity themes [http://art.gnome.org/themes/metacity](http://art.gnome.org/themes/metacity)

Designing Metacity Themes [http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

---

### Post by urukrama on 2008-07-13
You can set different Gtk themes for certain applications, but I don't think using a different Metacity theme would work.

If you want to use a different Gtk theme for f-spot, launch it with the following command:

> GTK2_RC_FILES=/path/to/your/theme/gtkrc f-spot

Your theme's gtkrc file will be either in /home/USERNAME/.themes/THEMENAME/gtk-2.0/gtkrc for themes you have installed, or /usr/share/themes/THEMENAME/gtk-2.0/gtkrc for themes that you installed systemwide (as through Synaptic or apt).

If you'd also like to set a custom icon theme and font for the application, create an empty file, wherever you find convenient (for example in /home/USERNAME/.themes) and call it fspot.gtkrc or so. Then add the following to that file:

> 
#To set the Gtk theme
include "/path/to/your/theme/gtkrc"

#To set the icon theme
gtk-icon-theme-name = "Human"

#To set the font
style "Sans"
{
font_name = "Sans 8"
}
widget_class "*" style "Sans"
gtk-font-name = "Sans 8"


Change 'Human' to the icon theme you'd like to use, and "Sans" to the font you'd like to use. The /path/to/your/theme/gtkrc is the same as mentioned above.

To launch the application with these settings, use the following:

> GTK2_RC_FILES=/home/USERNAME/.themes/fspot.gtkrc f-spot

(If you saved the file elsewhere, adjust the above appropriately.)

If using this in a launcher doesn't work (it works from the terminal), try the following:

> bash -c 'GTK2_RC_FILES=/path/to/your/gtkrc f-spot'

EDIT: This works fine in Openbox, which is the window manager I use, but it seems that if you have either gnome-settings-daemon or xfce-mcs-manager running (which control the Gtk theme and more in Gnome and Xfce respectively) this method doesn't work.

---

### Post by Vadi on 2008-07-13
Different gtk themes for applications is a yes, metacity highly likely no.

---

### Post by artrbinfo on 2008-07-16
Sorry for my late answer!
Thank you very much! Now I'll try to do that all.
TNX again!

---

