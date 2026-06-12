---
title: "problems with compiz"
date: 2007-11-17
forum: Desktop Environments
---

### Post by drewcoon on 2007-11-17
Hello, I've been playing around with compiz trying to get it to work, but i'm having problems.

If I go to System > Preferences > Desktop Effects, and press the "Enable effects" button, I get a "Desktop effects could not be enabled" error message.

Here's my terminal output when I type "compiz":

-
/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
-

I've tried doing the suggested --replace, and all that happens is the screen flashes for a second and I get this output:

-
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
-

I've been looking at other topics about compiz problems and i'm still stumped... I'm running an ATI radeon XPress 200 graphics card (with working driver), if that's any help. :)

---

### Post by x64Jimbo on 2007-11-17
By working, do you mean that it displays things on the screen, or do you mean that you have installed the binary driver from ATI and verified that it supports 3D rendering?

---

### Post by drewcoon on 2007-11-18
I have the ATI driver (downloaded from the ATI site) working as a restricted driver, is that still good?

The driver is making a difference for sure, the more intense screensavers used to be really choppy, but they aren't now. Is it not properly set up?

---

### Post by x64Jimbo on 2007-11-18
Are you using driver version 8.42.3? This version enables AIGLX support. It should be available [here.]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")
It's not in the repos for Gutsy because by the time it was released, Gutsy was in feature freeze.
There's a discussion about this driver [here.]("http://ubuntuforums.org/showthread.php?t=588498")

---

