---
title: "I can't enable the restricted nVidia drivers in Gusty"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by Da-Bomb1 on 2007-10-20
When I try to enable the restricted nVidia drivers, it comes up with a dialog box saying, "The software source for the package 'nvidia-glx-new' is not enabled", and when I close the box, it says to restart the computer when the new graphics driver is active, but nothing installed and nothing changes after restarting the computer.  I have an nVidia GeForce 6200 card in the computer at the moment.
Note: I've tried doing this from the Visual Effects menu under Appearance Preferences and under the Restricted Drivers Manager.

---

### Post by icic on 2007-10-20
hi there!

i had this exact same problem when i installed gutsy, and the problem is this:
not all the software sources are enabled by default, and the nvidia driver is not on the default ubuntu source.

so go to System->Administration->Software Sources

under the "ubuntu software tab", make sure that the "proprietary drivers (restricted)" check box is ticked.


so if it was already ticked, then im sorry but i don't know what your problem is....


hope this helps!

---

