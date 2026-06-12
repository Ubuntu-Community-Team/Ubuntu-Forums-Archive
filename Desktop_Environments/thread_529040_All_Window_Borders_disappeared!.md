---
title: "All Window Borders disappeared!"
date: 2007-08-18
forum: Desktop Environments
---

### Post by myke on 2007-08-18
I don't know what the hell just happened but I restarted I had been out of the house for just a short while and I boot back up into my Gnome environment and now all of my window borders have gone.  As in ... no minimize, maximize buttons, etc.  the entire borders are gone, gone, gone.  When I go to preferences in either themes or just windows, its says my window manager config file is now missing.  I didn't remove anything so where the hell did it go????   I tried reinstalling metacity and nautilus but it didn't work.

This has taken away a lot of functionality.   I can't even maximize the browser window and couldn't shut others.  HELP!  I had to install the base of kde just to get into the forum to ask this as the window manager problem also wouldnt' let me input into any window fields!

BTW -- this is the error message I get when trying to access the "windows" settings from the preferences section of the gnome main menu:

[I]Cannot start the preferences application for your window manager

Window manager "unknown" has not registered a configuration tool[/I]

---

### Post by MTZeon on 2007-08-18
Open the terminal and write:
metacity --replace&

That should do it... probably compiz was messed up...

---

