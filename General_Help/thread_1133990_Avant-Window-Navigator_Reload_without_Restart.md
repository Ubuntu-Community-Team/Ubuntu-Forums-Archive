---
title: "Avant-Window-Navigator Reload without Restart?"
date: 2009-04-23
forum: General Help
---

### Post by codeseer on 2009-04-23
I'm trying to figure out how to get Avant-Window-Navigator to reload the settings (the icon layout) from the ~/.gconf/apps/avant-window-navigator/window_manager/%gconf.xml file, without having to restart. I have tried refreshing in the AWN interface and killing all the AWN related processes, then relaunching AWN.

I don't think this has anything to do with it, but I should note that due to some weird bug in AWN, I read-only protect the %gconf.xml file when I'm not manually editing it to keep AWN from resetting it and messing it up.

I added a new entry to the file; I would think if it is even making a read at all to that file when I killall and restart it, that it would display the new icon, but it doesn't. I looked at the man pages and it doesn't have anything of use in that and also used the --help-all parameter with AWN and nothing there is of help.

I was hoping somebody else had experienced this and figured out how to reload it on demand.

---

### Post by codeseer on 2009-04-23
Bumpity bump-bump!

---

### Post by codeseer on 2009-04-23
Bumpilicious!

---

### Post by codeseer on 2009-04-24
Bump.

---

