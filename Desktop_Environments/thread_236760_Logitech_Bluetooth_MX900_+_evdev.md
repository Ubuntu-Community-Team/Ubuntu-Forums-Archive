---
title: "Logitech Bluetooth MX900 + evdev"
date: 2006-08-15
forum: Desktop Environments
---

### Post by jacaru on 2006-08-15
Hi all,

I am having a small problem trying to setup the MX900 with evdev driver.  I dont know why it is not working. evdev driver is installed and appears on 'lsmod'. event9 is created correctly and evtest works ok. I dont know if the fact that event9 wont be created until the mouse connects to the dongle has anything to do with this, but just restarting the X once I am sure the mouse is connected wont work either.

Here is Xorg log

```


(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-00:07:61:0D:31:AD: Core Pointer
(II) Configured Mouse-00:07:61:0D:31:AD: Found 2 absolute axes.
(II) Configured Mouse-00:07:61:0D:31:AD: Configuring as pointer.
(**) Configured Mouse-00:07:61:0D:31:AD: Configuring in Absolute mode.
(**) Configured Mouse-00:07:61:0D:31:AD: AbsoluteScreen: -1.

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a86]
1: [0xffffe420]
2: /usr/lib/xorg/modules/input/evdev_drv.so [0xb79f64a3]
3: /usr/lib/xorg/modules/input/evdev_drv.so [0xb79f7655]
4: /usr/lib/xorg/modules/input/evdev_drv.so(evdevNewDriver+0x44) [0xb79f7c3f]
5: /usr/lib/xorg/modules/input/evdev_drv.so [0xb79f6b8e]
6: /usr/bin/X(InitInput+0x1a0) [0x809cfe5]
7: /usr/bin/X(main+0x368) [0x806df94]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7da4ea2]
9: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting

```

Here is xorg conf

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/event9"
EndSection

```

Here is the rule to map the mouse to event9 (/etc/udev/rules.d/19-local.rules)

```

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech Bluetooth Mouse", NAME="input/event9"

```

Here is my bluez-utils HIDD conf

```

HIDD_ENABLED=1
#HIDD_OPTIONS="--master --server"
HIDD_OPTIONS="--server --search"
HIDD_OPTIONS="--connect 00:07:61:09:18:61 --server"

```

And here is part of 'cat /proc/bus/input/devices'

```

I: Bus=0003 Vendor=046d Product=c705 Version=2704
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-4.1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0005 Vendor=046d Product=b001 Version=2200
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:61:0D:31:AD
S: Sysfs=/class/input/input4
H: Handlers=mouse1 event3 ts1
B: EV=f
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=300 0

```

Thanks for your help

---

