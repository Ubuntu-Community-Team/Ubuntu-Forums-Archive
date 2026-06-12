---
title: "Linsta3 Firefox Openoffice menubar bug"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by stchman on 2007-11-10
I am using Linsta3 and it is really cool.  There is the problem with Firefox and Openoffice.org.
Seems that the menubar is black with black text. Has anyone figured out a fix?

There is a pseudo work around but it makes all your drop down menus black and not that appealing.


Thanks.

---

### Post by Hagar Delest on 2007-11-10
For FF, there was a workaround here : [ Change font color in OpenOffice toolbar]("http://ubuntuforums.org/showthread.php?t=465931"). But for OOo, it's still an issue. But strangely, a high contrast theme on my Dapper (with OOo 2.3) works fine.

For Linsta, I'm wondering if it's not specific to this theme. Someone had had the same issue some months ago and we had worked a workaround tweaking the gtkrc file with the following code :
```
class "GtkMenuBar*"                style "menubar-black"
widget_class "*MenuBar.*"             style "menubar-vista"
widget_class "*Nautilus*.GtkMenuBar*"    style "menubar-blue-dark"
#widget_class "*E*GtkMenuBar*"        style "menubar-green"
#widget_class "*Gimp*GtkMenuBar*"    style "menubar-purple-deep"
#widget_class "*Firefox*GtkMenuBar*"    style "menubar-brown"

#class "GtkMenu"                       style "menu-silver"
class "GtkMenu"                       style "menu-black"

#class "GtkMenuItem"                       style "menuitem-silver"
#class "GtkTearoffMenuItem"            style "tearoffmenuitem-silver"
#class "GtkImageMenuItem"            style "menuitem-silver"
class "GtkMenuItem"                       style "menuitem-black"
class "GtkTearoffMenuItem"            style "tearoffmenuitem-black"
class "GtkImageMenuItem"            style "menuitem-black"

widget_class "*Panel*Toplevel*GtkMenu"                       style "menu-black"
widget_class "*Panel*Toplevel*GtkMenuItem"            style "menuitem-black"
widget_class "*Panel*Toplevel*GtkTearoffMenuItem"        style "tearoffmenuitem-black"
widget_class "*Panel*Toplevel*GtkImageMenuItem"        style "menuitem-black"
```

---

### Post by stchman on 2007-11-10
I was surfing Gnome-look and found this theme.  It is a variant of Linsta3 and it rocks.

[http://www.gnome-look.org/content/show.php/OrangeLiNstaBlackPlastic?content=62434](http://www.gnome-look.org/content/show.php/OrangeLiNstaBlackPlastic?content=62434)

Check it out.

---

