---
title: "Gnome desktop fails to start after login"
date: 2006-08-18
forum: Desktop Environments
---

### Post by satimis on 2006-08-18
Hi folks,

For unknow reason, Gnome desktop fails to start after login, only the mouse pointer hanging.  Switching to runlevel 3 with [Ctrl]+[Alt]+F4 functions


Looked at /etc/X11/xorg.conf and found;

Section "Monitor"
Identifier "Genteric Monitor"
Options "DPMS"
HosizSync 28-64

Not indicating the running monitor "Philips 190B"


Section "Screen"
SubSection 1
Depth     1
Modes    "1280x1024" "1024x768" "800x600" etc
EndSubSection

etc.

SubSection 16
Depth     16
Modes    "1280x1024" "1024x768" "800x600" etc.
EndSubSection
SubSection 24
Depth     24
Modes    "1280x1024" "1024x768" "800x600" etc.
EndSubSection


Removed all SubSections leaving only SubSection 16 and 24.  Also removed all resolution only retaining "1280x1024" "1024x768"

But problem still remains, x-window failed to start.

Please advise.  TIA


B.R.
satimis

---

### Post by murataht on 2006-08-18
do you mean gdm starts but gnome does not? or both of them don't start?
maybe look for the x log files will provide you with some useful information.
or post the error messages here to ask help from others.

good luck

Murat

---

### Post by satimis on 2006-08-18
Hi murat,

> do you mean gdm starts but gnome does not? or both of them don't start?
Initially gdm/login page can start.  Only X-window/gnome failed to start.  After working a while trying to fix the problem, now both of them can't start.

/var/log/Xorg.log```
...
....
Option "Device" "/dev/wacom"
(EE) xf860OpenSerial:cannot open /dev/wacom
no such file or directory
Error opening /dev/wacom No such file of directory
```
the above message repeated continuously.

I don't have Wacom tablet.

/etc/X11/xorg.conf```
....
....
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection
.....

```

B.R.
satimis

---

### Post by niko7865 on 2006-08-18
I'm getting the same error, was wondering if there is a way to install an older kernel without useing sudo commands (I can log into the terminal but sudo commands cause it to hang). In another thread they suggested it was the buggy -26- kernel so I'm going to try useing an older version to see if that fixes it.

Edit: I was able to boot back into gnome by going into recovery and running dpkg-reconfigure xserver-xorg a couple of times. I'm afraid to reboot incase it's just a temporary fix and it stopped xgl/compiz from working.

---

### Post by niko7865 on 2006-08-21
Ya it definatly wasn't that, must have just been a coincidence that it worked after reconfiging xserver. I think it's haning at something like "Loading Startup Scripts (etc/rc.local)" Wrong wording but it's something to that extent. Thats the last thing that shows up when i try logging in, let it hang for awhile at the brown screen and mouse pointer, and then hit Control + Alt + Backspace.

---

### Post by satimis on 2006-08-21
Hi niko7865,

Tks for your advice.

Now my case maybe differ from yours.  gdm does not start, no login page.  The mouse cursor/pointer only hangs on a black screen.

"hit Control + Alt + Backspace" did not work here.

B.R.
satimis

---

### Post by niko7865 on 2006-08-21
Well your description sounded the same in your first post, how you're able to log in and then you just get a mouse pointer. Anyway I hope we can resolve the issue(s) soon, I hate beign stuck on windows :(

---

### Post by satimis on 2006-08-21
Hi niko7865,

I leave the problem there unsolved is solely for learning.  In fact it is better to erase it and start over again, much easier.  I have confidence to get it right after reinstallation.  But I can't guaranttee this problem won't reoccure.

I'll start over soon.  This HD is for testing software only therefore I can leave the problem there for a while.

B.R.
satimis

---

### Post by xtknight on 2006-08-21
Try using the vesa driver in Xorg.conf.

---

### Post by satimis on 2006-08-21
Hi xtknight,

Tks for your advice.

> Try using the vesa driver in Xorg.conf.
Sorry I don't catch it.  How to get it done?  Tks.

Before problem started, Ubuntu was running without much problem.  I don't know how this problem started.  After lunch on turning on the PC, this problem started.

First unabled to start X-window.  After tuning the OS a while even gdm failed to work.

B.R.
satimis

---

### Post by xtknight on 2006-08-21
Try these commands:

sudo apt-get install xserver-xorg --reinstall
sudo apt-get install gdm --reinstall

sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure gdm

Can you post your whole Xorg.conf file here?  Maybe you're already using the vesa driver.

---

### Post by satimis on 2006-08-21
Hi xtknight,

Ran
$ sudo apt-get install xserver-xorg --reinstall
Copied files from installCD

$ sudo apt-get install gdm --reinstall
Supposed it copied files from Internet

$ sudo dpkg-reconfigure xserver-xorg
Went through w/o problem

$ sudo dpkg-reconfigure gdm
It went back to gdm starting page, a black screen with live mouse pointer on it (can be moved).

So switched to text-mode again and ran
$ sudo shutdown -r now

This time Ubuntu failed to boot hanging on```

....
Uncompressing Linux .... OK, booting the kernel
```

Pressed "reset" to force-reboot PC.  Now this time it started to boot hanging on;```

Loading essential drivers OK
Mounting root file system ......
```


/etc/X11/xorg.conf (copied before Ubuntu failed to boot```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc102"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
	VideoRam	64000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
```



Pressed "reset" to force-reboot PC again.  This time selected "Rescue Mode".  It booted hanging on;```

....
.....
ohci_hcd 000:00:0b:0)OHCI Host Controller
```

B.R.
satimis

---

### Post by xtknight on 2006-08-21
If you can't get to a console your most time-effective way of fixing this is probably to just back up your files and reinstall.  I'm not sure what's going on but something must have been corrupted.

---

### Post by niko7865 on 2006-08-21
I've reinstalled quite a few times and always get this problem, however I did not have this problem with previous kernels. I suppose I'll just wait till the ISO is updated with a newer kernel and download and install that.

---

### Post by satimis on 2006-08-21
Hi folks,

This PC is for testing purpose so no important data are there.  I'll erase Ubuntu soon.

Tks.

B.R.
satimis

---

