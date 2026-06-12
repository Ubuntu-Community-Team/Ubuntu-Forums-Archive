---
title: "Menus between XFCE, GNOME and KDE"
date: 2006-01-08
forum: Desktop Environments
---

### Post by vayu on 2006-01-08
There seems to be some overlap on the menus as I switch from one DE to another.  XFCE has several double entries.  
The definition file in ~/.config/xfce4/desktop/menu.xml describes some of its own entries then it includes "system" for the universal shared between DE stuff and for the Debian menu it includes "menudefs.hook" which also resides in that directory.

```

  <include type="system"/>

  <menu name="Debian" icon="debian">
	  <include type="file" src="menudefs.hook"/>
  </menu>

```

My questions are, what and where is "system" defined, and why does xfce duplicate some of its entries?

And the Debian menus are described in menudefs.hook, making me think that it will not be updated as I add and remove programs.  Where do I find the official Debian menu from where menudefs.hook came and how can I periodically update from the master Debian menu?

---

