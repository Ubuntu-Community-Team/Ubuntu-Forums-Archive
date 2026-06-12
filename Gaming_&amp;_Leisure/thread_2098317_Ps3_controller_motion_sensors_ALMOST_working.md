---
title: "Ps3 controller motion sensors ALMOST working"
date: 2012-12-26
forum: Gaming &amp; Leisure
---

### Post by AR_Kozz on 2012-12-26
controller tilted right, but level front/back (no buttons pressed or sticks moved)
> Axes:  0: -1261  1: -1738  2:   774  3:  -512  4:     0  5:     0  6:     0  7:     0  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 **23: 31072 24:  1272** 25: 32767 26:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:off 17:off 18:off ^Z
[13]+  Stopped                 jstest /dev/input/js0

tilted forward, but level left/right
> Axes:  0: -1261  1: -1738  2:   774  3:  -512  4:     0  5:     0  6:     0  7:     0  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 **23:  1129 24: 32767** 25: 21860 26:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:off 17:off 18:off ^Z
[14]+  Stopped                 jstest /dev/input/js0

Axis 23 is  left/right, and 24 is forward/backward!

Axis 25 is another motion-sensing axis, but it doesn't seem to make any sense, or is broken on my controller.

All three are corrected by jscal from their native values of about -4000 to 4000, with axis 23 reversed.

They work easily with games, but games don't seem to recognize them as axes the way jstest does. I've tried, so far, (both with and without jscal corrections), assigning them in flightgear, supertuxkart, neverball and
torcs. In neverball, they almost work, but only tilt the field a tiny bit. 

I'm gonna get this motion sensor working in neverball, dammit. Neverball was made for this controller. I'm sure it's inputting data differently from the other axes, I just need to know how.

---

### Post by AR_Kozz on 2012-12-26
I figured out axis 25. It is an up-down acceleration sensor.

It returns a zero any time the controller is tilted more than about 45 degrees in any direction, including when it's upside down. Less than 45 degrees, right side up, it returns a negative from 0 to about -1500, scaled to how much it's tilted. Upside down it returns positive from 0 to about 5000.

When jerked either up or down, the magnitude increases, to a max of pretty near 32767, as far as I can tell.

---

