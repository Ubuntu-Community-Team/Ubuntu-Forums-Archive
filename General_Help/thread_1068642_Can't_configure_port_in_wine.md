---
title: "Can't configure port in wine"
date: 2009-02-13
forum: General Help
---

### Post by Doug11 on 2009-02-13
Hi,,I am try to run a program in wine whcih uses a com port. My laptop does not ahve a come port so i have a usb-serial adapter. The program I am using only list com ports in it's dropdown list. this is where my adatper is connected ..
doug@lappy:~$ dmesg | grep USB
[   22.936836] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   22.937206] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   22.992896] hub 1-0:1.0: USB hub found
[   23.096905] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   23.152785] hub 2-0:1.0: USB hub found
[   23.256894] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   23.400484] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   23.412476] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.412611] hub 3-0:1.0: USB hub found
[   24.451891] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   24.963606] usb 1-3: new low speed USB device using ohci_hcd and address 4
[   25.201718] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-3/1-3:1.0/input/input2
[   25.211524] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-3
[   25.216590] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-3
[   25.216611] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.362596] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   41.362637] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   41.410507] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[   41.410706] usb 1-1: pl2303 converter now attached to ttyUSB0
[   41.410718] /build/buildd/linux-2.6.24/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver


Is there a way to link this ttyUSB0 to one of the comports in wine. I read a report somewhere that one guy did it but did not tell how.
I also have a program to do the same job compiled for linux as a .deb package but it to only lists com ports and that's it.

---

### Post by humppe on 2009-02-27
That should be easy. Make a symbolic link com1 to your ~/.wine/dosdevices -directory.

```
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
```

---

### Post by Doug11 on 2009-03-01
> **humppe said:**
> That should be easy. Make a symbolic link com1 to your ~/.wine/dosdevices -directory.

```
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
```

That did not work right off,,but I went back into configure wine and checked to see if I was missing anything. I changed the setting for that program from Vista to XP and it worked no problem. Thank you.

---

