---
title: "Dual monitors with laptop - &quot;primary screen&quot; issue"
date: 2010-04-06
forum: Desktop Environments
---

### Post by Karmic650 on 2010-04-06
Hey,

So i recently started using dual monitors using nVidia's "twin view".  My monitor is on the left, and my laptop screen is on the right.  Originally I had it the other way around, but I found it important for the monitor to be at the (0,0) position so that full-screen flash videos would go to the monitor (the nicer screen).

Similarly, I like for my monitor to be the primary screen since it is the nicer screen of the two.

The problem is, if I disconnect my monitor (like if I'm not home and I'm using my laptop on the go), my desktop becomes pretty much unusable.  The computer doesn't recognize that I'm not trying to use a monitor any more, so I just get the "right side" desktop.  No tool bars, no icons, etc.

Any suggestions for fixes while keeping my monitor as the primary screen?

(Note:  when my laptop screen was the primary screen, whenever I didn't have the monitor connected, the computer WOULD recognize it, and scale my desktop background accordingly)

(Ubuntu Karmic)

---

### Post by asmoore82 on 2010-04-06
The is the standard answer, but with nVidia your mileage may vary...
see the manual for xrandr: ```
man xrandr
```
the fix may be something as simple as ```
xrandr --auto
```

---

### Post by Karmic650 on 2010-04-07
no luck with

xrandr --auto

or 

sudo xrandr --auto
Interestingly, when I tried to simply make my laptop screen the primary screen, it messed up my top and bottom tool bars.  It's probably something to do with my monitor having a higher resolution than my laptop screen.  Either the top or bottom bars of on my laptop screen would be off center when my primary screen is my laptop screen.

---

### Post by Karmic650 on 2010-04-14
i think that instead of trying to get the screens to "auto-switch" primary screens when the monitor is not attached, I am just going to make my laptop my primary screen.

However, I am still having that toolbar issue.  Basically, my laptop screen is set +1280 to the right, and 224 pixels down.  My toolbar is in the weirdest place.  It isn't at the top of the laptop screen, but like, 224 pixels down from the top of the screen.

If i just set it to +1280 pixels to the right and 0 pixels up/down, my bottom toolbar gets messed up.

---

### Post by Karmic650 on 2010-04-14
UPDATE:

Found a temporary fix.  I just removed the auto-hide feature of the top toolbar.  There's still "empty space" above my toolbar though, that is my mouse doesn't stop at the top of the screen.  I guess that's just the way "twinview" works... it stretches the highest resolution monitor and makes the rest empty space.

---

### Post by nroose on 2010-05-04
I am having a potentially related issue.  I have dual monitors, and I am fine with having my toolbars on my laptop screen, but if I set them as autohide, the one that is not lined up with the edge of the external monitor keeps hiding an showing when I try to mouse over it.  It is like it can not decide where it is...

---

