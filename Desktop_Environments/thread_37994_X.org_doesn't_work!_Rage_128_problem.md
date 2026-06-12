---
title: "X.org doesn't work! Rage 128 problem"
date: 2005-05-29
forum: Desktop Environments
---

### Post by y4r0ze on 2005-05-29
When I first installed Ubuntu, the video driver was set to ati and X couldn't start. I've did then run xorgconfig to change the X settings and it didn't worked then either, the video driver was then changed to r128 insted of ati.
I've googled some and found some help that said that i should use:

Option "UseFBDev" "True"

But it didn't work either...here's some of my errors:

Symbol xfDoEDID_DDC2 from module /usr/X11R6/lib/modules/drivers/r128_drv.o is unresolved 

Symbol xf86SetDDCproperties from module /usr/X11R6/lib/modules/drivers/r128_drv.o is unresolved 

Symbol xf86ForceHWCursor from module /usr/X11R6/lib/modules/drivers/r128_drv.o is unresolved 

Symbol xf86ForceHWCursor from module /usr/X11R6/lib/modules/drivers/r128_drv.o is unresolved

---

### Post by y4r0ze on 2005-05-29
Doesn't atleast someone know the problem?

---

