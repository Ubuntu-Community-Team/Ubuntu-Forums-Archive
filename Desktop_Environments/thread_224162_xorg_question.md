---
title: "xorg question"
date: 2006-07-27
forum: Desktop Environments
---

### Post by BatteryCell on 2006-07-27
Ok, so I was looking around my xorg.conf file and found a number of items refering to wacom
```

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

```
and then later in the ServerLayout section:
```
 InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"

```

But this doesnt make any sense to me because I dont have a tablet pc...does anyone else have these seemingly useless sections in their /etc/X11/xorg.conf?

---

### Post by Paerez on 2006-07-27
yeah its the default so that people who do have a tablet can use it automatically.

It won't affect your experience. It will generate errors in the xorg logs but they can be ignored. You can delete them if you want.

---

### Post by BatteryCell on 2006-07-27
Ok thanks :-)

---

