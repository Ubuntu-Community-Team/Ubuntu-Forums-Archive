---
title: "Dual monitors, different resolutions, no advanced graphics features/compiz, ATI video"
date: 2010-09-19
forum: Desktop Environments
---

### Post by nihilion on 2010-09-19
I'm running Ubuntu 10.04 on 64-bit with the following configuration:

ATI Radeon 4850 HD graphics board with dual monitors,
 24' monitor @ 1920x1080
 20' monitor @ 1680x1050
Proprietary drivers installed.

I've managed to get both monitors to display at native resolution and gain basic multi-monitor features (like dragging windows from screen to screen) using the Xinerama mode. 

However, I'm unable to use any advanced visual effects or compiz. When I attempt to select normal or advanced visual effects in appearance settings, I get the message "The composite extension is not available". 

Is there anything I can do about this?

Thanks,
Nick

---

### Post by nihilion on 2010-09-30
bump

---

### Post by aarons6 on 2010-10-01
what video card do you have??
nvidia uses something called twinview and ATI uses something called big desktop..

you shouldnt be using xinerama unless you have a very old video card or one built in thats not supported very well.

---

### Post by nihilion on 2010-10-03
Thanks for the reply! I disabled Xinerama, so now compiz and advanced graphics features work, but I can't seem to enable Big Desktop. I tried running through a tutorial I found here:[http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)

But unfortunately, I get an error message that reads:

Error: Options, e.g. --dtop and --desktop-setup, are not supported when RandR 1.2 is enabled!
Error: pair mode is not supported when RandR 1.2 is enabled!

I have no idea what this means. Can anyone help?

---

