---
title: "[SOLVED] Apple icon gone on Mac theme when upgraded"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by jmagick07 on 2007-10-31
The little apple icon near "Applications" has reverted to the Ubuntu default when I upgraded to the latest version (7.10)

Is there a way to get the apple back?

[img]http://i8.tinypic.com/6ezoth5.png[/img]

---

### Post by Forlong on 2007-10-31
> **jmagick07 said:**
> The little apple icon near "Applications" has reverted to the Ubuntu default when I upgraded to the latest version (7.10)
It's not a bug, it's a feature.
> **jmagick07 said:**
> Is there a way to get the apple back?
No. Ubuntu had to remove any Apple-related stuff from your install because of patent issues.


SCNR :)

I guess the path of the responsible image has changed (again) in Ubuntu's latest version.
You can change it manually in **/usr/share/icons/<your icon theme>/22x22/places**. The file you have to replace is called **start-here.png**
(if you changed the size of your panel, you might have to do that in a different location than 22x22)

---

### Post by jmagick07 on 2007-10-31
My icon theme isn't listed :(


[img]http://i11.tinypic.com/4loq3km.png[/img]



[img]http://i1.tinypic.com/4zw0h37.png[/img]

---

### Post by Forlong on 2007-11-01
Ah, OK. Then you didn't install it for all users.
Have a look in **/home/<your name>/.icons** (that's a hidden folder)

---

### Post by boeing777 on 2007-11-01
the problem i think is that the icon package is not yet 100% compatible with the newest Ubuntu version, they are working on a updated icon package and it should be out anytime soon and that will fix the problem i think

---

### Post by jsully1 on 2007-11-01
A number of icon themes no longer work because of the update to Gnome 2.20 - you'll need to wait for specific icon pack updates before they work properly, or get down and dirty in the packages and do some renaming. Some do work - for example, Oxygen Refit and nuoveXT both work, OsX_MoD, and Mac4Lin do not, as you've noticed.

---

### Post by boeing777 on 2007-11-01
I wonder how much longer do we have to wait before the new icon pack comes out.

---

### Post by jmagick07 on 2007-11-02
I found [this  icon theme](http://www.gnome-look.org/content/show.php/Mac4Lin+Leopard+GTK+Icon+Theme?content=68413) which looks pretty nice, and is updated for the new version of Gnome.  I'm using it now.  If any of you are looking for an updated icon theme, try that one :)

Thanks everyone for your help.

---

