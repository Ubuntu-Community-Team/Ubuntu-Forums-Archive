---
title: "Stumped on theme manager error"
date: 2007-08-09
forum: Desktop Environments
---

### Post by dkaddict on 2007-08-09
I have no idea of how to solve this problem. When I try to change the root theme of Ubuntu 7.04, I get this error message and am unable to change gtk or meta-city styles. I open a terminal>>>

> 'gksu gnome-theme-manager'

always results in this>>

> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

I have looked around but can't work out what I need to change. My .gtkrc-2.0 reads>>

> # This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

style "user-font"
{
	font_name="Monospace 10"
}
widget_class "*" style "user-font"

gtk-theme-name="Qt"
gtk-font-name="Monospace 10"
include ".gtkrc-2.0-gnome-color-chooser"

I am thinking that it is a problem with KDE which has arisen because I once had both kde and gnome installed. Now I just have gnome. Is there any place I can find out what to do to solve this? Any advice or links will help a lot.

Thanx

dk

---

### Post by Goliath! on 2007-08-23
Same problem here.  Anyone have a solution?  Or even a hint?  Would be very very appreciated!!

---

### Post by dkaddict on 2007-08-24
Bump

---

