---
title: "Unity and xrandr resolution problem"
date: 2011-08-04
forum: Desktop Environments
---

### Post by Earl_Maroon on 2011-08-04
[FONT="Arial"]I damaged my laptop and the right edge of the screen has a mass of dead pixels. So, in order to be able to see the right edge of anything on screen I have used xrandr to change my resolution so there is a black border to the right and bottom of the desktop that contains the dead areas of my screen. This works just fine except that Unity doesn't scale to fit. The panel and launcher are the same sizes as before and go off the screen, meaning I can't see the clock or the recycle bin.

How can I make Unity aware of my screen resolution so it fits?

(I have tried [FONT="Courier New"]unity --replace[/FONT] but that does not work.)[/FONT]

---

### Post by iveand on 2011-12-20
I have the same problem.  I am not sure if you are still checking this thread or not.  If so, how did you use xrandr to only avoid the right and bottom?  For me, I did the following:

```
cvt 1400 900
```

output:

```
 # 1400x900 59.96 Hz (CVT) hsync: 56.01 kHz; pclk: 103.50 MHz
Modeline "1400x900_60.00"  103.50  1400 1480 1624 1848  900 903 913 934 -hsync +vsync
```

Then, ran the following command with the above info:

```
xrandr --newmode "1400x900_60.00"  103.50  1400 1480 1624 1848  900 903 913 934 -hsync +vsync
```

finally, added this new mode to the monitor (LSVD1)

```
xrandr --addmode LVDS1 1400x900_60.00
```

Then I could select this new mode.  Problem is that it is "centered", not "left justified" as you mention.  So, wondering how you did that.  Also, the resolution is now "fuzzy".  So, instead of 40 px on left being dropped, it sort of "fuzzies and centers" the whole thing.

---

