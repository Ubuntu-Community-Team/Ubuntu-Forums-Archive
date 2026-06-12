---
title: "Pen/Ink Desktop in Unity"
date: 2011-05-07
forum: Desktop Environments
---

### Post by spamalam on 2011-05-07
I have a lenovo x201t tablet, which has the ultrabright/sunlight monitor with pen input only.

Looking through compiz I found that I can ink, which is great, however I can't get the pen to act like a pen.  How do i configure so when i touch the screen with the pen and press a button i can ink, and when i use the eraser it erases (without holding a key).

I couldn't find an obvious way to configure this behaviour

---

### Post by spamalam on 2011-05-07
I'd like the eraser button 1 to be erase, the stylus button 1 to ink, and the side button (button 2?) to clear:

jbriggs@jbriggs-x201t:~$ xinput list-props "Serial Wacom Tablet eraser"
Device 'Serial Wacom Tablet eraser':
        Device Enabled (127):   1
        Coordinate Transformation Matrix (129): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (247):     0
        Device Accel Constant Deceleration (248):       1.000000
        Device Accel Adaptive Deceleration (249):       1.000000
        Device Accel Velocity Scaling (250):    10.000000
        Wacom Tablet Area (270):        0, 0, 26312, 16520
        Wacom Rotation (271):   0
        Wacom Pressurecurve (272):      0, 0, 100, 100
        Wacom Serial IDs (273): 144, 0, 10, 0
        Wacom Capacity (274):   -1
        Wacom Pressure Threshold (275): 27
        Wacom Sample and Suppress (276):        2, 4
        Wacom Enable Touch (277):       0
        Wacom Enable Touch Gesture (278):       0
        Wacom Touch Gesture Parameters (279):   50, 20, 250
        Wacom Tool Type (280):  "ERASER" (264)
        Wacom Button Actions (281):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Debug Levels (282):       0, 0
jbriggs@jbriggs-x201t:~$ xinput list-props "Serial Wacom Tablet stylus"
Device 'Serial Wacom Tablet stylus':
        Device Enabled (127):   1
        Coordinate Transformation Matrix (129): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (247):     0
        Device Accel Constant Deceleration (248):       1.000000
        Device Accel Adaptive Deceleration (249):       1.000000
        Device Accel Velocity Scaling (250):    10.000000
        Wacom Tablet Area (270):        0, 0, 26312, 16520
        Wacom Rotation (271):   0
        Wacom Pressurecurve (272):      0, 0, 100, 100
        Wacom Serial IDs (273): 144, 0, 2, 0
        Wacom Capacity (274):   -1
        Wacom Pressure Threshold (275): 27
        Wacom Sample and Suppress (276):        2, 4
        Wacom Enable Touch (277):       0
        Wacom Hover Click (285):        1
        Wacom Enable Touch Gesture (278):       0
        Wacom Touch Gesture Parameters (279):   50, 20, 250
        Wacom Tool Type (280):  "STYLUS" (283)
        Wacom Button Actions (281):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
        Wacom Debug Levels (282):       0, 0

---

### Post by Favux on 2011-05-07
Hi spamalam,

The list-props shows you have your tablet pc on the Wacom X driver xf86-input-wacom.  I don't know the default version you have because I don't know what release of Ubuntu you are using.  It has to be at least Maverick because you have the CTM in your properties.

Have you tried using the stylus and eraser in programs designed for them?  Like Xournal, CellWriter, Gimp, Inkscape, and MyPaint, etc.?  To set up in Gimp and Inkscape see the screenshots near the bottom of the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

What you are asking for should be the driver defaults for the stylus and eraser.

---

