---
title: "Usb problems"
date: 2006-01-02
forum: General Help
---

### Post by thessem on 2006-01-02
Whenever I boot ubuntu up, I get the bootsplash thing, but it never progresses beyond "Loading Modules", after about a minute of showing that it cuts back into the text bootup thing, and it shows the error message "drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed".

Using dmesg I also found the error message in the bootup
"usb 1-1: device not accepting address 2, error -110
usb 1-1: new full speed USB device using ohci_hcd and address 4
usb 3-1: new low speed USB device using ohci_hcd and address 2
usbcore: registered new driver hiddev
drivers/usb/input/hid-core.c: timeout initializing reports

input: USB HID v1.10 Keyboard [BELKIN RF Mouse] on usb-0000:00:03.2-1
drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
drivers/usb/input/hid-core.c: timeout initializing reports

input: USB HID v1.10 Mouse [BELKIN RF Mouse] on usb-0000:00:03.2-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver"

If it helps I'm using a wireless usb mouse.

Although the mouse seems to be working, its just annoying that I dont get the bootsplash, and that my machine takes ages to boot. Also, I think that the usb gamepads thing I did with Automatix had something to do with this.


And also, does anyone here know how to disable the ntp thing at boot, as I am on dialup and I also have to wait for that to timeout.

---

