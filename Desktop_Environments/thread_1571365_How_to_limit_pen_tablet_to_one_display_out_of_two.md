---
title: "How to limit pen tablet to one display out of two?"
date: 2010-09-09
forum: Desktop Environments
---

### Post by 1script on 2010-09-09
Hi all, this task got me scratchin' my head hard now knowing where to start, so any idea that may push me in the right direction will be greatly appreciated.

I'm running a 

Release 10.04(lucid)
Kernel Linux 2.6.32-24-generic
GNOME 2.30.2

Using NVIDIA Driver Version 195.36.24 with two monitors 1280x1024 each in TwinView configuration

My Pen tablet is ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet, Wizardpen driver (not sure how to lookup its version)

The tablet is currently working just fine except for this one thing I'm trying to fix: it now covers the entire 2560 pixel width of the desktop and 1024 pixel height. Given that the tablet itself has a 4x3 side ratio, it results in its horizontal resolution being half of the vertical one. Basically, when you use it to draw anything you always have to mentally correct what you do by limiting your horizontal movements to only half of vertical ones which makes drawing a (relatively) straight line an impossible task. 

So, this got me thinking that I want to make sure the tablet only works on one of the two displays - the one I'd open Gimp and Inkscape on - the only two programs I ever use the tablet with.  However, when I look at the calibration settings of the tablet itself, it only allows me to limit the area of the tablet I want to be sensitive, not the area of display. I cannot find any such settings in NVIDIA X Server Settings either although I think this is where it might have been.

So, does anyone know how to leave the same size of the tablet drawing area but make it move the cursor only on one particular monitor in TwinView configuration?

Thank you for all your suggestions!

---

### Post by shadarack on 2010-12-26
I have the same issue, but with a genius pensketch 9x12 and a 3200x900 display. No clue how to limit it to one monitor, but would a possible workaround be to change the area of the tablet that is sensitive to match the dimensions of your desktop? This would mean giving up a big chunk of your tablet, but would at least make it usable, yes?

Only problem is, I have no clue how to do that. I followed the tutorial here to get my tablet working:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

but bzr is not working for me for some reason - I suspect a server may be down, so I cannot install the calibration tool. No clue how to manually configure xorg.conf to calibrate my tablet properly without it.

---

### Post by Favux on 2010-12-26
Hi shadarack,

I don't know either.  Maybe we can figure it out.  Enter in a terminal:
```
xinput --list
```
and then post its output.  Then using the "Device name" it uses for your stylus let's look at:
```
xinput list-props "Device name"
```
using the quotes around the Device name and post its output.  Let's see if we can use xinput to set or map to the screen.

---

### Post by shadarack on 2010-12-28
Ack! I was so not expecting such a swift response! Here you go:

xinput --list results in:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet             	id=10	[slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet             	id=11	[slave  pointer  (2)]
&#9116;   &#8627;                 9x12 Tablet             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse             	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=8	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=9	[slave  keyboard (3)]
```

```
xinput list-props "                 9x12 Tablet" gives me:
```

```

Device '                9x12 Tablet':
	Device Enabled (121):	1
	Device Accel Profile (242):	0
	Device Accel Constant Deceleration (243):	1.000000
	Device Accel Adaptive Deceleration (245):	1.000000
	Device Accel Velocity Scaling (246):	10.000000
	Evdev Reopen Attempts (236):	10
	Evdev Axis Inversion (247):	0, 0
	Evdev Axis Calibration (248):	<no items>
	Evdev Axes Swap (249):	0
	Axis Labels (250):	"Abs X" (239), "Abs Y" (240), "Abs Pressure" (241)
	Button Labels (251):	"Button 0" (238), "Button Unknown" (237), "Button Unknown" (237), "Button Wheel Up" (125), "Button Wheel Down" (126)
	Evdev Middle Button Emulation (252):	2
	Evdev Middle Button Timeout (253):	50
	Evdev Wheel Emulation (254):	0
	Evdev Wheel Emulation Axes (255):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (256):	10
	Evdev Wheel Emulation Timeout (257):	200
	Evdev Wheel Emulation Button (258):	4
	Evdev Drag Lock Buttons (259):	0

```

---

### Post by Favux on 2010-12-28
Hi Hi shadarack,

Doesn't look like much to work with.  What is your video chipset?:
```
lspci | grep VGA
```
and what video driver are you using?  Did it add entries into the xorg.conf in /etc/X11?

But first we need to take a step back.  The list-props seems to indicated that your tablet is on the evdev failsafe driver, not WizardPen.  So let's deal with that first.  What is your tablet line look like from?:
```
lsusb
```

---

### Post by shadarack on 2010-12-28
My video chipset is Nvidia. Specifically:

```
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
```

If it makes any sort of difference, I'm running a dual monitor setup at 3200 x 900 resolution, twinview.

As for the Wizardpen driver, I'm actually rather surprised at that. I did follow a tutorial that had me install the drivers. I was not aware that Ubuntu had incorporated any sort of default working drivers for tablets! Last time I tried to install a tablet(a few years ago, also a wizardpen tablet), it didn't work until I had working drivers for it. Regardless, lsusb gives this return:

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 5543:0042 UC-Logic Technology Corp. Tablet PF1209
Bus 004 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Favux on 2010-12-29
Are you using the Nvidia proprietary drivers?

Alright, it's a UC-Logic tablet.  What WizardPen driver did you install and how?  Also we should take a look at your 70-wizardpen.conf at /usr/lib/X11/xorg.conf.d/.  Please post it.

---

### Post by SnickerSnack on 2010-12-29
I am having the same issue with a wacom based tablet.  I can make a new thread or wait my turn in this one if that's better.

Here's my info:

```
zsharon@Weierstrass:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                     	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Gaming Mouse               	id=9	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

```

```
zsharon@Weierstrass:~$ xinput list-props "Serial Wacom Tablet"
Device 'Serial Wacom Tablet':
	Device Enabled (135):	1
	Device Accel Profile (257):	0
	Device Accel Constant Deceleration (258):	1.000000
	Device Accel Adaptive Deceleration (260):	1.000000
	Device Accel Velocity Scaling (261):	10.000000
	Wacom Tablet Area (282):	0, 0, 24576, 18432
	Wacom Rotation (283):	0
	Wacom Pressurecurve (284):	0, 0, 100, 100
	Wacom Serial IDs (285):	144, 0, 2, 0
	Wacom TwinView Resolution (286):	0, 0, 0, 0
	Wacom Display Options (287):	-1, 0, 1
	Wacom Screen Area (288):	0, 0, 1024, 768
	Wacom Proximity Threshold (289):	0
	Wacom Capacity (290):	-1
	Wacom Pressure Threshold (291):	7
	Wacom Sample and Suppress (292):	2, 4
	Wacom Enable Touch (293):	0
	Wacom Hover Click (294):	1
	Wacom Tool Type (295):	"STYLUS" (297)
	Wacom Button Actions (296):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

I can try some guesswork with these settings...

EDIT: Okay, I've pushed a few things around to regain some familiarity, but I'm not sure how to change only one of the settings in a list, like this one:

Wacom Screen Area (288):	0, 0, 1024, 768

I don't want to break anything, so I'm going to google around before trying...




EDIT: This might be useful

zsharon@Weierstrass:/usr/bin$ xsetwacom list param
.
.
.
.
mmonitor         - Turns on/off across monitor movement in multi-monitor desktop, default is on

This didn't seem to work:

zsharon@Weierstrass:/usr/bin$ xsetwacom --set 13 mmonitor 0

---

### Post by Favux on 2010-12-29
Hi SnickerSnack, good to hear from you again,

Partly it depends on which release of Ubunutu you are in and what version of xf86-input-wacom.

The multimonitor support has been dropped with 0.10.9 xf86-input-wacom and up but we are given a new command:
```
xsetwacom set <device name> "MapToOutput" VGA1
```
As an example.  You'd use the output device you want of course.  So we should know your video chipset, driver, and xrandr output.  I don't think we need to look at 'xrandr -q --verbose':
```
xrandr
```
The problem is with using it we've been getting an error.  I think I may have figured out the problem.

So if you have updated past the default 0.10.8 in Maverick try the command and let's see what error you get.

If you are still with the default we can try some of the old xsetwacom commands.  But the Xorg developer working on xf86-input-wacom was commenting that they were broken anyway as he dropped them.  However some people were reporting being able to use them.

---

### Post by SnickerSnack on 2010-12-29
> **Favux said:**
> Hi SnickerSnack, good to hear from you again,

You too.  I also stumbled on some of your comments [-Pen-tablet-causes-Save-As-dialog-problem.html"]here (link)]("http://www.allquests.com/question/4014622/[ubuntu) as I'm having a bit of trouble with GIMP as well.  I've just about nailed down an issue that I'll soon post a description of here to make sure I'm not overlooking something, and then I'll submit a bug report if needed.

> **Favux said:**
> Partly it depends on which release of Ubunutu you are in and what version of xf86-input-wacom.

I'm still using 10.04 Lucid and xserver-xorg-input-wacom 1:0.10.5-0ubuntu4.  As far as I know, I don't have xf86-input-wacom installed.  I should probably update, but I haven't taken the time to see whether doing so would break anything I've set up.  Sigh...I guess it's time.  I'll do that and see about this problem afterward.

Thanks.

---

### Post by Favux on 2010-12-29
In Lucid you have the default 0.10.5 xf86-input-wacom.  And it still has the multimonitor support.  Confusingly the package name it and xsetwacom are in is called xserver-xorg-input-wacom.  The same package name they were using in Karmic and earlier for linuxwacom.

While it still allegedly has multimonitor support they rewrote xsetwacom for xf86-input-wacom.  And 0.10.5 is practically the first release.  So xsetwacom was still feature incomplete and a lot of it is broken.  I really don't know what to advise you to do.

I guess I'd try xsetwacom commands until I was convinced they don't work and then clone the git repository to get the latest and start over with it and the alleged new method.  See part II. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") or section 2 of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Edit:  Oops!  Looks like I'm wrong.  I just read the new method apparently relies on a property added to X server l.9 so you won't be able to use it in Lucid (1.7).  If I remember right there were some commits finally fixing all of the mapping stuff right before it was all removed.  So we need to figure out when that was and you could download a snapshot of that last multimonitor commit and use that.

---

### Post by shadarack on 2010-12-29
Hmmmm. I thought I was using the Envy Nvidia drivers, but looking at my Nvidia Xserver console, it doesn't say anything about Envy and it appears I no longer have it installed. I guess sometime in the past when I had to reinstall things I stopped using Envy. I'm using the Nvidia driver verison 195.36.24 if that helps.

As for the Wizardpen drivers, I'm not 100% sure what the proper name for the driver is. According to the tutorial I followed, I added the following line to my sources list:
```
ppa:doctormo/xorg-wizardpen 
```

And then used the following command line commands:

```
sudo apt-get update
sudo apt-get install xserver-xorg-input-wizardpen
```

I rebooted my system and plugged the tablet in, and it worked, except of course that since my tablet proportions are so different from my screen proportions that everything is stretched horizontally.

70-wizardpen.conf reads as follows:

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection
```

I'm pretty sure that that file was created by myself rather then any automated process. I seem to recall following a tutorial that did not fix the issue, but I did not remove the 70-wizardpen.conf file it had me create since it didn't appear to make any difference in the way the tablet acted at that time.

---

### Post by Favux on 2010-12-29
Ok, try changing the 70-wizardpen.conf to:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
And see what that does to 'xinput --list' and the list-props command.  By the way you can also see if it is on the right driver by looking at Xorg.0.log in /var/log.

---

### Post by shadarack on 2010-12-29
Made the changes to 70-wizardpen.conf and there was no changes to xinput --list

Does this require I restart X for the new configuration file to be put to use? I can't reboot at present, I'm working.

Xorg.0.log has a LOT in it, and I'm uncertain if some of the lines here indicate an incorrect driver, but it appears that perhaps the drivers I installed were incorrect or something. I found a line that states:

```
(II) No input driver/identifier specified (ignoring)
``` 

in the section that is dealing with the tablet. Would you like me to post that whole section? It's pretty long.

---

### Post by Favux on 2010-12-29
Right, if you open Xorg.0.log in gedit use Find to locate the tablet section using the keywords UC-LOGIC, wizardpen, or tablet or whatever is showing up in the section.

Yes you need to reboot or at least restart X.  xinput might not reflect that the tablet is on the proper driver although I think it might change.  To be sure you need the list-props or Xorg.0.log.

---

### Post by shadarack on 2010-12-29
Well, I can't restart X until I'm done working. I've got a quota unfortunately, and as long as it takes to start Windows back up in Virtualbox, and then get all my work software up and running again, I'll just have to wait. As for Xorg.0.log, here is the section on the tablet:

```
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/event5)
(**)                 9x12 Tablet: Applying InputClass "evdev tablet catchall"
(**)                 9x12 Tablet: always reports core events
(**)                 9x12 Tablet: Device: "/dev/input/event5"
(II)                 9x12 Tablet: Found 1 mouse buttons
(II)                 9x12 Tablet: Found absolute axes
(II)                 9x12 Tablet: Found x and y absolute axes
(II)                 9x12 Tablet: Found absolute tablet.
(II)                 9x12 Tablet: Configuring as tablet
(**)                 9x12 Tablet: YAxisMapping: buttons 4 and 5
(**)                 9x12 Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "                9x12 Tablet" (type: TABLET)
(II)                 9x12 Tablet: initialized for absolute axes.
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/event6)
(**)                 9x12 Tablet: Applying InputClass "evdev pointer catchall"
(**)                 9x12 Tablet: always reports core events
(**)                 9x12 Tablet: Device: "/dev/input/event6"
(II)                 9x12 Tablet: Found 3 mouse buttons
(II)                 9x12 Tablet: Found scroll wheel(s)
(II)                 9x12 Tablet: Found relative axes
(II)                 9x12 Tablet: Found x and y relative axes
(II)                 9x12 Tablet: Configuring as mouse
(**)                 9x12 Tablet: YAxisMapping: buttons 4 and 5
(**)                 9x12 Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "                9x12 Tablet" (type: MOUSE)
(II)                 9x12 Tablet: initialized for relative axes.
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/event7)
(**)                 9x12 Tablet: Applying InputClass "evdev tablet catchall"
(**)                 9x12 Tablet: always reports core events
(**)                 9x12 Tablet: Device: "/dev/input/event7"
(II)                 9x12 Tablet: Found 3 mouse buttons
(II)                 9x12 Tablet: Found absolute axes
(II)                 9x12 Tablet: Found x and y absolute axes
(II)                 9x12 Tablet: Found absolute tablet.
(II)                 9x12 Tablet: Configuring as tablet
(**)                 9x12 Tablet: YAxisMapping: buttons 4 and 5
(**)                 9x12 Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "                9x12 Tablet" (type: TABLET)
(II)                 9x12 Tablet: initialized for absolute axes.
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event8)
(**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event8"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Found relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(WW) Dec 27 05:59:52 NVIDIA(0): WAIT (2, 6, 0x8000, 0x00002568, 0x000026e0)
(WW) Dec 27 05:59:57 NVIDIA(0): WAIT (1, 6, 0x8000, 0x00002568, 0x000026e0)
```

---

### Post by Favux on 2010-12-29
Yep, it's on evdev.  Everytime you see:
```
(II) XINPUT: Adding extended input device "                9x12 Tablet" (type: TABLET)

```
it's being taken by the evdev driver.  In fact that happens 3 times.  Two of the events are spurious.  I'm amazed the stylus functions at all.

So we need to straighten that out first.

---

### Post by shadarack on 2010-12-29
Just to be sure, I do that in theory by rebooting or restarting X, now that I've made the changes to 70-wizardpen.conf?

---

### Post by Favux on 2010-12-29
Yes.  We'll have to check to be sure we have you on the WizardPen driver.

---

### Post by Fwirt on 2010-12-29
I'm an Arch user who has been looking for a solution to the same problem you guys are having.  I'm using a Genius MousePen 8x6, and my goal was to change the tablet aspect ratio to my dual-head aspect ratio. The package for my distro seemed to have many different conflicting config files... There were a couple for HAL in /usr/share/hal/fdi/preprobe/20thirdparty/, I tried removing them and the tablet doesn't seem any worse off without them... There's a udev file which actually seems to load the driver (/lib/udev/rules.d/67-xorg-wizardpen.rules) and there was another configuration file (/etc/udev/rules.d/70-xorg-wizardpen-settings.rules) with all the lines commented out which looked like it would allow me to adjust MaxX, MaxY, etc., but that didn't work for me either. Eventually what I ended up doing a few minutes ago (and what seems to be working) is adding some lines to /etc/X11/xorg.conf.d/70-wizardpen.conf, like so:
```

# This input class already existed
Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
# I added all these options... so far so good
   Option          "TopX"          "0"
   Option          "BottomX"       "32767"
   Option          "TopY"          "0"
   Option          "BottomY"       "32767"
   Option          "TopZ"          "0"
   Option          "BottomZ"       "1024"
   Option          "MaxX"          "32767"
   Option          "MaxY"          "32767"
   Option          "MaxZ"          "1024"
   Option          "Rotate90"      "0"
   Option          "TPCButton"     "off"
EndSection

```
I copied the options over from the udev config file and it seems to be working with hotplugging and everything. Included there are the options for the wizardpen driver which seemed useful. Other options I found in the udev config file were ScreenX and ScreenY (Which unfortunately didn't let me limit the screen area, give them a try if you want) as well as MouseSpeed, MouseAccel, and DebugLevel. Hope you guys have some luck with this!

---

### Post by Favux on 2010-12-29
Hi Fwirt,

Welcome to Ubuntu forums!

Thanks for pitching in.  Are you confining the tablet to the left monitor?

If so does:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    Option          "TopX"          "0"
    Option          "TopY"          "0"
    Option          "BottomX"       "32767"
    Option          "BottomY"       "32767"
#   Option          "MaxX"          "32767"
#   Option          "MaxY"          "32767"
    Option          "TopZ"          "0"
    Option          "BottomZ"       "1024"
#   Option          "MaxZ"          "1024"
#   Option          "Rotate90"      "0"
    Option          "TPCButton"     "off"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
work for you?  I think by removing the udev rule you removed the 'MatchTag  "wizardpen"'.  Also I think you just would need the coordinates in the wizardpen.conf and not the xorg.conf.

For 'man wizardpen' also see the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").

---

### Post by SnickerSnack on 2010-12-29
> **Favux said:**
> In Lucid you have the default 0.10.5 xf86-input-wacom.  And it still has the multimonitor support.  Confusingly the package name it and xsetwacom are in is called xserver-xorg-input-wacom.  The same package name they were using in Karmic and earlier for linuxwacom.

While it still allegedly has multimonitor support they rewrote xsetwacom for xf86-input-wacom.  And 0.10.5 is practically the first release.  So xsetwacom was still feature incomplete and a lot of it is broken.  I really don't know what to advise you to do.

I guess I'd try xsetwacom commands until I was convinced they don't work and then clone the git repository to get the latest and start over with it and the alleged new method.  See part II. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") or section 2 of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Edit:  Oops!  Looks like I'm wrong.  I just read the new method apparently relies on a property added to X server l.9 so you won't be able to use it in Lucid (1.7).  If I remember right there were some commits finally fixing all of the mapping stuff right before it was all removed.  So we need to figure out when that was and you could download a snapshot of that last multimonitor commit and use that.

I've upgraded to maverick (sheesh it took a long time....), so know I'm looking into how I should update *-input-wacom past 10.8.

I've never "cloned a git repo", so I'm sure I'll have fun figuring that out.  I was hoping for a ppa. :)  I'll try the old commands first, though.

Edit: Would it be better to just update to the newest version, or is there a chance that it won't work for me, and I should try the old commands first?  Also, I'm not sure that I know which commands to try...

---

### Post by Favux on 2010-12-29
Wow!  You've been busy.  Took a long time because of a ton of updates?

I think you should probably try the old commands first.  I found what I think is the last commit for the old commands before they were removed with "Allow 0 for TwinView resolution if TwinView is NONE."  You'd want the snapshot of that I guess:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog;pg=1](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog;pg=1) if the current default 0.10.8 doesn't work.  The snapshot would sort of be the last of 0.10.8.  You just find the commit and click on snapshot and it'll download that version to compile.

They would look something like:
```
xsetwacom --set "Wacom Volito2 4x5" Twinview Horizontal
xsetwacom --set "Wacom Volito2 4x5" Screen_No 1
xsetwacom --set "Wacom Volito2 4x5" TopX 851
xsetwacom --set "Wacom Volito2 4x5" BottomX 5104
```
from:  [http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)

---

### Post by Fwirt on 2010-12-29
> **Favux said:**
> Thanks for pitching in.  Are you confining the tablet to the left monitor?
Unfortunately no, I wasn't able to confine the tablet to the left monitor. I was attempting to help with what shadarack suggested:
> **shadarack said:**
> I have the same issue, but with a genius pensketch 9x12 and a 3200x900 display. No clue how to limit it to one monitor, but would a possible workaround be to change the area of the tablet that is sensitive to match the dimensions of your desktop? This would mean giving up a big chunk of your tablet, but would at least make it usable, yes?
The options I put in /etc/X11/xorg.conf.d/70-wizardpen.conf do exactly that. I know that it's not a solution, but I thought it might be a step in the right direction.
> **Favux said:**
> 
Also I think you just would need the coordinates in the wizardpen.conf and not the xorg.conf.
I believe that is what I did, that .conf file is the only place that the tablet configuration happens, I didn't add any lines to my xorg.conf.

Also, I forgot to mention in my last post, you actually have to calculate the correct values for TopY and BottomY from your desktop aspect ratio and tablet aspect ratio. For example, my desktop is 2720x1024, and my tablet is a 4:3 aspect ratio, so to get the height of the area to confine the tablet to, I did:
Maximum Axis Value * (Desktop Height/Desktop Width) * (Tablet Width/Tablet Height) = Axis Area Height
32767 * (1024 / 2720) * (8 / 6) = 16448
And then you can adjust the values to put the area where you want, so the options in my configuration file look like:
```

   Option          "TopX"          "0"
   Option          "BottomX"       "32767"
   Option          "TopY"          "8124"
   Option          "BottomY"       "24572"

```
Also, I found out that MaxX, Y, and Z don't seem to do anything, so the maximum values for my tablet seem to be 32767... Sorry this didn't solve the problem, but I at least hope this helps with configuring wizardpen tablets.

---

### Post by Favux on 2010-12-29
Hi Fwirt,

Don't apologize, you are contributing.

So the calculations are like what they did on the Wacom thread I linked above.

The Top X & Y are usually grouped together and 0,0 then refers to the top left corner of the monitor.  Then Bottom X is how far you go horizontally and Bottom Y how far down vertically.

I wonder if the Max X & Y would apply to adding the resolutions of both monitors together?  The Z axis is pressure so it is referring to pressure levels and a pressure "threshold" you could maybe set.

---

### Post by SnickerSnack on 2010-12-29
EDIT: you can probably just ignore this post.  I'm installing the new version of xf86-input-wacom.

I'm having serious difficulty.  The dimensions are not scaling even close to the way in the thread you linked.  For one thing, my numbers are huge.  Using BottomX of ~28000 gets the stylus to span across the twinview** (that is, touching the left edge of the tablet screen hits the left edge of the external monitor, and touching the right edge of the tablet hits the right edge of the laptop screen).  Secondly, things seem to be scaling inversely!  Setting larger values for BottomX results in a smaller workable area!

And setting Screen_No doesn't seem to do anything.  I have two choices that don't return errors, 0 and -1, but they seem to have the same effect.

I currently have

zsharon@Weierstrass:~$ xsetwacom --get 13 TopX
0
zsharon@Weierstrass:~$ xsetwacom --get 13 BottomX
27600
zsharon@Weierstrass:~$ xsetwacom --get 13 TopY
0
zsharon@Weierstrass:~$ xsetwacom --get 13 BottomY
32500

and this gives the situation described above at **.

Before I started, these were set to 0,24576,0,18432, respectively, and it seemed to work pretty much as it does now.  I suspect that Screen_No may have something to do with it, but I'm not sure.  The ratio of the BottomYs that seemed to work "normally" is ~1.76, but this is not the same as the ration between 1024 and 768 (the two heights of the screens involved).  But, it is approximately (1024/(1024+768))^(-1) ?

I suppose I could resort to finding an interpolating polynomial to relate these quantities.... EDIT: From reading your post in the How-To thread I'm guessing that this is due to the coordinate transformation.

---

### Post by shadarack on 2010-12-29
Okay, restarted X and checked xinput --list

No change.

Just to be sure, I rebooted completely, still the same. So pretty sure whatever we did with 70-wizardpen.conf had no effect, or at least no effect on the output of xinput --list

Checked Xorg.0.log and it is still applying InputClass "evdev tablet catchall" and "evdev pointer catchall" three times too.

The tablet still works...sort of.

---

### Post by Favux on 2010-12-29
Ok, assuming you installed Doctor Mo's PPA correctly let's try:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

---

### Post by shadarack on 2010-12-30
No change, again. This time I just restarted X by logging out and then logging back in. That should do it, right? Or do I need to reboot completely for this?

---

### Post by Favux on 2010-12-30
X restart should do it, but I would reboot, even a couple of times, to make sure things shake out.

---

### Post by Favux on 2010-12-30
If that doesn't work let's assume that the tablet is identified to the system as '9x12 Tablet' for whatever reason.  After all that's what xinput and Xorg.0.log say.  So try:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|9x12 Tablet"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|9x12 Tablet"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection

```

---

### Post by SnickerSnack on 2010-12-30
I don't yet understand why/how, but I got it working.  Here are the default values that work normally with one display and then stretch the stylus across both screens when two (same resolutions) are active:

TopX 0
BottomX 24576
TopY 0
BottomY 18432

To restrict the stylus to the main tablet display when a second display is on the *left* I use:

TopX -24576
BottomX 24576
TopY 0
BottomY 18432

To restrict the stylus to the main tablet display when a second display is on the *right* I use:

TopX 0
BottomX 49152
TopY 0
BottomY 18432

After reading

```
zsharon@Weierstrass:~$ xinput --list 14
Serial Wacom Tablet stylus              	id=14	[slave  pointer  (2)]
	Reporting 8 classes:
		Class originated from: 14
		Buttons supported: 32
		Button labels: None None None None None None None None None None None None None None None None None None None None None None None None None None None None None None None None
		Button state:
		Class originated from: 14
		Keycodes supported: 248
		Class originated from: 14
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 24576.000000
		  Resolution: 2540 units/m
		  Mode: relative
		Class originated from: 14
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 18432.000000
		  Resolution: 2540 units/m
		  Mode: relative
		Class originated from: 14
		Detail for Valuator 2:
		  Label: Abs Pressure
		  Range: 0.000000 - 2048.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 14
		Detail for Valuator 3:
		  Label: Abs Tilt X
		  Range: -64.000000 - 63.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 14
		Detail for Valuator 4:
		  Label: Abs Tilt Y
		  Range: -64.000000 - 63.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 14
		Detail for Valuator 5:
		  Label: Abs Wheel
		  Range: -900.000000 - 899.000000
		  Resolution: 1 units/m
		  Mode: relative
```

a bit more carefully, it would seem that 1024 pixels corresponds to 24576 units, so since setting TopX to U and BottomX to V tells the stylus to use the horizontal region from U to V, the only thing you have to do is decide what region (in terms of U and V) corresponds to the display you want.  Apparently, the left edge of the display which is (not physically, but as far as the computer knows) on the left is always 0.  For my current setup, the width of my two screens (both 1024 wide) is 49152 units, which makes things make a bit more sense.

While testing out a few more things, it suddenly stopped working.  The stylus doesn't seem to work at all and trying to use it freezes all pointers for a few seconds.  I'll do a restart and keep at it.

EDIT: Okay, no restart needed.  Using these buttons (which have two commands in each one) sets

TopX 0
BottomX 0
TopY 0
BottomY 14

which is of course a problem.  I'd guess it happens because when I use a launched on the xfce panel, the second command (setting BottomX) starts while the first command (setting TopX) is working?

---

### Post by SnickerSnack on 2010-12-30
I'm fairly sure that the instructions below are correct.  These instructions may be incorporated into a guide here as well: [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)  That guide will also have instructions for other, similar setups.

I followed this post and it seems correct, if cryptic: [http://ubuntuforums.org/showpost.php?p=9853590&postcount=15](http://ubuntuforums.org/showpost.php?p=9853590&postcount=15).  I'm going to state my interpretation of that here, and I'll also cover changing vertical values for those who have different resolutions on their monitors.

[SIZE="5"]Preliminaries:[/SIZE]

These instructions assume that you haven't changed anything using xsetwacom.  If you have, you should reset to default values (that is, the stylus should work normally when no external monitor is connected); rebooting should accomplish this.  Also, I'm using xf86-input-wacom 0.10.8.  I'm using

```
xsetwacom set "Serial Wacom Tablet Stylus" Screen_No -1
```

I don't fully understand this setting yet, though it doesn't appear to do anything.

I'm using xrandr to use an external monitor, so this may not work for those using the nvidia drivers.

[SIZE="5"]Using xsetwacom:[/SIZE]

To start with, we're going to need to get some values using xinput.  Read the output of

```
xinput list
```

and find the lines that correspond to your stylus and eraser (if you have one).  For me, it's this:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Gaming Mouse               	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

```

Also notice the id for each device; this will make the commands a fair bit shorter.  The device ids can change, so if you're going to write scripts to automate this, then you need to use the device names in quotes.  Run the following commands:

```
xsetwacom get [device name/id] BottomX
xsetwacom get [device name/id] BottomY
```

the first value will be called Wxsw(Left+Right) and the second will be called Hxsw(Large) (these labels will make sense later).  It's a good idea to record these somewhere.  They appear to correspond to the resolution of the wacom digitizer, and better tablets will have larger values......I think.

Example:

```
zsharon@Weierstrass:~$ xsetwacom get "Serial Wacom Tablet stylus" BottomX
24576

```

Of course the stylus only works by pointing it at the tablet screen, but we can easily control which screen the pointer appears on, and we'll scale it correctly so that pointing the stylus at the bottom right corner of the tablet screen will move the pointer to the bottom right corner of whichever screen we've chosen, regardless of the resolution.  You'll generally use this only to restrict the stylus to the tablet screen, but I found it more clear to write this more generally since an external monitor can be on the right or the left.

[SIZE="5"]Horizontal settings:[/SIZE]

Using "Left" and "Right" to refer to our monitors only with regard to their xinput topology (that is, we don't care which is physically on the left, only which X thinks is on the left), we'll use the following notation:

```
Wxsw(monitor) = the width that xsetwacom seems to ascribe to the screen,
Wact(monitor) = the "actual" physical width in pixels of the screen.
```

These can also be used for the whole display, so Wact(Left+Right) is the sum of the physical widths of the two displays; in other words, it's the same as Wact(Left)+Wact(Right).  The number we found earlier for Wxsw(Left+Right) is how wide xsetwacom thinks the whole display is.

Now, *for reasons unknown*, 

```
Wxsw(Left)*Wact(Left)=Wxsw(Right)*Wact(Right)=Wxsw(Left+Right)*Wact(Left+Right)
```

In other words, the width ascribed to a screen by xsetwacom is inversely proportional to its physical width, with constant of proportionality equal to Wxsw(-)*Wact(-) *for any of the screens involved*.  Since we know Wact(-) for each of our screens, knowing Wxsw(-) for any one of them gives us a numerical value for the constant of proportionality and allows us to determine Wxsw(-) for each of the others.  For example, if we know

```
Wxsw(Left+Right)=24576
Wact(Left+Right)=Wact(Left)+Wact(Right)=1280+1024=2304
Wact(Right)=1024
```

Then the constant of proportionality is

```
Wxsw(Left+Right)*Wact(Left+Right)=24576*2304=56623104
```

and therefore

```
Wxsw(Right)=Wxsw(Left+Right)*Wact(Left+Right)/Wact(Right)=56623104/1024=55296
```

so xsetwacom sees the Right display as being 55,296 units wide.

So how do we use this?  Disconnect any external monitor and restart your computer to reset the xsetwacom values (simply restarting X may be enough).  Use xrandr to connect the secondary display and check that the stylus is (incorrectly) mapped across both screens.  Use

```
xsetwacom get [device name/id] BottomX
```

as detailed above to find Wxsw(Left+Right).  Use this number to find Wxsw(Left) and Wxsw(Right).

Now, if you wish to map the stylus to the Left screen, use "xsetwacom set" to set the following values:

```
TopX = 0
BottomX = Wxsw(Left)
```

We set TopX=0 since we want the stylus to abut the left edge of the whole display, and we set BottomX=Wxsw(Left) so that the stylus uses the proper width, that is we want

```
BottomX-TopX=Wxsw(Left)
```

If you wish to map the stylus to the Right screen, use "xsetwacom set" to set the following values:

```
TopX = Wxsw(Left+Right)-Wxsw(Right)
BottomX = Wxsw(Left+Right)
```

We set BottomX=Wxsw(Left+Right) so the the stylus abuts the right edge of the display (remember that Wxsw(Left+Right) is the width that xsetwacom assigns to the whole display) and set TopX=Wxsw(Left+Right)-Wxsw(Right) so that the stylus uses the proper width, which is

```
BottomX-TopX=Wxsw(Left+Right)-[Wxsw(Left+Right)-Wxsw(Right)]=Wxsw(Right)
```

To continue the earlier example, if I want to map my stylus to the Right screen only, then I use

```
xsetwacom set 14 TopX -30720
xsetwacom set 14 BottomX 24576
```

Yes, I use a negative value for TopX, which seems odd, but it works.

To recap:

```
1. Find Wxsw(-) for the default (wrong) setting.
2. Compute the constant of proportionality.
3. Find Wxsw(Left) or Wxsw(Right).
4. Input values.
```

Unless you change the resolutions for your screens, you should only have to find the constant of proportionality once.

[SIZE="5"]Vertical settings:[/SIZE]

When you use xrandr to use a second monitor, the stylus should scale according to the larger screen, so if you intend to use the stylus with the larger screen, no changes are needed.

If you want to use the stylus with a screen which is the smaller of the two screens, then you'll want to adjust the vertical as well.  All you should need to do is scale things.  Let

```
Hact(Large) = Larger screen height in pixels
Hact(Small) = Smaller screen height in pixels
Hxsw(Large) = height xsetwacom assigns to the larger screen
Hxsw(Small) = height xsetwacom assigns to the smaller screen

```

Again, these values are related by

```
Hact(Large)*Hxsw(Large)=Hact(Small)*Hxsw(Small)
```

To get the value needed to restrict the stylus to the vertical region spanned by the smaller screen, obtain Hxsw(Large) using 

```
xsetwacom get [device name/id] BottomY
```

and set

```
BottomY = Hsxw(Small)=Hxsw(Large)*Hact(Large)/Hact(Small)
```

using the command

```
xsetwacom set [device name/id] BottomY VALUE
```

For me, this is 18342*1024/768=24456, so

```
xsetwacom set 14 BottomY 24456
```

sets my stylus to have the desired height range.  Of course, I still have TopY = 0.

[SIZE="4"]Eraser:[/SIZE]

If you have an eraser on your stylus, don't forget to adjust the eraser as well.  Use the same commands you used for the stylus but with the id for the eraser instead.

I hope this is clear enough.

---

### Post by shadarack on 2010-12-31
Okay, wow. I'm starting to think that my driver installation just did not work and the tablet is only working off the evdev driver. I tried that last 70-wizardpen.conf setup and still nothing. I even tried using ```
"                9x12 Tablet"
``` instead of "9x12 Tablet" because xinput --list shows it with a ton of spaces before hand, but that didn't work either. Xorg.0.log still shows it using "evdev tablet catchall" On the off chance that perhaps I'm looking at the wrong thing, I will include the appropriate sections of Xorg.0.log at the end of this post. Should I try the alternate method of driver installation suggested in this howto?

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)


Here is the xorg.0.log section I promised:

```
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/event5)
(**)                 9x12 Tablet: Applying InputClass "evdev tablet catchall"
(**)                 9x12 Tablet: always reports core events
(**)                 9x12 Tablet: Device: "/dev/input/event5"
(II)                 9x12 Tablet: Found 1 mouse buttons
(II)                 9x12 Tablet: Found absolute axes
(II)                 9x12 Tablet: Found x and y absolute axes
(II)                 9x12 Tablet: Found absolute tablet.
(II)                 9x12 Tablet: Configuring as tablet
(**)                 9x12 Tablet: YAxisMapping: buttons 4 and 5
(**)                 9x12 Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "                9x12 Tablet" (type: TABLET)
(II)                 9x12 Tablet: initialized for absolute axes.
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/event6)
(**)                 9x12 Tablet: Applying InputClass "evdev pointer catchall"
(**)                 9x12 Tablet: always reports core events
(**)                 9x12 Tablet: Device: "/dev/input/event6"
(II)                 9x12 Tablet: Found 3 mouse buttons
(II)                 9x12 Tablet: Found scroll wheel(s)
(II)                 9x12 Tablet: Found relative axes
(II)                 9x12 Tablet: Found x and y relative axes
(II)                 9x12 Tablet: Configuring as mouse
(**)                 9x12 Tablet: YAxisMapping: buttons 4 and 5
(**)                 9x12 Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "                9x12 Tablet" (type: MOUSE)
(II)                 9x12 Tablet: initialized for relative axes.
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/event7)
(**)                 9x12 Tablet: Applying InputClass "evdev tablet catchall"
(**)                 9x12 Tablet: always reports core events
(**)                 9x12 Tablet: Device: "/dev/input/event7"
(II)                 9x12 Tablet: Found 3 mouse buttons
(II)                 9x12 Tablet: Found absolute axes
(II)                 9x12 Tablet: Found x and y absolute axes
(II)                 9x12 Tablet: Found absolute tablet.
(II)                 9x12 Tablet: Configuring as tablet
(**)                 9x12 Tablet: YAxisMapping: buttons 4 and 5
(**)                 9x12 Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "                9x12 Tablet" (type: TABLET)
(II)                 9x12 Tablet: initialized for absolute axes.
(II) config/udev: Adding input device                 9x12 Tablet (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
```

---

### Post by Favux on 2011-01-10
Hi 1script, shadarack, and Fwirt,

We've figured out a way to confine the tablet to one Monitor I think.  If you go to the "**[HOW TO Setup a Wacom Tablet with Multi-Monitors in Maverick and Natty]("http://ubuntuforums.org/showpost.php?p=10297093&postcount=1")**" using the 'Coordinate Transformation Matrix' method.  This is provided you have Xorg 1.9 (Maverick), which is when it was added.  I think this will work for any tablet.

SnickerSnack's method using xsetwacom coordinates will also work for tablets on the Wacom driver in Xorg 1.9 and earlier.


Hi shadarack,

I do not understand why we are seeing what we are seeing, i.e. the tablet name truncated to '9x12 Tablet' with obvious whitespaces in front indicating the missing name.  I'm wondering about a problem with your tablet's firmware.  Or did you add or modify a udev rule somewhere?  A wizardpen.rules or something?

When you enter:
```
lsusb
```
in a terminal does the line in the output with the tablet have the whole name or is it truncated also?

---

### Post by 1script on 2011-01-11
Just coming back to my old thread after a few months of neglect and I'm so happy to see that there'd been positive developments, at least for Wacom tablet users.

Since I'm in the Wizardpen camp (WP8060U), I'm still struggling. There seems to be quite a difference between 

[LIST=1]
[*]Gnome versions' handling of input from HAL devices - I'm still using 1.7; have a feeling the 1.9 may actually be the key to this fix.

[*]Wacom driver vs. Wizardpen handling of configurations. Confusingly, they seem to use the same files but parse them differently
[/LIST]

My *xinput list-props* output seems to be different that what's been reported in the Wacom threads and does not include the transformation matrix:
```
user@box:~$ xinput list-props "UC-LOGIC Tablet WP8060U"Device
 'UC-LOGIC Tablet WP8060U':
	Device Enabled (121):	1
	Device Accel Profile (241):	0
	Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (244):	1.000000
	Device Accel Velocity Scaling (245):	10.000000
 
```

So, can we do a roll call here please: those people that have been able to limit the pen tablet to one monitor out of two:

[LIST=1]
[*]What version of Gnome you're using?
[*]Are you using Wacom or Wizardpen drivers?
[/LIST]

I've got some configs I've tried **unsuccessfully** (/etc/hal/fdi/policy/99-x11-wizardpen.fdi, /usr/lib/X11/xorg.conf.d/70-wizardpen.conf etc.) Does anyone see any value to this thread in posting **non-working** configs?

---

### Post by Favux on 2011-01-11
Hi 1script,

Good to hear from you.

That's why I linked you to the Multi-monitor HOW TO above.  I think the "Coordinate Transformation Matrix" will work for any tablet.  But it depends on you having Xorg 1.9/Maverick installed, which is why you're not seeing it in list-props.  Unless you want to try updating your Xorg in Lucid.

---

### Post by 1script on 2011-01-11
Favux, thanks!

I'm just about to start upgrade to 10.10 because updating Xorg in 10.04 does not seem to make any sense. Additionally, I'm having some performance issues with Evolution that may go away with the new versions. There are also other benefits of staying current, so I'll just do it and then come back to this thread with results.

> **Favux said:**
> Hi 1script,

Good to hear from you.

That's why I linked you to the Multi-monitor HOW TO above.  I think the "Coordinate Transformation Matrix" will work for any tablet.  But it depends on you having Xorg 1.9/Maverick installed, which is why you're not seeing it in list-props.  Unless you want to try updating your Xorg in Lucid.

---

### Post by 1script on 2011-01-11
Well, upgrade to 10.10 , along with the weird fonts, brought an unpleasant surprise: the tablet stopped working completely. So I'm back to square one (well, slightly before that, actually). I need go fix it and then tackle the monitor targeting one more time.

---

### Post by 1script on 2011-01-12
A quick update: I am now on 10.10 Maverick Meerkat and after only 5 hours of dancing around a non-working tablet, it works again. 

Well, sort of.

First of all: lessons learned from the upgrade fiasco: if you've made so many changes to different configuration files, just uninstall the thing and install again. This is what in the end fixed it - it did 
```

sudo apt-get remove xserver-xorg-input-wizardpen
sudo apt-get purge xserver-xorg-input-wizardpen
sudo apt-get install xserver-xorg-input-wizardpen

```
It installs version 0.7.4 that is not the latest but the latest 0.8 xserver-xorg-input-wizardpen does not compile on Maverick. 

In any case, by using the coordinate transformation matrix from [this post]("http://ubuntuforums.org/showpost.php?p=10297093&postcount=1")  I now have a tablet who's cursor is bound within the monitor that I want (tried both left and right - both 1280x1024)

**HOWEVER:**

When you attempt drawing, the cursor selects things on a wrong monitor! I guess the best I can describe it as if there is another, invisible cursor in the same vertical position but on the opposite monitor and if you put the stylus down to the tablet, it selects at the position of the invisible cursor rather than the one that you're looking at.

:-k

So, it looks like the coordinate transformation matrix works for the cursor but not buttons?

Here is my xinput --list now:

```
user@box:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
[COLOR="Red"]&#9116;   &#8627; stylus                                  	id=6	[slave  [/COLOR]pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Logitech USB Multimedia Keyboard        	id=10	[slave  keyboard (3)]
    &#8627; Logitech USB Multimedia Keyboard        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
```

The selection in red is new - I did not have *stylus* separate from the *UC-LOGIC Tablet WP8060U* device before.

In any case, running *xinput set-prop* for a separate device called *stylus* did not help the issue.

Anyone has any idea on where to go from here?

---

### Post by Favux on 2011-01-12
Hi 1script,

My guess is stylus is from a wizardpen section in xorg.conf.  You shouldn't use both the xorg.conf and the 70-wizardpen.conf.  The "UC-LOGIC Tablet WP8060U" should be your stylus.  Did you try installing the WizarPen driver from DoctorMo's PPA?:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick](https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick)

---

### Post by 1script on 2011-01-12
> **Favux said:**
> Hi 1script,
My guess is stylus is from a wizardpen section in xorg.conf.  You shouldn't use both the xorg.conf and the 70-wizardpen.conf.  

I noticed that when I removed/reinstalled wizardpen, *70-wizardpen.conf* was just gone, all by itself so I'm pretty extra sure I have just xorg.conf.

> **Favux said:**
> 
The "UC-LOGIC Tablet WP8060U" should be your stylus.  Did you try installing the WizarPen driver from DoctorMo's PPA?:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick](https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick)

Yes, that's where I've installed it from but it was so late at night that I decided to do it again anyways, so I've added the DoctorMO's PPA again (and also removed a bunch of other wizardpen-related repositories that were marked "disabled on upgrade to...") then removed/purged/installed is again until I saw
```
Setting up xserver-xorg-input-wizardpen (0.7.4-3maverick0)
```

I am still experiencing the issue from last night and, upon closer look, I realized that even before I start messing with the transformation matrix the cursor selects things approx 50px up and to the left from the actual position of the cursor on the screen. So, my guess is that a calibration is in order but I cannot find the "calibrate" utility. Anyone knows where it gets put at when you install wizardpen from a repository rather than by a compillation?

---

### Post by Favux on 2011-01-12
I'm pretty sure if you remove or comment out the WizardPen entries from xorg.conf and just use the 70-wizardpen.conf, maybe with a few tweaks, your issues will go away.  Another WizardPen tablet user elnaurethI just reported he was able to set up his monitors using the 'Coordinate Transformation Matrix' method:  [http://ubuntuforums.org/showthread.php?p=10348699#post10348699](http://ubuntuforums.org/showthread.php?p=10348699#post10348699)

---

### Post by 1script on 2011-01-12
I am happy to report that the issue has been solved.

Basically, I had to hunt down and delete all the traces of the tweaks I've done yesterday **before** upgrade to Ubuntu 10.10 . If you were to approach this task afresh, it will be much easier, so to summarize it, to limit a wizardpen-controlled tablet (any tablet other than Wacom) takes these steps:
[LIST=1]
[*]Upgrade to Ubuntu 10.10 (or just upgrade Xorg to version 1.9 separately if you're feeling adventurous)

[*]Install the latest stable version of xserver-xorg-input-wizardpen (0.7.4-3maverick0) from DoctorMo's PPA: [https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick](https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick)

[*]Run xinput --list to figure out the correct name of your tablet. You should see something like 
```
user@box:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; [COLOR="Red"]UC-LOGIC Tablet WP8060U[/COLOR]                 	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=11	[slave  pointer  (2)]
``` where "UC-LOGIC Tablet WP8060U" is the correct name of the tablet. I have two tablets of the same size by different manufacturers (Genius and LaPazz) and they both show up as *UC-LOGIC Tablet WP8060U*

[*]If you have a rather simple setup like I do with two monitors of the same resolution, run 
```
xinput set-prop "UC-LOGIC Tablet WP8060U" --type=float "Coordinate Transformation Matrix" 0.5 0 0.5 0 1 0 0 0 1
``` as instructed by Favux in the [Wacom thread here]("http://ubuntuforums.org/showpost.php?p=10297093&postcount=1"). If your monitor setup is different (more monitors, different resolution) read more awesome instructions from Favux in the above mentioned thread. Again, substitute "UC-LOGIC Tablet WP8060U" for your actual tablet name from the previous step.

[*]The *xinput set-prop* directive is not going to last through restart so create a file with this one line in it ```
xinput set-prop "UC-LOGIC Tablet WP8060U" --type=float "Coordinate Transformation Matrix" 0.5 0 0.5 0 1 0 0 0 1
```, save it as, say ~/.limit_tablet.sh and then run ```
chmod 755  ~/.limit_tablet.sh
```. You could then either put it under System->Preferences->Startup Applications (use full path as in *sh /home/username/.limit_tablet.sh*) to run it every time you reboot or create a shortcut in, say, the Applications->Graphics menu. I made one just below Gimp and Inkscape and start is manually when I need it. Seems to be working for me so far but I may go back to starting it automatically every time I reboot.

[*]Enjoy!
[/LIST]

Thanks Favux for the great instructions and references!

---

### Post by Favux on 2011-01-12
Great!

Nice summary.

Did you use thread tools above your first post to mark the thread solved?

---

### Post by 1script on 2011-01-12
> **Favux said:**
> Great!
Did you use thread tools above your first post to mark the thread solved?
I've actually manually added [SOLVED] to the first post's title before I saw your post. Then I decided to go and use the thread tools to mark as "solved" for a good measure, so I hope it'll mark it as such.


Another thing I wanted to add before I let it go: I did not include any sample config files because you don't have to edit any. **Everything** works with default settings (calibration data of the tablet included) right out of the box, you just need to lookup the proper name of the tablet once and use it in *xinput set-prop* command and that's the extent of customization in this whole solution.

---

