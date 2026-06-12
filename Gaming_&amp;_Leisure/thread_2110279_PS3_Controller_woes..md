---
title: "PS3 Controller woes."
date: 2013-01-29
forum: Gaming &amp; Leisure
---

### Post by Azelphur on 2013-01-29
Hi folks, I'm having a bit of a nightmare with some PS3 controllers I purchased to use with emulators on my PC.

The controllers are called [GOIGAME Rechargeable Bluetooth Wireless DoubleShock III Controller for PS3 - Black](http://dx.com/p/goigame-rechargeable-bluetooth-wireless-doubleshock-iii-controller-for-ps3-black-140342)

In dmesg they show up as:
```

[224268.708854] usb 2-2.1.3: new full-speed USB device number 92 using ehci_hcd
[224268.804383] usb 2-2.1.3: New USB device found, idVendor=054c, idProduct=0268
[224268.804387] usb 2-2.1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[224268.804390] usb 2-2.1.3: Product: PS(R) Gamepad
[224268.804392] usb 2-2.1.3: Manufacturer: Gasia Co.,Ltd
[224268.805532] sony 0003:054C:0268.0053: Fixing up Sony Sixaxis report descriptor
[224268.806685] input: Gasia Co.,Ltd PS(R) Gamepad as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2.1/2-2.1.3/2-2.1.3:1.0/input/input326
[224268.807059] sony 0003:054C:0268.0053: input,hiddev0,hidraw9: USB HID v1.11 Joystick [Gasia Co.,Ltd PS(R) Gamepad] on usb-0000:00:1d.7-2.1.3/input0

```

I have tried using sixad, sixpair runs correctly, I start sixad and it asks me to press the PS button, but unfortunately it doesn't detect me doing so. I've sat down and talked to the developer of qtsixa about it and it seems to be a bug, but it's unlikely to get fixed any time soon. I have replicated the issue using different controllers (since I have 4 of them), 3 different computers, and 2 different bluetooth adapters. :(

I know that the controllers are physically functional, as they work using sixpair controller on my Nexus 7 (Android)

Unfortunately this leaves me a little stuck, as I've purchased 4 of these with the goal of using them with my PC for emulators (I don't even own a PS3) does anyone have any suggestions as to what I can do to get them working?

Thanks

---

