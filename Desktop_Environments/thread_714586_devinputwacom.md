---
title: "/dev/input/wacom"
date: 2008-03-04
forum: Desktop Environments
---

### Post by jane21 on 2008-03-04
OpenOffice froze and I had to do a hard shutdown of Kubuntu.  Ever since, I've seen the following errors when I try to start KDE (Ubuntu boots to the command line fine):

(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
      No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
      No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
      No such file or directory.
Error opening /dev/input/wacom : No such file or directory
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

When booted to the recovery console, I managed to get KDE to boot once, but then I rebooted and it went back to its same prior state of brokenness.

It's pretty evident to me at this point that some part of KDE is effed up, but I'm at a loss as to where the problem is.

---

