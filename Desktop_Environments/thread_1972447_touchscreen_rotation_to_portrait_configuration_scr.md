---
title: "touchscreen rotation to portrait configuration scripts using QUANTA driver"
date: 2012-05-03
forum: Desktop Environments
---

### Post by yerb on 2012-05-03
Hi all.

I wanted to rotate touchscreen monitor (IIYAMA T2250MTS) to portrait mode but coordinates for cursor were still working in landscape mode. I have searched for exact answer but it was hard to find.

So, here it is:

Make the .sh scripts and run them. They will change the display rotation and set the proper cursor coordinates.

First list all input devices in terminal (ctrl+alt+t):
```
xinput -list
```it should list something like this:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; QUANTA OpticalTouchScreen                   id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=7    [slave  keyboard (3)]
    &#8627; Chicony USB Keyboard                        id=8    [slave  keyboard (3)]
    &#8627; Chicony USB Keyboard                        id=9    [slave  keyboard (3)]
```then make .sh scripts using gedit:

for landscape:
```
#!/bin/sh

#landscape (normal)

xrandr -o normal
xinput set-prop "QUANTA OpticalTouchScreen" --type=float "Coordinate Transformation Matrix" 0 0 0 0 0 0 0 0 0
```for portrait (left rotation):
```
#!/bin/sh

#portrait (left)

xrandr -o left
xinput set-prop "QUANTA OpticalTouchScreen" --type=float "Coordinate Transformation Matrix" 0 -1 1 1 0 0 0 0 1
```Don't forget to set chmod to execute for .sh files:
```
chmod 777 *.sh
```Run them like this:
```
./portrait.sh
```enjoy!

---

