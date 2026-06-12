---
title: "Dilong gamepad not detected"
date: 2013-11-16
forum: Gaming &amp; Leisure
---

### Post by uncleBez on 2013-11-16
This same question was asked 2+years ago but no real answers in the thread: [http://ubuntuforums.org/showthread.php?t=1845577](http://ubuntuforums.org/showthread.php?t=1845577)

I have just bought two cheap gamepads, one auto detects and just works (its a tevion) and the other doesn't.

The working one shows up in lsusb the other does not.

I have got the similar resutls on both my laptop and my desktop machine.

the desktop is Ubuntu 13.04 and the laptop is Ubuntu 12.04.3 LTS
The working pad shows in lsusb as :Bus 002 Device 011: ID 0f30:001c Jess Technology Co., Ltd PS3 Guitar Controller Dongle


A listing of dmesg after plugging in the non-working one shows this:
[ 1401.617083] usb 2-1.3: new low-speed USB device number 18 using ohci_hcd
[ 1401.697086] usb 2-1.3: device descriptor read/64, error -62
[ 1401.881077] usb 2-1.3: device descriptor read/64, error -62
[ 1402.061086] usb 2-1.3: new low-speed USB device number 19 using ohci_hcd
[ 1402.141073] usb 2-1.3: device descriptor read/64, error -62
[ 1402.325074] usb 2-1.3: device descriptor read/64, error -62
[ 1402.505074] usb 2-1.3: new low-speed USB device number 20 using ohci_hcd
[ 1402.912051] usb 2-1.3: device not accepting address 20, error -62
[ 1402.989077] usb 2-1.3: new low-speed USB device number 21 using ohci_hcd
[ 1403.396038] usb 2-1.3: device not accepting address 21, error -62
[ 1403.398086] hub 2-1:1.0: unable to enumerate USB device on port 3

---

