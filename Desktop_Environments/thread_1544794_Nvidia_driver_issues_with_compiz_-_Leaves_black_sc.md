---
title: "Nvidia driver issues with compiz - Leaves black screen"
date: 2010-08-03
forum: Desktop Environments
---

### Post by gtpitch on 2010-08-03
Ok so I've been using Ubuntu for a while but I'm not real familiar with it so please make sure to spell out any fixes... thanks :)

I recently upgraded to Ubuntu 10.04 Lucid and am having trouble enabling desktop effects.  I'm using the latest NVIDIA driver and have checked that it is installed, active, and in use.  

When I enable desktop effects it says searching for available drivers and then the screen just goes black.  I'm able to kind of guess where the buttons are and set it back to normal so that I can see the screen again.

For full disclosure I had an NVIDIA card that was failing on me and I replaced it with an ATI card.  I got frustrated that it wasn't working correctly so I got a new NVIDIA card.  I have a GEFORCE 9500 1gb card I believe.  I think I wiped out all the old ATI driver information though.

Anyway... thanks for you help ahead of time.

Output of compiz-check (not sure how to fix the errors)

> Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 


---

### Post by gtpitch on 2010-08-03
Bump?

---

### Post by gtpitch on 2010-08-03
Nevermind.

Through some fluke - I uninstalled and reinstalled the drivers (again) and this time it worked.  Go figure.

---

