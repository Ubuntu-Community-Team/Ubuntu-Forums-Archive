---
title: "The low down on Window Maker"
date: 2005-05-19
forum: Desktop Environments
---

### Post by Psquared on 2005-05-19
**In General:**

I got Window Maker from Synaptic but I believe it is the most uptodate and stable version. It is a fast Window Manager and can be configured as a full-blown DE with a little tweaking. Window Maker is very fast and very well developed. It loads in a split second compared to Gnome and KDE -- even XFCE.

**Configuration:**
In the upper right hand corner you should see three icons. The first one is the Window Maker icon, the second is terminal and the third is the configurator. You can play around with those settings. I will warn you that the menu configurator does not work too well. (see below)

**Dockapps:**
This is the central feature of Window Maker.

When you search for add-ons or dockapps as they are called, use "wm" in your search. It will bring up a bunch of superfluous stuff, but scroll down to the things that start with "w" and click on each and read the description. Window Maker itself is called "wmaker" in Synaptic.

Some programs are written especially for Window Maker. I installed WMweather+, wmmail, wmclock, wmnetmon and a couple of others from Synaptic. For other dockapps see [www.dockapps.org](www.dockapps.org).

Anything can be added as a dockapp. Use "terminal" to start the program and an icon will appear in the bottom left corner. Grab the corner of the icon with your mouse and drag it to the upper right or upper left and it will dock. Close terminal and then right click on the new icon (which will have changed appearance) and holding the mouse button down select "launch". If you want it to start with Window Maker right click again and select properties/preferences and that will open a properties window. Select the button at the top to start.

Before you exit Window Maker be sure you save your session!!!

**Menus:**
The menu is selected by right clicking on the desktop, but the choices are limited so you will need a program called "menumaker." It's not available in the debian sources so you will have to download the tarball and install it. (sorry, I don't have the link)

When you run menumaker it will parse your Gnome, XFCE and KDE menus and add native apps. It will not add OpenOffice, Synaptic, Amule and some others, but you can do that by hand. (see dockapps above)

**Customize:**
Window Maker comes with a bunch of themes. Be careful using Nautilus in Window Maker because it will allow Gnome to take over your desktop. Use Rox-filer instead.

---

### Post by Stormy Eyes on 2005-05-19
[QUOTE=Psquared]**Customize:**
Window Maker comes with a bunch of themes. Be careful using Nautilus in Window Maker because it will allow Gnome to take over your desktop. Use Rox-filer instead.[/QUOTE]

You can safely use Nautilus in Window Maker as long as you run it with the **--no-desktop** switch. This applies to other window managers as well, like Openbox, Fluxbox, Enlightenment, etc.

---

### Post by Psquared on 2005-05-19
[QUOTE=Stormy Eyes]You can safely use Nautilus in Window Maker as long as you run it with the **--no-desktop** switch. This applies to other window managers as well, like Openbox, Fluxbox, Enlightenment, etc.[/QUOTE]


Good point. I forgot about that.

I also wanted to point out that there are some deb repos out there that have dockapps available. The description in [www.dockapps.org](www.dockapps.org) will tell you which ones have deb sources and you can add them to your sources.list file, install the dockapp and then comment them out.

---

### Post by bytor4232 on 2008-03-27
For a full, but lightweight desktop, install xubuntu-desktop, and put the following in $HOME/GNUstep/Library/WindowMaker/autostart
```

#!/bin/bash
xfce4-session &

```
Make sure you make it executable.  I tweaked a bunch of things by hand with WPrefs once I got it going.  Its worked out pretty nice for me.

---

