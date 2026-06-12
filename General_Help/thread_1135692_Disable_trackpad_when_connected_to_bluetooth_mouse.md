---
title: "Disable trackpad when connected to bluetooth mouse"
date: 2009-04-24
forum: General Help
---

### Post by Aphoxema on 2009-04-24
I'm trying to figure out how to make a script that will disable all trackpad input (sentellics) when I have a usb or bluetooth mouse connected.

Where should I start?

---

### Post by Aphoxema on 2009-04-28
First I need to know is a reliable way to check if there's a bluetooth mouse paired and connected.

---

### Post by Aphoxema on 2009-04-28
So far I've found is that /dev/input/mouse1 is the trackpad and when I "connect" my bluetooth mouse a /dev/input/mouse2 is created. When I turn off the bluetooth mouse /dev/input/mouse2 disappears after a moment.

What I need to figure out now is how to get X to stop using /dev/input/mice and use /dev/input/mouse1 until /dev/input/mouse2 is present, then stop accepting information from /dev/input/mouse1 until /dev/input/mouse2 disappears again.

What I'm thinking of is somehow making a script that makes a symlink like /dev/input/current.

---

### Post by SeanBlader on 2009-04-29
Keep us posted, I'm debating whether to disable the trackpad with a bluetooth mouse connected, or to just try and disable it while typing, which is probably a little harder.

---

### Post by Aphoxema on 2009-05-06
I haven't made any progress, the big hurdle is I can't seem to override x.org's use of /dev/input/mice.

I tried doing something with this...

```
Section "InputDevice"
Identifier "CurrentMouse"
Driver	"mouse"
  Option	"CorePointer"
  Option	"Device" "/dev/input/current"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "ServerLayout"
	Identifier "DefaultLayout"
	Screen "Default Screen"
	InputDevice "Keyboard" "CoreKeyboard"
	InputDevice "CurrentMouse" "CorePointer"
	InputDevice "dummy"
EndSection
```

but it doesn't appear to make any difference. The idea I had in mind was when /dev/input/mouse2 existed (because my bluetooth mouse connected) it would be symlinked to /dev/input/current, and when it went away it would go back to /dev/input/mouse1 which is apparently my sentellics touchpad.

---

### Post by mazz0 on 2009-08-18
What would happen if you renamed mouse1 so the system can't recognize it?  Might crash the system, but it might not!

---

