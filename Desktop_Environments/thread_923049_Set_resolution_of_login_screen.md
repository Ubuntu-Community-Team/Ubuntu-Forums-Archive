---
title: "Set resolution of login screen?"
date: 2008-09-17
forum: Desktop Environments
---

### Post by kooldino on 2008-09-17
Searched around and couldn't quite find an answer...How can I set the resolution of my KDE 3 login screen that loads when I boot the machine?

Note: I'm running 8.04

---

### Post by Denestria on 2008-09-18
The virtual resolution in /etc/X11/xorg.conf should fix it.
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        Defaultdepth    16
        SubSection "Display"
                Depth   16
                **Virtual 1024    768**

```

**or is it /etc/X11/XF86Config in KDE2?

---

### Post by kooldino on 2008-09-18
**edited first post - Sorry, typo...KDE 3 is what I'm running.

I'll give that a whirl tonight.

---

