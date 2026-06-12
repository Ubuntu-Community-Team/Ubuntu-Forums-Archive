---
title: "Touchpad not working, Inspirion 1525n w/ 8.04"
date: 2008-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tylersontag on 2008-04-25
I just upgraded to the final release version of Hardy Hareon from 7.10 on my Dellbuntu Inspirion 1525n and i was all set.  The compiz team fixed it so i could watch movies and have my cube, had everything working perfect.  I even was able to turn on a screensaver, since the video problem had made that impossible.

So the first time it kicks into screensaver mode i look over, i have it on "Flocks" and its running smooth and looking amazing it had been running a while but i was so mesmerized i just stared for a few seconds talking to a friend of mine.  Then the screen locked up with in a multicolor static.  I tried switching to terminal 1 or 2, couldn't system was completely locked up so i had no choice but to cold boot it.

When i turned it back on, the touchpad would not work, everything else seems fine, i plugged in my USB mouse and it works.  The buttons on the touch pad work, just not the pad itself.  I don't understand what could have broken it.  Any ideas?

heres hte pertaining lines of my xorg file
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

---

### Post by tylersontag on 2008-04-26
sorry for the double post, but i found a fix for my problem, posted at the Hardware/Laptops forums.

[http://ubuntuforums.org/showthread.php?t=767720](http://ubuntuforums.org/showthread.php?t=767720)

This problem was odd, perhaps just some new release jitters

---

