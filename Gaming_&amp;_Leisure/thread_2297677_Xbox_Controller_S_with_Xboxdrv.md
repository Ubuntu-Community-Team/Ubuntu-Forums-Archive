---
title: "Xbox Controller S with Xboxdrv"
date: 2015-10-05
forum: Gaming &amp; Leisure
---

### Post by Dukenukemx on 2015-10-05
Decided to use my old Xbox Original Controller S to play some Steam games and having trouble.  I'm trying to map it as a Xbox 360 controller but not having any luck.  I've followed some guides and so far the controller works in Steam but only in Steam Big Picture Mode.  Just launching the game itself doesn't detect the controller.  It is fully working in Emulators, at least with Kega the Sega Genesis emulator.  

What I've done is create a XboxControllerS.xboxdrv and loaded that profile using the stuff bellow.  Except that when I use "xboxdrv -c" I get the error "string2btn(): couldn't convert string "btn_trigger_happy3" to XboxButton" which are the buttons for the dpad, which might explain why dpad doesn't work in Steam.  Also the right analog stick is just wrong like the up is left and down is right but I mapped it perfectly as far as I know.  

I need help, this xboxdrv is impossible to work with.  

```

[axismap]

[buttonmap]

[device-name]

[device-usbid]

[evdev-absmap]

[evdev-keymap]

[modifier]

[relative-axis]

[ui-axismap]

[ui-buttonmap]
BTN_TRIGGER_HAPPY3=du
BTN_TRIGGER_HAPPY4=dd
BTN_TRIGGER_HAPPY1=dl
BTN_TRIGGER_HAPPY2=dr

[evdev-absmap]
ABS_X=x1
ABS_Y=y1
ABS_RX=x2
ABS_RY=y2
BTN_TL2=lt
BTN_TR2=rt


[evdev-keymap]
BTN_X=x
BTN_Y=y
BTN_A=a
BTN_B=b
BTN_SELECT=back
BTN_START=start
BTN_TL=lb
BTN_TR=rb
BTN_THUMBL=tl
BTN_THUMBR=tr

[xboxdrv]
evdev=/dev/input/event2
evdev-debug=false
mimic-xpad=true
mimic-xpad-wireless=false
silent=true
detach-kernel-driver=true
dpad-as-button=true
deadzone=6000
trigger-as-button=true

[calibration]

[xboxdrv-daemon]
```

---

### Post by Dukenukemx on 2015-10-06
I got it to accept this without issue but Steam still doesn't see my changes.  I've rebooted as well but Steam for some reason sees like 6 or 7 Xbox 360 wireless controllers.  I don't know if that has anything to do with this?  
```

[axismap]

[buttonmap]

[device-name]

[device-usbid]

[evdev-absmap]

[evdev-keymap]

[modifier]

[relative-axis]

[ui-axismap]

[ui-buttonmap]

[evdev-absmap]
ABS_X=x1
ABS_Y=y1
ABS_RX=x2
ABS_RY=y2


[evdev-keymap]
BTN_X=x
BTN_Y=y
BTN_A=a
BTN_B=b
BTN_SELECT=back
BTN_START=start
BTN_TL=lb
BTN_TR=rb
BTN_THUMBL=tl
BTN_THUMBR=tr

BTN_TL2=lt
BTN_TR2=rt

BTN_TRIGGER_HAPPY3=du
BTN_TRIGGER_HAPPY4=dd
BTN_TRIGGER_HAPPY1=dl
BTN_TRIGGER_HAPPY2=dr

[xboxdrv]
evdev=/dev/input/event9
evdev-debug=false
mimic-xpad=true
mimic-xpad-wireless=false
silent=true
detach-kernel-driver=true
dpad-as-button=true
deadzone=6000
trigger-as-button=true

[calibration]

[xboxdrv-daemon]

```

---

