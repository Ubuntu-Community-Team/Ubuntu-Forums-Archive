---
title: "Problems with xorg synaptics driver after upgrading to feisty"
date: 2007-04-27
forum: Desktop Environments
---

### Post by j-lo on 2007-04-27
Hello,

I upgraded from edgy to feisty a week ago. Everything else has been a positive experience except for the following: The touchpad scrolling functionality (when sliding a finger on the right edge of the touchpad) stopped working. It had worked right out of the box in edgy, but now it's broken. The problem seem to be that xorg fails to load the synaptic driver. My laptop is a sony vaio sz. Here's the relevant part of xorg log file:

 (II) Synaptics touchpad driver version 0.14.6 (1406)
(**) Option "Device" "/dev/input/event2"
(**) Option "SHMConfig" "true"
(**) Option "LeftEdge" "120"
(**) Option "RightEdge" "930"
(**) Option "TopEdge" "120"
(**) Option "BottomEdge" "700"
(**) Option "VertScrollDelta" "10"
(**) Option "HorizScrollDelta" "0"
(**) Option "EdgeMotionMinSpeed" "200"
(**) Option "EdgeMotionMaxSpeed" "200"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "110"
(**) Option "ClickTime" "0"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "FingerLow" "14"
(**) Option "FingerHigh" "15"
(**) Option "UpDownScrolling" "1"
(**) Option "RTCornerButton" "2"
(**) Option "RBCornerButton" "3"
(**) Option "TapButton2" "2"
(**) Option "CircularScrolling" "0"
(**) Option "CircScrollTrigger" "2"
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

Is anybody else seeing this problem? Is there a patch maybe somewhere?

Thanks in advance, juhis

---

### Post by kiloxxx on 2007-04-30
Hello,
same problem here. After upgrade to feisty synaptics touchpad stopped to work. It works with common feature, but there is no scrolling and I can't configure it via ksynaptics. Also the second and the third buttons stopped to work (I have a Toshiba Satellite 5200-801).

Here the synaptics' Xorg.0.log session:

```
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 18 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "on"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
```


and the relative xorg.conf sessions:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
EndSection
```

Any help will be appreciated. Thanks

---

### Post by latle on 2007-05-01
Kiloxxx: Try to change the "SHMConfig" "on" to "SHMConfig" "true". Restart x and you should be able to use ksynaptics.

---

### Post by kiloxxx on 2007-05-01
I changed "SHMConfig" "on" with "SHMConfig" "true", but the problem is still there. The touchpad isn't recognised and ksynaptics still says "Shared Memory is not accessible. Please add the option 'SHMConfig 'on' into the touchpad section of /etc/X11/xorg.conf".

---

### Post by ZiVvmO on 2007-06-05
i have a very similar problem.  any time i try to use ksynaptics i get the shared memory error.  however, my scrolling still works, but ksynaptics crashes nearly every time i shutdown.  this also just started happening when i upgraded from edgy to feisty.

ill attach a trace...

---

### Post by Dzs on 2007-07-26
Hi everyone.
I was just fighting for approx. 4 hours with this ksynaptics SHMconfig problem. Finaly i reach some kind of success. I was trying lot of combinations, i was reading lot of config files, nowhere was even word about SHM anything. After that, i start playing with xorg.conf (again :) )

So working solution in xorg.conf is look like this :
....
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice" #Inteligent OS put here also /dev/psaux
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection
...

But just this funny change still didn`t help without next step. In the end (five minutes before this post) i tried to disable DMA for USB ports directly in BIOS. And "voila" it is working now. Its true, that I get each boot some nice and pretty error message (dmesg | tail -100) about problem with reseting synaptics, but configuration and also scrolling in all directions is working. I hope it will help to you as well. I will work on it in the future again because i have suspicion that problem is somewhere in configuration of UDEV.

Well what else can I say? Try it and leave me here your observations please.

So folks, for today, have a nice night, i will celebrate my succes with looong sleep.

Always yours Dzs.  :lolflag:



HP Compaq nx6310 1.8GHz 1.5Gigs of RAM.

---

### Post by mnewsom on 2007-07-27
Dzs, can you give some specific details for a noob. I'm getting the exact same error.

---

