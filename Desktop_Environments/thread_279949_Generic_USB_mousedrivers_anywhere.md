---
title: "Generic USB mousedrivers anywhere?"
date: 2006-10-18
forum: Desktop Environments
---

### Post by CheeseEatingBulldog on 2006-10-18
For a while now I cannot use my usb ports on my laptop. When I plug an external mouse into the usb, I do see an unknown device, (which dissapears when I dissconnect the mouse).

So how do I install a driver for it, or tell my comp it's a mouse?

---

### Post by mssever on 2006-10-18
Sounds like some bad hardware. Ubuntu has built in support for USB mice. You could try looking for info in /var/log/messages.

---

### Post by CheeseEatingBulldog on 2006-10-19
It's not bad hardware as nothing works when I plug into either of the TWO usb ports. You do see devices being connected and disconnected though.

So I can't 'force' install a driver for a particular device?

---

### Post by mssever on 2006-10-19
Try this: type ```
less /var/log/messages
``` and hit F (<shift>F). Now, plug your mouse in and see what messages you get.

For example, when I plug in my USB mouse, I get the following: ```
Oct 19 04:03:10 localhost kernel: [17188141.928000] usb 2-2: new low speed USB device using uhci_hcd and address 3
Oct 19 04:03:10 localhost kernel: [17188142.116000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input5
Oct 19 04:03:10 localhost kernel: [17188142.116000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.1-2
```Do you get anything similar?

---

