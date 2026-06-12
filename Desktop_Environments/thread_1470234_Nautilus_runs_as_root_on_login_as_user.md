---
title: "Nautilus runs as root on login as user"
date: 2010-05-02
forum: Desktop Environments
---

### Post by linfidel on 2010-05-02
I recently installed Lucid Lynx fresh, and everything was working fine.  Then, while doing some tweaks, I created a menu item for a root Nautilus starter, adding gksu to an existing menu item, the one for "File Browser", so it said "gksu nautilus --no-desktop --browser %U".  When I tried to run it, it didn't work, didn't prompt me or anything.  But next time I started up, it displayed the gksu dialog for my passwork, and my desktop was not mine, it was the root desktop.  My home directory is still correct, and my login is not root, but I can't use my desktop.

If I cancel from the opening dialog, I still get the root desktop, but I can't interact with it at all.

I've looked everywhere I know, but can't find anything to change this.  I guess I need to learn about the startup process, but I've wasted a lot of time so far, so I'm hoping someone can point me in the right direction.

---

### Post by linfidel on 2010-05-02
After screwing around with Nautilus and the configuration editor settings, something seemed to persuade Nautilus to realize that I didn't want to see root's desktop.  I don't know exactly what, if anything, I did to change it.

The only weird after-effect is that I was unable to run Nautilus from either a shortcut or from gnome-do unless I added a path after the command.  So, instead of "nautilus", I had to put "nautilus /", or "nautilus Desktop".  That's OK with me, but it took a while before I lucked into figuring that out.

---

