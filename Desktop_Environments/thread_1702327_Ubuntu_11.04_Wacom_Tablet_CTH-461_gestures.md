---
title: "Ubuntu 11.04 Wacom Tablet CTH-461 gestures"
date: 2011-03-07
forum: Desktop Environments
---

### Post by chaemil on 2011-03-07
hi i have a minor problem with the wacom tablet CTH-461. the gestures and mouse sensitivity with the finger touch is too sensitive... i mean that the mouse is moving really fast and you have to be very careful when you are pinching / zooming with your fingers...

and second question. where i have to submit this "bug" bcs the 11.04 is still alpha and i want the tablet to be in final release as much as possible supported.

thanks ;)

---

### Post by Favux on 2011-03-07
Hi chaemil,

Try adjusting these parameters by entering these commands in a terminal:
```
xinput set-prop "Wacom BambooFun 2FG 4x5 Finger touch" --type=float "Device Accel Constant Deceleration" 1.250000
xinput set-prop "Wacom BambooFun 2FG 4x5 Finger touch" --type=float "Device Accel Adaptive Deceleration" 1.150000
xinput set-prop "Wacom BambooFun 2FG 4x5 Finger touch" --type=float "Device Accel Velocity Scaling" 1.150000
```
The default is 1.000000, those are the values I'm currently using.  The most important one is "Device Accel Constant Deceleration".  Use your "device name" for touch from *xinput list*.

Bug submissions go to LaunchPad.  There should be a sticky on how to submit on the Natty development forum.

---

### Post by chaemil on 2011-03-12
Thanks now it works a lot better. How can i display all the parameters that i can set? i would like to set the finger touch/click sensitivity if it's possible.

---

### Post by Favux on 2011-03-12
To see the Wacom parameters use:
```
xsetwacom list parameters
```
Not all of them apply to every input tool.  Use the get command with the parameter name to check, see *man xsetwacom*.

For xinput use:
```
xinput list-props "device name"
```

Not sure what you mean by sensitivity but for touch Threshold would be 27 by default.

---

