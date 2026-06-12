---
title: "Only one core after wakeup"
date: 2007-07-04
forum: Dell  Ubuntu Support
---

### Post by michou on 2007-07-04
Hello!
I'm running Kubuntu 7.04 on a Dell Inspiron 1501, with an AMD Turion X2 TL-56 @ 1.8GHz, 2GB RAM, ATi X1150. Everything works fine excepting that upon wakeup after hibernate or suspend I only get 1 core working. Just before the X comes up I get a glimpse of a message complaining about CPU Vendor Unknown, using generic init.
The full listing of kern.log is as follows:

```
Jul  4 12:34:54 chou-isle kernel: [ 1098.000000] APIC error on CPU0: 00(40)
Jul  4 12:50:19 chou-isle kernel: [ 2022.864000] APIC error on CPU1: 00(40)
Jul  4 13:26:48 chou-isle kernel: [ 4211.352000] APIC error on CPU1: 40(40)
Jul  4 13:52:08 chou-isle kernel: [ 5731.276000] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Jul  4 13:52:14 chou-isle kernel: [ 5737.212000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  4 13:52:15 chou-isle kernel: [ 5737.872000] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Jul  4 13:52:28 chou-isle kernel: [ 5750.884000] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Jul  4 13:52:41 chou-isle kernel: [ 5763.892000] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Jul  4 13:52:54 chou-isle kernel: [ 5776.900000] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Jul  4 13:52:57 chou-isle kernel: [ 5779.844000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul  4 13:53:14 chou-isle kernel: [ 5797.748000] eth1: no IPv6 routers present
Jul  4 14:10:19 chou-isle kernel: [ 6822.232000] APIC error on CPU0: 40(40)
Jul  4 14:12:58 chou-isle kernel: [ 6981.140000] APIC error on CPU0: 40(40)
Jul  4 14:36:01 chou-isle kernel: [ 8364.020000] ndiswrapper: device eth1 removed
Jul  4 14:36:01 chou-isle kernel: [ 8364.020000] ACPI: PCI interrupt for device 0000:05:00.0 disabled
Jul  4 14:36:01 chou-isle kernel: [ 8364.024000] usbcore: deregistering interface driver ndiswrapper
Jul  4 14:36:02 chou-isle kernel: [ 8364.644000] ACPI: PCI interrupt for device 0000:08:00.0 disabled
Jul  4 14:36:06 chou-isle kernel: [ 8368.920000] PM: Preparing system for mem sleep
Jul  4 14:36:06 chou-isle kernel: [ 8368.920000] Disabling non-boot CPUs ...
Jul  4 14:36:06 chou-isle kernel: [ 8368.952000] Cannot set affinity for irq 0
Jul  4 14:36:06 chou-isle kernel: [ 8368.952000] Breaking affinity for irq 19
Jul  4 14:36:06 chou-isle kernel: [ 8368.956000] CPU 1 is now offline
Jul  4 14:36:06 chou-isle kernel: [ 8368.956000] SMP alternatives: switching to UP code
Jul  4 16:28:34 chou-isle kernel: [ 8368.968000] CPU1 is down
Jul  4 16:28:34 chou-isle kernel: [ 8368.968000] Stopping tasks ... done.
Jul  4 16:28:34 chou-isle kernel: [ 8369.100000] Suspending console(s)
Jul  4 16:28:34 chou-isle kernel: [ 8369.100000] platform bluetooth: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8369.100000] usbhid 3-1:1.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8369.100000] usb 3-1: suspend, may wakeup
Jul  4 16:28:34 chou-isle kernel: [ 8369.120000]  usbdev6.1_ep81: PM: suspend 0->2, parent 6-0:1.0 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8369.120000] hub 6-0:1.0: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8369.120000] hub 6-0:1.0: PM: suspend 2->2, parent usb6 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8369.120000]  usbdev6.1_ep00: PM: suspend 0->2, parent usb6 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8369.120000] usb usb6: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8369.120000] sd 0:0:0:0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8369.120000] ata1: exception Emask 0x40 SAct 0x0 SErr 0x800 action 0x3
Jul  4 16:28:34 chou-isle kernel: [ 8369.660000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  4 16:28:34 chou-isle kernel: [ 8369.664000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jul  4 16:28:34 chou-isle kernel: [ 8369.668000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jul  4 16:28:34 chou-isle kernel: [ 8369.668000] ata1.00: configured for UDMA/133
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000]  usbdev5.1_ep81: PM: suspend 0->2, parent 5-0:1.0 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 5-0:1.0: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 5-0:1.0: PM: suspend 2->2, parent usb5 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000]  usbdev5.1_ep00: PM: suspend 0->2, parent usb5 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] usb usb5: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000]  usbdev4.1_ep81: PM: suspend 0->2, parent 4-0:1.0 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 4-0:1.0: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 4-0:1.0: PM: suspend 2->2, parent usb4 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000]  usbdev4.1_ep00: PM: suspend 0->2, parent usb4 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] usb usb4: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 3-0:1.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] usb usb3: suspend, may wakeup
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000]  usbdev2.1_ep81: PM: suspend 0->2, parent 2-0:1.0 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 2-0:1.0: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 2-0:1.0: PM: suspend 2->2, parent usb2 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000]  usbdev2.1_ep00: PM: suspend 0->2, parent usb2 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] usb usb2: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000]  usbdev1.1_ep81: PM: suspend 0->2, parent 1-0:1.0 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 1-0:1.0: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] hub 1-0:1.0: PM: suspend 2->2, parent usb1 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000]  usbdev1.1_ep00: PM: suspend 0->2, parent usb1 already 2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] usb usb1: PM: suspend 2-->2
Jul  4 16:28:34 chou-isle kernel: [ 8370.144000] ide-cdrom 0.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.148000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jul  4 16:28:34 chou-isle kernel: [ 8370.148000] vesafb vesafb.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.148000] platform eisa.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.148000] i8042 i8042: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.148000] sda: Write Protect is off
Jul  4 16:28:34 chou-isle kernel: [ 8370.148000] sda: Mode Sense: 00 3a 00 00
Jul  4 16:28:34 chou-isle kernel: [ 8370.148000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] serial8250 serial8250: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pci_express 0000:00:06.0:pcie02: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pci_express 0000:00:06.0:pcie00: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pci_express 0000:00:05.0:pcie00: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pcspkr pcspkr: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] system 00:09: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] system 00:08: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] i8042 aux 00:07: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] i8042 kbd 00:06: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pnp 00:05: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pnp 00:04: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pnp 00:03: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pnp 00:02: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] system 00:01: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.740000] pnp 00:00: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.744000] pci 0000:08:01.1: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.744000] sdhci 0000:08:01.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.744000] ACPI: PCI interrupt for device 0000:08:01.0 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.760000] pci 0000:08:00.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.760000] pci 0000:05:00.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.760000] fglrx_pci 0000:01:05.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.760000] [fglrx] firegl_gps_setpowerdown .
Jul  4 16:28:34 chou-isle kernel: [ 8370.780000] ACPI: PCI interrupt for device 0000:01:05.0 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.780000] k8temp 0000:00:18.3: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.780000] pci 0000:00:18.2: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.780000] pci 0000:00:18.1: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.780000] pci 0000:00:18.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.780000] pci 0000:00:14.4: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.780000] pci 0000:00:14.3: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.780000] HDA Intel 0000:00:14.2: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.788000] ACPI: PCI interrupt for device 0000:00:14.2 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.804000] ATIIXP_IDE 0000:00:14.1: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.804000] pci 0000:00:14.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.804000] ehci_hcd 0000:00:13.5: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.804000] ACPI: PCI interrupt for device 0000:00:13.5 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ohci_hcd 0000:00:13.4: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ACPI: PCI interrupt for device 0000:00:13.4 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ohci_hcd 0000:00:13.3: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ACPI: PCI interrupt for device 0000:00:13.3 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ohci_hcd 0000:00:13.2: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ACPI: PCI interrupt for device 0000:00:13.2 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ohci_hcd 0000:00:13.1: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ACPI: PCI interrupt for device 0000:00:13.1 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ohci_hcd 0000:00:13.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ACPI: PCI interrupt for device 0000:00:13.0 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ahci 0000:00:12.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ata1: ACPI get timing mode failed.
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ata2: ACPI get timing mode failed.
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ata3: ACPI get timing mode failed.
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ata4: ACPI get timing mode failed.
Jul  4 16:28:34 chou-isle kernel: [ 8370.820000] ACPI: PCI interrupt for device 0000:00:12.0 disabled
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pcieport-driver 0000:00:06.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pcieport-driver 0000:00:05.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:01.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:00.0: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] acpi acpi: suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] PM: Entering mem sleep
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] platform bluetooth: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] vesafb vesafb.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] platform eisa.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] i8042 i8042: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] serial8250 serial8250: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pcspkr pcspkr: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:08:01.1: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] sdhci 0000:08:01.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:08:00.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:05:00.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] k8temp 0000:00:18.3: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:18.2: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:18.1: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:18.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:14.4: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:14.3: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] HDA Intel 0000:00:14.2: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] ATIIXP_IDE 0000:00:14.1: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:14.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pcieport-driver 0000:00:06.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pcieport-driver 0000:00:05.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:01.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] pci 0000:00:00.0: LATE suspend
Jul  4 16:28:34 chou-isle kernel: [ 8370.836000] Back to C!
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:00.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:01.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pcieport-driver 0000:00:05.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pcieport-driver 0000:00:06.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ahci 0000:00:12.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ohci_hcd 0000:00:13.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ohci_hcd 0000:00:13.1: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ohci_hcd 0000:00:13.2: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ohci_hcd 0000:00:13.3: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ohci_hcd 0000:00:13.4: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ehci_hcd 0000:00:13.5: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:14.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ATIIXP_IDE 0000:00:14.1: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] HDA Intel 0000:00:14.2: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:14.3: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:14.4: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:18.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:18.1: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:18.2: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] k8temp 0000:00:18.3: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] fglrx_pci 0000:01:05.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:05:00.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:08:00.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] sdhci 0000:08:01.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:08:01.1: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pcspkr pcspkr: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] serial8250 serial8250: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] i8042 i8042: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] platform eisa.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] vesafb vesafb.0: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] platform bluetooth: EARLY resume
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Finishing wakeup.
Jul  4 16:28:34 chou-isle kernel: [15115.836000] acpi acpi: resuming
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:00.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:00.0 at offset 7 (was e0000004, writing 0)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:00.0 at offset 3 (was 0, writing 4000)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:00.0 at offset 1 (was 22200006, writing 32200006)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pci 0000:00:01.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:01.0 at offset 9 (was 10001, writing cff1c001)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pcieport-driver 0000:00:05.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:05.0 at offset f (was ff, writing 400ff)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:05.0 at offset 9 (was 10001, writing 1fff1)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:05.0 at offset 8 (was 0, writing fff0)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:05.0 at offset 7 (was 101, writing 1f1)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:05.0 at offset 6 (was 0, writing 40200)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:05.0 at offset 3 (was 10000, writing 10008)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:05.0 at offset 1 (was 100000, writing 100004)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PCI: Setting latency timer of device 0000:00:05.0 to 64
Jul  4 16:28:34 chou-isle kernel: [15115.836000] pcieport-driver 0000:00:06.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:06.0 at offset f (was ff, writing 400ff)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:06.0 at offset 9 (was 10001, writing 1fff1)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:06.0 at offset 8 (was 0, writing b020b020)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:06.0 at offset 7 (was 101, writing 200001f1)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:06.0 at offset 6 (was 0, writing 70500)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:06.0 at offset 3 (was 10000, writing 10008)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PM: Writing back config space on device 0000:00:06.0 at offset 1 (was 100000, writing 100007)
Jul  4 16:28:34 chou-isle kernel: [15115.836000] PCI: Setting latency timer of device 0000:00:06.0 to 64
Jul  4 16:28:34 chou-isle kernel: [15115.836000] ahci 0000:00:12.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15115.852000] PM: Writing back config space on device 0000:00:12.0 at offset 9 (was fec00400, writing b0004000)
Jul  4 16:28:34 chou-isle kernel: [15115.852000] PM: Writing back config space on device 0000:00:12.0 at offset 2 (was 1018f00, writing 1060100)
Jul  4 16:28:34 chou-isle kernel: [15115.852000] PM: Writing back config space on device 0000:00:12.0 at offset 1 (was 2300007, writing a300007)
Jul  4 16:28:34 chou-isle kernel: [15115.852000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 19
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ata1: ACPI set timing mode failed.
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ata2: ACPI set timing mode failed.
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ata3: ACPI set timing mode failed.
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ata4: ACPI set timing mode failed.
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ohci_hcd 0000:00:13.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ohci_hcd 0000:00:13.1: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ohci_hcd 0000:00:13.2: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ohci_hcd 0000:00:13.3: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ohci_hcd 0000:00:13.4: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Jul  4 16:28:34 chou-isle kernel: [15116.856000] ehci_hcd 0000:00:13.5: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.872000] PCI: Enabling device 0000:00:13.5 (0000 -> 0002)
Jul  4 16:28:34 chou-isle kernel: [15116.872000] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 20
Jul  4 16:28:34 chou-isle kernel: [15116.872000] PM: Writing back config space on device 0000:00:13.5 at offset 1 (was 2b00006, writing 2b00017)
Jul  4 16:28:34 chou-isle kernel: [15116.872000] pci 0000:00:14.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.872000] ATIIXP_IDE 0000:00:14.1: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.872000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jul  4 16:28:34 chou-isle kernel: [15116.872000] HDA Intel 0000:00:14.2: resuming
Jul  4 16:28:34 chou-isle kernel: [15116.888000] PM: Writing back config space on device 0000:00:14.2 at offset f (was 10a, writing a)
Jul  4 16:28:34 chou-isle kernel: [15116.888000] PM: Writing back config space on device 0000:00:14.2 at offset 1 (was 4100006, writing 4100002)
Jul  4 16:28:34 chou-isle kernel: [15116.888000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jul  4 16:28:34 chou-isle kernel: [15117.032000] pci 0000:00:14.3: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] pci 0000:00:14.4: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] pci 0000:00:18.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] pci 0000:00:18.1: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] pci 0000:00:18.2: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] k8temp 0000:00:18.3: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] fglrx_pci 0000:01:05.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
Jul  4 16:28:34 chou-isle kernel: [15117.032000] [fglrx] firegl_gps_setpowerup .
Jul  4 16:28:34 chou-isle kernel: [15117.032000] pci 0000:05:00.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] PM: Writing back config space on device 0000:05:00.0 at offset f (was 100, writing 10b)
Jul  4 16:28:34 chou-isle kernel: [15117.032000] PM: Writing back config space on device 0000:05:00.0 at offset 4 (was 0, writing b0200000)
Jul  4 16:28:34 chou-isle kernel: [15117.032000] PM: Writing back config space on device 0000:05:00.0 at offset 3 (was 0, writing 8)
Jul  4 16:28:34 chou-isle kernel: [15117.032000] PM: Writing back config space on device 0000:05:00.0 at offset 1 (was 100000, writing 100003)
Jul  4 16:28:34 chou-isle kernel: [15117.032000] pci 0000:08:00.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.032000] PM: Writing back config space on device 0000:08:00.0 at offset 1 (was 100006, writing 100002)
Jul  4 16:28:34 chou-isle kernel: [15117.032000] sdhci 0000:08:01.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.048000] PM: Writing back config space on device 0000:08:01.0 at offset f (was 209, writing 20b)
Jul  4 16:28:34 chou-isle kernel: [15117.048000] PM: Writing back config space on device 0000:08:01.0 at offset 4 (was b0302c00, writing b0302800)
Jul  4 16:28:34 chou-isle kernel: [15117.048000] PM: Writing back config space on device 0000:08:01.0 at offset 3 (was 800000, writing 804000)
Jul  4 16:28:34 chou-isle kernel: [15117.048000] ACPI: PCI Interrupt 0000:08:01.0[B] -> GSI 20 (level, low) -> IRQ 22
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pci 0000:08:01.1: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] PM: Writing back config space on device 0000:08:01.1 at offset f (was 200, writing 209)
Jul  4 16:28:34 chou-isle kernel: [15117.052000] PM: Writing back config space on device 0000:08:01.1 at offset 4 (was 0, writing b0302c00)
Jul  4 16:28:34 chou-isle kernel: [15117.052000] PM: Writing back config space on device 0000:08:01.1 at offset 1 (was 2100000, writing 2100006)
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pnp 00:00: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] system 00:01: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pnp 00:02: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pnp 00:03: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pnp 00:04: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pnp 00:05: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] i8042 kbd 00:06: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pnp: Device 00:06 does not support activation.
Jul  4 16:28:34 chou-isle kernel: [15117.052000] i8042 aux 00:07: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pnp: Device 00:07 does not support activation.
Jul  4 16:28:34 chou-isle kernel: [15117.052000] system 00:08: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] system 00:09: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pcspkr pcspkr: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pci_express 0000:00:05.0:pcie00: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pci_express 0000:00:06.0:pcie00: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] pci_express 0000:00:06.0:pcie02: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] serial8250 serial8250: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] i8042 i8042: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.052000] atkbd serio0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.100000] platform eisa.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.100000] psmouse serio1: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.172000] ata2: SATA link down (SStatus 0 SControl 300)
Jul  4 16:28:34 chou-isle kernel: [15117.172000] ata3: SATA link down (SStatus 0 SControl 300)
Jul  4 16:28:34 chou-isle kernel: [15117.172000] ata4: SATA link down (SStatus 0 SControl 300)
Jul  4 16:28:34 chou-isle kernel: [15117.660000] vesafb vesafb.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.660000] ide-cdrom 0.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.668000]  usbdev1.1_ep00: PM: resume from 0, parent usb1 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.668000]  usbdev1.1_ep81: PM: resume from 0, parent 1-0:1.0 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.668000]  usbdev2.1_ep00: PM: resume from 0, parent usb2 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.668000]  usbdev2.1_ep81: PM: resume from 0, parent 2-0:1.0 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.668000] usb usb3: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.748000] hub 3-0:1.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.748000]  usbdev4.1_ep00: PM: resume from 0, parent usb4 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.748000]  usbdev4.1_ep81: PM: resume from 0, parent 4-0:1.0 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.748000]  usbdev5.1_ep00: PM: resume from 0, parent usb5 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.748000]  usbdev5.1_ep81: PM: resume from 0, parent 5-0:1.0 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.748000] sd 0:0:0:0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.748000]  usbdev6.1_ep00: PM: resume from 0, parent usb6 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.748000]  usbdev6.1_ep81: PM: resume from 0, parent 6-0:1.0 still 2
Jul  4 16:28:34 chou-isle kernel: [15117.748000] usb 3-1: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.796000] usbhid 3-1:1.0: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.796000] platform bluetooth: resuming
Jul  4 16:28:34 chou-isle kernel: [15117.796000] Restarting tasks ... <6>ata1: waiting for device to spin up (8 secs)
Jul  4 16:28:34 chou-isle kernel: [15118.720000] done.
Jul  4 16:28:34 chou-isle kernel: [15118.720000] Enabling non-boot CPUs ...
Jul  4 16:28:34 chou-isle kernel: [15118.732000] SMP alternatives: switching to SMP code
Jul  4 16:28:34 chou-isle kernel: [15118.732000] Booting processor 1/1 eip 3000
Jul  4 16:28:34 chou-isle kernel: [15118.740000] Initializing CPU#1
Jul  4 16:28:34 chou-isle kernel: [15118.820000] Calibrating delay using timer specific routine.. 3591.26 BogoMIPS (lpj=7182529)
Jul  4 16:28:34 chou-isle kernel: [15118.820000] CPU: Vendor unknown, using generic init.
Jul  4 16:28:34 chou-isle kernel: [15118.820000] CPU: Your system may be unstable.
Jul  4 16:28:34 chou-isle kernel: [15118.820000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
Jul  4 16:28:34 chou-isle kernel: [15118.820000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
Jul  4 16:28:34 chou-isle kernel: [15118.820000] CPU1: AuthenticAMD AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
Jul  4 16:28:34 chou-isle kernel: [15118.824000] CPU1 is up
Jul  4 16:28:42 chou-isle kernel: [15126.644000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  4 16:28:42 chou-isle kernel: [15126.652000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jul  4 16:28:42 chou-isle kernel: [15127.192000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jul  4 16:28:42 chou-isle kernel: [15127.192000] ata1.00: configured for UDMA/133
Jul  4 16:28:42 chou-isle kernel: [15127.192000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jul  4 16:28:42 chou-isle kernel: [15127.192000] sda: Write Protect is off
Jul  4 16:28:42 chou-isle kernel: [15127.192000] sda: Mode Sense: 00 3a 00 00
Jul  4 16:28:42 chou-isle kernel: [15127.192000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  4 16:28:45 chou-isle kernel: [15129.788000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Jul  4 16:28:45 chou-isle kernel: [15129.820000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Jul  4 16:28:45 chou-isle kernel: [15129.820000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Jul  4 16:28:45 chou-isle kernel: [15129.820000] PCI: Setting latency timer of device 0000:05:00.0 to 64
Jul  4 16:28:45 chou-isle kernel: [15129.824000] ndiswrapper: using IRQ 18
Jul  4 16:28:46 chou-isle kernel: [15130.636000] wlan0: ethernet device 00:19:7d:48:71:ae using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
Jul  4 16:28:46 chou-isle kernel: [15130.636000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jul  4 16:28:46 chou-isle kernel: [15130.640000] usbcore: registered new interface driver ndiswrapper
Jul  4 16:28:46 chou-isle kernel: [15130.640000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
Jul  4 16:28:46 chou-isle kernel: [15130.688000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  4 16:28:46 chou-isle kernel: [15130.784000] b44.c:v1.01 (Jun 16, 2006)
Jul  4 16:28:46 chou-isle kernel: [15130.784000] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
Jul  4 16:28:46 chou-isle kernel: [15130.792000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:4d:77:20
Jul  4 16:28:46 chou-isle kernel: [15130.900000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  4 16:28:48 chou-isle kernel: [15131.516000] input: Power Button (FF) as /class/input/input10
Jul  4 16:28:48 chou-isle kernel: [15131.516000] ACPI: Power Button (FF) [PWRF]
Jul  4 16:28:48 chou-isle kernel: [15131.516000] input: Power Button (CM) as /class/input/input11
Jul  4 16:28:48 chou-isle kernel: [15131.516000] ACPI: Power Button (CM) [PWRB]
Jul  4 16:28:48 chou-isle kernel: [15131.516000] input: Sleep Button (CM) as /class/input/input12
Jul  4 16:28:48 chou-isle kernel: [15131.516000] ACPI: Sleep Button (CM) [SLPB]
Jul  4 16:28:48 chou-isle kernel: [15131.516000] input: Lid Switch as /class/input/input13
Jul  4 16:28:48 chou-isle kernel: [15131.516000] ACPI: Lid Switch [LID]
Jul  4 16:28:48 chou-isle kernel: [15131.992000] ACPI: Thermal Zone [THRM] (34 C)
Jul  4 16:28:48 chou-isle kernel: [15132.068000] ACPI: AC Adapter [ACAD] (on-line)
Jul  4 16:28:48 chou-isle kernel: [15132.088000] ACPI: Battery Slot [BAT1] (battery present)
Jul  4 16:28:51 chou-isle kernel: [15134.800000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul  4 16:29:01 chou-isle kernel: [15144.920000] eth1: no IPv6 routers present
Jul  4 16:29:55 chou-isle kernel: [15198.772000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  4 16:30:57 chou-isle kernel: [15260.992000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul  4 16:31:14 chou-isle kernel: [15276.384000] eth1: no IPv6 routers present
```

If I use the function keys to see the battery status and cpu frequencies, the second core is grayed out, and doesn't seem to be affected by power management policy changes
So any ideas on how to wake up all cores? :D. I must mention that this problem arises with or without ndiswrapper (that I currently use for full speed WiFi), and with no matter what video card driver.

Big thanks in advance,
miChou

---

### Post by hellmet on 2007-07-04
This might be a bug as well. There are quite some bugs related to waking up after hibernation. I had a problem with the kernel on wake-up too. Try searching for this in the existing bugs, or post a new one if not already existing.

---

