---
title: "Intrepid multiseat config (evdev issues)"
date: 2008-12-30
forum: Desktop Environments
---

### Post by serrs on 2008-12-30
I have a successful multiseat config on Hardy with OpenGL on both -- the works.

I'm trying to build another on Intrepid.  My main problem is getting ONE keyboard attached to each X.  evdev and HAL fight.  Disable HAL like this:
```
Section "ServerFlags"
        Option "AutoAddDevices" "false"
EndSection

```

OK, now specify one keyboard like this:
```

Section "InputDevice"
    Identifier   "Keyboard0"
    Driver       "evdev"
    Option       "Device"      "/dev/input/event1"
    Option       "CoreKeyboard"
    Option       "XkbRules"    "xorg"
    Option       "XkbModel"    "evdev"
    Option       "XkbLayout"   "us"
EndSection

```

This works...  I am able to get into X.  The "other" keyboard is dead -- appropriately.  This keyboard works, but now "up arrow" runs "ScreenShot" as if you hit the PrintScreen button.

There are many people that have had this issue with evdev, but not with multiseat.  [https://bugs.launchpad.net/ubuntu/+bug/255167](https://bugs.launchpad.net/ubuntu/+bug/255167)  [https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008](https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008)

It seems common to switch away from using evdev as a work around.  In my case, with multiseat, I can't use the kbd driver or HAL.

It would be sad if Hardy was the last version (ever) to make real multiseat quite easy.

Any ideas on the wacko evdev?  Or how to start working this through the system?

---

### Post by madrivereric on 2009-01-01
I don't have any assistance for your issue, but I was struggling to get my Feisty multi-seat config working under Intrepid and your comment about how to disable HAL was exactly what I was looking for!  THANK YOU!!

(my set up has a void keyboard/mouse for the first seat and the real keyboard/mouse for the 2nd seat.  The first seat is controlled via LIRC -- since its just a Myth process displayed on the TV out of a PVR-350.  The second seat is the "normal" computer.  [X.org|HAL|???] was trying to put the real keyboard on the first seat and ended up with the void ones for the second seat...)

---

### Post by barshociaj on 2009-04-20
Hope this helps others who also searched for an answer here first.

Remove the XkbModel option and set XkbRules to evdev, e.g.:

```
Section "InputDevice"
	Identifier	"KeyboardTV"
	Driver		"evdev"
	Option		"Device"	"/dev/input/by-id/usb-Itron_Powerful_Receiver-event-kbd"
	Option		"XkbRules"	"evdev"
	Option		"XkbLayout"	"gb,sk"
	Option		"CoreKeyboard"
EndSection
```

---

