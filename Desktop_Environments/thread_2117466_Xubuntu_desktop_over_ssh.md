---
title: "Xubuntu desktop over ssh"
date: 2013-02-18
forum: Desktop Environments
---

### Post by mightymouse3062 on 2013-02-18
Good afternoon, 
I have a Xubuntu 12.10 x64 virtual machine running and I only have SSH access to it. I do not have any console, or GUI access. With that being said, I would like to get VNC running on it so I can remotely connect. 

I have installed x11vnc and I have tried to start x11vnc by doing x11vnc -display :0 or x11vnc -nopw (I know the no password isn't secure), both of which fail on XOpenDisplay failed. x11vnc was unable to open the X DISPLAY: ":0", it cannot continue. 

I believe the reason is I don't have xubuntu-desktop running (It is installed). I have tried startx and it hangs Loading extension GLX... 
Here is the Xorg.0.log: 
```
[     9.698] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     9.698] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     9.698] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input1/event1"
[     9.698] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 7)
[     9.698] (**) Option "xkb_rules" "evdev"
[     9.698] (**) Option "xkb_model" "pc105"
[     9.698] (**) Option "xkb_layout" "us"
[     9.698] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event2)
[     9.698] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[     9.698] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "vmmouse"
[     9.698] (II) LoadModule: "vmmouse"
[     9.699] (II) Loading /usr/lib/xorg/modules/input/vmmouse_drv.so
[     9.699] (II) Module vmmouse: vendor="X.Org Foundation"
[     9.699] 	compiled for 1.13.0, module version = 12.9.0
[     9.699] 	Module class: X.Org XInput Driver
[     9.699] 	ABI class: X.Org XInput driver, version 18.0
[     9.699] (II) VMWARE(0): VMMOUSE module was loaded
[     9.699] (II) Using input driver 'vmmouse' for 'ImPS/2 Generic Wheel Mouse'
[     9.699] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[     9.699] (II) VMWARE(0): vmmouse is available
[     9.699] (**) Option "Device" "/dev/input/event2"
[     9.700] (**) ImPS/2 Generic Wheel Mouse: ZAxisMapping: buttons 4 and 5
[     9.700] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input2/event2"
[     9.700] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 8)
[     9.700] (II) VMWARE(0): VMMOUSE DEVICE_INIT
[     9.700] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[     9.700] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[     9.700] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[     9.700] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[     9.700] (II) VMWARE(0): VMMOUSE DEVICE_ON
[     9.700] (II) VMWARE(0): vmmouse enabled
[     9.700] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[     9.700] (II) No input driver specified, ignoring this device.
[     9.700] (II) This device may have been added with another device file.
[   187.244] (II) VMWARE(0): VMMOUSE DEVICE_OFF/CLOSE
[   224.506] (II) Open ACPI successful (/var/run/acpid.socket)
[   224.714] (II) VMWARE(0): VMMOUSE DEVICE_ON
[   224.715] (II) VMWARE(0): vmmouse enabled
[  1046.464] (II) VMWARE(0): VMMOUSE DEVICE_OFF/CLOSE
[  1178.515] (II) Open ACPI successful (/var/run/acpid.socket)
[  1178.719] (II) VMWARE(0): VMMOUSE DEVICE_ON
[  1178.720] (II) VMWARE(0): vmmouse enabled
[  1183.024] (II) VMWARE(0): VMMOUSE DEVICE_OFF/CLOSE
[  1351.144] (II) Open ACPI successful (/var/run/acpid.socket)
[  1351.353] (II) VMWARE(0): VMMOUSE DEVICE_ON
[  1351.354] (II) VMWARE(0): vmmouse enabled
[  1887.044] (II) VMWARE(0): VMMOUSE DEVICE_OFF/CLOSE
[  1903.237] (II) Open ACPI successful (/var/run/acpid.socket)
[  1903.450] (II) VMWARE(0): VMMOUSE DEVICE_ON
[  1903.451] (II) VMWARE(0): vmmouse enabled

```

How do I start the xubuntu-desktop over ssh so I can get a VNC connection setup?

Thank you.

---

