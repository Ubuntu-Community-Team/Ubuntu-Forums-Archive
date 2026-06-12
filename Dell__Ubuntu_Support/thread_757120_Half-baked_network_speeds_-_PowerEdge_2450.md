---
title: "Half-baked network speeds - PowerEdge 2450"
date: 2008-04-16
forum: Dell  Ubuntu Support
---

### Post by pot_roast on 2008-04-16
I have Ubuntu 6.06 LTS (Dapper Drake) on two identical Dell PowerEdge 2450 boxes. 

I am unable to get more than 22mbit/sec off of either machine. Earlier today, I installed a base install of CentOS 5.1 and was able to get nearly 75mbit down. (I'm testing this by using curl on various kernel sources, Linux ISOs, etc.. all of the upstream sites have WAY more than 100mbit.

Both boxes are plugged into a Cisco switch. Other boxes on the same switch are able to get 70-80mbit speeds. 

Is there something I can tweak to address this?

Here's a snippet from dmesg (CentOS install):

[42949408.290000] FDC 0 is a National Semiconductor PC87306
[42949408.310000] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[42949408.320000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[42949408.320000] e100: Copyright(c) 1999-2005 Intel Corporation
[42949408.320000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 16 (level, low) -> IRQ 193
[42949408.350000] e100: eth0: e100_probe: addr 0xf9100000, irq 193, MAC addr 00:B0:D0:49:56:96
[42949408.530000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949408.540000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949408.660000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[42949409.000000] lp0: using parport0 (interrupt-driven).
[42949409.200000] Adding 2931820k swap on /dev/sda5.  Priority:-1 extents:1 across:2931820k
[42949409.320000] EXT3 FS on sda1, internal journal
[42949409.630000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949409.630000] md: bitmap version 4.39

---

### Post by pot_roast on 2008-04-22
I upgraded from a fresh install of 6.06 LTS to 8.04 RC (direct upgrade, and it actually worked!) and the speeds are a LOT better. Easily 3x what I was getting before.

So, it looks like the answer might just be "upgrade" :|

---

