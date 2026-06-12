---
title: "Panel autohide speed settings deprecated"
date: 2008-06-08
forum: Desktop Environments
---

### Post by ja4509 on 2008-06-08
Has anyone found a way to make the panels in gnome autohide instantly. The settings for this have been deprecated as well as the minimum visible setting. This is driving me nuts to the point that I am about to switch desktops. 

If anyone has a work around other than hacking the src and compiling let me know.

---

### Post by p-w on 2008-06-10
Hi there, I has this problem too.  In the end the solution I found was to uncheck enable_animations and set unhide_delay to 0 in apps->panel->toplevels->top_panel_screen0 in gconf-editor.  I also set the auto_hide_size to 0 so the panel was properly hidden.

---

### Post by lexein on 2009-05-01
Gotta say, I do wish gconf-config was in the Control Center or Preferences menu already!   I'm liking the desktop again now that I've done the above.

---

