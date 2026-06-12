---
title: "Missing Menu bar"
date: 2011-05-01
forum: Desktop Environments
---

### Post by jpheymans on 2011-05-01
Hi everyone! 
I was trying out several desktop environments in ubuntu 11.04 until I found xfce, installed it and removed all others, but I do have a problem with it: several of my applications are missing their menu bar.
I'm posting because all I found in the forum about menus in xfce was people having touble with the panels. This is not the case,what I'm missing is the file/edit/insert/view/tools/help menu.
If anyone has any ideas of what to do, I'll be glad to hear them!
By the way, this is my first post in the forums :D

---

### Post by teachop on 2011-05-01
I am using Xubuntu and not seeing that.  Which applications are having trouble?  Firefox can have a no-menu look now, but that is an option to turn on/off.

---

### Post by jpheymans on 2011-05-01
Yes, I know, and I did activate it, but the "Firefox" menu should appear, and I don't get that either, also I'm experiencing the problem in Banshee, GIMP, Ubuntu Software Center, Vitualbox and Nautilus, also in Thurnar, gwget, the xfce terminal and Gmusicbrowser (for those last four I'm not quite shure if a menu should show, since I never used them before xubuntu)
The menu works for thunderbird, libreoffice, pidgin, gparted and some other programs.
If I switch to compiz the same thing happens so it might not be xfwm related
I attached a screenshot, for you to see what I mean

---

### Post by jpheymans on 2011-05-03
Today I found out it may have something to do with Unity global menu, I say that because I disabled Firefox global menu addon and the menu is now working. It doesn't yet in other programs anyway, so maybe someone can tell me how to remove unity (which additional packages/coonfigs do i have to remove, etc)
Thanks in advance!

---

### Post by ManualSparrow on 2011-05-10
```
xfwm4 --replace
```
Possibly add that to startup applications list - restarts / starts the XFCE window manager and I think fixed that problem for me.

You should be able to remove Unity and Gnome things in the Synaptic Package Manager.

---

### Post by jpheymans on 2011-05-11
I got tired and had my \home in another partition so I just reinstalled with a true Xbuntu live cd.
For the record I had done xfwm4 --replace and didn't (metacity --replace/compiz --replace) didn't help either, And I removed all Unity packages, with sudo apt-get remove unity* and checking that ther were none left form synaptics. What I didn't think of was removing also gnome packages, so that may help if somebody else has the same problem.
Thanks to all that replied!!

---

### Post by gaz514 on 2011-05-11
Same problem here. I figure it's something to do with whatever hacks they did to implement the Unity global menu bar. I was hoping not to have to reinstall from the Xubuntu liveCD but looks like I probably will.

---

### Post by morgengenuss on 2011-05-12
it should be pretty straight-forward to fix this, all you need to do is uninstall the package "indicator-applet-appmenu".
then logout and re-login, that should be it.

---

### Post by ManualSparrow on 2011-05-12
Darn, you're right - that's what I did, because the Indicator Applet was all glitchy and varied in size or became invisible arbitrarily, while at the same time hiding the menu bar on open windows.

---

### Post by gaz514 on 2011-05-12
I fixed it by deleting my Xfce config (.config/xfce), to fix the seemingly unrelated problem of indicator-applet having disappeared, and now both the indicator applet and the menus work again. Looks like that's the culprit.

---

