---
title: "How do I execute xrandr commands on xserver startup?"
date: 2008-03-28
forum: Desktop Environments
---

### Post by double1116 on 2008-03-28
I have a need to execute commands to adjust xrandr 1.2 settings when the xserver starts up. Any idea where to do so?

/etc/X11/Xsession.d does not work, I do not believe DISPLAY is available yet and the 'xrandr' command needs it.

I don't want to use .xsession or the like in my home directory for I would like all users to have the same settings.

---

