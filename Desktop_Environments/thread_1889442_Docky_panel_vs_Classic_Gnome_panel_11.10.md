---
title: "Docky panel vs Classic Gnome panel 11.10?"
date: 2011-12-01
forum: Desktop Environments
---

### Post by PhilOSparta on 2011-12-01
As a desktop developer I've found my upgrading to Unity to be a big mistake on my part. The "new" Classic Gnome leaves lots to be desired over what it replaced, but Docky seems to provide most of the functionality that is absent in the "new" Classic Gnome.

How does one get the Docky panel to stay on top of the Gnome panel? Or better yet, how do you remove the Gnome panel completely since the object of Docky is to replace the Gnome panel?

Attached are the images of a Normal panel and a panel with a mouse rollover.  As can be seen, there is a problem trying to get to the active windows when you rollover.  

Bottom line:  How do you control stacking the panels, or getting the Docky panel to be positioned just above the Gnome panel?  

Thanks for any help.

Phil

---

### Post by Copper Bezel on 2011-12-01
I'd just remove the bottom Gnome panel. You can use Alt+Right Click to access its Properties or remove it.

The stacking can be controlled through Compiz (if you're using it) by using Window Rules to make Docky always-on-top, or possibly using devilspie if you're using Metacity, but I don't know why you'd want to keep the panel if you're using Docky for task management.

---

### Post by kurt18947 on 2011-12-01
if you're talking about the gnome 2ish -- applications -- places on top & lower panel, I'd think that uninstalling the gnome-session-fallback package should remove the gnome-classic & gnome-classic no effects.   Highlighting the package in Synaptic then right-clicking properties will let you look at dependencies etc.  Will Docky install/reinstall  its own dependences?

---

