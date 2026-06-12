---
title: "Lost the startup screen"
date: 2005-04-27
forum: Desktop Environments
---

### Post by ppyvras on 2005-04-27
I prefer KDE to Gnome so I thought I would get rid of a load of Gnome stuff that I no longer needed.  Through Synaptic I got rid of pretty much everything with Gnome in the title that did not have any dependancies that I thought I needed - big mistake.  Well not that big, as everything in KDE still works fine.  My only problem is that I don't get the startup screen where you can login.

When I boot up, all it does at the moment is leave me at the commant prompt menu and I have to type 'startx' to get into KDE.  What packages do I need to install to get that login screen back or is there an alternative for KDE that would be better?  

I can't seem to find any clues on the net, probably cause I don't know what to call the thing.  On another point, is there a way of shutting down the computer directly from KDE, because despite checking the right boxes, there was no option on the menu and logging out would send me back to this login screen that I am now missing.

Cheers in advance for any pearls of wisdom.
 :???:

---

### Post by LeNain on 2005-04-27
Well, the package you removed and allowed you to login is called GDM (for gnome) and KDM for KDE.
 
Did you install kdm ? if not try to "sudo apt-get install kdm"
 
I think that the first time you'll run kdm as you logging manager it will set itself up, but i'm not sure of it.
 
Btw, if you just want this package and not gnome, just "sudo apt-get install gdm"

---

