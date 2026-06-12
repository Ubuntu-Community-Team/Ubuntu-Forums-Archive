---
title: "How to change GNOME main menu button"
date: 2007-06-22
forum: Desktop Environments
---

### Post by deepclutch on 2007-06-22
I tried  and failed.any method to replace Ubuntu logo icon of GNOME main menu.will be useful

---

### Post by dizee on 2007-06-22
Change the logo by replacing the png file  at ```
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```

---

### Post by deepclutch on 2007-06-22
I dont have such a directory.Is there a generalized how to working with most themes.

---

### Post by jayson.rowe on 2007-06-22
download these two icon packs...

[http://gnome-look.org/content/show.php/nuoveXT?content=26448](http://gnome-look.org/content/show.php/nuoveXT?content=26448)

[http://art.gnome.org/themes/icon/1352](http://art.gnome.org/themes/icon/1352)

Go into the index.theme file of the nuoveXT theme w/ gedit and change

Inherits=gnome

to 

Inherits=gnome-icon-theme-2.18.0

You now have the Gnome Foot, AND better icons everywhere else too :)

I also use this window theme...

[http://gnome-look.org/content/show.php/Ubuntulooks-cool?content=49363](http://gnome-look.org/content/show.php/Ubuntulooks-cool?content=49363)

And here is the end result: I love the more 3D appearance ubuntulooks-cool gives the panels

[IMG]http://www.lamerc.com/uploads/jgnome.jpg[/IMG]

---

