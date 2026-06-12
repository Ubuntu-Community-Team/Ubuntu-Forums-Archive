---
title: "LiNsta 3 theme (xfce)"
date: 2006-12-19
forum: Desktop Environments
---

### Post by msx2 on 2006-12-19
How i can solve these defaults errors?

[[IMG]http://aycu16.webshots.com/image/8415/2004941689259233738_rs.jpg[/IMG]See the picture](http://allyoucanupload.webshots.com/v/2004941689259233738)

Theme: LiNsta 3 (Linux is Not Vista): Version:  0.3

---

### Post by paparucino on 2006-12-19
> **msx2 said:**
> How i can solve these defaults errors?

Theme: LiNsta 3 (Linux is Not Vista): Version:  0.3
You must change the theme :-)
or goto
[http://www.gnome-look.org/content/show.php?content=44570](http://www.gnome-look.org/content/show.php?content=44570)
and select the download you prefer (there is not so much...)

---

### Post by westley.anderson on 2007-11-27
extract the tar.b2z file and then edit the LiNsta3/gtk-2.0/gtkrc file with nero, vi or what ever you like.
change the last part to the following and then archive back to tar.b2z install new them and your good to go

class "*BonoboDockItem"			style "toolbar-clear-alt-1"
widget_class "*BonoboDockItem"		style "toolbar-clear-alt-1"
class "*HandleBox"					style "toolbar-clear-alt-1"
widget_class "*HandleBox"			style "toolbar-clear-alt-1"
class "*Toolbar"					style "toolbar-clear-alt-1"
widget_class "*Toolbar"				style "toolbar-clear-alt-1"

class "GtkMenuBar*"				style "menubar-clear"
widget_class "*MenuBar.*" 			style "menubar-clear"
widget_class "*Nautilus*.GtkMenuBar*"	style "menubar-blue-deep"
#widget_class "*E*GtkMenuBar*"		style "menubar-green"
#widget_class "*Gimp*GtkMenuBar*"	style "menubar-purple-deep"
#widget_class "*Firefox*GtkMenuBar*"	style "menubar-brown"

class "GtkMenu"       				style "menu-silver"
#class "GtkMenu"       				style "menu-black"

class "GtkMenuItem"           			style "menuitem-silver"
class "GtkTearoffMenuItem"			style "tearoffmenuitem-silver"
class "GtkImageMenuItem"			style "menuitem-silver"
#class "GtkMenuItem"           			style "menuitem-black"
#class "GtkTearoffMenuItem"			style "tearoffmenuitem-black"
#class "GtkImageMenuItem"			style "menuitem-black"

#widget_class "*Panel*Toplevel*GtkMenu"       				style "menu-black"
#widget_class "*Panel*Toplevel*GtkMenuItem"			style "menuitem-black"
#widget_class "*Panel*Toplevel*GtkTearoffMenuItem"		style "tearoffmenuitem-black"
#widget_class "*Panel*Toplevel*GtkImageMenuItem"		style "menuitem-black"

---

