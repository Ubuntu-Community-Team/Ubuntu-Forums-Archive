---
title: "Multiseat Computer under 7.10"
date: 2008-02-19
forum: Desktop Environments
---

### Post by bumcheekcity on 2008-02-19
[http://www.linuxtoys.org/multiseat/multiseat.html](http://www.linuxtoys.org/multiseat/multiseat.html)

Hi. I'm looking at trying to get a multiseat computer going using Ubuntu 7.10 (using Gnome), I'm using the tutorial at the top, but not having too much luck. Here's my hardware:

P4 3Ghz
768MB RAM
Radeon 9550 (1x DVI, 1x VGA)
17" LCD (In the DVI)
22" CRT (In the VGA)
PS/2 Keyboard and Mouse (Generic)
USB Keyboard and Mouse (Generic)

My current xorg.conf file is at the end of this post. However, this gives me two screens replicating EXACTLY the same output, and both sets of keyboard and mice work simultaneously, which is obviously not what I want. Can anyone give me any advice as to what I should do? If you require any other information about my system files, I'll provide it ASAP.

I think the problem could be in the "Device" section. I've got the device recognised twice. Is this right?

```
Section "Files"
EndSection

############################
#Seat 1
############################

Section "InputDevice"
    Identifier     "Keyboard1"
    Driver         "evdev"
    Option         "Device" "/dev/input/event1"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
    Identifier     "Mouse1"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mouse1"
    Option         "ZAxisMapping" "6 7"
EndSection

Section "Device"
	Identifier	"device1"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier     "monitor1"
    ModelName      "Flat Panel 1024x768"
    HorizSync       31.5 - 48.5
    VertRefresh     40.0 - 70.0
    ModeLine       "768x576" 50.0 768 832 846 1000 576 590 595 630
    ModeLine       "768x576" 63.1 768 800 960 1024 576 578 590 616
EndSection

Section "Screen"
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1024 768
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "seat1"
    Screen      0  "Screen1" 0 0
    InputDev  ice    "Mouse1" "CorePointer"
    InputDevice    "Keyboard1" "CoreKeyboard"
EndSection

############################
#Seat 2
############################

Section "InputDevice"
    Identifier     "Keyboard2"
    Driver         "evdev"
    Option         "Device" "/dev/input/event2"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
    Identifier     "Mouse2"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mouse2"
    Option         "ZAxisMapping" "6 7"
EndSection

Section "Device"
	Identifier	"device2"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier     "monitor2"
    ModelName      "Flat Panel 1024x768"
    HorizSync       31.5 - 48.5
    VertRefresh     40.0 - 70.0
    ModeLine       "768x576" 50.0 768 832 846 1000 576 590 595 630
    ModeLine       "768x576" 63.1 768 800 960 1024 576 578 590 616
EndSection

Section "Screen"
    Identifier     "screen2"
    Device         "device2"
    Monitor        "monitor2"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1024 768
        Depth       24
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "seat2"
    Screen      0  "Screen2" 0 0
    InputDevice    "Mouse2" "CorePointer"
    InputDevice    "Keyboard2" "CoreKeyboard"
EndSection
```

---

### Post by motin on 2008-02-25
I got multiseat working on 7.10 this morning and just finished a tutorial on the subject. I'll paste the url as soon as it gets accepted into the Tutorial and Tips section in the forums. 

Cheers,

Fredrik

---

### Post by bumcheekcity on 2008-02-25
> **motin said:**
> I got multiseat working on 7.10 this morning and just finished a tutorial on the subject. I'll paste the url as soon as it gets accepted into the Tutorial and Tips section in the forums. 

Cheers,

Fredrik
Thankyou for your help. I hear that 8.4 will MASSIVELY help with xorg 7.3 included. I await with baited breath for this. Was it hard to do for you?

---

### Post by motin on 2008-02-25
Yeah, I ran into many obstacles. After around 14 hours of fiddling however, I have a routine that works for me at least. Hold on until that tutorial gets through mate! ;)

---

### Post by motin on 2008-02-26
Ok now it is approved: [http://ubuntuforums.org/showthread.php?t=707796](http://ubuntuforums.org/showthread.php?t=707796)

Hopefully it is what you were looking for... If not - sorry I don't know any other way atm. 

Cheers,

Fredrik

---

### Post by bumcheekcity on 2008-02-26
Thanks mate. I'll use that later on today and let you know.

---

