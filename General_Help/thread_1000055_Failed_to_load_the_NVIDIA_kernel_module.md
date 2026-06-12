---
title: "Failed to load the NVIDIA kernel module"
date: 2008-12-02
forum: General Help
---

### Post by Musicalmidget on 2008-12-02
Since I _[rebuilt my xorg.conf file](http://ubuntuforums.org/showpost.php?p=6225297&postcount=7)_ a couple of weeks ago, I've been using Ubuntu daily without any problems.  I have two identical monitors attached to my computer.

A couple of days ago, I started up Ubuntu as normal and was presented with a message when Gnome began to load, stating that the system was running in low graphics mode.  These were the details in the message.

> (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration

I can start Ubuntu up in safe graphics mode and only use one screen but this isn't ideal for the way I generally use Ubuntu.  I've tried booting into Windows and can confirm that the monitor hasn't died.  I can still use both monitors Windows without any issue.  This issue only began a short time ago and I'm not aware of any change to the system which could have caused it.  I am using the latest Nvidia drivers for x64 Linux.

Any suggestions on how to go about getting both screens working again would be most appreciated as I've been unable to find a solution myself so far.

For reference, I'll post the contents of my xorg.conf file below.

```
Section "ServerLayout"
   	Identifier     "Default Layout"
	Screen		0  "Left Monitor"  0	   0
	Screen		1  "Right Monitor"  RightOf  "Left Monitor"
	InputDevice    "Keyboard0"	"CoreKeyboard"
	InputDevice    "Mouse0"		"CorePointer"
	Option		"Xinerama"	"Off"
	Option		"Clone"		"On"
EndSection

Section "InputDevice"
	# generated from default
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	# generated from default
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier	"Primary Monitor"
	VendorName	"HannsG"
	ModelName	"HU196D"
	HorizSync	30.0 - 80.0
	VertRefresh	50.0 - 75.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Secondary Monitor"
	VendorName	"HannsG"
	ModelName	"HU196D"
	HorizSync	30.0 - 80.0
	VertRefresh	50.0 - 75.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 8800 GT"
	BusID          "PCI:7:0:0"
	Screen          0
EndSection

Section "Screen"
	Identifier	"Left Monitor"
	Device		"Device0"
	Monitor		"Primary Monitor"
	DefaultDepth	24
	Option		"TwinView"	"1"
	SubSection "Display"
	    Depth	24
	    Modes	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Right Monitor"
	Device		"Device0"
	Monitor		"Secondary Monitor"
	DefaultDepth	24
	Option		"TwinView"	"1"
	SubSection "Display"
	    Depth	24
	    Modes	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by laceration on 2008-12-02
Just glancing it looks like your conf file is in order.  Why not try reinstalling the nvidia drivers?  Envy is the easiest + best way to do it.  Here's the website:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

If want to search on these forums I'm sure there is plenty of stuff too.  

As to what caused it, there was kernel upgrade for 8.04 a couple of days ago???

---

### Post by Musicalmidget on 2008-12-03
Thanks!  I still had a copy of the latest Nvidia driver on the machine so I reinstalled it and all is well once again.  I don't know why I didn't think of that before.

Now that I think back, I do recall downloading and installing a large number of updates to the system a few days ago including a new kernel.  This was probably the last time I used to machine before the problem began so I suspect you're probably right and something in the latest batch of updates must have somehow caused the error.

Many thanks for the help. :)

---

