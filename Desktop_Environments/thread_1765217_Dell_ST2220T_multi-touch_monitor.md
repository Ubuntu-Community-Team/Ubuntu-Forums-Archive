---
title: "Dell ST2220T multi-touch monitor"
date: 2011-05-22
forum: Desktop Environments
---

### Post by cccc on 2011-05-22
Hi

I have Ubuntu 10.04 and bought Dell ST2220T multi-touch monitor with USB interface:```

# cat /proc/bus/input/devices
I: Bus=0003 Vendor=1fd2 Product=0064 Version=0100
N: Name="LG Display LGD-MultiTouch"
P: Phys=usb-0000:00:1d.7-2.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.1/1-2.1:1.0/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=1b
B: KEY=403 0 30000 0 0 0 0 0 0 0 0
B: ABS=700 3f
B: MSC=10
```

Touch screen works under Vista without problems, but howto get it working under Ubuntu?

---

### Post by cccc on 2011-05-24
Has someone any idea howto get touch screen working?

---

### Post by Copper Bezel on 2011-05-24
I think the usual solution has to do with recognizing the touchscreen as a Wacom device. I don't have any hands-on experience with touchscreen support, however. Unless someone more knowledgeable comes along, I'd suggest Google searching for wacom device support in Ubuntu. There's also the experimental work in [ginn/uTouch]("https://wiki.ubuntu.com/Multitouch").

---

### Post by cccc on 2011-05-25
Thx, but still doesn't work.

---

### Post by Copper Bezel on 2011-05-25
As I said, I can't offer much help on this subject, but could you post exactly what you tried so that someone can help to diagnose the problem?

---

### Post by Favux on 2011-05-25
They have it partially working in Natty.  See this launchpad bug report:  [https://bugs.launchpad.net/utouch/+bug/736752](https://bugs.launchpad.net/utouch/+bug/736752)
The Ubuntu Multi-touch wiki also tells you what hardware is supported and other useful stuff.

For Lucid it depends on if it is supported in the 2.6.32 kernel.  It seems like it might be at least partially supported since you're getting some output mentioning it.  You should also run in a terminal:
```
lsusb
and
xinput list
```
And see what the outputs show for the device's name so you have something to google with.  Right now it looks like "LGD-MultiTouch"?  Or is the "LG Display" part of the name too?

Then you need an X driver.  Evdev is probably picking it up by default but apparently isn't working.  You could try evtouch and/or google around to see if anything works.  My guess is in Lucid you'll only be able to get single finger touch, if you get it working.  But you'll need to do some more research.

---

### Post by cccc on 2011-05-27
Thx, I get these outputs, but cannot find a solution:```


# **lsusb**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 003: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 003 Device 002: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1fd2:0064  
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

# **xinput list**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=10	[slave  pointer  (2)]
**&#9116;   &#8627; LG Display LGD-MultiTouch               	id=11	[slave  pointer  (2)]**
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard Hub              	id=8	[slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard Hub              	id=9	[slave  keyboard (3)]
    &#8627; ACPI Virtual Keyboard Device            	id=12	[slave  keyboard (3)]
```

---

### Post by Favux on 2011-05-27
In *lsusb* is it?:
```
Bus 001 Device 004: ID 1fd2:0064
```
If it is that gives us the Vendor and Product ID's.  Oh sure it is, that's the same ones as from cat */proc/bus/input/devices*.

The system knows it's there given the *xinput* output so evdev should be picking it up.  Let's find out with the output of:
```
xinput list-props "LG Display LGD-MultiTouch"
```

---

### Post by mrsellout on 2011-05-27
I am in the same boat.
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; LG Display LGD-MultiTouch                   id=8    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse                 id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]

```
Here's the output from xinput list-props "LG Display LGD-MultiTouch"
```

$ xinput list-props "LG Display LGD-MultiTouch"
Device 'LG Display LGD-MultiTouch':
    Device Enabled (116):    1
    Coordinate Transformation Matrix (118):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (243):    0
    Device Accel Constant Deceleration (244):    1.000000
    Device Accel Adaptive Deceleration (245):    1.000000
    Device Accel Velocity Scaling (246):    10.000000
    Evdev Axis Inversion (247):    0, 0
    Evdev Axis Calibration (248):    <no items>
    Evdev Axes Swap (249):    0
    Axis Labels (250):    "Abs X" (236), "Abs Y" (237), "Abs Z" (238), "Abs Rotary X" (239), "Abs Rotary Y" (240), "Abs Rotary Z" (241), "Abs Misc" (242), "Abs Misc" (242), "Abs Misc" (242)
    Button Labels (251):    "Button Left" (119), "Button Unknown" (235), "Button Right" (121), "Button Wheel Up" (122), "Button Wheel Down" (123)
    Evdev Middle Button Emulation (252):    0
    Evdev Middle Button Timeout (253):    50
    Evdev Wheel Emulation (254):    0
    Evdev Wheel Emulation Axes (255):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (256):    10
    Evdev Wheel Emulation Timeout (257):    200
    Evdev Wheel Emulation Button (258):    4
    Evdev Drag Lock Buttons (259):    0

```

I also ran evtest, touching the screen produces no change (when running evtest on the mouse changes do occur).

```
$ sudo evtest /dev/input/event3
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x1fd2 product 0x64 version 0x100
Input device name: "LG Display LGD-MultiTouch"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value      0
      Min        0
      Max     1920
    Event code 1 (Y)
      Value      0
      Min        0
      Max     1080
    Event code 2 (Z)
      Value      0
      Min        0
      Max     1920
    Event code 3 (Rx)
      Value      0
      Min        0
      Max     1080
    Event code 4 (Ry)
      Value      0
      Min        0
      Max    32767
    Event code 5 (Rz)
      Value      0
      Min        0
      Max    32767
    Event code 40 (Misc)
      Value      0
      Min        0
      Max        1
    Event code 41 (?)
      Value      0
      Min        0
      Max        1
    Event code 42 (?)
      Value      0
      Min        0
      Max     1080
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)

```

I am running Natty xubutntu, updated from Maverick and beyond that in the past.

However I do have an issue with the graphics card. Something broke a while back (when I upgraded to Maverick) and I haven't  yet got the proprietory Nvidia ones working again. I am running a pretty old GeForce2 MX/MX 400 card, and I've had nightmares trying to get the legacy drivers running on Fedora, I'm going to have another bash this weekend with a clean install of Natty. (I've tried installing a fresh version of Natty, but didn't try fixing the drivers, and I had no joy with the touchscreen).

The reason I brought that up is the monitor was unknown in the GNOME Display Settings configuration app and I can't get a resolution higher than 1024x768. Is this important? The event codes seem to go to the max resolution.

In the mouse configuration program there are 2 mice displayed: the actual mouse and the 'LG Display LGD-MultiTouch'. There are no extra settings under the MultiTouch mouse.

What I will try to do this weekend is get a clean install of Natty up, try fixing the Nvidia driver issue and then seeing how it goes from there.

---

### Post by Favux on 2011-05-27
Alright, we may have something here:
> Evdev Axis Calibration (248 ):    <no items>
It looks like the kernel isn't feeding evdev the min and max x & y.  We should be able to put that in manually.
> Option "Calibration" "min-x max-x min-y max-y"
    Calibrates the X and Y axes for devices that need to scale to a different coordinate system than reported to the X server. This feature is required for devices that need to scale to a different coordinate system than originally reported by the kernel (e.g. touchscreens). The scaling to the custom coordinate system is done in-driver and the X server is unaware of the transformation. Property: "Evdev Axis Calibration". 
I'm thinking the following might only work for Natty.  Get the touch working on evdev if possible.  Then rely on Canonical's implementing multitouch stuff in Natty.  I'm hoping with multitouch working on evdev (we can install mtview to check) then ginn and its wishes.xml may give us multitouch gestures.  A pre-Natty release like Lucid might only support single finger touch with the default kernel and evdev driver, once we figure out the correct coordinates to use.

Unfortunately I don't know how to figure out the touchscreen coordinates.  Some combination of the active area and resolution?

The kernel reports in points/micrometer.  So it should be the active area (screen size?) in cm.s or mm.s converted to micrometers.

The Xserver uses points/meter.  So you convert the resolution to that.

But that's the extent of my knowledge so we'll likely be guessing.  But we should be able to test coordinates with xinput before we construct a LGD-MultiTouch.conf to apply them permanently.  Presumably if we can find the scaling for one axis it should apply to the other.

So I suppose use:
xinput --set-prop "LG Display LGD-MultiTouch" "Evdev Axis Calibration" ? ? ? ?
and guess. Starting with 0 0 1000 1000?  Scaling the max x and y to the screen ratios.  So need at least the screen size from someone.

---

### Post by cccc on 2011-05-31
Thx, I've tried this, but still doesn't work:

```
# xinput --set-prop "LG Display LGD-MultiTouch" "Evdev Axis Calibration" 0 0 1000 1000

# xinput list-props "LG Display LGD-MultiTouch"
Device 'LG Display LGD-MultiTouch':
	Device Enabled (121):	1
	Device Accel Profile (240):	0
	Device Accel Constant Deceleration (241):	1.000000
	Device Accel Adaptive Deceleration (243):	1.000000
	Device Accel Velocity Scaling (244):	10.000000
	Evdev Reopen Attempts (238):	10
	Evdev Axis Inversion (245):	0, 0
	Evdev Axis Calibration (246):	0, 0, 1000, 1000
	Evdev Axes Swap (247):	0
	Axis Labels (248):	"Abs X" (259), "Abs Y" (260), "Abs Z" (261), "Abs Rotary X" (262), "Abs Rotary Y" (263), "Abs Rotary Z" (264), "None" (0), "None" (0), "None" (0)
	Button Labels (250):	"Button Left" (122), "Button Unknown" (249), "Button Right" (124), "Button Wheel Up" (125), "Button Wheel Down" (126)
	Evdev Middle Button Emulation (251):	2
	Evdev Middle Button Timeout (252):	50
	Evdev Wheel Emulation (253):	0
	Evdev Wheel Emulation Axes (254):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (255):	10
	Evdev Wheel Emulation Timeout (256):	200
	Evdev Wheel Emulation Button (257):	4
	Evdev Drag Lock Buttons (258):	0

# evtest /dev/input/event0
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x1fd2 product 0x64 version 0x100
Input device name: "LG Display LGD-MultiTouch"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value      0
      Min        0
      Max     1920
    Event code 1 (Y)
      Value      0
      Min        0
      Max     1080
    Event code 2 (Z)
      Value      0
      Min        0
      Max     1920
    Event code 3 (Rx)
      Value      0
      Min        0
      Max     1080
    Event code 4 (Ry)
      Value      0
      Min        0
      Max    32767
    Event code 5 (Rz)
      Value      0
      Min        0
      Max    32767
    Event code 40 (Misc)
      Value      0
      Min        0
      Max        1
    Event code 41 (?)
      Value      0
      Min        0
      Max        1
    Event code 42 (?)
      Value      0
      Min        0
      Max     1080
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)

```

---

### Post by Favux on 2011-05-31
Alright, no response anywhere on the screen?

What are the monitors dimensions?  what x what?

Does Dell give you more specifications?  For example touch accuracy is +/_ 3mm or something.  That might give us a clue as to touch resolution.  So any specifications along those lines would be good.

---

### Post by cccc on 2011-05-31
> **Favux said:**
> Alright, no response anywhere on the screen?

What are the monitors dimensions?  what x what?

Does Dell give you more specifications?  For example touch accuracy is +/_ 3mm or something.  That might give us a clue as to touch resolution.  So any specifications along those lines would be good.

There is no response anywhere on the screen under linux, but under Vista works well.

**Touch response time: 15ms**
**Accuracy: +/-2.5mm over 95% of touchable area**

Here are some specifications of this monitor:

[http://vr-zone.com/articles/dell-quietly-updates-online-store-with-ips-panel-totting-st2220t-touchscreen-monitor/10583.html](http://vr-zone.com/articles/dell-quietly-updates-online-store-with-ips-panel-totting-st2220t-touchscreen-monitor/10583.html)

[http://www.tftcentral.co.uk/reviews/dell_st2220t.htm](http://www.tftcentral.co.uk/reviews/dell_st2220t.htm)

---

### Post by gtejasvarma on 2011-06-01
Hey,

    I installed ubuntu along with windows 7. Touch screen works when i login into windows restart (note: not shutdown) and then login in ubuntu touch screen works out of the box.If i reboot (not shut down)from ubuntu any no of time touch screen still works but if i shut it down and boot directly into ubuntu touch screen doesnt work . I suspect some resources which are required for touch screen to work are not loaded by ubuntu at the start. 

Can some please throw some light on this.

Thanks a ton

---

### Post by cccc on 2011-06-02
> **gtejasvarma said:**
> Hey,

    I installed ubuntu along with windows 7. Touch screen works when i login into windows restart (note: not shutdown) and then login in ubuntu touch screen works out of the box.If i reboot (not shut down)from ubuntu any no of time touch screen still works but if i shut it down and boot directly into ubuntu touch screen doesnt work . I suspect some resources which are required for touch screen to work are not loaded by ubuntu at the start. 

Can some please throw some light on this.

Thanks a ton

Some more details needed.

1.) Is this Dual Boot?
2.) Which Boot Manager?
3.) Which Monitor type do you have?
4.) How is your touch screen configuration?
5.) Can you post your /etc/X11/xorg.conf?

---

### Post by gtejasvarma on 2011-06-07
> **cccc said:**
> Some more details needed.

1.) Is this Dual Boot?
Yes, this is Dual Boot. 
> 
2.) Which Boot Manager?Grub
> 
3.) Which Monitor type do you have?
DELL ST2220T
> 
4.) How is your touch screen configuration?

It is with the default config. Its a fresh install with no changes made.> 
5.) Can you post your /etc/X11/xorg.conf?I attached 10-evdev,conf in my /usr/share/X11/xorg,conf,d/ . Please check it

---

### Post by luckymurari on 2011-06-07
> **gtejasvarma said:**
> Hey,

    I installed ubuntu along with windows 7. Touch screen works when i login into windows restart (note: not shutdown) and then login in ubuntu touch screen works out of the box.If i reboot (not shut down)from ubuntu any no of time touch screen still works but if i shut it down and boot directly into ubuntu touch screen doesnt work . I suspect some resources which are required for touch screen to work are not loaded by ubuntu at the start. 

Can some please throw some light on this.

Thanks a ton
I too have an exact problem which I asked in here [http://ubuntuforums.org/showthread.php?t=1772728](http://ubuntuforums.org/showthread.php?t=1772728) . Any help is appreciated.

---

### Post by cccc on 2011-06-07
It seems to work now using **evdev** driver, but if I touch a screen icon, then an application will be opened 20 and more times.
Knows someone howto solve this problem?

Here is /var/log/Xorg.0.log output:
```

   137.005] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   137.005] (II) AIGLX: enabled GLX_INTEL_swap_event
[   137.005] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   137.005] (II) AIGLX: enabled GLX_SGI_make_current_read
[   137.005] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   137.005] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[   137.005] (II) GLX: Initialized DRI2 GL provider for screen 0
[   137.007] (II) intel(0): Setting screen physical size to 507 x 285
[   137.121] (II) Using input driver 'evdev' for 'mytouchscreen'
[   137.121] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   137.122] (**) Option "SendCoreEvents"
[   137.122] (**) mytouchscreen: always reports core events
[   137.122] (**) mytouchscreen: Device: "/dev/input/event0"
[   137.122] (--) mytouchscreen: Found 3 mouse buttons
[   137.122] (--) mytouchscreen: Found absolute axes
[   137.122] (--) mytouchscreen: Found x and y absolute axes
[   137.122] (--) mytouchscreen: Found absolute tablet.
[   137.122] (II) mytouchscreen: Configuring as tablet
[   137.122] (**) mytouchscreen: YAxisMapping: buttons 4 and 5
[   137.122] (**) mytouchscreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   137.122] (II) XINPUT: Adding extended input device "mytouchscreen" (type: TABLET)
[   137.122] (II) mytouchscreen: initialized for absolute axes.
[   137.123] (**) mytouchscreen: (accel) keeping acceleration scheme 1
[   137.123] (**) mytouchscreen: (accel) acceleration profile 0
[   137.123] (**) mytouchscreen: (accel) acceleration factor: 2.000
[   137.123] (**) mytouchscreen: (accel) acceleration threshold: 4
```

evtest:
```

# evtest /dev/input/event0

Input driver version is 1.0.0
Input device ID: bus 0x3 vendor 0x1fd2 product 0x64 version 0x100
Input device name: "LG Display LGD-MultiTouch"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value   1852
      Min        0
      Max     1920
    Event code 1 (Y)
      Value    948
      Min        0
      Max     1080
    Event code 2 (Z)
      Value  65535
      Min        0
      Max     1920
    Event code 3 (Rx)
      Value  65535
      Min        0
      Max     1080
    Event code 4 (Ry)
      Value      0
      Min        0
      Max    32767
    Event code 5 (Rz)
      Value      0
      Min        0
      Max    32767
    Event code 40 (Misc)
      Value    120
      Min        0
      Max        1
    Event code 41 (?)
      Value    121
      Min        0
      Max        1
    Event code 42 (?)
      Value      2
      Min        0
      Max     1080
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)
Event: time 1307470639.789544, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.789557, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.789562, type 1 (Key), code 320 (ToolPen), value 1
Event: time 1307470639.789570, type 3 (Absolute), code 0 (X), value 102
Event: time 1307470639.789574, type 3 (Absolute), code 1 (Y), value 536
Event: time 1307470639.789578, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.789579, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.789597, -------------- Report Sync ------------
Event: time 1307470639.797541, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.797553, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.797572, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.797573, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.797591, -------------- Report Sync ------------
Event: time 1307470639.805547, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.805558, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.805576, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.805577, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.805595, -------------- Report Sync ------------
Event: time 1307470639.813539, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.813561, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.813579, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.813581, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.813597, -------------- Report Sync ------------
Event: time 1307470639.821551, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.821567, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.821586, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.821587, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.821605, -------------- Report Sync ------------
Event: time 1307470639.829566, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.829588, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.829606, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.829607, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.829624, -------------- Report Sync ------------
Event: time 1307470639.841555, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.841566, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.841585, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.841586, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.841603, -------------- Report Sync ------------
Event: time 1307470639.849562, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.849583, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.849601, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.849602, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.849620, -------------- Report Sync ------------
Event: time 1307470639.857640, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.857687, type 1 (Key), code 330 (Touch), value 1
Event: time 1307470639.857706, type 4 (Misc), code 4 (ScanCode), value d0042
Event: time 1307470639.857707, type 1 (Key), code 330 (Touch), value 0
Event: time 1307470639.857724, -------------- Report Sync ------------
Event: time 1307470639.865598, type 1 (Key), code 320 (ToolPen), value 0
Event: time 1307470639.865666, -------------- Report Sync ------------

```

and here my /etc/X11/xorg.conf:```



Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "mytouchscreen" "SendCoreEvents"
        #InputDevice    "dummy"  
        Option "AllowEmptyinput" "false"
        #Option "AutoAddDevices" "false"
        #Option "AutoEnableDevices" "false"      
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "record"
	Load  "dbe"
	Load  "extmod"
	Load  "dri"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

#Section "InputDevice"
#       Identifier      "dummy"
#       Driver          "void"
#       Option          "Device" "/dev/input/mice"
#EndSection

Section "InputDevice"
        Identifier "mytouchscreen"
        Option      "Name" "LG Display LGD-MultiTouch"
        Driver      "evdev"  
        Option      "Device" "/dev/input/event0"
        Option      "SendCoreEvents"        "true"
        Option      "AbsoluteScreen"         "0"
        Option      "XAbsoluteAxisMap"       "1"
        Option      "YAbsoluteAxisMap"       "0" 
        Option      "Evdev Multitouch"       "2"
        Option      "MinX"  "957" 
        Option      "MaxX"  "967"
        Option      "MinY"  "1696" 
        Option      "MaxY"  "1706"
        Option      "ScreenNumber"  "0"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "LinearFramebuffer"  	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

BTW it happens the same if I delete /etc/X11/xorg.conf completely.
It seems to be **pressure sensitivity problem of evdev driver**, but really don't know howto change it.

---

### Post by ragerino on 2011-07-29
> **cccc said:**
> It seems to work now using **evdev** driver, but if I touch a screen icon, then an application will be opened 20 and more times.
Knows someone howto solve this problem?


can you tell us what you did? would be great to make it work on my pandaboard too!

---

### Post by cccc on 2011-07-29
> **ragerino said:**
> can you tell us what you did? would be great to make it work on my pandaboard too!

You'll see what I did, if you read my postings before.
BTW it still doesn't work correctly.

---

### Post by toko5 on 2011-10-15
is there anything known yet about the hardware support status of this Monitor?

has someone managed it, to get it to work?



I find this Hardware is quite nice,  without knowing if there is a possible support in ubuntu its just hard to decide if this is the right thing to buy...

---

### Post by HughR on 2012-10-29
There's a new thread at [http://ubuntuforums.org/showthread.php?p=12181989]("http://ubuntuforums.org/showthread.php?p=12181989")

---

### Post by wildmanne39 on 2012-10-29
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

