---
title: "Trying to get Mupen64plus and Wireless Controllers to work"
date: 2012-03-20
forum: Emulators
---

### Post by rafe101 on 2012-03-20
I have Mupen version 1.99.5-1 from the repos, but for some reason I don't have an InputAutoCfg.ini file. That's okay because my controller doesn't appear to be in it anyway. I can get a working config for a wired N64 controller, but I want to use the wireless controllers that I use for other emus.

They are Hama PS3 controllers which SDLJoyTest identifies as "ELAN TURBO PAD". I identified all the buttons and axes with SDLJoyTest and created an input section for mupen64plus.cfg. It looks like this:

```
[Input-SDL-Control1]
plugged = True
plugin = 1
mouse = False
device = 0
name = "ELAN TURBO PAD"
AnalogDeadzone = "4096,4096"
AnalogPeak = "32768,32768"
DPad R = "hat(0,Right)"
DPad L = "hat(0,Left)"
DPad D = "hat(0,Down)"
DPad U = "hat(0,Up)"
Start = "button(9)"
Z Trig = "button(7)"
B Button = "button(0)"
A Button = "button(1)"
C Button R = "axis(2-)"
C Button L = "axis(2+)"
C Button D = "axis(3+)"
C Button U = "axis(3-)"
R Trig = "button(5)"
L Trig = "button(4)"
Mempak switch = 
Rumblepak switch =
X Axis = "axis(0-,0+)"
Y Axis = "axis(1-,1+)"

```

However, when I run Mupen64plus, the section gets replaced with an automatic keyboard configuration:

```
[Input-SDL-Control1]

# Mupen64Plus SDL Input Plugin config parameter version number.  Please don't change
version = 1.000000
# Specifies whether this controller is 'plugged in' to the simulated N64
plugged = True
# Specifies which type of expansion pak is in the controller: 1=None, 2=Mem pak, 5=Rumble pak
plugin = 2
# If True, then mouse buttons may be used with this controller
mouse = False
# Specifies which joystick is bound to this controller: -2=Keyboard/mouse, -1=Auto config, 0 or more= SDL Joystick number
device = -2
# SDL joystick name (name check disabled if this is empty string)
name = "AutoKeyboard"
# Scaling factor for mouse movements.  For X, Y axes.
MouseSensitivity = "2.00,2.00"
# The minimum absolute value of the SDL analog joystick axis to move the N64 controller axis value from 0.  For X, Y axes.
AnalogDeadzone = "4096,4096"
# An absolute value of the SDL joystick axis >= AnalogPeak will saturate the N64 controller axis value (at 80).  For X, Y axes. For each axis, this must be greater than the corresponding AnalogDeadzone value
AnalogPeak = "32768,32768"
# Digital button configuration mappings
DPad R = "key(100)"
DPad L = "key(97)"
DPad D = "key(115)"
DPad U = "key(119)"
Start = "key(13)"
Z Trig = "key(122)"
B Button = "key(306)"
A Button = "key(304)"
C Button R = "key(108)"
C Button L = "key(106)"
C Button D = "key(107)"
C Button U = "key(105)"
R Trig = "key(99)"
L Trig = "key(120)"
Mempak switch = "key(44)"
Rumblepak switch = "key(46)"
# Analog axis configuration mappings
X Axis = "key(276,275)"
Y Axis = "key(273,274)"
```

I assume Mupen is not detecting my controllers correctly, but everything looks fine with SDLJoyTest. I can see one if one is plugged in or two if both are.

Does anyone know how I can get this working?

---

### Post by rafe101 on 2012-04-15
I still haven't gotten this resolved. I sometimes wonder if it would be easier to get working if I could use a GUI, but CuteMupen isn't working after the update to Mupen64plus about a month ago.

---

