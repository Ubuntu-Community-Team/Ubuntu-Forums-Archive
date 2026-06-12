---
title: "CANNOT get all of my mouse buttons working"
date: 2006-01-12
forum: General Help
---

### Post by tonyisntcreative on 2006-01-12
I've tried multiple HOWTO's (forums, the Ubuntu wiki, google, etc...) and I can't get anything to work for some reason.  The only conclusion that I can come to is that it won't remap the buttons, or something.  I've tried xmodmap -e "pointer = 1 2 3 6 7 4 5", I've tried naming files .xmodmap and other assorted things I've read in howto's with that in them.

My mouse is a Belkin F8E850-OPT with two side buttons and a scroller.  It's plugged into a USB port (I think this might be what is making it not want to remap.)

This is my xorg.conf section for it (this is how I've read to have it in more than one howto)
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Button"	"false"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"6 7"
```

These are the results I get after pressing each button in xev.
Left Click
```
ButtonPress event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2663917, (35,21), root:(40,93),
    state 0x10, button 1, same_screen YES

EnterNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2663917, (35,21), root:(40,93),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 272

KeymapNotify event, serial 26, synthetic NO, window 0x0,
    keys:  64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2664237, (35,21), root:(40,93),
    state 0x110, button 1, same_screen YES

LeaveNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2664237, (35,21), root:(40,93),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```
Right Click
```
ButtonPress event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2730603, (56,46), root:(61,118),
    state 0x10, button 3, same_screen YES

EnterNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2730603, (56,46), root:(61,118),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1040

KeymapNotify event, serial 26, synthetic NO, window 0x0,
    keys:  64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2731051, (56,46), root:(61,118),
    state 0x410, button 3, same_screen YES

LeaveNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2731051, (56,46), root:(61,118),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```
Clicking with the scroll button
```
ButtonPress event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2780043, (41,29), root:(46,101),
    state 0x10, button 2, same_screen YES

EnterNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2780043, (41,29), root:(46,101),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 528

KeymapNotify event, serial 26, synthetic NO, window 0x0,
    keys:  64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2780267, (41,29), root:(46,101),
    state 0x210, button 2, same_screen YES

LeaveNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2780267, (41,29), root:(46,101),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```
Left side button
```
ButtonPress event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2878770, (33,30), root:(38,102),
    state 0x10, button 2, same_screen YES

EnterNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2878770, (33,30), root:(38,102),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 528

KeymapNotify event, serial 26, synthetic NO, window 0x0,
    keys:  64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2878914, (33,30), root:(38,102),
    state 0x210, button 2, same_screen YES

LeaveNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2878914, (33,30), root:(38,102),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```
And finally...right side button
```
ButtonPress event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2958614, (46,60), root:(51,132),
    state 0x10, button 3, same_screen YES

EnterNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2958614, (46,60), root:(51,132),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1040

KeymapNotify event, serial 26, synthetic NO, window 0x0,
    keys:  64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x2e00002, time 2958782, (46,60), root:(51,132),
    state 0x410, button 3, same_screen YES

LeaveNotify event, serial 26, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 2958782, (46,60), root:(51,132),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```

Any help would be greatly appreciated seeing as I can't get this figured out for anything.

EDIT:  I forgot moving the scroll up and down.  I can add those if they will help.

---

### Post by daschl on 2006-01-12
why do you disable "Emulate3Buttons"?

i have a mouse with 5 buttons, E3B is enabled and it works great :)

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

```

---

### Post by Thunk on 2006-01-12
I don't know if you have noticed, but your scroll-button and left side buton are assigned as the same button (button 2) and the same thing for right and side-right buttons (button 1). I am having the same problem and couldn't find an answer anywhere.

---

### Post by dcstar on 2006-01-12
Does this help?:

[http://doc.gwos.org/index.php/5ButtonMouse](http://doc.gwos.org/index.php/5ButtonMouse)

---

