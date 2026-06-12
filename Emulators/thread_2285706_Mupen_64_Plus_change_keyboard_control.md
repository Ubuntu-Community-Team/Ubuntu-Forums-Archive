---
title: "Mupen 64 Plus change keyboard control"
date: 2015-07-08
forum: Emulators
---

### Post by rolandpish on 2015-07-08
Hi. I just installed mupen64plus and I just wanted to change a couple of keys of my keyboard control. It's simple, I just want to change the A and B buttons to be the keys X and C (like project64). How can I modify the configuration file so I can change the Ctrl and Shift keys to be X and C?

Thanks!

---

### Post by QIII on 2015-07-08
*Moved to **Emulators***.

---

### Post by deadflowr on 2015-07-08
Beat me to it Q!

But alas.
You can edit the config file in ~/.config/mupen64plus.
You'll need to look over the sdl keyboard reference to point to correct keys.
[http://www.libsdl.org/release/SDL-1.2.15/include/SDL_keysym.h](http://www.libsdl.org/release/SDL-1.2.15/include/SDL_keysym.h)
But first you need to generate a config file.
To do so run
```
mupen64plus --saveoptions
```
this will create a mupen64plus.conf file, if one did not exist to begin with.
The full path will be /home/username/.config/mupen64plus/mupen64plus.conf.
inside it should be a keyboard layout.You can edit this using the keyboard layout linked above.
then save when finished.

If prior to running the --saveoptions command you would like to set other parameters you can do so.
I tend to set the resolution, since that tends to be set at something odd like 800x600, which is a tad small.
(But any option you want can be editing or added to the conf file at anytime, so there is no rush, imo)
just run mupen64plus -h for a quick list of options.

For the record as a reference, sort of, here an old layout I have
```
[Input-SDL-Control1]

# Mupen64Plus SDL Input Plugin config parameter version number.  Please don't change
version = 1
# Specifies whether this controller is 'plugged in' to the simulated N64
plugged = True
# Specifies which type of expansion pak is in the controller: 1=None, 2=Mem pak, 5=Rumble pak
plugin = 2
# If True, then mouse buttons may be used with this controller
mouse = False
# Specifies which joystick is bound to this controller: -2=Keyboard/mouse, -1=Auto config, 0 or more= SDL Joystick number
device = -1
# SDL joystick name (name check disabled if this is empty string)
name = "Keyboard"
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
C Button R = "key(275)"
C Button L = "key(276)"
C Button D = "key(274)"
C Button U = "key(273)"
R Trig = "key(113)"
L Trig = "key(9)"
Mempak switch = "key(44)"
Rumblepak switch = "key(46)"
# Analog axis configuration mappings
X Axis = "key(260,262)"
Y Axis = "key(264,258)"



``` Note this is an old layout I have,(I needed to dig to find one for a keyboard as I use a joystick now)
so I have no clue as to what the keys are, and I am not digging into the reference linked to figure it out..

Not sure if this will help, hope it does.

---

### Post by rolandpish on 2015-07-08
Thanks for the help deadflowr, I added the [Input-SDL-Control1] section in the config file and changed the A button and B button with the corresponding keys for 'x' and 'c' according to the SDK_keysym.h file but the keys in the game are behaving the same. I'm still searching how to change them :)
Cheers.

---

### Post by deadflowr on 2015-07-08
I forgot to mention alternatively to figuring out how to get the configs to work via the command line way.
You could try one of the various frontends
m64py is one
[http://m64py.sourceforge.net/](http://m64py.sourceforge.net/)
cutemupen is another
[http://sourceforge.net/projects/cutemupen/](http://sourceforge.net/projects/cutemupen/)

m64py is easier to setup, imo.

---

### Post by rolandpish on 2015-07-08
I used your input sdl control1 as a base; and after lots of trial and error, I ended up with this in my configuration file and it finally worked!

> [Input-SDL-Control1]

plugged = True
plugin = 2
mouse = False
name = "Keyboard"
device = -2
Y Axis = "key(273,274)"
X Axis = "key(276,275)"
Start = "key(13)"
Z Trig = "key(122)"
B Button = "key(99)"
A Button = "key(120)"
C Button R = "key(100)"
C Button L = "key(97)"
C Button U = "key(117)"
C Button D = "key(115)"
R Trig = "key(99)"
L Trig = "key(120)"

Thanks a lot!

---

