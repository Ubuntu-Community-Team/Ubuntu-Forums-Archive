---
title: "Help needed getting Joystick going..."
date: 2011-05-23
forum: Gaming &amp; Leisure
---

### Post by hopelessone on 2011-05-23
Hi,

Ubuntu 10.10 64bit with **Saulabi 4k** USB joystick (works on windows)

**Directions:** UP,DOWN,LEFT,RIGHT (Working)
**Buttons:** 1,2,3,4,5,6,7,8,9,10 (Nothing)

Logs Show:
```
May 23 20:35:59 ubuntu kernel: [47742.170038] usb 3-1: new low speed USB device using uhci_hcd and address 5
May 23 20:35:59 ubuntu kernel: [47742.379508] input: ISAULABI   USBKeyStick as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input6
May 23 20:35:59 ubuntu kernel: [47742.379682] generic-usb 0003:0EF5:3000.0006: input,hidraw2: USB HID v1.00 Keyboard [ISAULABI   USBKeyStick] on usb-0000:00:1d.1-1/input0
May 23 20:36:24 ubuntu kernel: [47767.371407] generic-usb: probe of 0003:0EF5:3000.0007 failed with error -110
May 23 20:36:49 ubuntu kernel: [47792.372472] generic-usb: probe of 0003:0EF5:3000.0008 failed with error -110
```

What is error 110? can't find it on google? how to fix?

[B]Here's the dump:
[/B]```
2c2
< Dumping 129 device(s) from the Global Device List:
---
> Dumping 133 device(s) from the Global Device List:
1074a1075
>   storage.partitioning_scheme = ''  (string)
1755a1757,1872
> udi = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial'
>   info.linux.driver = 'usb'  (string)
>   info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
>   info.product = 'USBKeyStick'  (string)
>   info.subsystem = 'usb_device'  (string)
>   info.udi = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial'  (string)
>   info.vendor = 'PointChips'  (string)
>   linux.device_file = '/dev/bus/usb/005/004'  (string)
>   linux.hotplug_type = 2  (0x2)  (int)
>   linux.subsystem = 'usb'  (string)
>   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2'  (string)
>   usb_device.bus_number = 5  (0x5)  (int)
>   usb_device.can_wake_up = false  (bool)
>   usb_device.configuration_value = 1  (0x1)  (int)
>   usb_device.device_class = 0  (0x0)  (int)
>   usb_device.device_protocol = 0  (0x0)  (int)
>   usb_device.device_revision_bcd = 0  (0x0)  (int)
>   usb_device.device_subclass = 0  (0x0)  (int)
>   usb_device.is_self_powered = false  (bool)
>   usb_device.linux.device_number = 4  (0x4)  (int)
>   usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2'  (string)
>   usb_device.max_power = 100  (0x64)  (int)
>   usb_device.num_configurations = 1  (0x1)  (int)
>   usb_device.num_interfaces = 3  (0x3)  (int)
>   usb_device.num_ports = 0  (0x0)  (int)
>   usb_device.product = 'USBKeyStick'  (string)
>   usb_device.product_id = 12288  (0x3000)  (int)
>   usb_device.speed = 1.5 (1.5) (double)
>   usb_device.vendor = 'PointChips'  (string)
>   usb_device.vendor_id = 3829  (0xef5)  (int)
>   usb_device.version = 1.0 (1) (double)
> 
> udi = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial_if1'
>   info.linux.driver = 'usbhid'  (string)
>   info.parent = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial'  (string)
>   info.product = 'USB HID Interface'  (string)
>   info.subsystem = 'usb'  (string)
>   info.udi = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial_if1'  (string)
>   linux.hotplug_type = 2  (0x2)  (int)
>   linux.subsystem = 'usb'  (string)
>   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1'  (string)
>   usb.bus_number = 5  (0x5)  (int)
>   usb.can_wake_up = false  (bool)
>   usb.configuration_value = 1  (0x1)  (int)
>   usb.device_class = 0  (0x0)  (int)
>   usb.device_protocol = 0  (0x0)  (int)
>   usb.device_revision_bcd = 0  (0x0)  (int)
>   usb.device_subclass = 0  (0x0)  (int)
>   usb.interface.class = 3  (0x3)  (int)
>   usb.interface.number = 1  (0x1)  (int)
>   usb.interface.protocol = 2  (0x2)  (int)
>   usb.interface.subclass = 0  (0x0)  (int)
>   usb.is_self_powered = false  (bool)
>   usb.linux.device_number = 4  (0x4)  (int)
>   usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1'  (string)
>   usb.max_power = 100  (0x64)  (int)
>   usb.num_configurations = 1  (0x1)  (int)
>   usb.num_interfaces = 3  (0x3)  (int)
>   usb.num_ports = 0  (0x0)  (int)
>   usb.product = 'USB HID Interface'  (string)
>   usb.product_id = 12288  (0x3000)  (int)
>   usb.speed = 1.5 (1.5) (double)
>   usb.vendor = 'PointChips'  (string)
>   usb.vendor_id = 3829  (0xef5)  (int)
>   usb.version = 1.0 (1) (double)
> 
> udi = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial_if0'
>   info.linux.driver = 'usbhid'  (string)
>   info.parent = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial'  (string)
>   info.product = 'USB HID Interface'  (string)
>   info.subsystem = 'usb'  (string)
>   info.udi = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial_if0'  (string)
>   linux.hotplug_type = 2  (0x2)  (int)
>   linux.subsystem = 'usb'  (string)
>   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0'  (string)
>   usb.bus_number = 5  (0x5)  (int)
>   usb.can_wake_up = false  (bool)
>   usb.configuration_value = 1  (0x1)  (int)
>   usb.device_class = 0  (0x0)  (int)
>   usb.device_protocol = 0  (0x0)  (int)
>   usb.device_revision_bcd = 0  (0x0)  (int)
>   usb.device_subclass = 0  (0x0)  (int)
>   usb.interface.class = 3  (0x3)  (int)
>   usb.interface.number = 0  (0x0)  (int)
>   usb.interface.protocol = 1  (0x1)  (int)
>   usb.interface.subclass = 0  (0x0)  (int)
>   usb.is_self_powered = false  (bool)
>   usb.linux.device_number = 4  (0x4)  (int)
>   usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0'  (string)
>   usb.max_power = 100  (0x64)  (int)
>   usb.num_configurations = 1  (0x1)  (int)
>   usb.num_interfaces = 3  (0x3)  (int)
>   usb.num_ports = 0  (0x0)  (int)
>   usb.product = 'USB HID Interface'  (string)
>   usb.product_id = 12288  (0x3000)  (int)
>   usb.speed = 1.5 (1.5) (double)
>   usb.vendor = 'PointChips'  (string)
>   usb.vendor_id = 3829  (0xef5)  (int)
>   usb.version = 1.0 (1) (double)
> 
> udi = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial_if0_logicaldev_input'
>   info.addons.singleton = {'hald-addon-input'} (string list)
>   info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
>   info.category = 'input'  (string)
>   info.parent = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial_if0'  (string)
>   info.product = 'ISAULABI   USBKeyStick'  (string)
>   info.subsystem = 'input'  (string)
>   info.udi = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial_if0_logicaldev_input'  (string)
>   input.device = '/dev/input/event4'  (string)
>   input.originating_device = '/org/freedesktop/Hal/devices/usb_device_ef5_3000_noserial_if0'  (string)
>   input.product = 'ISAULABI   USBKeyStick'  (string)
>   linux.device_file = '/dev/input/event4'  (string)
>   linux.hotplug_type = 2  (0x2)  (int)
>   linux.subsystem = 'input'  (string)
>   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input5/event4'  (string)
> 
2631c2748
< Dumped 129 device(s) from the Global Device List.
---
> Dumped 133 device(s) from the Global Device List.
```

**How can I make it work before throwing it out the window?** Emailed the supplier (Korean) no answer...so upset and sad as can't get refund...

If I made a .fdi file would it still work?

Many Thanks,

---

### Post by mips on 2011-05-23
install and try using 'evtest'

---

