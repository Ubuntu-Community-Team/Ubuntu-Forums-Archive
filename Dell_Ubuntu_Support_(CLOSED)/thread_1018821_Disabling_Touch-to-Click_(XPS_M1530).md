---
title: "Disabling Touch-to-Click (XPS M1530)"
date: 2008-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zephyrcat on 2008-12-22
I can't stand the touch-to-click feature on any laptop, so when I first got my XPS M1530, I went to System > Preferences > Mouse and disabled it. I have since had to resinstall from the DVD that I burnt when I first got the computer. I noticed the problem again today, but there is no longer a trackpad tab under Mouse preferences. I don't know if this has been the case since the reinstall or not.

How can I get the trackpad options back?

Thanks!

---

### Post by spongypants23 on 2008-12-22
Try adding the following line to xorg.conf, in the area that appends to the trackpad.

```
Option "ClickTime" "0"
```



ALTERNATIVELY:

Install the gsynaptics application,
```
sudo apt-get install gsynaptics
```

Add the following line to the touchpad area of xorg.conf
```
Option "SHMConfig" "True"
```

Restart the X server, and run gsynaptics.

This tends to be a bit iffy and not work all the time.

---

### Post by zephyrcat on 2008-12-22
Thanks. That does not seem to eliminate touch-to-click, but it makes it much harder to do, so it doesn't happen accidentally. Thank you.

---

