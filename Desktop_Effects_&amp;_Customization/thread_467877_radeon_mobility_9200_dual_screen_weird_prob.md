---
title: "radeon mobility 9200 dual screen weird prob"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by xor.be on 2007-06-08
Hello all,

I've been fighting for DAYS with this now :(
i must have a zillion xorg.conf.backups :p

all i want to do is extendmy lcd from my laptop.
the closest i got now is that when i boot,my lcd (on the right) shows the login, and the laptop screen shows the backgruond color,and a vertical line when i move my mouse.

Then i'm able to use either one, or BOTH .. (clone)

But not extend .. 

Could somebody PLEASE have a quick look at my very basic (now) xorg.conf file ..
It must be something really small :(

```
Section "Device"
	Identifier	"ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Secondary Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device		"ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)]"
	Monitor		"Secondary Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"2 screen layout"
	Screen		1 "Default Screen"
	Screen 		0 "Secondary Screen" RightOf "Default Screen"
	Option		"Xinerama" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
    Option    "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Soybean on 2007-06-08
> **xor.be said:**
> the closest i got now is that when i boot,my lcd (on the right) shows the login, and the laptop screen shows the backgruond color,and a vertical line when i move my mouse.
Hmm. Can you clarify this a bit? At the login screen, if everything's working correctly, you *should* have one screen with the standard login stuff, and the other screen just showing the background color. So that sounds ok.

But then, what's this about a vertical line? Is it like, the mouse works fine on one screen, but does something crazy on the other? Or the mouse just doesn't work right at all, anywhere? And what happens if you log in?

Just glancing over your xorg.conf, nothing stands out as a problem. But I used Xinerama a couple of years ago, and I remember that some of those settings seemed pretty finnicky in ways that I didn't really understand. 

So. I don't know what the problem is, but I can give a couple of general "debugging X" tips:
1) Check the logs for warnings/errors (I think /var/log/Xorg.* is your best bet). They're not always very clear, but they can be helpful.
2) I assume your xorg.conf is based on an example you found somewhere... try finding a different example somewhere else, and basing it on that. It's a "guess and test" method, but at least the guesses are based on something that worked for someone at least once. ;)
3) When it boots, if you've got a mouse cursor on one screen or the other, try moving it off both sides of the screen. I remember with Xinerama, the last thing I got working was screen placement. During the whole "almost working" stage, it kept identifying the screens differently than I expected it to, so they'd often end up reversed. Might've just been me, but it's worth checking.

EDIT: Should the Identifiers in the Device sections be different from one another? I'm not actually sure -- maybe they shouldn't, where it's the same card (or something) -- but it seems to me like they ought to be different so that the file can clearly identify which screen is attached to which device.

EDIT 2: Another thought: try it with lower resolutions. If it IS getting your monitors confused, where one has a higher resolution than the other, things could get wonky. Pick some lower resolution that you're sure both screens can handle happily, until you've got things working.

---

