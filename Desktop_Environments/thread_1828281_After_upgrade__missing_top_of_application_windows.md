---
title: "After upgrade  missing top of application windows"
date: 2011-08-18
forum: Desktop Environments
---

### Post by mashedbear on 2011-08-18
Hi
I am having problems with the display of all application windows after upgrading to 11.04. The problem is present in both Unity and 'Classic'

The top of application windows appear behind what used to be called the launcher (ie. the panel at the very top of the screen). Application windows can not be resized to fill the full screen either - so I have about 3cm of space at the bottom of the screen that application windows' can't go into and about 12cm on the right of the screen too. 

3 example screen shots (in classic mode) attached .

My system is:
Release 11.04 (2.6.38-10-generic onx86_64)
Nvidia Graphics card GeForce 9400 GT
Am using CompizConfig (CompizConfig Settings Manager 0.9.4)
Screen resolution is 1440 x 900

Thanks for advice and help

---

### Post by mashedbear on 2011-08-18
Additional information to add to this - as I am finding that not all applications are behaving the same. 

Chrome & Shotwell seem to behave correctly - i.e. filling the whole screen and have application menus plus close and resize icons in the top bar.

Libre Office just seems to live in the middle of the screen and can't be resized. but does have an application menu. 

However terminal, firefox, most system setting windows all behave as per previous post. 

Have added another screen shot showing libre office writer in the foreground with shotwell in the background. This time using Unity interface.

---

### Post by eric-yorba on 2011-08-19
Does this happen all the time?  I've seen something like this occurring where a reboot fixed it. Another thought -- which graphic driver are you using?  The open source nvidia driver, or the binary one?

You might already know this, but if a window is "stuck" under something  or off the screen where you can't drag it, you can hold down the Alt key  and drag any part of the window to move it around.  (Not the best solution, obviously.)

---

### Post by mashedbear on 2011-08-19
Thanks - I think I have solved this be resetting unity

```
unity --reset
```

---

