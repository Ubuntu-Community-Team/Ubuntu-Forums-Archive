---
title: "USB initialization problem"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Bazzaah on 2007-04-22
I have a USB device that does not initialise at boot - it works if I unplug it and replug it once booted up. It is a CH Products joystick and the problem seems to be a longstanding one, in that I have seen the exact same problem reported on other forums over the last 2 years or so. It apparently remains unresolved. 

I want to get this problem addressed but not sure whether it would be a problem within Ubuntu or the hardware - could someone give me a rough idea where the problem might lie so I can try and get the problem addressed?

here's my dmesg | grep usb ,fyi

[    2.991642] usbcore: registered new interface driver usbfs
[    2.991675] usbcore: registered new interface driver hub
[    2.991709] usbcore: registered new device driver usb
[    2.993386] usb usb1: configuration #1 chosen from 1 choice
[    3.095366] usb usb2: configuration #1 chosen from 1 choice
[    3.199363] usb usb3: configuration #1 chosen from 1 choice
[    3.303714] usb usb4: configuration #1 chosen from 1 choice
[    3.408140] usb usb5: configuration #1 chosen from 1 choice
[    3.439862] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.512499] usb usb6: configuration #1 chosen from 1 choice
[    3.622389] usb 2-1: configuration #1 chosen from 1 choice
[    3.628235] usb usb7: configuration #1 chosen from 1 choice
[    3.635470] usb 2-1: USB disconnect, address 2
[    3.732896] usb usb8: configuration #1 chosen from 1 choice
[    4.831798] usb 7-8: new high speed USB device using ehci_hcd and address 3
[    4.969143] usb 7-8: configuration #1 chosen from 1 choice
[    5.550093] usbcore: registered new interface driver hiddev
[    5.550160] usbcore: registered new interface driver libusual
[    5.786745] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    5.963722] usb 5-1: configuration #1 chosen from 1 choice
[    6.221137] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    6.397980] usb 5-2: configuration #1 chosen from 1 choice
[    6.415057] usb-storage: device found at 3
[    6.415060] usb-storage: waiting for device to settle before scanning
[    6.434883] input: USB HID v1.00 Joystick [CH PRODUCTS CH COMBATSTICK USB] on usb-0000:02:06.0-1
[    6.446864] input: USB HID v1.00 Joystick [CH PRODUCTS CH PRO PEDALS USB ] on usb-0000:02:06.0-2
[    6.446887] usbcore: registered new interface driver usbhid
[    6.446891] usbcore: registered new interface driver usb-storage
[    6.446902] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    6.655211] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    6.837210] usb 2-1: configuration #1 chosen from 1 choice
[    6.860205] input: USB HID v1.11 Keyboard [Cypress WirelessUSB] on usb-0000:00:1d.1-1
[    6.893215] input,hiddev96: USB HID v1.11 Mouse [Cypress WirelessUSB] on usb-0000:00:1d.1-1
[   11.405364] usb-storage: device scan complete
[   17.731567] usbcore: registered new interface driver xpad
[   17.731574] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   18.321375] usbcore: registered new interface driver iforce


Thanks in advance.....

---

### Post by Bazzaah on 2007-04-22
sorry seem to have posted it in the wrong forum, woops! feel free to ignore.....

---

### Post by Darti on 2007-04-22
I am having a simular problem, see [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2497673]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2497673") it seems that the usb detection in fiesty is having problems, I cant even managed to get it to install. 
Please post back if you manage to get a solution.

---

