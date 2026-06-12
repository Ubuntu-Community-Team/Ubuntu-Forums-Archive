---
title: "Lucid Lynx Jscal Calibration"
date: 2011-07-25
forum: Gaming &amp; Leisure
---

### Post by Einder on 2011-07-25
[FONT=Book Antiqua][SIZE=2]I am currently running Lucid Lynx and want to use Jscal to calibrate my game/joy pad. I can find it in dmesg as it appears below:[/SIZE][/FONT]

```
[SIZE=2][42374.247485] ISOFS: changing to secondary root
[51241.713077] usb 5-2: new low speed USB device using uhci_hcd and address 2
[51241.880540] usb 5-2: configuration #1 chosen from 1 choice
[51242.236608] usbcore: registered new interface driver hiddev
[51242.236685] usbcore: registered new interface driver usbhid
[51242.236688] usbhid: v2.6:USB HID core driver
[51242.407480] input: Twin USB Joystick as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input13
[51242.407935] input: Twin USB Joystick as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input14
[51242.408932] pantherlord 0003:0810:0001.0001: input,hidraw0: USB HID v1.10 Joystick [Twin USB Joystick] on usb-0000:00:1d.0-2/input0
[51242.408958] pantherlord 0003:0810:0001.0001: Force feedback for PantherLord/GreenAsia devices by Anssi Hannula <anssi.hannula@gmail.com>
[51479.264110] hub 5-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[51479.264125] usb 5-2: USB disconnect, address 2
[51480.001122] usb 5-2: new low speed USB device using uhci_hcd and address 3
[51480.065566] hub 5-0:1.0: unable to enumerate USB device on port 2
[51724.800134] usb 5-2: new low speed USB device using uhci_hcd and address 4
[51724.970398] usb 5-2: configuration #1 chosen from 1 choice
[51725.014576] input: Twin USB Joystick as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input15
[51725.014890] input: Twin USB Joystick as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input16
[51725.015210] pantherlord 0003:0810:0001.0002: input,hidraw0: USB HID v1.10 Joystick [Twin USB Joystick] on usb-0000:00:1d.0-2/input0
[51725.015237] pantherlord 0003:0810:0001.0002: Force feedback for PantherLord/GreenAsia devices by Anssi Hannula <anssi.hannula@gmail.com>[/SIZE]

```

[FONT=Book Antiqua][SIZE=2]The Twin USB Joystick as you can see is found. My problem is that I don't know how to configure it using jscal. I've never done this kind of thing through linux so for me it's proposing a problem. All help is very much appreciated.[/SIZE][/FONT]

---

### Post by Einder on 2011-07-29
Perhaps I don't need to configure it but to get linux to correctly recognize it? After going through many other posts on this forum as well as others I think this is what needs to happen...unfortunately I don't know how to make it happen....

---

### Post by Einder on 2011-07-29
Ok, scratch all the above and sorry if any updates on my own personal finding are causing issues.

Let me know what you need and I'll get it but here's the "heart" of my issue. I'm using a PS PS2 USB Dual Controller to Adapter Converter to try and configure my PS controller for use with an emulator. Using PCSX as the emulator I am unable to "change" the configuration file for my controller which is stored in /dev/input/js0 according to the file label. Obviously the controller is not being read though it is receiving power. I managed to get it disabled from trying to be used as a mouse already. I am just not sure what else I should do to get it working.

---

### Post by Einder on 2011-07-29
user error, sorry. Tested through ZNES config and it worked just fine..will have to find another emulator

---

