---
title: "LG Voyager using Bitpim via Bluetooth"
date: 2009-03-12
forum: General Help
---

### Post by SunmanXII on 2009-03-12
I am trying to connect my LG Voyager to my computer via bluetooth.
I used this guide to set up my bitpim and my bluetooth port:
[http://arstechnica.com/open-source/news/2007/12/using-a-bluetooth-phone-with-linux.ars](http://arstechnica.com/open-source/news/2007/12/using-a-bluetooth-phone-with-linux.ars)

However, when I run bitpim (under sudo) it cannot detect my phone.
In the settings, Bitpim lists the bluetooth port as unavailable, when I brows the com-ports. This is what it has on my bluetooth port:
```

USB Device - Vendor Cambridge Silicon Radio, Ltd, Product Bluetooth Dongle (HCI mode), (Interface #00)	usb::003::002::0

This port is active but not available for use.
Property	Value	Description
PID	        0x0001	Product ID
VID	        0x0A12	Vendor ID
active	        True	Your operating system shows this driver and port is correctly configured and a device attached
available	False	It was not possible to open this port
description	USB Device - Vendor Cambridge Silicon Radio, Ltd, Product Bluetooth Dongle (HCI mode), (Interface #00)	 
libusb	        True	This indicates if the usb library is in use to access this device. Operating system device drivers (if any) are bypassed when BitPim talks to the device
name	usb::003::002::0	This is the name the port is known to your operating system as
protocol	Wireless / Radio Frequency / Bluetooth	This is the protocol the USB device claims to speak
```

Also, if this is important, I can see my phone and can browse it using the obex:// feature in Nautilus. I would like to get it working with bitpim though. 
Thank you,

---

