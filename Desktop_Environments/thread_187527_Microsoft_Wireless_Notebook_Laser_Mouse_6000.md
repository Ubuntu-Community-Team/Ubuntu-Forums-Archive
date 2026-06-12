---
title: "Microsoft Wireless Notebook Laser Mouse 6000"
date: 2006-06-03
forum: Desktop Environments
---

### Post by firecrotch on 2006-06-03
Hi,

I'm trying to get my Microsoft Wireless Notebook Laser Mouse 6000 to work fully in Dapper, and I have no clue where to begin.  The mouse features a scroll wheel with tilt-wheel function, and a side button on the left hand side.  The scroll feature works properly, as do the normal two buttons and clicking with the scroll-wheel as the middle mouse button.  The thumb button does not do anything, nor does tilting the wheel left or right.  xev gives the following output for the thumb button:

```
ButtonPress event, serial 28, synthetic NO, window 0x1200001,
    root 0x4c, subw 0x0, time 2583836729, (81,66), root:(923,569),
    state 0x0, button 9, same_screen YES

ButtonRelease event, serial 28, synthetic NO, window 0x1200001,
    root 0x4c, subw 0x0, time 2583836921, (81,66), root:(923,569),
    state 0x0, button 9, same_screen YES

```

There is no output in xev for tilting the wheel in either direction.

The following is the mouse section from my xorg.conf file:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

Previous discussion of this problem can be found here: [http://ubuntuforums.org/showthread.php?t=165068](http://ubuntuforums.org/showthread.php?t=165068)

Note that that thread was made while I was using Breezy.  Any help would be greatly appreciated!

---

