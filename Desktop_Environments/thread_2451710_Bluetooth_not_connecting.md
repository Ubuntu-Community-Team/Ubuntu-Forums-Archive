---
title: "Bluetooth not connecting"
date: 2020-10-09
forum: Desktop Environments
---

### Post by whtemple1959 on 2020-10-09
I will admit that this is the first time I am attempting a bluetooth  connection
I have successfully paired and connected the TreLab  headphones
I am attempting to connect a ps4 bluetooth controller
I have  installed python-pip, python-dev, and ds4drv
The controller has paired  successfully
But, when I attempt to connect the controller will connect  and them immediately disconnect.
Some basic information about the system  ...
$ lsusbBus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd  Bluetooth Dongle (HCI mode)
$ bluetoothctl
[NEW] Controller  00:1A:7D:DA:71:13 pavilion [default]
[NEW] Device 41:42:9C:AC:1F:76  Wireless Controller
[NEW] Device 50:18:12:22:09:F5 Treblab XR100
Agent  registered
$ ds4drv
[info][controller 1] Created devices /dev/input/js0  (joystick) /dev/input/event15 (evdev)
[info][bluetooth] Scanning for  devices
[info][bluetooth] Found device  41:42:9C:AC:1F:76
[error][bluetooth] Unable to connect to detected  device: Failed to set operational mode: [Errno 107] Transport endpoint  is not connected
As I have Thunar running in the background via sudo I  noticed this error in the terminal window
$ sudo thunar
thunar-volman:  Unsupported input device type "(null)"
thunar-volman: Unsupported input  device type "/dev/input/event15"
thunar-volman: Unsupported input device  type "/dev/input/js0"
When using the GUI to connect the controller I get this error ...
connection failed blueman bluez errors dbus failed error resource temporarily unavailable
Any advice on what I am doing wrong?

---

