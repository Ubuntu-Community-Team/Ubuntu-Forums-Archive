---
title: "Keyboard 'stuck'   only types lower case / crashes windows"
date: 2008-11-25
forum: Desktop Environments
---

### Post by grayhatter on 2008-11-25
Occasionally my keyboard will 'crash.' The symptoms are stuck on num lock light, and inability to use the shift key (upper case, special characters, etc. don't work).

I've tried different keyboards and the problem does not go away.  (needless to say unplugging / plugging in the keyboard doesn't help).

The other oddity, is the keyboard still works fine inside virtual machines (I have VMware running).

Lower case keys work in terminal, however if I open a new application... any button press apparently forces the window to close.

I searched the forum and couldn't not find a similar problem, hopefully you guys can help.

ssh from another workstation works fine, i don't see any other issues.  Is there a 'keyboard service' i can restart?

Primarily i'm using a Dell Keyboard, the computer is a Dell Precision 380.  (The other keyboard tested was a belkin)

Ubuntu v.8.04 (up to date)

DMESG of keyboard being plugged in:
[92353.236073] usb 3-2: new full speed USB device using uhci_hcd and address 11
[92353.413172] usb 3-2: configuration #1 chosen from 1 choice
[92353.419045] hub 3-2:1.0: USB hub found
[92353.420005] hub 3-2:1.0: 3 ports detected
[92353.745820] usb 3-2.1: new full speed USB device using uhci_hcd and address 12
[92353.880894] usb 3-2.1: configuration #1 chosen from 1 choice
[92353.889688] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2.1/3-2.1:1.0/input/input20
[92353.931783] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-2.1
[92353.939825] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2.1/3-2.1:1.1/input/input21
[92353.979764] input,hidraw1: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1d.2-2.1

---

