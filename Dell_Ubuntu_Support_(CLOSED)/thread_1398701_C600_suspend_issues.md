---
title: "C600 suspend issues"
date: 2010-02-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drc330 on 2010-02-04
I'm running Ubuntu 9.10 on my Dell Latitude C600 and everything works great except... suspend.  Shut down is fine, hibernate is fine.  Suspend either doesn't complete its routine or when it does, will not restore.  I searched around and tried a number of fixes but nothing helped.  

What did work is using uswsusp but it only works from a command prompt.  I've tried changing the suspend command in the file:
usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
to use s2ram but for some reason it doesn't work when I close the lid or select suspend from the shut down menu.

The s2ram command works from an icon I've created for the desktop but it would be nice if would work when I closed the lid.

Maybe I'm not editing the right file?
Thanks in advance!

---

