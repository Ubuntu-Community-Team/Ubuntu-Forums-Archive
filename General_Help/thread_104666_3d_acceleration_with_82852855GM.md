---
title: "3d acceleration with 82852/855GM"
date: 2005-12-16
forum: General Help
---

### Post by j0rge on 2005-12-16
hi i had mepis, dont remember what version.
But it used Xfree86. 3d acceleration support was out of the box, also in ubuntu but in mepis i had like 1000fps.
here i got 3062 frames in 5.0 seconds = 612.315 FPS
I thought it might be a problem with xorg.
In mepis(xfree86) cedega runs smooth, even better than windows(warcraft3).
but here it is unplayable, very slow.
But enemy territory runs fine and return to castle wolfenstein native(but trough cedega it runs very slow).
i have the latest i910 DRI installed.
any clue??

using a travelmate 4000 centrino 1.4
Intel Corp. 82852/855GM Integrated Graphics Device

thanks a lot for the help

---

### Post by kairu0 on 2005-12-22
Check for the "drm" module in your /etc/X11/xorg.conf file. It should be in there, along with the other modules, at the top of the file.

---

### Post by tafsen on 2006-01-07
Any sucsess?

---

