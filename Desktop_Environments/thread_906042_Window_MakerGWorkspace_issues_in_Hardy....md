---
title: "Window Maker/GWorkspace issues in Hardy..."
date: 2008-08-31
forum: Desktop Environments
---

### Post by nray on 2008-08-31
So I'd really like to get Window Maker running well as my desktop environment in Hardy, and I'd like to stick to the packages if possible rather than compile a lot of code (this is on an Acer Aspire One Intel Atom-based notebook).

I've seen a lot of oddities... first I tried to change my desktop environment to Window Maker from within the default one (I think it was under Appearance or somesuch, there was a drop down where I could select Window Maker).  Logging out and logging back in made no difference, but if I selected 'Options' on the login screen and then selected Window Maker, that worked.

So far so good, but I've noticed that gnome applications like Terminal and Desktop have an absurd default UI in Window Maker - fonts are gigantic, heck every bit of the UI is too big.  Where do I fix this?  I can't use the apps like this, my screen is 1280x600.  This seems like pretty basic stuff, but my google searches haven't turned up anything that helps.

Next up, I'm trying to use GWorkspace.app, but the only way I've gotten it to come up is to type 'openapp GWorkspace.app &' from the command line.  Is that right?  While openning the terminal gets spammed with a lot of errors like this "2008-08-31 00:44:36.801 GWorkspace[22718] X-Windows error - BadPixmap (invalid Pixmap parameter)" - is that normal?  And then even odder, it seems to have it's own dock on the right hand side of my screen, *below* my existing Window Maker dock, without any icon borders, and with just the GWorkspace icon and the Recycler (which btw is not showing up in my Window Maker dock!)  What's going on with the double docks, and where's the Recycler in Window Maker?

There are a lot of other things I'm wondering too, like how hard will it be for me to disable the scrolling feature of my Synaptics touchpad in Window Maker (it was pretty easy in the standard Ubuntu desktop), and how difficult will it be to manage my Wifi connection in Window Maker?  I haven't seen any graphical network configuration tools, and the clone of the Preferences app from OS X, 'System Preferences', currenly only has pref panes for Date & Time, File System, Modifier Keys and Volumes.

This all strikes me as problematic and hodgepodge, unless I'm just missing something - I really want to like and use Window Maker too, so if someone can enlighten me, I'm all ears...

---

### Post by Nergui on 2008-08-31
Hi nray,

If I understand correctly, you are not running WMaker in combination w/GNOME, but are simply trying to run a few GNOME apps in a vanilla WMaker setup. You may want to consider either running the gnome-settings-daemon automatically on startup, or editing your .gtkrc by hand to display the fonts, theme, and icons correctly. The latter is admittedly more of a pain, but it works for me.

Also, I wouldn't bother with GWorkspace if I were you. It is part of the collection of GNUstep tools, which is intended to be part of a GNUstep environment which is not yet very compatible with other desktops/toolkits, in terms of integration and settings. WindowMaker is technically the official GNUstep window manager, but has been almost unmaintained for the last 3 years or so, and its documentation is not exactly complete. It also has some inconsistency in its interactions with GNUstep apps, partly due to the fact that it is based around the WINGS widget toolkit rather than directly on GNUstep libraries. Some GNUstep desktop projects have actually written a fork of Openbox, called Azalea, to use as their window manager, hoping to integrate it more closely from the beginning.

Having said all this, I still love WMaker in its own right. It is quite stable and efficient, and works perfectly well with most gtk/Qt/etc. apps.
There are a few tricks you may need to get it to play nice with apps from other environments, but most of these are the same tricks used by users of, say, IceWM, Fluxbox, Openbox, etc.

Since it is only a window manager, though, you will have to use other programs to manage your system settings and wifi. And I definitely recommend you try wmakerconf. It's a gtk preferences utility for WMaker, and although its interface is perhaps less elegant than the builtin preferences utility, it offers a few extra options that you may otherwise have to edit config files to use.

Nergui



EDIT: You might might find this link helpful:

[http://linux.byexamples.com/archives/239/gtk-configuration-for-non-gnome-desktop-user/](http://linux.byexamples.com/archives/239/gtk-configuration-for-non-gnome-desktop-user/)

---

