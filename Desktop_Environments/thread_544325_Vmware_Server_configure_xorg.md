---
title: "Vmware Server configure xorg"
date: 2007-09-06
forum: Desktop Environments
---

### Post by heffo_j on 2007-09-06
Hi there,

I'm running XP as a guest but I am unable to get full screen mode to work. The following is the error message:

> Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode.

I have no xf86config file in that directory. I have an nvidia card which relies on xorg rather  than xf86config.

Any suggestions around this problem are welcome. Can I make a dummy XF86Config file and insert specs from xorg and then insert guest mode into the display section?

Regards
John

---

