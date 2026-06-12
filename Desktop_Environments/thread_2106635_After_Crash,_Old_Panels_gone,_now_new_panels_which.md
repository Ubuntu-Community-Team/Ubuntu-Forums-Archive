---
title: "After Crash, Old Panels gone, now new panels which I can't control"
date: 2013-01-19
forum: Desktop Environments
---

### Post by wdavro on 2013-01-19
I'm using PRecise and Gnome 3.4.2.
I had a couple crashes because of a gone-bad usb cable for my external usb ubuntu boot drive.  I have a new cable and now I can boot to ubuntu.  But my 2 panels are gone and they have been replaced with what looks like default panels.  But I can't edit/control/delete or otherwise change these panels.
However I can 'edit menus' by right clicking on the Applications menu.

I've tried (in order):
    Alt-right click on panels - no response
    windows key right click - no response
    ctrl-right click - no response
    I renamed ~/.gconf to ~/goncf.bak and copied a backup copy of gconf and rebooted - no change
   per thread: Why do I have a new panel on my desktop I cant get rid of?
   I tried advance settings disable 'have file manager handle the desktop' - no change
  logout log back in - no change
  I turned 'have file manager handle the desktop' back on
  I tried 'sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt'
  logout log back in - no change

This is where I am at this point.  My programs seem to work fine using the menus, all my bookmarks, etc seem to be in Firefox.  My various local settings seem to be intact.  My desktop shortcuts and launchers are present. Although I notice I no longer have a 'Home' and 'Computer' and 'Network' shortcut.  I believe these are provided by the system.  I went into advance settings and turned them on and they're back.

I am the only user of the system.  I have created a 2nd admin user just in case my current user goes away or gets crippled.  I logged in as the 2nd user and I have the same panel problem.

I have two questions:
1. How can I control these two panels so I can delete them?
2. Every few days I copy my entire home directory (including hidden files) to another computer.  I assume I have therefore copied my original panel settings which I would love to get back.  What folders can I replace to get them back?

Thanks

---

