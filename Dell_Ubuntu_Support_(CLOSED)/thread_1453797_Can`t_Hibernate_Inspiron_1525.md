---
title: "Can`t Hibernate Inspiron 1525"
date: 2010-04-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tantric on 2010-04-13
Hi there,
It seems that hibernate function stopped working after updating to **karmic**. The hibernate function only logs me off without turning off the laptop. 
**kernel 2.6.31-21-generic**
here is the** kern.log** just after a failed hibernate:

> Apr 13 23:49:14 Sirius kernel: [10400.040194] sky2 eth0: disabling interface
Apr 13 23:49:29 Sirius kernel: [10400.495967] PM: Marking nosave pages: 0000000000001000 - 0000000000006000
Apr 13 23:49:29 Sirius kernel: [10400.495971] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Apr 13 23:49:29 Sirius kernel: [10400.495976] PM: Basic memory bitmaps created
Apr 13 23:49:29 Sirius kernel: [10400.495977] PM: Syncing filesystems ... done.
Apr 13 23:49:29 Sirius kernel: [10400.498727] Freezing user space processes ... (elapsed 0.00 seconds) done.
Apr 13 23:49:29 Sirius kernel: [10400.499644] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Apr 13 23:49:29 Sirius kernel: [10400.499716] PM: Shrinking memory...  -\|/-\|/-\done (86929 pages freed)
Apr 13 23:49:29 Sirius kernel: [10411.780240] PM: Freed 347716 kbytes in 11.28 seconds (30.82 MB/s)
Apr 13 23:49:29 Sirius kernel: [10411.780244] Suspending console(s) (use no_console_suspend to debug)
Apr 13 23:49:29 Sirius kernel: [10411.780582] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Apr 13 23:49:29 Sirius kernel: [10411.782181] sdhci-pci 0000:02:09.1: PME# disabled
Apr 13 23:49:29 Sirius kernel: [10411.782189] sdhci-pci 0000:02:09.1: PCI INT B disabled
Apr 13 23:49:29 Sirius kernel: [10411.820473] wl 0000:0b:00.0: PCI INT A disabled
Apr 13 23:49:29 Sirius kernel: [10411.840367] sky2 0000:09:00.0: PME# disabled
Apr 13 23:49:29 Sirius kernel: [10411.900533] ata5: port disabled. ignoring.
Apr 13 23:49:29 Sirius kernel: [10411.900601] ata_piix 0000:00:1f.1: PCI INT A disabled
Apr 13 23:49:29 Sirius kernel: [10411.900636] HDA Intel 0000:00:1b.0: PCI INT A disabled
Apr 13 23:49:29 Sirius kernel: [10411.952539] ricoh-mmc: Suspending.
Apr 13 23:49:29 Sirius kernel: [10411.952551] ricoh-mmc: Controller is now re-enabled.
Apr 13 23:49:29 Sirius kernel: [10411.955492] ACPI: Preparing to enter system sleep state S4
Apr 13 23:49:29 Sirius kernel: [10411.957427] PM: Saving platform NVS memory
Apr 13 23:49:29 Sirius kernel: [10411.957526] Disabling non-boot CPUs ...
Apr 13 23:49:29 Sirius kernel: [10412.060015] CPU 1 is now offline
Apr 13 23:49:29 Sirius kernel: [10412.060018] SMP alternatives: switching to UP code
Apr 13 23:49:29 Sirius kernel: [10412.066504] CPU0 attaching NULL sched-domain.
Apr 13 23:49:29 Sirius kernel: [10412.066507] CPU1 attaching NULL sched-domain.
Apr 13 23:49:29 Sirius kernel: [10412.066516] CPU0 attaching NULL sched-domain.
Apr 13 23:49:29 Sirius kernel: [10412.066698] CPU1 is down
Apr 13 23:49:29 Sirius kernel: [10412.066745] Extended CMOS year: 2000
Apr 13 23:49:29 Sirius kernel: [10412.066845] PM: Creating hibernation image: 
Apr 13 23:49:29 Sirius kernel: [10412.070007] PM: Need to copy 146570 pages
Apr 13 23:49:29 Sirius kernel: [10412.070007] PM: Normal pages needed: 146570 + 1024 + 38, available pages: 375164
Apr 13 23:49:29 Sirius kernel: [10412.070007] PM: Hibernation image created (146570 pages copied)
Apr 13 23:49:29 Sirius kernel: [10412.070007] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 13 23:49:29 Sirius kernel: [10412.070007] CPU0: Thermal monitoring enabled (TM2)
Apr 13 23:49:29 Sirius kernel: [10412.070007] Extended CMOS year: 2000
Apr 13 23:49:29 Sirius kernel: [10412.070007] Enabling non-boot CPUs ...
Apr 13 23:49:29 Sirius kernel: [10412.070007] SMP alternatives: switching to SMP code
Apr 13 23:49:29 Sirius kernel: [10412.073245] Booting processor 1 APIC 0x1 ip 0x6000
Apr 13 23:49:29 Sirius kernel: [10412.066361] Initializing CPU#1
Apr 13 23:49:29 Sirius kernel: [10412.066361] Calibrating delay using timer specific routine.. 3990.06 BogoMIPS (lpj=19950316)
Apr 13 23:49:29 Sirius kernel: [10412.066361] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 13 23:49:29 Sirius kernel: [10412.066361] CPU: L2 cache: 2048K
Apr 13 23:49:29 Sirius kernel: [10412.066361] CPU 1/0x1 -> Node 0
Apr 13 23:49:29 Sirius kernel: [10412.066361] CPU: Physical Processor ID: 0
Apr 13 23:49:29 Sirius kernel: [10412.066361] CPU: Processor Core ID: 1
Apr 13 23:49:29 Sirius kernel: [10412.066361] mce: CPU supports 6 MCE banks
Apr 13 23:49:29 Sirius kernel: [10412.066361] CPU1: Thermal monitoring enabled (TM2)
Apr 13 23:49:29 Sirius kernel: [10412.066361] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Apr 13 23:49:29 Sirius kernel: [10412.231374] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
Apr 13 23:49:29 Sirius kernel: [10412.231433] CPU0 attaching NULL sched-domain.
Apr 13 23:49:29 Sirius kernel: [10412.232516] Switched to high resolution mode on CPU 1
Apr 13 23:49:29 Sirius kernel: [10412.270023] CPU0 attaching sched-domain:
Apr 13 23:49:29 Sirius kernel: [10412.270026]  domain 0: span 0-1 level MC
Apr 13 23:49:29 Sirius kernel: [10412.270028]   groups: 0 1
Apr 13 23:49:29 Sirius kernel: [10412.270032] CPU1 attaching sched-domain:
Apr 13 23:49:29 Sirius kernel: [10412.270034]  domain 0: span 0-1 level MC
Apr 13 23:49:29 Sirius kernel: [10412.270036]   groups: 1 0
Apr 13 23:49:29 Sirius kernel: [10412.272518] CPU1 is up
Apr 13 23:49:29 Sirius kernel: [10412.272521] ACPI: Waking up from system sleep state S4
Apr 13 23:49:29 Sirius kernel: [10412.282895] ricoh-mmc: Resuming.
Apr 13 23:49:29 Sirius kernel: [10412.282905] ricoh-mmc: Controller is now disabled.
Apr 13 23:49:29 Sirius kernel: [10412.316399] i915 0000:00:02.0: setting latency timer to 64
Apr 13 23:49:29 Sirius kernel: [10412.708601] [drm] LVDS-8: set mode 1280x800 19
Apr 13 23:49:29 Sirius kernel: [10413.170251] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x109)
Apr 13 23:49:29 Sirius kernel: [10413.170280] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Apr 13 23:49:29 Sirius kernel: [10413.170290] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
Apr 13 23:49:29 Sirius kernel: [10413.170320] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Apr 13 23:49:29 Sirius kernel: [10413.170330] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr 13 23:49:29 Sirius kernel: [10413.170370] pci 0000:00:1e.0: setting latency timer to 64
Apr 13 23:49:29 Sirius kernel: [10413.170402] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880001, writing 0x2880005)
Apr 13 23:49:29 Sirius kernel: [10413.170413] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 13 23:49:29 Sirius kernel: [10413.170418] ata_piix 0000:00:1f.1: setting latency timer to 64
Apr 13 23:49:29 Sirius kernel: [10413.170476] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
Apr 13 23:49:29 Sirius kernel: [10413.170514] ahci 0000:00:1f.2: setting latency timer to 64
Apr 13 23:49:29 Sirius kernel: [10413.170570] ata4.00: _GTF evaluation failed (AE 0x1001)
Apr 13 23:49:29 Sirius kernel: [10413.170729] ata5: port disabled. ignoring.
Apr 13 23:49:29 Sirius kernel: [10413.190326] sky2 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
Apr 13 23:49:29 Sirius kernel: [10413.190394] sky2 0000:09:00.0: PME# disabled
Apr 13 23:49:29 Sirius kernel: [10413.210405] wl 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
Apr 13 23:49:29 Sirius kernel: [10413.210480] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 13 23:49:29 Sirius kernel: [10413.210491] wl 0000:0b:00.0: setting latency timer to 64
Apr 13 23:49:29 Sirius kernel: [10413.240260] ohci1394 0000:02:09.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
Apr 13 23:49:29 Sirius kernel: [10413.240271] ohci1394 0000:02:09.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
Apr 13 23:49:29 Sirius kernel: [10413.302254] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 13 23:49:29 Sirius kernel: [10413.320258] sdhci-pci 0000:02:09.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
Apr 13 23:49:29 Sirius kernel: [10413.320268] sdhci-pci 0000:02:09.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
Apr 13 23:49:29 Sirius kernel: [10413.320287] sdhci-pci 0000:02:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Apr 13 23:49:29 Sirius kernel: [10413.400506] ata4.00: configured for UDMA/33
Apr 13 23:49:29 Sirius kernel: [10413.444929] sd 0:0:0:0: [sda] Starting disk
Apr 13 23:49:29 Sirius kernel: [10413.520231] ata3: SATA link down (SStatus 0 SControl 300)
Apr 13 23:49:29 Sirius kernel: [10413.542763] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 13 23:49:29 Sirius kernel: [10413.543965] ata1.00: configured for UDMA/100
Apr 13 23:49:29 Sirius kernel: [10413.697596] PM: writing image.
Apr 13 23:49:29 Sirius kernel: [10413.697598] PM: Cannot find swap device, try swapon -a.
Apr 13 23:49:29 Sirius kernel: [10413.737657] Restarting tasks ... done.
Apr 13 23:49:29 Sirius kernel: [10413.738087] PM: Basic memory bitmaps freed
Apr 13 23:49:29 Sirius kernel: [10414.805900] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input15
Apr 13 23:49:29 Sirius kernel: [10414.832240] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input16
Apr 13 23:49:37 Sirius kernel: [10422.387886] sky2 eth0: enabling interface
Apr 13 23:49:37 Sirius kernel: [10422.388462] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 13 23:49:47 Sirius kernel: [10432.490126] eth1: no IPv6 routers presentAny help is appreciated. Thanks !

---

### Post by Tantric on 2010-04-19
Bump !

---

### Post by Tantric on 2010-04-29
Anyone ?!:lolflag:

---

