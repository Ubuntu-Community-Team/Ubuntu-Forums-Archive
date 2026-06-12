---
title: "log full of PCI errors!"
date: 2006-06-13
forum: Desktop Environments
---

### Post by evil_elman on 2006-06-13
The following can be seen in my /var/log/kern.log:

```
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: Using ACPI for IRQ routing
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
Jun 13 03:13:22 localhost kernel: [4294670.133000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
Jun 13 03:13:22 localhost kernel: [4294670.134000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
Jun 13 03:13:22 localhost kernel: [4294670.134000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
```

Specs: Acer TravelMate 4601LCi
1.6Ghz PM
915PM Chipset
Mobility Radeon X600
Ubuntu 6.06

Everything works fine... Except that the laptop hardlocks and has to be manually switched off every now and then when being connected to the Internet. Happens especially when using torrents for some reason and also in Windows (dual-booting).

I haven't tried all the different bits and bobs in the laptop (for example the infrared port, vga, s-video, modem and so on) so I don't really know if any of them could be the culprit.

Also, BIOS settings for serial / parallel and infrared ports are set to 'let OS decide settings' so they're not locked in to any specific setting.

The reason for me noticing this at all is that the above 'can't allocate resource...' messages flashes by for a split second after GRUB is finished loading and before the Ubuntu logo appears on screen.

Any ideas?

[EDIT] Disabled the above mentioned parallel, serial and infrared port thingies in the BIOS but messages still appear.

---

