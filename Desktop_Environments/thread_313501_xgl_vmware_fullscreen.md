---
title: "xgl vmware fullscreen"
date: 2006-12-06
forum: Desktop Environments
---

### Post by hrabeX on 2006-12-06
When I try to switch to fullscreen, vmware workstation gives me error:

Unable to find an appropriate host video mode.
Adding the guest mode to the 'display' subsection of the 'screen' section of your /etc/X11/XF86Config and restarting X is likely to help.

Failed to switch to full screen SVGA mode.

Any ideas, please?

---

### Post by galego on 2006-12-06
yeah it will not go to full screen while running XGL. what you can do in order for it to be full screen is this:

from the view button on the vmware window uncheck "tabs", and then check "quick switch". also check "autofit window" and "autofit guest", make sure you install vm tools and you are done. now you can run XGL/compiz or beryl and have a full side of the cube just for vmware (XP or whatever) then just use samba to network the virtual machines to the host.

---

### Post by dacool25 on 2007-04-02
When i do this, i still get the scroll bars on the right and bottom of the screen.  Does anyone know how to fix this?

---

### Post by samson85 on 2007-04-06
I think this might solve your problem:

[http://forum.beryl-project.org/viewtopic.php?f=39&t=2702&p=16228&hilit=fullscreen](http://forum.beryl-project.org/viewtopic.php?f=39&t=2702&p=16228&hilit=fullscreen)

---

