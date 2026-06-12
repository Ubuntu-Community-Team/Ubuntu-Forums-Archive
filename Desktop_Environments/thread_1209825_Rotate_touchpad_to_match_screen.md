---
title: "Rotate touchpad to match screen?"
date: 2009-07-10
forum: Desktop Environments
---

### Post by celticbhoy on 2009-07-10
I have a netbook that I sometimes hold sideways on (like a book) using the screen rotation from the display applet. I would like to know if it is possible to rotate the touchpad in the same way?

---

### Post by celticbhoy on 2009-07-24
Bump....

---

### Post by Zorael on 2009-07-24
I'm not sure there is, unless there's a way to tell X specifically that all incoming mouse events should be rotated.
```
Device 'SynPS/2 Synaptics TouchPad':                                                
        Device Enabled (90):            1                                           
        Synaptics Edges (237):          1632, 5312, 1575, 4281                      
        Synaptics Finger (238):         24, 29, 255                                 
        Synaptics Tap Time (239):               180                                 
        Synaptics Tap Move (240):               221                                 
        Synaptics Tap Durations (241):          180, 180, 100                       
        Synaptics Tap FastTap (242):            0
        Synaptics Middle Button Timeout (243):          75
        Synaptics Two-Finger Pressure (244):            280
        Synaptics Scrolling Distance (245):             100, 100
        Synaptics Edge Scrolling (246):         1, 0, 0
        Synaptics Two-Finger Scrolling (247):           0, 0
        Synaptics Edge Motion Pressure (248):           29, 159
        Synaptics Edge Motion Speed (249):              1, 401
        Synaptics Edge Motion Always (250):             0
        Synaptics Button Scrolling (251):               1, 1
        Synaptics Button Scrolling Repeat (252):                1, 1
        Synaptics Button Scrolling Time (253):          100
        Synaptics Off (254):            0
        Synaptics Guestmouse Off (255):         0
        Synaptics Locked Drags (256):           0
        Synaptics Locked Drags Timeout (257):           5000
        Synaptics Tap Action (258):             2, 3, 0, 0, 1, 2, 3
        Synaptics Click Action (259):           1, 1, 1
        Synaptics Circular Scrolling (260):             0
        Synaptics Circular Scrolling Trigger (261):             0
        Synaptics Circular Pad (262):           0
        Synaptics Palm Detection (263):         0
        Synaptics Palm Dimensions (264):                10, 199
        Synaptics Pressure Motion (265):                29, 159
        Synaptics Grab Event Device (266):              1
```
Those are the Synaptics xinput settings available to me on Jaunty. Compare to what's available for my connected Logitech cordless mouse;
```
Device 'Logitech USB Receiver':
        Device Enabled (90):            1
**        Evdev Axis Inversion (236):             0, 0**
        Evdev Reopen Attempts (225):            10
        Evdev Axis Calibration (226):
        **Evdev Axes Swap (227):          0**
        Evdev Middle Button Emulation (228):            2
        Evdev Middle Button Timeout (229):              50
        Evdev Wheel Emulation (230):            0
        Evdev Wheel Emulation Axes (231):               0, 0, 4, 5
        Evdev Wheel Emulation Inertia (232):            10
        Evdev Wheel Emulation Timeout (233):            200
        Evdev Wheel Emulation Button (234):             4
        Evdev Drag Lock Buttons (235):          0
```
So the evdev "driver" can swap and invert axes, but the synaptics one can't.

Perhaps that's worthy of a wishlist report on the [freedesktop.org bug tracker](http://bugs.freedesktop.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=xorg&component=Input%2Fsynaptics), or on Launchpad? Of course, you could load your touchpad with the evdev driver too, but you'd lose out on drag-to-scroll, tap-to-click, and other stuff.


edit: Addendum; Karmic options.
```
Device 'SynPS/2 Synaptics TouchPad':
        Device Enabled (89):    1
        Synaptics Edges (236):  394, 5235, 1491, 5527
        Synaptics Finger (237): 24, 29, 255
        Synaptics Tap Time (238):       180
        Synaptics Tap Move (239):       221
        Synaptics Tap Durations (240):  180, 180, 100
        Synaptics Tap FastTap (241):    0
        Synaptics Middle Button Timeout (242):  75
        Synaptics Two-Finger Pressure (243):    280
        Synaptics Two-Finger Width (244):       7
        Synaptics Scrolling Distance (245):     100, 100
        Synaptics Edge Scrolling (246): 1, 0, 0
        Synaptics Two-Finger Scrolling (247):   1, 0
        Synaptics Move Speed (248):     0.400000, 0.700000, 0.009952, 40.000000
        Synaptics Edge Motion Pressure (249):   29, 159
        Synaptics Edge Motion Speed (250):      1, 401
        Synaptics Edge Motion Always (251):     0
        Synaptics Button Scrolling (252):       1, 1
        Synaptics Button Scrolling Repeat (253):        1, 1
        Synaptics Button Scrolling Time (254):  100
        Synaptics Off (255):    0
        Synaptics Guestmouse Off (256): 0
        Synaptics Locked Drags (257):   0
        Synaptics Locked Drags Timeout (258):   5000
        Synaptics Tap Action (259):     2, 3, 0, 0, 1, 2, 3
        Synaptics Click Action (260):   1, 1, 1
        Synaptics Circular Scrolling (261):     0
        Synaptics Circular Scrolling Distance (262):    0.100000
        Synaptics Circular Scrolling Trigger (263):     0
        Synaptics Circular Pad (264):   0
        Synaptics Palm Detection (265): 0
        Synaptics Palm Dimensions (266):        10, 199
        Synaptics Coasting Speed (267): 0.000000
        Synaptics Pressure Motion (268):        29, 159
        Synaptics Pressure Motion Factor (269): 1.000000, 1.000000
        Synaptics Grab Event Device (270):      1
        Synaptics Gestures (271):       1
        Synaptics Capabilities (272):   1, 1, 1, 1, 1
        Synaptics Pad Resolution (273): 88, 58
        Synaptics Area (274):   0, 0, 0, 0
```

---

### Post by celticbhoy on 2009-07-24
Just put a suggestion on the brainstorm.

---

### Post by diegorodriguezv on 2009-10-31
I'm doing something similar in my Hardy for a Genius Traveler 350 trackball to invert the axes and switch some buttons.

Here is the relevant xorg.conf section:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        # Invert Axes
        Option          "InvX"          "1"
        Option          "InvY"          "1"
        # Invert wheel-up / wheel-down
        Option          "ZAxisMapping"  "5 4"
        # Invert middle and right mouse buttons
        # Invert back and forward buttons also
        Option          "ButtonMapping" "1 3 2 9 8"
EndSection

```

They are properties of the "mouse" driver, I found this in google "man mouse" or "option invx". 

Hope it helps.

---

### Post by diegorodriguezv on 2009-11-01
I've struggled trying to make the same changes in Jaunty but I couldn't, it seemed that the X server wasn't reading the xorg.config file so I sticked to Hardy.

Fiddling again in Karmic I had the same problem but I resolved it with the following commands:

```

xinput set-button-map "KYE  Traveler 350" 1 3 2 5 4 6 7 9 8
xinput set-int-prop  "KYE  Traveler 350" "Evdev Axis Inversion"  8 1 1

```

To make this commands run every boot I just added them at System > Preferences > Startup Applications (or something like that, my desktop is in spanish).

---

### Post by lacunoso on 2009-11-16
You can use a patched synaptics.  ;)
[http://cc.oulu.fi/~rantalai/synaptics/]("http://cc.oulu.fi/~rantalai/synaptics/")

---

