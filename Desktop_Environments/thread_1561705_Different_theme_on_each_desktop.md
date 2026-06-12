---
title: "Different theme on each desktop?"
date: 2010-08-26
forum: Desktop Environments
---

### Post by Halifax on 2010-08-26
Is it possible to install a different theme on each of the multiple virtual desktops? For example, I thought it would be interesting to have the default Ubuntu theme installed on the primary desktop, on the secondary desktop have a Windows 7 theme, on the third desktop have a Mac OSX theme, and perhaps another theme on the fourth.

After looking at sites like these I am interested in finding out if this is possible:
[http://linuxtrends.com/making-ubuntu-look-like-windows-7/](http://linuxtrends.com/making-ubuntu-look-like-windows-7/)
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

I realize switching between themes may be a tough thing for a computer to do quickly, but if it is possible I'd at least like to try it on my desktop, which has enough processing power to at least make the transition time bearable. Does anyone know if/how I can set virtual desktop specific themes?

---

### Post by x1a4 on 2010-08-26
It depends on which GUI you're running you may be able to do it.  At least in part.  Sawfish is an incredibly configurable window manager which works with most environments, including Gnome and Xfce or in its own session.  If you're using GNOME replace Metacity with Sawfish or replace Xfwm4 with it if you're using Xfce.   Using Sawfish's config tool you can set different themes based on an assortment of conditions including the workspace an application loads on.  The theme will not change if you move the application to another workspace though.  AfterStep can have different wallpapers and colours on each workspace.  

If you want different GTK themes for each workspace you'll have to get the source and change things there.  

Beyond that I don't think it's possible to do what you're asking.

---

