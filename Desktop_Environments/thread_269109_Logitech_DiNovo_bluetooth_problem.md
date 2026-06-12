---
title: "Logitech DiNovo bluetooth problem"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Ibbelz on 2006-10-01
I've a Logitech DiNovo cordless desktop but I can't get it to work properly. :( I followed [this]("http://www.ubuntuforums.org/showthread.php?t=113184&highlight=bluetooth+mouse") guide, it is for the MX900 but I figured it should work for the MX1000 and other bluetooth devices too (DiNovo desktop exists of MX1000 mouse, bluetooth keyboard and mediapad).

When I do **hcitool scan** i get te following message:

```

Device is not available: No such device

```

So I can't connect to my bluetooth devices. I know bluetooth works correctly because the mediapad that comes with the DiNovo desktop worked out of the box :-?  without any extra configuration. :(

Output from **lsusb**:

```

Bus 003 Device 006: ID 0424:2228 Standard Microsystems Corp.
Bus 003 Device 005: ID 0424:2602 Standard Microsystems Corp.
Bus 003 Device 004: ID 0424:2502 Standard Microsystems Corp.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 006: ID 046d:c70c Logitech, Inc.
Bus 001 Device 005: ID 046d:c70b Logitech, Inc.
Bus 001 Device 004: ID 046d:0b02 Logitech, Inc.
Bus 001 Device 003: ID 04a9:1094 Canon, Inc. PIXMA iP3000x Printer
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 001: ID 0000:0000

```

Output from **dmesg bluetooth related stuff**:

```

[17179618.924000] Bluetooth: HCI device and connection manager initialized
[17179618.924000] Bluetooth: HCI socket layer initialized
[17179618.960000] Bluetooth: L2CAP ver 2.8
[17179618.960000] Bluetooth: L2CAP socket layer initialized
[17179618.976000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179626.964000] Bluetooth: RFCOMM socket layer initialized
[17179626.964000] Bluetooth: RFCOMM TTY layer initialized
[17179626.964000] Bluetooth: RFCOMM ver 1.7
[17179942.736000] usb 1-3: new full speed USB device using ohci_hcd and address 4
[17179942.960000] hub 1-3:1.0: USB hub found
[17179942.960000] hub 1-3:1.0: 3 ports detected
[17179943.292000] usb 1-3.2: new full speed USB device using ohci_hcd and address 5
[17179943.436000] input: Logitech Logitech BT Mini-Receiver as /class/input/input4
[17179943.436000] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:02.0-3.2
[17179943.644000] usb 1-3.3: new full speed USB device using ohci_hcd and address 6
[17179943.788000] input: Logitech Logitech BT Mini-Receiver as /class/input/input5
[17179943.788000] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:02.0-3.3

```

I'am realy desperate to get this working because I work with a very bad mouse at the moment. Could anyone pleasy point me in te right direction? I would love to use my DiNovo desktop in Ubuntu! :cool:

---

### Post by Ibbelz on 2006-10-02
Hmm no good ideas? I would really like to work with this desktop set. :(

---

