---
title: "Small font sizes in Gnome via VNC"
date: 2008-01-11
forum: Desktop Environments
---

### Post by bradsucks on 2008-01-11
When I VNC into a separate Gnome desktop, my desktop fonts are too small. When I check in System -> Preferences -> Fonts they're all set the same as my :0 desktop that looks fine. How do I fix this?

Backstory:  I wanted an alternate VNC desktop so I set up Xrealvnc on :1 and edited /home/me/.vnc/xstartup to be:

#!/bin/sh

unset SESSION_MANAGER
exec /etc/X11/Xsession

If I increase the font sizes in the preferences, it increases the fonts in :0 as well. If I increase the DPI in Fonts -> Details it only increase :0 and doesn't affect :1.

I'm pretty new to this whole multiple desktop jazz so I hope this makes sense, thanks!

---

