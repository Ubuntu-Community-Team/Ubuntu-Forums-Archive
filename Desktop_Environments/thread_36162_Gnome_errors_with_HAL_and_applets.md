---
title: "Gnome errors with HAL and applets"
date: 2005-05-22
forum: Desktop Environments
---

### Post by agds on 2005-05-22
Sometimes but not always, Gnome takes several minutes to load and finally yields the following error messages:

Failed to initialize HAL.

The panel encountered a problem while loading "OAFIID:GNOME_ShowDesktopApplet".  Do you want to delete the applet from your configuration?

This time I only got those two, but on other occasions there have been additional error messages similar to the latter.  In the past I have simply clicked "Don't Delete" and reinstalled HAL and gnome-applets via Synaptic.  Everything worked fine for a while.  Then I started getting these errors again.  I'm growing weary of digging out the Ubuntu CD and reinstalling these packages almost every other time I reboot.  

*Update:*  After reinstalling gnome-applets I don't receive the HAL error.  However, I see some new applet errors.  They're all in the format, "The panel encountered a problem while loading *x*.  Do you want to delete the applet from your configuration?"  I'll just provide the *x* for each error.

"OAFIID:GNOME_WorkspaceSwitcherApplet"

"OAFIID:GNOME_Panel_TrashApplet"

"OAFIID:GNOME_WindowListApplet"

"OAFIID:GNOME_ShowDesktopApplet"

I know I'm not providing much info, but I have no idea what's causing the problem.  Your advice would be most appreciated.

---

### Post by agds on 2005-05-22
Prompted by suggestions in similar threads, I opened my log files.  I'm not sure how to interpret them, so I'll post what seem to be the relevant sections.

**/var/log/syslog:**

```
May 22 09:08:41 localhost kernel: usb 3-1: epson timed out on ep0in
May 22 09:08:44 localhost kernel: eth0: no IPv6 routers present
May 22 09:08:46 localhost kernel: usb 3-1: epson timed out on ep0in
May 22 09:08:50 localhost gconfd (josh-7377): starting (version 2.10.0), pid 7377 user 'josh'
May 22 09:08:50 localhost gconfd (josh-7377): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 22 09:08:50 localhost gconfd (josh-7377): Resolved address "xml:readwrite:/home/josh/.gconf" to a writable configuration source at position 1
May 22 09:08:50 localhost gconfd (josh-7377): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 22 09:08:51 localhost kernel: usb 3-1: epson timed out on ep0in
May 22 09:08:56 localhost kernel: usb 3-1: epson timed out on ep0in
May 22 09:08:58 localhost gconfd (josh-7377): Resolved address "xml:readwrite:/home/josh/.gconf" to a writable configuration source at position 0
May 22 09:09:01 localhost kernel: usb 3-1: hald timed out on ep0in
May 22 09:09:06 localhost kernel: usb 3-1: hald timed out on ep0in
May 22 09:09:11 localhost kernel: usb 3-1: canon timed out on ep0in
May 22 09:09:26 localhost last message repeated 3 times
May 22 09:09:31 localhost kernel: usb 3-1: hald timed out on ep0in
May 22 09:10:01 localhost last message repeated 6 times
May 22 09:10:16 localhost last message repeated 3 times
May 22 09:10:16 localhost hald[6996]: Timed out waiting for hotplug event 1298. Rebasing to 1298
May 22 09:10:22 localhost kernel: usb 3-1: hald timed out on ep0in
May 22 09:10:37 localhost last message repeated 3 times
May 22 09:10:37 localhost kernel: UDF-fs: No VRS found
May 22 09:10:37 localhost kernel: ISO 9660 Extensions: Microsoft Joliet Level 3
May 22 09:10:38 localhost kernel: ISO 9660 Extensions: RRIP_1991A
```

**/var/log/messages:**

```
May 22 09:08:37 localhost lpd[7021]: restarted
May 22 09:08:41 localhost kernel: usb 3-1: epson timed out on ep0in
May 22 09:08:46 localhost kernel: usb 3-1: epson timed out on ep0in
May 22 09:08:50 localhost gconfd (josh-7377): starting (version 2.10.0), pid 7377 user 'josh'
May 22 09:08:50 localhost gconfd (josh-7377): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 22 09:08:50 localhost gconfd (josh-7377): Resolved address "xml:readwrite:/home/josh/.gconf" to a writable configuration source at position 1
May 22 09:08:50 localhost gconfd (josh-7377): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 22 09:08:51 localhost kernel: usb 3-1: epson timed out on ep0in
May 22 09:08:56 localhost kernel: usb 3-1: epson timed out on ep0in
May 22 09:08:58 localhost gconfd (josh-7377): Resolved address "xml:readwrite:/home/josh/.gconf" to a writable configuration source at position 0
May 22 09:09:01 localhost kernel: usb 3-1: hald timed out on ep0in
May 22 09:09:06 localhost kernel: usb 3-1: hald timed out on ep0in
May 22 09:09:11 localhost kernel: usb 3-1: canon timed out on ep0in
May 22 09:09:26 localhost last message repeated 3 times
May 22 09:09:31 localhost kernel: usb 3-1: hald timed out on ep0in
May 22 09:10:01 localhost last message repeated 6 times
May 22 09:10:37 localhost last message repeated 7 times
May 22 09:10:37 localhost kernel: UDF-fs: No VRS found
```

**/var/log/dmesg:**

```
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
usb 5-8: new high speed USB device using ehci_hcd and address 3
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
hub 5-8:1.0: USB hub found
hub 5-8:1.0: 4 ports detected
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usb 3-1: USB disconnect, address 2
hw_random hardware driver 1.0.0 loaded
usb 3-1: new full speed USB device using uhci_hcd and address 3
SCSI subsystem initialized
libata version 1.10 loaded.
ata_piix version 1.03
ACPI: PCI interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0xFE00 ctl 0xFE12 bmdma 0xFEA0 irq 18
ata2: SATA max UDMA/133 cmd 0xFE20 ctl 0xFE32 bmdma 0xFEA8 irq 18
ata1: SATA port has no device.
scsi0 : ata_piix
ata2: SATA port has no device.
scsi1 : ata_piix
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49208 usecs
intel8x0: clocking to 48000
Intel(R) PRO/1000 Network Driver - version 5.5.4-k2
Copyright (c) 1999-2004 Intel Corporation.
ACPI: PCI interrupt 0000:01:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
NET: Registered protocol family 17
e1000: eth0: e1000_watchdog: NIC Link is Up 10 Mbps Full Duplex
usb 3-1: grep timed out on ep0in
usb 3-1: grep timed out on ep0in
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
```

I've noticed a long delay during startup while it does something with hotplug.  Could this be the problem?  I'm not sure what it has to do with the applets.  Maybe that's a separate issue.  If I haven't provided enough info or the correct info, please let me know.  Alternately, if I've provided too much info, tell me and I'll pare it down to the essentials.

---

### Post by badteddy on 2007-03-06
i just started receiving the same issue.. mine however was with the trash applet and the something mixer.. any help is appreciated. i just booted up today. only thing i did was changed themes..

---

### Post by badteddy on 2007-03-06
i found something in there.. however i still dont quite understand it. 

[http://debcentral.org/modules/newbb/viewtopic.php?topic_id=330](http://debcentral.org/modules/newbb/viewtopic.php?topic_id=330)

---

