---
title: "USB Mouse isn't working after recent update"
date: 2012-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by IndigentToad on 2012-02-21
Dell Inspiron 1545 running Ubuntu Studio 11.10 (Xfce). Ran the most recent update a few days ago and the USB mouse stopped working. TrackPad on the laptop is working fine. Tried two other USB mice (one wireless, one wired) and neither worked. I've used other USB devices and they've been recognised, so I don't think it's an issue with USB devices docking correctly.

Note that the mouse isn't working at all - I know there was an issue with mice not working in Unity sometime ago - but the built in track pad is still operational.

Thanks!

---

### Post by RIchard Metzler on 2012-03-04
I probably have the same problem (running Ubuntu 10.04.4 LTS on a Samsung laptop). The USB mouse stopped working yesterday.

Interestingly, the mouse works fine until a few seconds after the desktop comes up.

So far, no idea how to fix this...

Edit: found this message in /var/log/message

> 
Mar  4 09:50:21 richard kernel: [ 1658.880766] generic-usb 0003:04F3:0210.0002: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.0-1/input0
Mar  4 09:50:22 richard kernel: [ 1659.041086] usb 6-1: USB disconnect, address 5
Mar  4 09:50:23 richard kernel: [ 1660.309048] usb 6-1: new low speed USB device using uhci_hcd and address 7
Mar  4 09:50:23 richard kernel: [ 1660.531277] usb 6-1: configuration #1 chosen from 1 choice
Mar  4 09:50:23 richard kernel: [ 1660.550461] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input12
Mar  4 09:50:23 richard kernel: [ 1660.550590] generic-usb 0003:04F3:0210.0003: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.0-1/input0
[B]Mar  4 09:50:23 richard kernel: [ 1660.751103] usb 6-1: input irq status -75  received
Mar  4 09:50:23 richard kernel: [ 1660.776117] usb 6-1: USB disconnect, address 7[/B]
Mar  4 09:50:24 richard kernel: [ 1661.512073] usb 6-1: new low speed USB device using uhci_hcd and address 8
Mar  4 09:50:32 richard kernel: [ 1669.540061] usb 3-1: new low speed USB device using uhci_hcd and address 2

Still no idea what this means - but maybe someone else does?

---

### Post by codemaniac on 2012-03-04
> **RIchard Metzler said:**
> I probably have the same problem (running Ubuntu 10.04.4 LTS on a Samsung laptop). The USB mouse stopped working yesterday.

Interestingly, the mouse works fine until a few seconds after the desktop comes up.

So far, no idea how to fix this...

Edit: found this message in /var/log/message


Still no idea what this means - but maybe someone else does?


Please start a new thread instead of hijacking others .

Best Regards

---

### Post by codemaniac on 2012-03-04
> **IndigentToad said:**
> Dell Inspiron 1545 running Ubuntu Studio 11.10 (Xfce). Ran the most recent update a few days ago and the USB mouse stopped working. TrackPad on the laptop is working fine. Tried two other USB mice (one wireless, one wired) and neither worked. I've used other USB devices and they've been recognised, so I don't think it's an issue with USB devices docking correctly.

Note that the mouse isn't working at all - I know there was an issue with mice not working in Unity sometime ago - but the built in track pad is still operational.

Thanks!

Can you check what **lsusb **says on your system , and post here .

---

