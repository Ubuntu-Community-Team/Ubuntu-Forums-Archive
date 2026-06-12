---
title: "Switch back to xfwm4 from beryl"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by leetrefz on 2007-09-15
after trying the excessive snazz of beryl, I'd like to go back to see what the transparency in xfwm4 is like. I select xfwm4 from beryl manager & quit beryl manager, click window manager tweaks, but it says "these setting cannot work with your current window manager (beryl)."
same if I try to go to window manager settings.

---

### Post by the yawner on 2007-09-15
Run the command: *xfwm4 --replace* to put enable xfwm4 (and disable beryl at the same time). Hope that helps.

---

### Post by leetrefz on 2007-09-16
```
lee@leemint-laptop:~$ xfwm4 --replace

** (xfwm4:16101): WARNING **: Another Window Manager is already running
lee@leemint-laptop:~$ 

```

weird, so easy to switch into beryl, not equally easy to switch out.

OK I just typed in sudo xfwm4 after startup & that worked.

---

