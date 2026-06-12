---
title: "Configuration missing under &quot;system&quot; menu"
date: 2005-06-15
forum: Desktop Environments
---

### Post by aulou05 on 2005-06-15
Hi all;

It seems that I've somehow lost all of the gnome applets for configuration.  When I open up the "system" menu on the panel---just after applications and places---there are two spots that now have folder icons and no text.  There aren't any entries in the submenus, so there is a little square that comes up, just a few pixels in area.

I'm not sure why they went away.  I don't remember installing/uninstalling any software since I noticed the problem, but I was using the menu editor to add an entry to the applications menu.  It's the smeg editor mentioned in the ubuntu-guide.

Any ideas? Thanks!

--
Lou.

---

### Post by aulou05 on 2005-06-15
Well, I seem to have found the problem.  I went on over to freedesktop.org and started reading the menu standard, then started pouring through the xdg config files.

Anyway, smeg creates a .config under your home directory.  I'm not sure what I messed up using the editor, but the local modification didn't merge correctly, and instead it overwrote the Preferences and Administration menus.

I just removed the .config directory, and I got the menus back again. Looks like I'll just leave editing menu's until the next gnome release.  That or hack at the files manually.

---

