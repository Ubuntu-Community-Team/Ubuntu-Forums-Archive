---
title: "[Help] I can't increase the refresh rate to 75 Hz"
date: 2008-08-20
forum: Desktop Environments
---

### Post by congminh1709 on 2008-08-20
I am using Ubuntu 8.04 x86_64, and i have this hardware

- Mainboard: ECS 945GCT-M2/1333

- Display Adapter: Integrated Intel® Graphics Media Accelerator 950 ( GMA950 )

- Monitor: Dell D1025TM -> [http://support.dell.com/support/edocs/monitors/55341/specs.htm](http://support.dell.com/support/edocs/monitors/55341/specs.htm)
This is Scanning Frequency of my monitor
Horizontal 	30 to 85 kHz
Vertical 	50 to 120 Hz

- With this hardware, on Windows XP SP3, i can use the resolution 1024 x 768 pixels and 75 Hz refesh rate well, but in Ubuntu i can't change the refesh rate to higher than 60 Hz.

- Follows the intrunction in this tip -> [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) , I edited the file /etc/X11/xorg.conf
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

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
[COLOR="Red"]	HorizSync          30-85
     	VertRefresh        50-120[/COLOR]

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

After that, i restarted PC. And when go to System -> Preferences -> Screen Resolution, i can see the option to change refresh rate to 75Hz. I selected this option (75 Hz) and apply, the screen can use this refresh rate in 1 s, but after that it appears a black screen and the monitor is switched off ( Oh, no, .... T_T) 

I turned off the power and restarted PC, Ubuntu used 60 Hz refresh rate again. 

Now, how to increase the refresh rate of my monitor to 75Hz in Ubuntu? Thank for reading my post.

---

### Post by Potatoj316 on 2008-08-20
why do you want the refresh rate so high?  its harder for LCD screens to have high refresh rates like that and may actually damage them.  I really doubt you will see any difference in anything with a change from 60Hz to 75Hz.

if you are seeing flickering than i really doubt it is because your refresh rate is 60Hz, your eye cant refresh that fast.

---

### Post by congminh1709 on 2008-08-20
When i use this CRT monitor at Windows XP SP 3 with 75 Hz refresh rate, my eyes feel comfortable, but in Ubuntu i can't use this 75 Hz (only 60 Hz), and i can see flickering *_*

---

