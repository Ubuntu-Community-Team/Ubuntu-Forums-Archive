---
title: "Gutsy Compiz Fusion window borders do not work"
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by shinikaru on 2007-12-06
shane@shane-macbookpro:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

-- This gives me no windows and my system is unusable until I do "metacity --replace" or "kwin --replace" ... that is, if a terminal is in sight. I can't move/switch windows or even alt-tab.

compizconfig-settings-manager is already the newest version.
compiz is already the newest version.
compiz-core is already the newest version.
compiz-fusion-plugins-main is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
compiz-kde is already the newest version.
compiz-plugins is already the newest version.
libcompizconfig-backend-gconf is already the newest version.
libcompizconfig0 is already the newest version.

This is running on  kubuntu Gutsy.. what am I doing wrong?

---

### Post by macaholic on 2007-12-06
it looks like compiz is crashing on load alltogether, what kind of graphics card do you have?

---

### Post by shinikaru on 2007-12-06
ATI x1600 Mobility Radeon

I switched to gnome and ran compiz --replace and.. no windows. But funny enough - I went to the top left corner - And it zoomed out and displayed two desktops. 

I'm pretty sure this is a Compiz feature? Still, no windows, and for some reason when I do metacity --replace I get this horrible horrible slowdown.

---

