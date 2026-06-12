---
title: "Mouse buttons stop working"
date: 2007-07-25
forum: Desktop Environments
---

### Post by Goombie on 2007-07-25
At random times when I'm using Ubuntu, my mouse buttons suddenly stop responding. I can't click on anything, and no objects on the screen react (display tooltips, etc) when I move the mouse cursor over them. I can move the mouse, but that's it. I can get my mouse working again by using Alt-Tab to switch applications a couple times. This issue happens several times a day, regardless of what applications I'm using at the time. If anyone could help, I'd greatly appreciate it. This problem is starting to drive me bonkers. :?

---

### Post by geraldm on 2007-07-25
Q: what kind of mouse: USB PS/2 other ? 
Q: mouse manufacturer, model ?
Q: what mouse protocol is used in X configuration file ?
Q: any suspicious messages in the log files ? /var/log/syslog ?

Gerald

---

### Post by Goombie on 2007-07-25
> **geraldm said:**
> Q: what kind of mouse: USB PS/2 other ? 
Q: mouse manufacturer, model ?
Q: what mouse protocol is used in X configuration file ?
Q: any suspicious messages in the log files ? /var/log/syslog ?

Gerald
USB.
Logitech LX7, although Ubuntu thinks it's a Logitech MX1000.
I have no idea. Where do I look for that?
Unfortunately I'm such a newbie, that I wouldn't know a suspicious message if it walked up and introduced itself. :( I assume I'd want to check the System Log Viewer?

---

### Post by geraldm on 2007-07-26
I was looking for items that distinguish your use from others who may have a similar
system, but do not have that problem to report.
Because it is a USB mouse, the driver was probably usbhid.  If you are using the
proc filesystem, the driver for the usb device is shown in file /proc/bus/usb/devices.
It is also available in the /sys filesystem.
If the driver caught some odd change signal, and the driver were sending debug messages
then the log file /var/log/syslog would have an entry from the driver name, e.g 
usbhid: reconfigure; no buttons (or whatever the author provided for a notice)
It is only possible that there would be a driver warning message; it is more likely that
you run a regular version which would be set to omit debug messages.
Always check the log whenever odd events occur.

Knowing the protocol that the mouse was to use would provide an additional clue area.
The protocol is listed in the X configuration file, usually /etc/X11/xorg.conf under
one of the Section "InputDevice" subheadings.

Gerald

---

### Post by Goombie on 2007-07-28
Well, I've checked the system logs, and nothing untoward seems to happen when the mouse quits. I forgot to mention that this affects my laptop's built-in touchpad/trackstick combination as well. Here are the configurations for the mouse and touchpad:
```

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"    
    Option        "Emulate3Buttons"    "true"
    Option        "Buttons" "9"
    Option        "ButtonMapping" "1 2 3 6 7 8 9"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
    Option        "SHMConfig"        "true"
EndSection

```
I should note that I have an Alps touchpad, but for some reason it says Synaptics Touchpad. I don't know if that makes a difference or not.

---

### Post by forsberg on 2007-08-19
I have the same problem as well, but in my case the alt-tab doesn't even work.   My only option is ctrl-alt-backspace or manually switch off my laptop.

The mouse I am using is Logitech G7.  Laptop is acer aspire 3610.

In my xorg.conf, it is the same as the prev poster...  the "Explorer/PS2" is whatever it detected when I plugged it in.

I have tried a HOWTO logitech mouse in another thread, and that one makes my mouse driver to be "evdev", "Logitech USB receiver" - but that configuration is not stable, as it completely freezes up my computer every once in a while.

---

