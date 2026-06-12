---
title: "Resolution problem"
date: 2009-05-30
forum: General Help
---

### Post by BmxITguru on 2009-05-30
Have a new HP w2207h  that im trying to use with and ubuntu 9.04 install. When plugged into the monitor it gives an message saying input out of range please set resolution to 1680 x 1050. things that i have tried to resolve this issue is to (1) plug into a different monitor and it work fine with a lower res. (2) follwed a couple google hits to reconfigure the /etc/X11/xorg.conf file manually to set the resolution to the correct size for the monitor yet it still does not work and throws out the same error when plugged into the HP monitor. 

specs to help resolve issue:
HP Pavilion with AMD phenom x4 64 bit
Installed and working copy of Ubuntu 9.04 X64
Nividia GeForce 6150 se 
4gb ram

---

### Post by sigixv on 2009-05-30
did you plug the monitor in when logged in or before?

i can only get stuff on my vga port configured by plugging it in and logging back in. The gui configuration tool doesn't work for me, always have to set my xorg and log back in

apparently big resolutions are a common problem but try this[ https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")[URL="https://wiki.ubuntu.com/X/Config/Resolution"]
[/URL]

---

### Post by BmxITguru on 2009-06-01
yes, I have tried multiple different resolution settings and have switched it between monitors both at the login screen and after logging in.

---

### Post by Legace on 2009-06-01
What is the refresh rate for your monitor?

---

### Post by BmxITguru on 2009-06-01
60 hz

---

### Post by Legace on 2009-06-01
Try a xorg.conf like this:

```
Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline        "1680x1050"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes      "1680x1050"
		Virtual	1680 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

---

