---
title: "GNOME problems in UbuntuStudio Hardy"
date: 2009-08-31
forum: Desktop Environments
---

### Post by flatko on 2009-08-31
Hi all.
I've installed Hardy from the Ubuntu Studio DVD. It runs pretty well, but Gnome has some problems that I can't solve.

First - keyboard applet don't seem to remember the settings. There are 2 Bulgarian layouts, "phonetic" and "bds". I use the "phonetic" one, but every time I log in, it switches to "bds". When I open the settings dialog, it says that the "phonetic" is selected, but the layout is actually "bds", so I have to remove it and add it again every time I turn the PC on...

Second - Volume control don't remember the window size and position. It forgets them at the moment I close the applet. I've tried deleting the .gnome2 dir, but it still forgets the settings. Tried also setting it through gconf-editor - it changes everything, but when i close gconf, it forgets it again.

I guess there are some permission problems?

---

### Post by flatko on 2009-09-25
Solved.
I found that gnome gets the xorg.conf settings, not its own. So I,ve changed the settings from /etc/X11/xorg.conf and it's working.

Volume control still doesn't remember its size and position.

---

