---
title: "Ubuntu 13.10 and how enable 3-fingers in Synaptics TouchPad ?"
date: 2014-02-28
forum: Desktop Environments
---

### Post by cvgaviao on 2014-02-28
Hi, I recently arrive from years of MacOS use and would like to add 3 finger workspace swipe.
My notebook is a Dell 15R with a Synaptics touch pad and ELAN Touchscreen.

Touchscreen is working out-of-box for:
[COLOR=#000000][FONT=verdana]1 finger press and drag to move window[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]3 finger touch to show grab handles[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]4 finger swipe left/right to reveal launcher (if the dock autohide is enabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]4 finger tap to open dash[/FONT][/COLOR]

Touchpad is working for two-finger scrolling.

I have tried ginn, but it is not working with 13.10 (there is a opened bug already).

Could someone point me to updated info on how to enable 3-fingers in my touchpad ?


$ xinput list-props 13
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (264):    1
    Device Accel Constant Deceleration (265):    2.500000
    Device Accel Adaptive Deceleration (266):    1.000000
    Device Accel Velocity Scaling (267):    12.500000
    Synaptics Edges (288):    1766, 5380, 1642, 4520
    Synaptics Finger (289):    25, 30, 0
    Synaptics Tap Time (290):    180
    Synaptics Tap Move (291):    236
    Synaptics Tap Durations (292):    180, 180, 100
    Synaptics ClickPad (293):    0
    Synaptics Middle Button Timeout (294):    75
    Synaptics Two-Finger Pressure (295):    282
    Synaptics Two-Finger Width (296):    7
    Synaptics Scrolling Distance (297):    107, 107
    Synaptics Edge Scrolling (298):    0, 0, 0
    Synaptics Two-Finger Scrolling (299):    1, 1
    Synaptics Move Speed (300):    1.000000, 1.750000, 0.037237, 0.000000
    Synaptics Off (301):    0
    Synaptics Locked Drags (302):    0
    Synaptics Locked Drags Timeout (303):    5000
    Synaptics Tap Action (304):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (305):    1, 1, 0
    Synaptics Circular Scrolling (306):    0
    Synaptics Circular Scrolling Distance (307):    0.100000
    Synaptics Circular Scrolling Trigger (308):    0
    Synaptics Palm Detection (309):    0
    Synaptics Palm Dimensions (310):    10, 200
    Synaptics Coasting Speed (311):    20.000000, 50.000000
    Synaptics Pressure Motion (312):    30, 160
    Synaptics Pressure Motion Factor (313):    1.000000, 1.000000
    Synaptics Resolution Detect (314):    1
    Synaptics Grab Event Device (315):    1
    Synaptics Gestures (316):    1
    Synaptics Capabilities (317):    1, 0, 1, 1, 1, 1, 1
    Synaptics Pad Resolution (318):    68, 44
    Synaptics Area (319):    0, 0, 0, 0
    Synaptics Noise Cancellation (320):    8, 8
    Device Product ID (253):    2, 7
    Device Node (254):    "/dev/input/event6"

---

### Post by el_garicimo on 2014-03-25
I'm having the same problems, on a Dell XPS 12 9Q33...any progress?

Edit: Looks like it may be an upstream bug...at least for me, touchscreen recognition is making the computer think the touch pad is normal

[http://libcoding.wordpress.com/2013/11/02/issue-with-touchpad-in-ubuntu-13-10-in-xps-12/comment-page-1/#comment-22](http://libcoding.wordpress.com/2013/11/02/issue-with-touchpad-in-ubuntu-13-10-in-xps-12/comment-page-1/#comment-22)

---

