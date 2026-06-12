---
title: "Fonts in aMule"
date: 2005-04-27
forum: Desktop Environments
---

### Post by MarcelB on 2005-04-27
I installed aMule, but the fonts look very ugly, because  there is no antialiasing.
How can I fix that?

I already did a fix for gnome apps as described here.
[http://www.guilinux.com/viewtopic.php?topic=321&forum=93](http://www.guilinux.com/viewtopic.php?topic=321&forum=93)
I made the fontsize 12 to match the fonts in KDE. After these changes Firefox and Synaptic looked good.

Why does aMule not? Is there another location where I have to change that?

---

### Post by MarioFuentes on 2005-04-27
aMule is a GTK+ 1.2 application, font settings in GNOME not affect this apps.

I fix this adding this to ~/.gtkrc.mine :
```
style "user-font" {
   fontset = "-bitstream-bitstream vera sans-medium-r-normal-*-*-80-*-*-p-*-iso8859-15"
}

widget_class "*" style "user-font"
``` 

I use gtkfontsel for obtaint the string of a particular font.

---

### Post by bored2k on 2005-04-27
You guys are using and old aMule.

aMule RC8 is already using GTK2, wich is beautiful.
[http://www.amule.org/files/details.php?file=59](http://www.amule.org/files/details.php?file=59)

> Hi,
After a long period of testing I can now say that the deb Packages of the CVS Snapshots are now available. And get updated every morning between 8am and 1pm.

If you want to just use the packages, put this line to your sources.list:

code:

1:

	

deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/)  testing amule wx


If you want to compile the snaps for your own, you have two options.

You can get the fixed wx packages by adding

code:

1:

	

deb [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing wx 


to your sources.list and get and compile aMule for your own. Or can can add a second line to get the pkg's source and create your own debs. For the last option you need the wx line above plus:

code:

1:

	

deb-src [http://www.vollstreckernet.de/debian/](http://www.vollstreckernet.de/debian/) testing amule


All pkg's should work on sid, too. My provider doesn't allow me to create symlinks, so I only setup the testing dir.


---

### Post by drx on 2005-04-27
As this is the KDE part of the forum i think you use KDE .... so why don't you try KMLdonkey instead of aMule? Works very good for me and fits into the KDE stuff interface nicely.

---

