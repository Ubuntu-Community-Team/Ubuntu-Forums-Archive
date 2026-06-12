---
title: "No backlight on Inspiron 6400"
date: 2008-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by georgm on 2008-11-11
After I upgraded to Intrepid Ibex, I started experiencing problems activating (or increasing?) my backlight on a Dell Inspiron 6400, preinstalled with Ubuntu (ordered from Germany), with Graphics Card Intel Media Accelerator 950 Up to 256MB of shared Memory for N-Series with TV and S-Video Output, Linux Only.

I have tried many different forums, following many different clues, but it hasn't worked. Here is a clue that suggests that this is not a hardware problem:
* Suspending and reviving causes the backlight to kick in for about 10 seconds, after which it disappears again.

Other information:
* Switching to a different virtual console and back (CTRL+ALT+F1 followed by CTRL+ALT+F7) does not affect the backlight.
* I installed the brightness applet. I can adjust the slide bar, but it doesn't effect anything.
* I am able to use Fn + Up and Fn + Down to change a slide bar, but it doesn't effect anything. I also note that this control jumps in big chunks (meaning that there are about 3 different settings possible).
* I tried using xgamma and xbacklight. xgamma seems to affect the contrast, while xbacklight doesn't do anything.
* I tried adjusting the backlight from a liveCD with no effect.
* I restored to factory install and here there was no backlight (also not after updating). 
* I downloaded a Hardy Heron liveCD and did a full reinstall, but still no backlight. This is the install I'm working on now.
* Hardware Drivers says that I do not have any proprietary drivers on my system.
* Here is my xorg.conf:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

My current install is Hardy Heron. Needless to say, I'm getting desperate. It is hard to read the screen without backlight. Please help me! :)

---

### Post by Linicks on 2008-11-11
Two things stand out.

You state that problems started AFTER the upgrade?  So it wasn't immediate?

Second, booting from a live CD makes no difference?

If this is the case, I guess the backlight really has blown.

Nick

---

### Post by georgm on 2008-11-11
Thanks for your post.

After the update I noticed that I didn't have any control over the backlight anymore. I do not remember if this was the first day or the second. Sometimes the backlight would be on for a while and sometimes off, but the gnome-power-manager didn't do anything anymore. Now starting the computer often begins with some backlight, which disappears after a couple of seconds. And booting from a liveCD indeed doesn't make any difference...

I wish there was a way to "directly" turn on the backlight, and keep it on, to test if this is still possible. Is there a way to tell this directly to the hardware?

---

### Post by Linicks on 2008-11-11
Well, I meant if a live CD doesn't make it work, then I suspect the backlight has failed!

It it has failed, then nothing will make it work.  In your original post you said you tried several things (re-install, live CD etc.) and nothing works now, so I would really think it's a hardware issue.

But I don't know how to test for that - nor how you can prove it other than what you have tried.

What happens if you go into BIOS setup screen - is it on then?

Nick

---

### Post by georgm on 2008-11-12
Backlight is on!

Yesterday when I wanted to watch a movie on an external screen, I used Fn + F8 to switch between screens. This caused the backlight to start and I now regained control over the intensity. After this I recalled that the problems started after I had switched screens in Intrepid Ibex, where the option didn't seem to work. My guess is that Fn + F8 set something on the hardware level, and I now set it back.

This has been the most bizarre bug I have ever encountered. Again, thanks for your replies.

---

### Post by selllwow on 2008-11-12
[size=2][color=#282827][color=#000000][sell wow gold](http://www.virdeal.com), [sell gaia gold](http://www.virdeal.com), [sell ffxi gil](http://www.virdeal.com), [sell maple story mesos](http://www.virdeal.com) [http://www.virdeal.com](http://www.virdeal.com) [/color][/color][/size]

---

