---
title: "Frequent USB keyboard/mouse failure"
date: 2009-03-27
forum: General Help
---

### Post by mkoonstra on 2009-03-27
I am experiencing serious troubles with my USB devices. These problems range from not working devices, sticking keys and other annoyances.

When I look at dmesg, I see these kind of messages:
```
[ 2137.436266] hub 6-2:1.0: port 2 disabled by hub (EMI?), re-enabling...
[ 2137.437599] usb 6-2.2: USB disconnect, address 3
[ 2137.672332] usb 6-2.2: new low speed USB device using ehci_hcd and address 6
[ 2137.769327] usb 6-2.2: configuration #1 chosen from 1 choice
[ 2137.770996] input: Wacom Volito as /devices/pci0000:00/0000:00:13.5/usb6/6-2/6-2.2/6-2.2:1.0/input/input8
[ 2137.861191] hub 6-2:1.0: port 4 disabled by hub (EMI?), re-enabling...
[ 2137.862470] usb 6-2.4: USB disconnect, address 5
[ 2138.121392] usb 6-2.4: new low speed USB device using ehci_hcd and address 7
[ 2138.221203] usb 6-2.4: configuration #1 chosen from 1 choice
[ 2138.227485] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.5/usb6/6-2/6-2.4/6-2.4:1.0/input/input9
[ 2138.277326] input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.5-2.4
[ 2751.701515] usb 6-2.3: reset low speed USB device using ehci_hcd and address 4
```

Is there anything I can do to fix these errors?

---

### Post by HavocXphere on 2009-03-27
Not much of a fix, but some ideas.

Use another USB port...looks like the bios or something disables the one you are using on startup. Take a look at you mobo manual and figure out which USB ports are split, so that you can select a pair that isn't being used by something else.

Make sure the receiver & keyboard are close to eachother...this can cause sticking keys. Ideally line of sight & <1m.

I also seem to recall a similar message extract being posted in the JJ Alpha discussions. What version are you running?

---

### Post by mkoonstra on 2009-03-28
I am running Ubuntu 8.10 with kernel 2.6.27-11-generic.

Right now, my mouse failed but keyboard still works.

I have no wireless devices, they are all connected via cable.

I will try other USB ports and/or directly connecting the devices to the pc to see if that makes any difference.

---

