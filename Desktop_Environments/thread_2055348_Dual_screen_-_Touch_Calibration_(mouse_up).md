---
title: "Dual screen - Touch Calibration (mouse up)"
date: 2012-09-09
forum: Desktop Environments
---

### Post by plo on 2012-09-09
After extensive searching and trying I'm stuck.

I have a dualscreen setup (Asus T231H touch screen + Panasonic TV).
I want the touch inputs to only scale to the first monitor.
"Mouse down" works good but when I release my finger "mouse up" the cursor jumps left and the "click" is registered in the wrong position.

'**xrandr**' gives:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 3200 x 1080, maximum 3200 x 1080
default connected 3200x1080+0+0 0mm x 0mm
   3200x1080      50.0     51.0* 
   1920x1080      52.0 
note. screens are touch 1920x1080 and tv 1290x720

I have tested almost every possible combination of sceen setups.

Using '**xinput test 10**' I get:
[email]mop@Asrock:/usr/share/X11/xorg.conf[/email].d$ xinput test 10
motion a[0]=276 a[1]=904 
button press   1 a[0]=276 a[1]=904 
button release 1 a[0]=165 a[1]=904 
motion a[0]=466 a[1]=912 
button press   1 a[0]=466 a[1]=912 
button release 1 a[0]=280 a[1]=912 
motion a[0]=589 a[1]=877 
button press   1 a[0]=589 a[1]=877 
button release 1 a[0]=353 a[1]=877

as you can see mouse up is registered at a different position than mouse down.

In usr/share/X11/xorg.conf.d/10-evdev.conf I have set

[I]Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchProduct    "Acer T231H"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
	Option	"Calibration"	"0 1920 0 1080"
	Option	"TransformationMatrix" "0.6 0 0 0 1 0 0 0 1"
	Option 	"GrabDevice"	"True"
EndSection[/I]

The last "GrabDevice" was just a test. So the transformation matrix setting works but fails on mouse up.

**lsusb** - Bus 006 Device 003: ID 0408:3001 Quanta Computer, Inc. Optical Touch Screen

I'm on ubuntu 12.04 with kernel updated to **3.3.6-030306-generic**
via ppa (I found a site about multitouch and that listed my screen needing at least 3.3 for multitouch to work - [http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html)).

Here follows output of '**xinput list-props 10**'
Device 'Acer T231H':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	0.600000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (244):	0
	Device Accel Constant Deceleration (245):	1.000000
	Device Accel Adaptive Deceleration (246):	1.000000
	Device Accel Velocity Scaling (247):	10.000000
	Device Product ID (240):	1032, 12289
	Device Node (241):	"/dev/input/event13"
	Evdev Axis Inversion (248 ):	0, 0
	Evdev Axis Calibration (249):	0, 1920, 0, 1080
	Evdev Axes Swap (250):	0
	Axis Labels (251):	"Abs MT Position X" (267), "Abs MT Position Y" (268 ), "None" (0), "None" (0)
	Button Labels (252):	"Button Unknown" (243), "Button Unknown" (243), "Button Unknown" (243), "Button Wheel Up" (127), "Button Wheel Down" (128 )
	Evdev Middle Button Emulation (253):	0
	Evdev Middle Button Timeout (254):	50
	Evdev Third Button Emulation (255):	0
	Evdev Third Button Emulation Timeout (256):	1000
	Evdev Third Button Emulation Button (257):	3
	Evdev Third Button Emulation Threshold (258 ):	20
	Evdev Wheel Emulation (259):	0
	Evdev Wheel Emulation Axes (260):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (261):	10
	Evdev Wheel Emulation Timeout (262):	200
	Evdev Wheel Emulation Button (263):	4
	Evdev Drag Lock Buttons (264):	0

Previously I had a perfectly working setup with a different touchscreen (smaller) on ubuntu 10.04 and using separate x-screens.The latter does not work anymore unfortunately.

If I disconnect the TV, touch works like a charm on the single screen.

Anyone???  :confused:

/Palle

---

