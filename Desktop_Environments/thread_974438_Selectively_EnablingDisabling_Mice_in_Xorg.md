---
title: "Selectively Enabling/Disabling Mice in Xorg?"
date: 2008-11-07
forum: Desktop Environments
---

### Post by mungewell on 2008-11-07
Hi,
Spent way too long on this last night, but without a result.

I would like to be able to selectively prevent Xorg from using a particular mouse on a system, whilst still receiving input from multiple others. At present Xorg automatically picks up any event sources (ie. /dev/input/event2).

I can force X to use a particular one in the xorg.conf file, but then I would be limited to only one pointer source and I don't believe this can be changed without restarting X. I can prevent a mouse registering with a 'ignore' udev rule, but then it is not available at all on the system. Ideally I would like commands to run from within X like 'event_source_drop /dev/input/event9' and 'event_source_use /dev/input/event9'.

The reason for doing/wanting to do this is so that a specific application can get soul use of a mouse. This may get a whole lot easier with MPX, but that's not here yet.


Any suggestions?
Mungewell.

---

### Post by mungewell on 2008-11-09
So a little more information.

There is a little util called 'Xinput', which will allow me to enable and disable the actions of a mouse (or keyboard) with a command like:
```
xinput set-int-prop "Logitech Optical USB Mouse" "Device Enabled" 32 0
```
and re-enable it with 
```
xinput set-int-prop "Logitech Optical USB Mouse" "Device Enabled" 32 1

```

It looks like with MPX this util will be able to create additional pointers, assign mice/keyboard to the and distroy them. See: [http://wearables.unisa.edu.au/mpx/?q=node/144](http://wearables.unisa.edu.au/mpx/?q=node/144)

Still, this is not what I want to do. I want X to completely release the device so that it's input can be used by another application directly (and not via the X calls) :-(

Mungewell.

---

### Post by mungewell on 2008-11-10
linux is like an onion.... it's many layers are making me cry.

So, X hotpluging uses HAL and DBus, to comunicate new hardware to the X server. See: [http://wiki.x.org/wiki/XInputHotplug](http://wiki.x.org/wiki/XInputHotplug)

My (example) device show up in 'lshal' as
```

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0'  (string)
  info.product = 'Logitech Optical USB Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0'  (string)
  input.product = 'Logitech Optical USB Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/class/input/input10/event8'  (string)

```

So does this means that something can either request a removal from X, or just tell X not to use the device anymore?

Mungewell.

---

### Post by mungewell on 2008-11-10
Success at last... at least on the disable front

```

hal-find-by-property --key info.product --string 'Logitech Optical USB Mouse'

sudo hal-device --remove /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0_0_logicaldev_input

sudo Xephyr :5 -mouse evdev,,device=/dev/input/event8

```

So what does this achieve? Now I can commit a particular mouse to a emulated Sugar session without having to frig with my xorg.config or reboot my X server.

I guess the same applies to multi-seat X using Xephyr on multi-header X configs.

Cheers,
Mungewell.

---

