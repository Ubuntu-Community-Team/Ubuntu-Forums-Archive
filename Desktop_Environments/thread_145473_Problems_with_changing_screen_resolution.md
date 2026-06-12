---
title: "Problems with changing screen resolution"
date: 2006-03-16
forum: Desktop Environments
---

### Post by JW9 on 2006-03-16
My monitor needs a screen resolution of 800x600 to work properly.  It seems the only time I can change it from 640x480 is with a new install.  I have done that several times and it works right untill I shut it down, and upon startup it is locked in on 640x480 again and can't be changed.  I need help with this problem. Thank you.

---

### Post by frodon on 2006-03-16
You should need to add the horizontal and vertical refresh rates parameters of your screen in your xorg.conf file, then restart your xserver (Ctrl+Alt+Backspace).
Details here : [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

