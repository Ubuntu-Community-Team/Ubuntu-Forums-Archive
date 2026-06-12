---
title: "Right click to open XFCE menu - Xubuntu"
date: 2008-10-24
forum: Desktop Environments
---

### Post by Ginsly on 2008-10-24
Hi.... Have been away from Ubuntu for a while, but I'm back as of yesterday with Xubuntu.

This is my first time using Xubuntu, but not XFCE. As with a normal XFCE desktop install, everything is easily changed to the way I like it (the reason its my favourite Desktop) except for one thing. Right clicking on the desktop, doesn't bring up the usual XFCE menu, instead it brings up a menu for adding a launcher/create a folder/url link to the desktop, and a shortcut to the desktop preferences. Am using the same version of XFCE in Debian Lenny, and sidux, and the XFCE menu is there on right click!!

If anyone knows if this can be changed, or if I'm just missing a checkbox somewhere in the Settings Manager, I'd be eternally grateful, as this is one of my favourite features of XFCE... 

Cheers..  :biggrin:

---

### Post by Ginsly on 2008-10-25
Sorry thread somehow got started twice.... Mods, can u pls delete this post

---

### Post by denham2010 on 2008-10-26
Open the Xfce Settings Manager and click on the Desktop icon.

Click on the Behaviour tab and alter your menu settings there.

Cheers.

---

### Post by mali2297 on 2008-10-26
In Settings Manager -> Desktop Preferences, check that "Allow Xfce to manage the desktop" is enabled.

Are you using Nautilus?
If so, see [http://spuriousinterrupt.org/projects/xfce4#faq](http://spuriousinterrupt.org/projects/xfce4#faq):
> Help!  My Xfce desktop disappeared!  It looks like GNOME!  And the desktop menu is gone too!  What do I do?

    * 	You ran nautilus, didn't you?  By default, Nautilus takes over the desktop when it runs.  First you need to kill Nautilus, and then you should run xfdesktop to make sure Xfce's desktop manager is running.  In the future, when you run Nautilus, pass it the --no-desktop option to instruct it to avoid drawing the desktop.  A more permanent solution is to set the gconf key /apps/nautilus/preferences/show_desktop to "false" (the --no-desktop will no longer be required).  This can be done using the graphical gconf-editor, or the command-line gconftool utility.

---

### Post by Ginsly on 2008-11-16
No , Thunar... but thankyou the "allow xfce to manage the desktop" checkbox was the one I was missing... I felt a bit silly for missing it...

---

