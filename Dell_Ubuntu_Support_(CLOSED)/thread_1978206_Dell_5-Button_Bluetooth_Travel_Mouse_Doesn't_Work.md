---
title: "Dell 5-Button Bluetooth Travel Mouse Doesn't Work"
date: 2012-05-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by madi on 2012-05-11
I've got this [5-Button Bluetooth Travel Mouse]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=330-1823&baynote_bnrank=1&baynote_irrank=0&~ck=baynoteSearch") from Dell and it works on windows xp, windows 7 and Fedora 11 on my Toshiba A200 laptop. Just stick and play, but it doesn't work on ubuntu 12.4


Here is dmesg:
```


[14054.072133] usb 7-2: new full-speed USB device number 2 using uhci_hcd
[14054.192208] usb 7-2: device descriptor read/64, error -71
[14054.416176] usb 7-2: device descriptor read/64, error -71
[14054.632102] usb 7-2: new full-speed USB device number 3 using uhci_hcd
[14054.752085] usb 7-2: device descriptor read/64, error -71
[14054.976163] usb 7-2: device descriptor read/64, error -71
[14055.192220] usb 7-2: new full-speed USB device number 4 using uhci_hcd
[14055.604097] usb 7-2: device not accepting address 4, error -71
[14055.716094] usb 7-2: new full-speed USB device number 5 using uhci_hcd
[14056.124126] usb 7-2: device not accepting address 5, error -71
[14056.124155] hub 7-0:1.0: unable to enumerate USB device on port 2
[14091.768133] usb 7-2: new full-speed USB device number 6 using uhci_hcd
[14091.953289] hub 7-2:1.0: USB hub found
[14091.955157] hub 7-2:1.0: 3 ports detected
[14092.237164] usb 7-2.2: new full-speed USB device number 7 using uhci_hcd
[14092.403817] input: Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input11
[14092.403963] generic-usb 0003:046D:C70E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech BT Mini-Receiver] on usb-0000:00:1d.2-2.2/input0
[14092.403985] usbcore: registered new interface driver usbhid
[14092.403988] usbhid: USB HID core driver
[14092.466277] usb 7-2.3: new full-speed USB device number 8 using uhci_hcd
[14092.631333] input: Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input12
[14092.631893] generic-usb 0003:046D:C70A.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech BT Mini-Receiver] on usb-0000:00:1d.2-2.3/input0
[14092.930283] usb 7-2.1: new full-speed USB device number 9 using uhci_hcd
```


I dont know why it says "Logitech BT Mini-Receiver" except its Dell bluetooth stick.

Any help please!

---

