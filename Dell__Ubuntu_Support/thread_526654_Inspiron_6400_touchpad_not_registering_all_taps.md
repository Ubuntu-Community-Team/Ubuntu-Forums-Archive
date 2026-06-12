---
title: "Inspiron 6400 touchpad not registering all taps"
date: 2007-08-15
forum: Dell  Ubuntu Support
---

### Post by bkraptor on 2007-08-15
It has a Synaptics touchpad and I figured out how to tweak all the settings with synclient and qsynaptics. But there's one thing that bothers me that I haven't been able to solve by myself: I use tap-to-click quite a lot (love it!) but the problem is that taps aren't always recognized, depending on how I tap. If it's a 100% sharp vertical tap there's a pretty good chance it will be recognized as a tap, but if I drag the finger just microns it won't get recognized as a tap and won't do anything. I tried tweaking ALL the settings with synclient but I didn't manage to make it register all the taps. I dual boot this laptop with WinXPSP2 and so I know the touchpad works perfectly fine with the Windows driver, so it's not a hardware issue.

Here's my xorg.conf:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"on"

	Option		"ClickTime"		"100"
	Option		"FastTaps" 		"1"
	Option		"PalmDetect"		"1"
	Option		"PalmMinWidth"		"10"
	Option		"PalmMinZ"		"200"

	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"LTCornerButton"	"0"
	Option		"LBCornerButton"	"0"

	Option		"VertScrollDelta"	"100"
	Option		"HorizScrollDelta"	"0"

	Option		"MinSpeed"		"0.09"
	Option		"MaxSpeed"		"0.18"
	Option		"AccelFactor"		"0.0015"
EndSection 
```

---

### Post by mirceade on 2007-08-16
I don't think this is exactly what you need but it might be related -> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/47971](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/47971)

---

### Post by strabes on 2007-08-16
Just install gsynaptics and use it to configure your touchpad. It has a lot of options.

---

### Post by bkraptor on 2007-08-16
gsynaptics and qsynaptics perform the same things: modify parameters of the synaptics driver. If you could point out exactly what parameter to modify that would help me a lot.

---

### Post by bkraptor on 2007-08-16
Okay I think I have found a bug:

by watching the output of "synclient -m 10" I have been able to find a pattern, when taps are registered and when they're not. I have found that every time a tap is not registered there is a weird "1" appearing on the X column and a "5855" on the Y column, meaning that my touchpad registered touch at the (1,5855) coordinates. This, coupled with the MaxTapMove=220 (default), means that it will register a movement during my tap and as such it will invalidate it as a tap.

Can anyone point me to where I could file a bug regarding this issue?

Attached is the output of a few of those taps.

---

### Post by bkraptor on 2007-08-18
Hmm... I filed a bug report, but nobody has bothered looking at it yet.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/133060](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/133060)

Is there something wrong that I did?

---

### Post by strabes on 2007-08-18
Can you just use the actual buttons on your laptop temporarily? I use them most of the time anyway.

---

### Post by bkraptor on 2007-08-19
I would, and am using them until a solution comes up. But I've been using tap-to-click in windows for a while and I kinda got used to it, and it becomes frustrating at first.

---

### Post by Jasman on 2007-11-10
bkraptor, I just found this thread, and finally someone who knows what they're doing has caught on to the problem with this touchpad in Ubuntu (and I should say, it's in any distro I've tried with this laptop). I've had several laptops and used several distros, and it's only with the e1505/6400 that the touchpad has such sensitivity issues. I agree that it works fine under Windows (either XP or Vista), so it must be a bug in the Linux Synaptics driver. I guess the thing to do would be to try to issue your bug with the maintainers of that driver, not with Ubuntu specifically. If I can figure out how to do that, I'll repost. Thanks.

---

### Post by Jasman on 2007-11-10
Now I see there's a "fix" of sorts in that bug report and, amazingly, it seems to solve the problem. Follow the steps near the bottom of the thread, and your Inspiron e1505 / 6400 touchpad will behave much better.

---

