---
title: "1680x1050 resolution on Dell 710m laptop with i810 (852GM/855GM)"
date: 2007-11-28
forum: Dell  Ubuntu Support
---

### Post by rostoker on 2007-11-28
Hi,

I have a Dell 710m running Ubuntu Feisty.  I just got a nice 22" Samsung SyncMaster 2232GW  LCD monitor which can support up to 1680x1050 resolution.  Does my graphics card support this?  Looks like my graphics card is (from log file) "Intel Corporation 82852/855GM Integrated Graphics Device".   If it can support it, how do I go about setting the right resolution?

Thanks!
Cam

---

### Post by jpl80 on 2007-11-28
I would plug it in and reboot and see what happens. 

To change the resolution you have to go into System - > Preferences - > Screen Resolution and see if the correct resolution is there.

report what happens.

---

### Post by rostoker on 2007-11-28
I've tried that...many times.  I've also tried most of the other suggestions on this forum for setting high resolution, like installing the 915resolution package, updating intel drivers, and editing the xorf.conf file to specify the 1680x1050 resolution (although I don't think I edited this file correctly).

Thanks,
Cam

---

### Post by sciurus on 2007-11-29
Try the X configuration in the thread linked to below. Then use xrandr to enable the LCD monitor.

[http://ubuntuforums.org/showthread.php?t=617934](http://ubuntuforums.org/showthread.php?t=617934)

---

### Post by serhito on 2007-11-29
> **rostoker said:**
> Hi,

I have a Dell 710m running Ubuntu Feisty.  I just got a nice 22" Samsung SyncMaster 2232GW  LCD monitor which can support up to 1680x1050 resolution.  Does my graphics card support this?  Looks like my graphics card is (from log file) "Intel Corporation 82852/855GM Integrated Graphics Device".   If it can support it, how do I go about setting the right resolution?

Thanks!
Cam

I have the same notebook but with 7.10 installed.
I am trying to do the same thing, but everytime i change the graphic card or any settings in Screens and Graphics menu, it will freeze on reboot just before loading the Gnome manager (whatever that is).

---

