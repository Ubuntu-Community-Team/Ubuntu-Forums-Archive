---
title: "touch-screen"
date: 2010-06-06
forum: Desktop Environments
---

### Post by dmiller2 on 2010-06-06
I have connect a "LG FLATRON L1730SF" to a computer with Ubuntu server 10.04. Ubuntu-desktop is installed.

The touchscreen works but the X and Y axes is swapped.
I try to fix this with:

```
xinput set-prop --type=int --format=8 "EVTouch TouchScreen" "Evdev Axes Swap" 1
```
```
xinput set-int-prop "EVTouch TouchScreen" "Evdev Axis Inversion" 8 0 1
```
```
xinput set-prop --type=int --format=32 "EVTouch TouchScreen" "Evdev Axis Calibration" 57 1938 162 1979
```

There is no effect and there is no error output from the commands!

Thanks, David!

---

