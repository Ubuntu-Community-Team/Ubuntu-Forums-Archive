---
title: "lost panels"
date: 2009-03-12
forum: General Help
---

### Post by sekani on 2009-03-12
i am using ubuntu 8:10. when i open firefox it cover the whole screen and i lose sight of the top panel (applications,places etc ) and bottom panel ( garbage bin etc ). therefore i can't use anything on those panels until i close firefox down. any suggestions to fix this? thanks

---

### Post by robert.rankin.jr on 2009-03-12
I've had this problem too, but don't suffer it any more because it went away. However, other people have had success with this fix:

press alt+f2, type in:

> ```
firefox -safe-mode
```

Select "Reset toolbars and controls" then click Continue in Safe Mode.

Then, restart and hopefully it will work. If not, a temporary work around is to press F11 twice (the first time putting it into its real full screen mode, the second returning it to normal mode).

Robert

---

### Post by sekani on 2009-03-13
It is still not working in safe mode but is ok when i use f11 twice,this seems strange,anyway for the time being i am happy to use f11....thanks for your help

---

### Post by firefly2442 on 2009-03-14
F11 is turning fullscreen mode on and off.  So you're saying it always starts up fullscreen no matter what?

---

### Post by zero777zero on 2009-03-14
system menu->preferences-appearance->visual effects: none

---

### Post by cubeist on 2009-03-14
you could try typing *about:config* into your address bar,

then search for *fullscreen*

and see if your fullscreen opts are different from mine...
```
browser.fullscreen.autohide;true
browser.fullscreen.animateUp;1
```

Not sure if this will help, just guessing...

---

### Post by sekani on 2009-03-14
thanks Zero your suggestion worked...problem solved. thanks everyone for your help.

---

