---
title: "evdev mouse protocol not sending ButtonPress events"
date: 2005-11-02
forum: Desktop Environments
---

### Post by iH8forcedRegistration on 2005-11-02
I've spent the past 2 days trying to make my new mouse work. My early attempts are detailed in [a thread I now feel dumb for having posted in the first place and which really is probably not worth reading at this point.]("http://ubuntuforums.org/showthread.php?t=85157")

At this point, I'd say I'm pretty close to having my mouse work the way I want it to. The only problem is that for buttons 1 and 3, I don't receive a ButtonPress event until I release the button, at which point I receive both ButtonPress and ButtonRelease events at once, making the act of 'dragging' impossible. At the moment, I've used xmodmap to make button 2 (which works normally) act as button 1, just so that I can actually use the computer, but since button 2 is my scroll wheel, it's becoming annoying very quickly to use it.

Here's the relevant section in my xorg.conf:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/event0"
	Option		"Protocol"		"evdev"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5 7 6"
    Option      "Buttons" "12" 
    Option      "Dev Name" "Logitech USB Receiver"
    Option      "Dev Phys" "usb-0000:00:03.0-1/input0"
EndSection

```

Someone please help my interminable mouse configuration ordeal finally come to an end!

---

### Post by iH8forcedRegistration on 2005-11-02
I showed this to a mac-user friend of mine, who's never actually done anything with xorg.conf before, and he found the problem right away. Removing the line
```
Option		"Emulate3Buttons"	"true"
```
fixed the problem.

Sorry for wasting everybody's time.

---

