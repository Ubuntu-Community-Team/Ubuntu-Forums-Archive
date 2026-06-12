---
title: "Change default login screen resolution?"
date: 2007-02-03
forum: Desktop Environments
---

### Post by Rippy on 2007-02-03
I have my screen resolution set to 1024x768, and it works fine. However, whenever I go to the login window, the resolution is way higher (1600x1200, the resolution Ubuntu defaulted to when I installed). How can I change its resolution to the same as my own desktop res?

(In Preferences/Screen Resolution, I made sure to set the resolution change to be for all users, but the login screen still doesn't change)

Thanks!

-Rippy

---

### Post by taurus on 2007-02-03
Perhaps you need to remove the high resolution that you don't want to use from /etc/X11/xorg.conf.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by maxwellcom on 2007-02-13
rippy,

[http://ubuntuforums.org/showthread.php?t=359310]("http://ubuntuforums.org/showthread.php?t=359310")

---

