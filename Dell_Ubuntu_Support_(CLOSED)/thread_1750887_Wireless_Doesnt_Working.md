---
title: "Wireless Doesnt Working"
date: 2011-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DaMonsterMonster on 2011-05-06
okay so i installed 10.04 from a disc onto my friends Dell Inspiron 1545 (a year old or so) and the wireless card doesnt work...
i went to the hardware druver utility thing and it popped up a few drivers to "activate" and it pulled up an error....
any ides?
thanks.

---

### Post by Elaztic on 2011-05-06
You have to be more precise and include more information if you want help and not guesses.

For starters you could document the error and supply that.
Then tell what you have tried, how, where and with what result.
What documentation and wikies have you consulted to resolve the error?

Then in the command line (terminal) you could post the response to these commands:

lsusb
lspci
dmesg

---

### Post by kooba on 2011-05-06
Doesn't working? ...or  Doesn't work? 


Works on my 4 year old Inspiron.
I deactivated the broadcom drivers, installed the b43-cutter ones and works great now.

---

### Post by DaMonsterMonster on 2011-05-06
> **Elaztic said:**
> You have to be more precise and include more information if you want help and not guesses.

For starters you could document the error and supply that.
Then tell what you have tried, how, where and with what result.
What documentation and wikies have you consulted to resolve the error?

Then in the command line (terminal) you could post the response to these commands:

lsusb
lspci
dmesg
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


[ 6061.868724] ACPI: Waking up from system sleep state S3
[ 6061.881894] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 6061.881903] i915 0000:00:02.0: restoring config space at offset 0x8 (was 0x1, writing 0xefe9)
[ 6061.881908] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 6061.881912] i915 0000:00:02.0: restoring config space at offset 0x4 (was 0x4, writing 0xf6c00004)
[ 6061.881917] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900000, writing 0x900407)
[ 6061.881948] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x4, writing 0xf6b00004)
[ 6061.881953] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 6061.881971] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 6061.881986] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x8 (was 0x1, writing 0x6f61)
[ 6061.882001] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6061.882024] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x207)
[ 6061.882039] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f81)
[ 6061.882054] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6061.882077] uhci_hcd 0000:00:1a.2: restoring config space at offset 0xf (was 0x300, writing 0x305)
[ 6061.882092] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x8 (was 0x1, writing 0x6fa1)
[ 6061.882107] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6061.882159] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 6061.882198] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[ 6061.882219] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xf6afc004)
[ 6061.882225] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6061.882232] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 6061.882268] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[ 6061.882282] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xc031c021)
[ 6061.882287] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xc010c000)
[ 6061.882293] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x2020)
[ 6061.882299] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
[ 6061.882308] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6061.882315] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6061.882367] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[ 6061.882381] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xc051c041)
[ 6061.882387] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf690f690)
[ 6061.882392] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x3030)
[ 6061.882398] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xc0c00)
[ 6061.882407] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6061.882414] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6061.882467] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x20300)
[ 6061.882481] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0xc071c061)
[ 6061.882486] pcieport 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0xf680f680)
[ 6061.882492] pcieport 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0xd0d0)
[ 6061.882498] pcieport 0000:00:1c.2: restoring config space at offset 0x6 (was 0x0, writing 0x90900)
[ 6061.882507] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6061.882514] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6061.882567] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[ 6061.882580] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
[ 6061.882586] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xf670f660)
[ 6061.882591] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0xc0c0)
[ 6061.882597] pcieport 0000:00:1c.4: restoring config space at offset 0x6 (was 0x0, writing 0xe0d00)
[ 6061.882606] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6061.882613] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6061.882681] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 6061.882704] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x207)
[ 6061.882719] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f21)
[ 6061.882734] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6061.882756] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x305)
[ 6061.882771] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0x6f41)
[ 6061.882786] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6061.882839] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 6061.882880] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
[ 6061.882942] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[ 6061.882978] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x300, writing 0x30a)
[ 6061.883004] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 6061.883045] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 6061.883066] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x4, writing 0xf6afbf04)
[ 6061.883075] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800103)
[ 6061.883344] pci 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 6061.883406] pci 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf69fc004)
[ 6061.883419] pci 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6061.883436] pci 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 6061.883543] sky2 0000:09:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 6061.883570] sky2 0000:09:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xde01)
[ 6061.883580] sky2 0000:09:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf68fc004)
[ 6061.883587] sky2 0000:09:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6061.883597] sky2 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6061.884051] PM: early resume of devices complete after 2.312 msecs
[ 6061.987839] i915 0000:00:02.0: setting latency timer to 64
[ 6062.176205] PM: resume of drv:i915 dev:0000:00:02.0 complete after 188.373 msecs
[ 6062.176220] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6062.176228] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 6062.176255] usb usb3: root hub lost power or was reset
[ 6062.176278] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 6062.176285] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 6062.176310] usb usb4: root hub lost power or was reset
[ 6062.176332] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 6062.176339] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 6062.176365] usb usb5: root hub lost power or was reset
[ 6062.176387] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 6062.176394] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 6062.176422] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 6062.176429] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 6062.290667] PM: resume of drv:HDA Intel dev:0000:00:1b.0 complete after 114.248 msecs
[ 6062.290692] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6062.290700] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 6062.290726] usb usb6: root hub lost power or was reset
[ 6062.290748] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 6062.290755] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 6062.290781] usb usb7: root hub lost power or was reset
[ 6062.290803] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 6062.290810] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 6062.290836] usb usb8: root hub lost power or was reset
[ 6062.290856] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6062.290863] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 6062.290878] pci 0000:00:1e.0: setting latency timer to 64
[ 6062.290896] ahci 0000:00:1f.2: setting latency timer to 64
[ 6062.420057] PM: resume of drv:usb dev:usb1 complete after 128.482 msecs
[ 6062.580057] usb 1-5: reset high speed USB device using ehci_hcd and address 2
[ 6062.616046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6062.624043] ata5: SATA link down (SStatus 0 SControl 300)
[ 6062.632047] ata6: SATA link down (SStatus 0 SControl 300)
[ 6062.691100] ata2.00: configured for UDMA/100
[ 6062.719882] PM: resume of drv:usb dev:1-5 complete after 250.921 msecs
[ 6062.719942] sd 1:0:0:0: [sda] Starting disk
[ 6063.280063] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 6063.281713] ata1.00: configured for UDMA/100
[ 6063.328115] PM: resume of drv:sd dev:1:0:0:0 complete after 608.173 msecs
[ 6063.331876] PM: resume of devices complete after 1445.252 msecs
[ 6063.332127] PM: resume devices took 1.448 seconds
[ 6063.332165] PM: Finishing wakeup.
[ 6063.332167] Restarting tasks ... done.
[ 6063.544641] sky2 eth0: enabling interface
[ 6063.544866] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6063.896343] VFS: busy inodes on changed media or resized disk sr0
[ 6064.558569] VFS: busy inodes on changed media or resized disk sr0
[ 6064.879077] VFS: busy inodes on changed media or resized disk sr0
[ 6064.993727] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input17
[ 6065.023412] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input18
[ 6065.028310] VFS: busy inodes on changed media or resized disk sr0
[ 6065.220603] VFS: busy inodes on changed media or resized disk sr0
[ 6065.348713] VFS: busy inodes on changed media or resized disk sr0
[ 6065.476863] VFS: busy inodes on changed media or resized disk sr0
[ 6085.444068] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 6085.474216] ISO 9660 Extensions: RRIP_1991A
[ 6138.569072] ata2: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
[ 6138.569077] ata2: irq_stat 0x00400000, PHY RDY changed
[ 6138.569081] ata2: SError: { PHYRdyChg CommWake }
[ 6138.569087] ata2: hard resetting link
[ 6138.734597] ata1.00: exception Emask 0x10 SAct 0x1 SErr 0x50000 action 0xe frozen
[ 6138.734602] ata1.00: irq_stat 0x00400000, PHY RDY changed
[ 6138.734606] ata1: SError: { PHYRdyChg CommWake }
[ 6138.734610] ata1.00: failed command: WRITE FPDMA QUEUED
[ 6138.734616] ata1.00: cmd 61/08:00:30:87:c4/00:00:0f:00:00/40 tag 0 ncq 4096 out
[ 6138.734617]          res 50/00:80:00:00:00/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[ 6138.734621] ata1.00: status: { DRDY }
[ 6138.734626] ata1: hard resetting link
[ 6139.292077] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6139.321651] ata2.00: configured for UDMA/100
[ 6139.323239] ata2: EH complete
[ 6139.456078] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 6139.457118] ata1.00: configured for UDMA/100
[ 6139.457128] ata1: EH complete
[ 6139.596054] sky2 eth0: disabling interface
[ 6139.868247] PM: Syncing filesystems ... done.
[ 6139.905079] PM: Preparing system for mem sleep
[ 6139.905083] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 6139.905901] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 6139.905978] PM: Entering mem sleep
[ 6139.905989] Suspending console(s) (use no_console_suspend to debug)
[ 6139.906558] sd 1:0:0:0: [sda] Synchronizing SCSI cache
[ 6139.981130] sd 1:0:0:0: [sda] Stopping disk
[ 6140.691587] PM: suspend of drv:sd dev:1:0:0:0 complete after 785.028 msecs
[ 6141.118474] PM: suspend of drv:psmouse dev:serio2 complete after 414.365 msecs
[ 6141.224057] PM: suspend of drv:atkbd dev:serio0 complete after 105.575 msecs
[ 6141.324073] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 6141.324083] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 6141.324093] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 6141.324103] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 6141.428360] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 6141.444059] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.935 msecs
[ 6141.444068] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 6141.444077] uhci_hcd 0000:00:1a.2: PCI INT C disabled
[ 6141.444087] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 6141.444097] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 6141.484381] PM: suspend of devices complete after 1578.038 msecs
[ 6141.484385] PM: suspend devices took 1.580 seconds
[ 6141.516277] PM: late suspend of devices complete after 31.887 msecs
[ 6141.523569] ACPI: Preparing to enter system sleep state S3
[ 6141.544013] Disabling non-boot CPUs ...
[ 6141.544032] CPU0 attaching NULL sched-domain.
[ 6141.544036] CPU1 attaching NULL sched-domain.
[ 6141.608015] CPU0 attaching NULL sched-domain.
[ 6141.712026] CPU 1 is now offline
[ 6141.712028] SMP alternatives: switching to UP code
[ 6141.718817] Extended CMOS year: 2000
[ 6141.718817] Back to C!
[ 6141.718817] CPU0: Thermal monitoring enabled (TM1)
[ 6141.718817] Extended CMOS year: 2000
[ 6141.718817] Enabling non-boot CPUs ...
[ 6141.718817] SMP alternatives: switching to SMP code
[ 6141.725215] Booting processor 1 APIC 0x1 ip 0x6000
[ 6141.718369] Initializing CPU#1
[ 6141.718369] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 6141.718369] CPU: L2 cache: 1024K
[ 6141.718369] CPU: Physical Processor ID: 0
[ 6141.718369] CPU: Processor Core ID: 1
[ 6141.718369] CPU1: Thermal monitoring enabled (TM1)
[ 6141.816047] CPU1: Intel Celeron(R) Dual-Core CPU       T3000  @ 1.80GHz stepping 0a
[ 6141.816107] CPU0 attaching NULL sched-domain.
[ 6141.844017] CPU0 attaching sched-domain:
[ 6141.844020]  domain 0: span 0-1 level MC
[ 6141.844023]   groups: 0 1
[ 6141.844027] CPU1 attaching sched-domain:
[ 6141.844029]  domain 0: span 0-1 level MC
[ 6141.844031]   groups: 1 0
[ 6141.844315] CPU1 is up
[ 6141.844726] ACPI: Waking up from system sleep state S3
[ 6141.857878] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 6141.857887] i915 0000:00:02.0: restoring config space at offset 0x8 (was 0x1, writing 0xefe9)
[ 6141.857891] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 6141.857896] i915 0000:00:02.0: restoring config space at offset 0x4 (was 0x4, writing 0xf6c00004)
[ 6141.857901] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900000, writing 0x900407)
[ 6141.857931] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x4, writing 0xf6b00004)
[ 6141.857937] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 6141.857955] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 6141.857970] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x8 (was 0x1, writing 0x6f61)
[ 6141.857985] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6141.858008] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x207)
[ 6141.858023] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f81)
[ 6141.858038] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6141.858061] uhci_hcd 0000:00:1a.2: restoring config space at offset 0xf (was 0x300, writing 0x305)
[ 6141.858076] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x8 (was 0x1, writing 0x6fa1)
[ 6141.858091] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6141.858143] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 6141.858182] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[ 6141.858203] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xf6afc004)
[ 6141.858209] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6141.858217] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 6141.858253] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[ 6141.858267] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xc031c021)
[ 6141.858272] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xc010c000)
[ 6141.858278] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x20002020)
[ 6141.858284] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
[ 6141.858293] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6141.858300] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6141.858354] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[ 6141.858367] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xc051c041)
[ 6141.858373] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf690f690)
[ 6141.858379] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x20003030)
[ 6141.858384] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xc0c00)
[ 6141.858393] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6141.858401] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6141.858454] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x20300)
[ 6141.858467] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0xc071c061)
[ 6141.858473] pcieport 0000:00:1c.2: restoring config space at offset 0x8 (was 0x0, writing 0xf680f680)
[ 6141.858479] pcieport 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x2000d0d0)
[ 6141.858484] pcieport 0000:00:1c.2: restoring config space at offset 0x6 (was 0x0, writing 0x90900)
[ 6141.858493] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6141.858500] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6141.858553] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[ 6141.858567] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
[ 6141.858572] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xf670f660)
[ 6141.858578] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0x2000c0c0)
[ 6141.858584] pcieport 0000:00:1c.4: restoring config space at offset 0x6 (was 0x0, writing 0xe0d00)
[ 6141.858593] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 6141.858600] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6141.858668] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 6141.858691] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x207)
[ 6141.858706] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f21)
[ 6141.858721] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6141.858743] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x305)
[ 6141.858758] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0x6f41)
[ 6141.858773] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
[ 6141.858826] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 6141.858867] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
[ 6141.858930] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[ 6141.858966] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x300, writing 0x30a)
[ 6141.858992] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 6141.859033] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 6141.859054] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x4, writing 0xf6afbf04)
[ 6141.859063] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800103)
[ 6141.859331] pci 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 6141.859394] pci 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf69fc004)
[ 6141.859406] pci 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6141.859424] pci 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 6141.859530] sky2 0000:09:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 6141.859557] sky2 0000:09:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xde01)
[ 6141.859567] sky2 0000:09:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf68fc004)
[ 6141.859575] sky2 0000:09:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6141.859584] sky2 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 6141.860040] PM: early resume of devices complete after 2.319 msecs
[ 6141.964940] i915 0000:00:02.0: setting latency timer to 64
[ 6142.108205] PM: resume of drv:i915 dev:0000:00:02.0 complete after 143.274 msecs
[ 6142.108220] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6142.108228] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 6142.108255] usb usb3: root hub lost power or was reset
[ 6142.108278] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 6142.108285] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 6142.108311] usb usb4: root hub lost power or was reset
[ 6142.108332] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 6142.108339] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 6142.108366] usb usb5: root hub lost power or was reset
[ 6142.108387] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 6142.108394] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 6142.108422] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 6142.108429] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 6142.222667] PM: resume of drv:HDA Intel dev:0000:00:1b.0 complete after 114.248 msecs
[ 6142.222692] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6142.222700] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 6142.222726] usb usb6: root hub lost power or was reset
[ 6142.222748] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 6142.222755] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 6142.222781] usb usb7: root hub lost power or was reset
[ 6142.222803] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 6142.222810] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 6142.222835] usb usb8: root hub lost power or was reset
[ 6142.222856] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 6142.222863] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 6142.222878] pci 0000:00:1e.0: setting latency timer to 64
[ 6142.222895] ahci 0000:00:1f.2: setting latency timer to 64
[ 6142.352058] PM: resume of drv:usb dev:usb1 complete after 128.488 msecs
[ 6142.508057] usb 1-5: reset high speed USB device using ehci_hcd and address 2
[ 6142.548046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6142.556043] ata5: SATA link down (SStatus 0 SControl 300)
[ 6142.564044] ata6: SATA link down (SStatus 0 SControl 300)
[ 6142.604153] ata2.00: configured for UDMA/100
[ 6142.647756] PM: resume of drv:usb dev:1-5 complete after 248.099 msecs
[ 6142.647814] sd 1:0:0:0: [sda] Starting disk
[ 6143.212063] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 6143.213622] ata1.00: configured for UDMA/100
[ 6143.253236] PM: resume of drv:sd dev:1:0:0:0 complete after 605.422 msecs
[ 6143.256712] PM: resume of devices complete after 1394.097 msecs
[ 6143.256950] PM: resume devices took 1.396 seconds
[ 6143.256987] PM: Finishing wakeup.
[ 6143.256989] Restarting tasks ... done.
[ 6143.568264] sky2 eth0: enabling interface
[ 6143.568498] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6143.939496] VFS: busy inodes on changed media or resized disk sr0
[ 6144.308405] ata2: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x10
[ 6144.308411] ata2: irq_stat 0x40000001
[ 6144.308414] sr 2:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 6144.308427] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 6144.308429]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 6144.308432] ata2.00: status: { DRDY ERR }
[ 6144.581263] VFS: busy inodes on changed media or resized disk sr0
[ 6144.900588] VFS: busy inodes on changed media or resized disk sr0
[ 6144.943389] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input19
[ 6144.973611] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input20
[ 6145.050119] VFS: busy inodes on changed media or resized disk sr0
[ 6145.263703] VFS: busy inodes on changed media or resized disk sr0
[ 6145.285526] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 6145.285890] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6145.413254] VFS: busy inodes on changed media or resized disk sr0
[ 6155.288050] eth0: no IPv6 routers present
[ 6164.598864] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 6164.615934] ISO 9660 Extensions: RRIP_1991A
[ 6691.513865] sky2 eth0: Link is down.
[ 6804.609710] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 6807.987443] sky2 eth0: Link is down.
[ 6815.231365] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx

---

### Post by DaMonsterMonster on 2011-05-06
> **kooba said:**
> Doesn't working? ...or  Doesn't work? 


Works on my 4 year old Inspiron.
I deactivated the broadcom drivers, installed the b43-cutter ones and works great now.
i meant doesnt work or not working...i was tired lol

---

### Post by DaMonsterMonster on 2011-05-06
so when i go to the driver installer it pulls this to activate 
Broadcom STA Driver 
These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.
but it fails to activate or download it

---

### Post by DaMonsterMonster on 2011-05-08
i just had to do the initial update thanks for your support guys

---

