---
title: "xrandr -o left gives black screen but LXQT Advanced monitor settings rotation works"
date: 2023-01-09
forum: Desktop Environments
---

### Post by elastufka on 2023-01-09
I recently installed Lubuntu 22.04.1 on an old tablet (Dell Venue 8 pro, 2GB RAM). When I try to use xrandr to rotate the display, only portrait modes work (normal and inverted). _Landscape modes (right/left) result in a black screen. _

Using **Preferences -> LXQT Settings -> Monitor -> Advanced -> Rotate** works to rotate the screen to the left or right. However, touch screen input is not similarly rotated, which is why I was trying xrandr in the first place, in order to rotate the touch input as well. 

Question 1 (the root of it all): How can touch input be rotated along with the display?
 Question 1a (presuming that can be solved): How can a desktop/keyboard shortcut to the Advanced monitor display rotation be created?

Failing that...

Question 2: What is the actual command line equivalent for what **Preferences -> LXQT Settings -> Monitor -> Advanced -> Rotate** is doing (so that I can do the same plus xrandr input rotation via a bash script)?

---

### Post by elastufka on 2023-01-09
Okay, found an answer to Question 2:

```bash
kscreen-doctor output.[Name_Of_monitor].rotation.right
```

left, normal, inverted works. However, the touch still doesn't rotate, and the xinput set-prop coordinate transforms I've tried don't seem to do the trick. So questions 1 and 1a are still outstanding, and I'll add Question 0: How can auto-rotate be enabled for a lubuntu tablet?

---

### Post by Holger_Gehrke on 2023-01-09
I don't use Lubuntu and I don't have a tablet with any Ubuntu flavour on it. That said, I can rotate the touchpad on my laptop by 90° counter-clockwise with
```

xinput --set-prop 'device-name-of-touchpad' "Coordinate Transformation Matrix" 0.0 1.0 0.0 1.0 0.0 0.0 0.0 0.0 1.0

```
by 180° with
```

xinput --set-prop 'device-name-of-touchpad' "Coordinate Transformation Matrix" -1.0 0.0 0.0 0.0 -1.0 0.0 0.0 0.0 1.0

```
by 270° with
```

xinput --set-prop 'device-name-of-touchpad' "Coordinate Transformation Matrix" 0.0 -1.0 0.0 -1.0 0.0 0.0 0.0 0.0 1.0

```
and back to 0° with 
```

xinput --set-prop 'device-name-of-touchpad' "Coordinate Transformation Matrix" 1.0 0.0 0.0 0.0 1.0 0.0 0.0 0.0 1.0

```

To get the device-name for your touchscreen look at the output of 'xinput --list'

Holger

---

### Post by elastufka on 2023-01-10
I eventually got that to work, the script I had was trying a more simple mirroring over the full transformation matrix so I guess that is where it came from.

---

