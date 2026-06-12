---
title: "USB Hub in Dapper Not Working (possibly ehci vs ohci)?"
date: 2006-12-24
forum: Desktop Environments
---

### Post by bhogg on 2006-12-24
Hey all,

I just upgraded to dapper as I was having trouble getting my MX Revolution mouse to work.  After upgrading it does work, but now I can only have one thing plugged into my usb hub/switch (which switches my mouse and keyboard between my laptop and desktop).  It is recognized when I flip the switch from laptop to desktop:

```
[17181412.132000] usb 3-4: USB disconnect, address 9
[17181412.132000] usb 3-4.1: USB disconnect, address 10
[17181413.380000] usb 3-4: new high speed USB device using ehci_hcd and address 14
[17181413.512000] hub 3-4:1.0: USB hub found
[17181413.512000] hub 3-4:1.0: 4 ports detected
[17181413.832000] usb 3-4.1: new full speed USB device using ehci_hcd and address 15
[17181413.944000] input: Logitech USB Receiver as /class/input/input18
[17181413.944000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:03.3-4.1
[17181413.948000] input: Logitech USB Receiver as /class/input/input19
[17181413.948000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:03.3-4.1

```

My mouse, which is the only thing plugged into the switch in the dmesg paste above, is working.  But there are a bunch of errors above that:

```
...
[17181412.124000] drivers/usb/input/hid-core.c: input irq status -71 received
[17181412.124000] drivers/usb/input/hid-core.c: input irq status -71 received
[17181412.128000] drivers/usb/input/hid-core.c: input irq status -71 received
[17181412.128000] drivers/usb/input/hid-core.c: input irq status -71 received
...
```

This wouldn't bother me but I can't get my USB keyboard to work when plugged into the usb switch, only when plugged directly into the desktop.  When I plug/unplug the keyboard directly into the desktop:

```
[17181605.136000] usb 1-3: USB disconnect, address 4
[17181652.272000] usb 2-3: new low speed USB device using ohci_hcd and address 3
[17181652.492000] input: HID 1267:0103 as /class/input/input20
[17181652.492000] input: USB HID v1.10 Keyboard [HID 1267:0103] on usb-0000:00:03.1-3
[17181652.504000] input: HID 1267:0103 as /class/input/input21
[17181652.504000] input: USB HID v1.10 Device [HID 1267:0103] on usb-0000:00:03.1-3

```

And when I unplug it and plug it into the switch:

```
[17181700.568000] usb 2-3: USB disconnect, address 3
[17181711.076000] usb 3-4.2: new low speed USB device using ehci_hcd and address 17
[17181711.192000] input: HID 1267:0103 as /class/input/input22
[17181711.192000] input: USB HID v1.10 Keyboard [HID 1267:0103] on usb-0000:00:03.3-4.2
[17181711.196000] input: HID 1267:0103 as /class/input/input23
[17181711.196000] input: USB HID v1.10 Device [HID 1267:0103] on usb-0000:00:03.3-4.2

```

When in the switch the keyboard does not work at all.

Looks like something with ehci_hcd verses ohci, but I don't really know the particulars there.  I'm currently using just the "mouse" driver in xorg instead of "evdev" which doesn't allow some of the advanced features, but had similar behavior with the keyboard either way.  The keyboard does work when plugged into the usb switch at the GRUB screen, and when plugged into the laptop, so the switch is working fine.

Any ideas?

Thanks,
Brian

---

