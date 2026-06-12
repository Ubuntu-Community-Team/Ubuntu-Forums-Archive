---
title: "Firewire External Hard Disk"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Sionide on 2005-11-27
I'm using Ubuntu Breezy and haven't had any real problems till now.

I have a problem with a firewire external hard disk, it won't mount when I plug it in - or at all.

It seems from dmesg that my firewire controller isn't working properly.

```
sionide@sphinx:~$ dmesg | grep 1394
[4294691.232000] ieee1394: Initialized config rom entry `ip1394'
[4294703.268000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294703.319000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[e00fd800-e00fdfff]  Max Packet=[2048]
[4294704.575000] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[4294705.857000] ieee1394: Error parsing configrom for node 0-00:1023
[4294705.857000] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[00030d4925565e0f][4294961.116000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4294964.739000] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[4294966.000000] ieee1394: Error parsing configrom for node 0-00:1023
[4294966.000000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023

```

I've run out of USB ports, so I'm trying to move this disk onto firewire but having no luck as yet.

Can anyone help?

---

