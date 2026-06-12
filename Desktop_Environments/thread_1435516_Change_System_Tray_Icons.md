---
title: "Change System Tray Icons"
date: 2010-03-21
forum: Desktop Environments
---

### Post by tenzinphoto on 2010-03-21
Hi, does anyone know how to change specific icons for items in the system tray in gnome 2.28.1?  I'm using Ubuntu 9.10.  Specifically the icons for Compiz Fusion Icon and Gnome-Power-Manager.

Thanks!

---

### Post by Nandox7 on 2010-03-22
Hey,

As for Gnome Power Manager you can change/edit it's icons by going into:

1. Is it a custom theme that implements it's own Power Manager Icons? 

--> /usr/share/icons/{theme_name}/{size}/apps/
And checking the gpm-* icon files.

2. Is it the default GPM icon set?

--> /usr/share/gnome-power-manager/icons/hicolor/{size}


As for compiz it might follow a similar scheme.

---

