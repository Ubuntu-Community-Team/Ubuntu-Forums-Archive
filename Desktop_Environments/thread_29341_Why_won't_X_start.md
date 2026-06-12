---
title: "Why won't X start?"
date: 2005-04-23
forum: Desktop Environments
---

### Post by jubei on 2005-04-23
X wont start when I add this line to my xorg.conf under the Section "InputDevice" for my mouse.

```

Option      "Protocol" "evdev"

```

here is a snippet from my xorg.conf

```

Section "InputDevice"
	Identifier	"Configured Mouse"
        Driver      "mouse"
	Option		"CorePointer"
        Option      "Protocol" "evdev"
        Option        "Dev Name" "B16_b_02 USB-PS/2 Optical Mouse" # cat /proc/bus/input/devices
        Option        "Dev Phys" "usb-0000:00:1f.2-1/input0" # cat /proc/bus/input/devices
        Option        "Device" "/dev/input/mice" # (/dev/input/mice also appears to work)
	Option      "Buttons" "4"
	Option		"ZAxisMapping"		"4 5"
	Option      "Resolution" "800"
EndSection

```

and here is my the end of my Xorg.o.log when I run startx

```

(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "evdev"
(**) Configured Mouse: Protocol: evdev
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Buttons" "4"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Dev Name" "B16_b_02 USB-PS/2 Optical Mouse"
(**) Option "Dev Phys" "usb-0000:00:1f.2-1/input0"
(EE) Configured Mouse: cannot open input device
No core pointer

Fatal server error:
failed to initialize core devices

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

and here is the result of  cat /proc/bus/input/devices

```

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c024 Version=9802
N: Name="B16_b_02 USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1f.2-1/input0
H: Handlers=mouse0 event2 ts0
B: EV=20007
B: KEY=f000f 0 0 0 0 0 0 0 0
B: REL=103
B: LED=fc00

```

Please help me :razz: !

---

### Post by Nis on 2005-04-24
Try replacing
```

Option      "Protocol" "evdev"
Option        "Dev Name" "B16_b_02 USB-PS/2 Optical Mouse" # cat /proc/bus/input/devices
Option        "Dev Phys" "usb-0000:00:1f.2-1/input0" # cat /proc/bus/input/devices

```
with
```

Option      "Protocol" "IMPS/2"

```

Why the need for the weird protocol and dev lines?

---

### Post by jubei on 2005-04-24
I want to use evdev for extra smooth mouse sampling in Quake 1.

I had evdev working in mandrake 10.0 by default

I followed this guide to try and get evdev working.

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46)

other people in #ubuntu have been saying that I dont need those weird lines either. Taking them out doesnt help evdev to work.

Option      "Protocol" "IMPS/2" works just fine, but I want evdev.

Any ideas why it wont work?

lsmod |grep evdev returns:
evdev                   9856  0

I'm also using this little tweak:[http://ubuntuforums.org/showthread.php?t=4357&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=4357&page=1&pp=10). Also I recompiled my kernel using this patch to increase the usb polling rate to 500hz [ftp://gibbage.mine.nu/tools/500hz%20USB%20Mouse%20Patches/](ftp://gibbage.mine.nu/tools/500hz%20USB%20Mouse%20Patches/)

also

ls /dev/input/ returns
event0  event1  mice

what should I try next?

thanks people.

---

### Post by kkith on 2005-04-24
What are your file permissions for /dev/input/mice?  It probably isn't the problem, but worth a look.

---

### Post by jubei on 2005-04-24
[QUOTE=kkith]What are your file permissions for /dev/input/mice?  It probably isn't the problem, but worth a look.[/QUOTE]

ls -l /dev/input/
total 0
crw-------  1 root root 13, 64 2005-04-24 13:35 event0
crw-------  1 root root 13, 65 2005-04-24 13:35 event1
crw-------  1 root root 13, 63 2005-04-24 13:35 mice

Is that ok?

---

