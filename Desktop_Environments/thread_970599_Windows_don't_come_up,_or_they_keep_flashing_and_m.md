---
title: "Windows don't come up, or they keep flashing and moving!"
date: 2008-11-04
forum: Desktop Environments
---

### Post by roxority on 2008-11-04
Hi,

this occurred after an upgrade from 8.04 to 8.10 but should not be directly related to the video hardware. (Thus I have created this new topic, originally I posted this one: [http://tinyurl.com/6g8r64](http://tinyurl.com/6g8r64) ) Desktop, icons, menus and deskbars show up just fine. HOWEVER, whenever a window that would typically have a chrome / border would have to show up, it either doesnt show up at all (most smallish programs) or if it does (Firefox, Evolution, Nautilus, gedit) the window keeps flashing (i.e. quickly switches between it being shown and the desktop being shown / the window not being shown) and if not maximized, is being moved by some unknown force until it is at the bottom right of the client screen space.

Specs: Acer TravelMate 5720, Intel Centrino Dual Core, 4GB RAM, ATI Radeon HD 2600 (newest driver installed, screen resolution and depth work fine), Synaptics touch pad, 64bit hardware and Ubuntu. The dist-upgrade was initially started from the 8.04 Gnome GUI. It then failed with the message "Could not install the upgrades: The upgrade aborts now. Your system could be in an unusable state. A recovery will run now." A recovery however was not run.

Now I've autoremoved-and-purged gdm and gnome completely, as well as compiz and co, I tried the xorg.conf.failsafe and the dpgk-reconfigure and reverted back to the xorg.conf.dist-upgrade backup that is the only xorg.conf that I could actually get to work. The problem persists, whether I run just startx or sudo startx, in the barest, gnome- and gdm-less scenario possible.

Update: by also autoremoving-and-purging metacity, the flashing-and-moving is gone, but still most windows don't show up.

---

### Post by roxority on 2008-11-04
> **roxority said:**
> 
or if it does (Firefox, Evolution, Nautilus, gedit) the window keeps flashing (i.e. quickly switches between it being shown and the desktop being shown / the window not being shown) and if not maximized, is being moved by some unknown force until it is at the bottom right of the client screen space.


Forgot to mention: those that show up and keep flickering and moving also never have a window border. Of all windows that show up, only the client / content area is ever shown (did I mention, in a flickering fashion?... :)

---

### Post by erikvw on 2008-11-16
i replied on your other post. check /usr/local/lib for any grahics libraries like cairo, glitz, pixman, ctemplate. i figure this is a conflict with cairo. remove the files and ubuntu won't use them

---

