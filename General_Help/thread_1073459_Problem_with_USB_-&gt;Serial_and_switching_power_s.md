---
title: "Problem with USB -&gt;Serial and switching power source"
date: 2009-02-18
forum: General Help
---

### Post by wowbagger53 on 2009-02-18
I have successfully installed Ubuntu 8.10 on an Acer Aspire 5650 laptop for use as a server with built-in UPS. The battery should keep it running for a couple of hours if the power goes off. I have an application that continually talks RS232 serial to a device. I am using a USB->serial converter as /dev/ttyUSB0.

The problem is this:

If the power mode switches from mains to battery or vice versa then it seems as though the USB->serial is unloaded then reloaded. Since the original port is open it can't be recreated as that name, so it becomes /dev/ttyUSB1. Meanwhile, my application hangs.

Does anyone know of a way to stop this behaviour?

FYI, here are the associated kernel log entries:

[FONT="Courier New"][SIZE="2"]Feb 18 13:31:10 penguin kernel: [75020.735071] CPU0 attaching NULL sched-domain.
Feb 18 13:31:10 penguin kernel: [75020.735093] CPU1 attaching NULL sched-domain.
Feb 18 13:31:10 penguin kernel: [75020.737128] CPU0 attaching sched-domain:
Feb 18 13:31:10 penguin kernel: [75020.737137]  domain 0: span 0-1 level MC
Feb 18 13:31:10 penguin kernel: [75020.737143]   groups: 0 1
Feb 18 13:31:10 penguin kernel: [75020.737152]   domain 1: span 0-1 level CPU
Feb 18 13:31:10 penguin kernel: [75020.737159]    groups: 0-1
Feb 18 13:31:10 penguin kernel: [75020.737167] CPU1 attaching sched-domain:
Feb 18 13:31:10 penguin kernel: [75020.737172]  domain 0: span 0-1 level MC
Feb 18 13:31:10 penguin kernel: [75020.737178]   groups: 1 0
Feb 18 13:31:10 penguin kernel: [75020.737186]   domain 1: span 0-1 level CPU
Feb 18 13:31:10 penguin kernel: [75020.737193]    groups: 0-1
Feb 18 13:31:14 penguin kernel: [75025.624131] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Feb 18 13:31:14 penguin kernel: [75025.624148] usb 2-1: USB disconnect, address 3
Feb 18 13:31:14 penguin kernel: [75025.628912] pl2303 2-1:1.0: device disconnected
Feb 18 13:31:15 penguin kernel: [75025.868106] usb 2-1: new full speed USB device using uhci_hcd and address 4
Feb 18 13:31:15 penguin kernel: [75026.024419] usb 2-1: configuration #1 chosen from 1 choice
Feb 18 13:31:15 penguin kernel: [75026.033865] pl2303 2-1:1.0: pl2303 converter detected
Feb 18 13:31:15 penguin kernel: [75026.045396] usb 2-1: pl2303 converter now attached to ttyUSB1[/SIZE][/FONT]

---

### Post by geraldm on 2009-02-18
I would suggest (read: I do not know if this works) looking for the serial number on the USB converter.  Some devices, such as those from FTDI, have the serial number, and you could try to assign it to a specific device, say /dev/ttyUSB8, by means of a UDEV assignment when the USB is being discovered on hub wake-up.
This has been mentioned in the Hardware&Laptop forum, so a search should find a UDEV assignment statement.

Gerald

---

### Post by wowbagger53 on 2009-02-19
Thanks, Gerald. Unfortunately the Prolific device does not have a serial number. I may try changing the configuration such that it does not go into laptop-mode on changing to battery power, but I suspect that this might prevent it shutting down when the battery gets too low.

---

