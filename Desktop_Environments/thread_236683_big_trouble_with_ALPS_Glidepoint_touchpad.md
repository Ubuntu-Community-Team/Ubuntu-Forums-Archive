---
title: "big trouble with ALPS Glidepoint touchpad"
date: 2006-08-15
forum: Desktop Environments
---

### Post by SqRt7744 on 2006-08-15
Hello,

the event designation of my touchpad takes on new and interesting guises each time I start my computer.  Currently 

cat /proc/bus/input/devices 

reports (among other things)

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1
B: EV=f
B: KEY=420 70000 0 0 0 0
B: REL=3
B: ABS=1000003

however, sometimes it is event4 or event3.  Is there a way to ensure that it is always the same event so that my configs in /etc/X11/xorg.conf are not but vain attempts at touchpad joy?

Thanks for any help!

---

### Post by bigken on 2006-08-15
Take a look here [http://www.ubuntuforums.org/showthread.php?t=78904&highlight=alps](http://www.ubuntuforums.org/showthread.php?t=78904&highlight=alps)

---

### Post by SqRt7744 on 2006-08-15
> **bigken said:**
> Take a look here [http://www.ubuntuforums.org/showthread.php?t=78904&highlight=alps](http://www.ubuntuforums.org/showthread.php?t=78904&highlight=alps)

Close but not cigar!  I suspect that whoever started that thread has the same problem as me since he hardcoded "event5" into his X configuration file.  If he has another device connected to his computer the touchpad may well be assigned a different event, e.g. event3, thus invalidating his configuration.  The problem will also be intermittent - from time to time a reboot will again assign the touchpad event5.

In the meantime I have gotten it to work regarless of the event # assigned to the touchpad.  This can be accomplished by setting the device to /dev/psaux rather than /dev/input/eventX and changing the protocol appropriately.  Now this DOESN'T work unless you also change the "configured mouse" section of the X file appropriately.  I have included below the relevant sections of my working configuration (copied from my /etc/X11/xorg.conf)

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ImPS/2"
	Option "Emulate3Buttons" "true"
	Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier "ALPS"
	Driver "synaptics"
	Option "AlwaysCore"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
#set MaxTapTime to 0 to disable tap-to-click	
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "ClickTime" "0"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "0"
	Option "MinSpeed" "0.45"
	Option "MaxSpeed" "0.75"
	Option "AccelFactor" "0.020"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "0"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
	Option "SHMConfig" "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"ALPS"
	InputDevice	"Configured Mouse"
EndSection

---

