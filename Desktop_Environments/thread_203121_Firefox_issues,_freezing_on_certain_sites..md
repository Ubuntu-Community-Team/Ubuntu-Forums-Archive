---
title: "Firefox issues, freezing on certain sites."
date: 2006-06-24
forum: Desktop Environments
---

### Post by anony on 2006-06-24
Hello, I have a fresh install of dapper drake 6.06 on my machine: Pentium 4 3.4ghz HT. Currently, this is the only operating system installed. Everything works great except for some firefox issues. Whenever I visit sites such as Gmail or Espn the screen freezes and I need to hold the power button down and force restart the computer. However firefox works on sites that do not have high end java/flash. For example forums such as ubuntuforums.org Then I installed automatix and tride browsing around my gmail and it worked. Then i tested my luck and visited: espn.com only to see it freeze. After force restarting my computer (again) I tested gmail only to see it freeze from now one. Does any one have any ideas? I am stuck.
Thanks,
anony

---

### Post by lamego on 2006-06-24
If your system hangs it is related to hw or drivers (kernel/modules) even if it is triggered by firefox on specific sites.
Check the output from your "dmesg" command your system log files on /var/log .

---

### Post by anony on 2006-06-24
****@****:~$ dmesg
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4. 0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007ff30000 (usable)
[17179569.184000]  BIOS-e820: 000000007ff30000 - 000000007ff40000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[17179569.184000] 1151MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 524080
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294704 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x0 00fadd0
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x05000527 MSFT 0x00000097) @  0x7ff30000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x05000527 MSFT 0x00000097) @  0x7ff30200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x05000527 MSFT 0x00000097) @  0x7ff30390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x05000527 MSFT 0x00000097) @  0x7ff40040
[17179569.184000] ACPI: DSDT (v001  100XX 100XX001 0x00000001 INTL 0x02002026) @  0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7 f7c0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3392.058 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.924000] Dentry cache hash table entries: 131072 (order: 7, 524288 byte s)
[17179571.928000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.000000] Memory: 2067904k/2096320k available (1976k kernel code, 27132k  reserved, 606k data, 288k init, 1178816k highmem)
[17179572.000000] Checking if this processor honours the WP bit even in supervis or mode... Ok.
[17179572.084000] Calibrating delay using timer specific routine.. 6788.43 BogoM IPS (lpj=13576863)
[17179572.084000] Security Framework v1.0.0 initialized
[17179572.084000] SELinux:  Disabled at boot.
[17179572.084000] Mount-cache hash table entries: 512
[17179572.084000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.084000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 0 0000000 00004400 00000000 00000000
[17179572.084000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.084000] CPU: L2 cache: 512K
[17179572.084000] CPU: L3 cache: 2048K
[17179572.084000] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000008 0 00004400 00000000 00000000
[17179572.084000] mtrr: v2.0 (20020519)
[17179572.084000] CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 05
[17179572.084000] Enabling fast FPU save and restore... done.
[17179572.084000] Enabling unmasked SIMD FPU exception support... done.
[17179572.084000] Checking 'hlt' instruction... OK.
[17179572.100000] checking if image is initramfs... it is
[17179572.512000] Freeing initrd memory: 6614k freed
[17179572.520000] ACPI: Looking for DSDT ... not found!
[17179572.520000] ENABLING IO-APIC IRQs
[17179572.524000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.664000] NET: Registered protocol family 16
[17179572.664000] EISA bus registered
[17179572.664000] ACPI: bus type pci registered
[17179572.664000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[17179572.664000] PCI: Using configuration type 1
[17179572.664000] ACPI: Subsystem revision 20051216
[17179572.668000] ACPI: Interpreter enabled
[17179572.668000] ACPI: Using IOAPIC for interrupt routing
[17179572.668000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.668000] PCI: Probing PCI hardware (bus 00)
[17179572.672000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179572.672000] Boot video device is 0000:01:00.0
[17179572.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.684000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179572.684000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.684000] pnp: PnP ACPI init
[17179572.688000] pnp: PnP ACPI: found 12 devices
[17179572.688000] PnPBIOS: Disabled by ACPI PNP
[17179572.688000] PCI: Using ACPI for IRQ routing
[17179572.688000] PCI: If a device doesn't work, try "pci=routeirq".  If it help s, post a report
[17179572.692000] pnp: 00:06: ioport range 0x290-0x297 has been reserved
[17179572.692000] PCI: Bridge: 0000:00:01.0
[17179572.692000]   IO window: d000-dfff
[17179572.692000]   MEM window: dfe00000-dfefffff
[17179572.692000]   PREFETCH window: bfd00000-dfcfffff
[17179572.692000] audit: initializing netlink socket (disabled)
[17179572.692000] audit(1151169247.692:1): initialized
[17179572.692000] highmem bounce pool size: 64 pages
[17179572.692000] VFS: Disk quotas dquot_6.5.1
[17179572.692000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.692000] Initializing Cryptographic API
[17179572.692000] io scheduler noop registered
[17179572.692000] io scheduler anticipatory registered
[17179572.692000] io scheduler deadline registered
[17179572.692000] io scheduler cfq registered
[17179572.692000] isapnp: Scanning for PnP cards...
[17179573.048000] isapnp: No Plug & Play device found
[17179573.060000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179573.060000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179573.060000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.060000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.060000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar ing enabled
[17179573.060000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.060000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.060000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.060000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.064000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b locksize
[17179573.064000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.064000] ide: Assuming 33MHz system bus speed for PIO modes; override w ith idebus=xx
[17179573.064000] mice: PS/2 mouse device common for all mice
[17179573.064000] EISA: Probing bus 0 at eisa.0
[17179573.064000] EISA: Detected 0 cards.
[17179573.064000] NET: Registered protocol family 2
[17179573.100000] IP route cache hash table entries: 131072 (order: 7, 524288 by tes)
[17179573.100000] TCP established hash table entries: 524288 (order: 9, 2097152 bytes)
[17179573.100000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.100000] TCP: Hash tables configured (established 524288 bind 65536)
[17179573.100000] TCP reno registered
[17179573.104000] TCP bic registered
[17179573.104000] NET: Registered protocol family 1
[17179573.104000] NET: Registered protocol family 8
[17179573.104000] NET: Registered protocol family 20
[17179573.104000] Using IPI Shortcut mode
[17179573.104000] ACPI wakeup devices:
[17179573.104000] PS2K UAR1 UAR2 EUSB  USB USB2 USB3 AC97 MC97 PCI1 PCI2 PCI3 RT LL
[17179573.104000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.104000] Freeing unused kernel memory: 288k freed
[17179573.140000] vga16fb: initializing
[17179573.140000] vga16fb: mapped to 0xc00a0000
[17179573.172000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.236000] Console: switching to colour frame buffer device 80x25
[17179573.236000] fb0: VGA16 VGA frame buffer device
[17179574.336000] Capability LSM initialized
[17179574.364000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179574.760000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179574.760000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.760000] SIS5513: chipset revision 1
[17179574.760000] SIS5513: not 100% native mode: will probe irqs later
[17179574.760000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179574.760000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb :DMA
[17179574.760000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd :DMA
[17179574.760000] Probing IDE interface ide0...
[17179575.500000] hda: DVD DC DQ60, ATAPI CD/DVD-ROM drive
[17179575.836000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.836000] Probing IDE interface ide1...
[17179576.408000] hda: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 1419kB Cache, UDMA(66)
[17179576.408000] Uniform CD-ROM driver Revision: 3.20
[17179576.444000] SCSI subsystem initialized
[17179576.444000] ACPI: bus type scsi registered
[17179576.444000] libata version 1.20 loaded.
[17179576.444000] sata_sis 0000:00:05.0: version 0.5
[17179576.444000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179576.444000] sata_sis 0000:00:05.0: Detected SiS 180/181 chipset in SATA mo de
[17179576.444000] ata1: SATA max UDMA/133 cmd 0xEFF0 ctl 0xEFE6 bmdma 0xEF90 irq  177
[17179576.444000] ata2: SATA max UDMA/133 cmd 0xEFA8 ctl 0xEFE2 bmdma 0xEF98 irq  177
[17179576.656000] ata1: dev 0 cfg 00:045a 49:2f00 82:74eb 83:7fea 84:4023 85:74e 9 86:3c02 87:4023 88:003f 93:0000
[17179576.656000] ata1: dev 0 ATA-6, max UDMA/100, 488397168 sectors: LBA48
[17179576.656000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0xdffe9f20
[17179576.660000] ata1: dev 0 configured for UDMA/100
[17179576.660000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0xdffe9f20
[17179576.664000] scsi0 : sata_sis
[17179576.868000] ata2: no device found (phy stat 00000000)
[17179576.868000] scsi1 : sata_sis
[17179576.868000]   Vendor: ATA       Model: HDS722525VLSA80   Rev: V36O
[17179576.868000]   Type:   Direct-Access                      ANSI SCSI revisio n: 05
[17179576.872000] Driver 'sd' needs updating - please use bus_type methods
[17179576.872000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179576.872000] SCSI device sda: drive cache: write back
[17179576.876000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179576.876000] SCSI device sda: drive cache: write back
[17179576.876000]  sda: sda1 sda2 < sda5 >
[17179576.904000] sd 0:0:0:0: Attached scsi disk sda
[17179577.060000] usbcore: registered new driver usbfs
[17179577.060000] usbcore: registered new driver hub
[17179577.060000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.060000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179577.060000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179577.088000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus nu mber 1
[17179577.088000] ohci_hcd 0000:00:03.0: irq 185, io mem 0xdffec000
[17179577.144000] hub 1-0:1.0: USB hub found
[17179577.144000] hub 1-0:1.0: 3 ports detected
[17179577.248000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 193
[17179577.248000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179577.276000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus nu mber 2
[17179577.276000] ohci_hcd 0000:00:03.1: irq 193, io mem 0xdffed000
[17179577.332000] hub 2-0:1.0: USB hub found
[17179577.332000] hub 2-0:1.0: 3 ports detected
[17179577.436000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 201
[17179577.436000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[17179577.460000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus nu mber 3
[17179577.460000] ohci_hcd 0000:00:03.2: irq 201, io mem 0xdffee000
[17179577.516000] hub 3-0:1.0: USB hub found
[17179577.516000] hub 3-0:1.0: 2 ports detected
[17179577.620000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 209
[17179577.620000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179577.620000] PCI: cache line size of 128 is not supported by device 0000:00 :03.3
[17179577.620000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus nu mber 4
[17179577.620000] ehci_hcd 0000:00:03.3: irq 209, io mem 0xdffef000
[17179577.620000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 D ec 2004
[17179577.620000] hub 4-0:1.0: USB hub found
[17179577.620000] hub 4-0:1.0: 8 ports detected
[17179577.748000] Probing IDE interface ide1...
[17179578.328000] Attempting manual resume
[17179578.336000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179578.336000] EXT3-fs: write access will be enabled during recovery.
[17179578.496000] usb 2-1: new low speed USB device using ohci_hcd and address 3
[17179578.716000] usbcore: registered new driver hiddev
[17179578.728000] input: Logitech Optical USB Mouse as /class/input/input1
[17179578.728000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb -0000:00:03.1-1
[17179578.728000] usbcore: registered new driver usbhid
[17179578.728000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179578.788000] EXT3-fs: recovery complete.
[17179578.788000] kjournald starting.  Commit interval 5 seconds
[17179578.788000] EXT3-fs: mounted filesystem with ordered data mode.
[17179585.568000] ts: Compaq touchscreen protocol output
[17179585.604000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179585.972000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.976000] agpgart: Detected SiS 661 chipset
[17179585.980000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179585.996000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.224000] 8139too Fast Ethernet driver 0.9.27
[17179586.224000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179586.224000] eth0: RealTek RTL8139 at 0xf88c6c00, 00:13:d4:41:05:dd, IRQ 21 7
[17179586.224000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179586.228000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179586.348000] Real Time Clock Driver v1.12
[17179586.576000] input: PC Speaker as /class/input/input2
[17179586.916000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179586.940000] parport: PnPBIOS parport detected.
[17179586.940000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRIST ATE,COMPAT,EPP,ECP,DMA]
[17179587.052000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 225
[17179587.372000] intel8x0_measure_ac97_clock: measured 54850 usecs
[17179587.372000] intel8x0: clocking to 48000
[17179587.656000] lp0: using parport0 (interrupt-driven).
[17179587.696000] Adding 6080560k swap on /dev/sda5.  Priority:-1 extents:1 acro ss:6080560k
[17179587.812000] EXT3 FS on sda1, internal journal
[17179587.924000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179587.924000] md: bitmap version 4.39
[17179588.008000] NET: Registered protocol family 17
[17179588.200000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@ redhat.com
[17179588.636000] cdrom: open failed.
[17179589.400000] NET: Registered protocol family 10
[17179589.400000] lo: Disabled Privacy Extensions
[17179589.400000] IPv6 over IPv4 tunneling driver
[17179594.352000] ACPI: Power Button (FF) [PWRF]
[17179594.352000] ACPI: Power Button (CM) [PWRB]
[17179594.420000] ibm_acpi: ec object not found
[17179594.448000] pcc_acpi: loading...
[17179597.196000] [drm] Initialized drm 1.0.1 20051102
[17179597.236000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179597.240000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179597.796000] ppdev: user-space parallel port driver
[17179597.968000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179597.968000] apm: overridden by ACPI.
[17179598.272000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179598.272000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179598.272000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179598.580000] [drm] Setting GART location based on new memory map
[17179598.580000] [drm] Loading R300 Microcode
[17179598.580000] [drm] writeback test succeeded in 1 usecs
[17179599.436000] Bluetooth: Core ver 2.8
[17179599.436000] NET: Registered protocol family 31
[17179599.436000] Bluetooth: HCI device and connection manager initialized
[17179599.436000] Bluetooth: HCI socket layer initialized
[17179599.480000] Bluetooth: L2CAP ver 2.8
[17179599.480000] Bluetooth: L2CAP socket layer initialized
[17179599.484000] Bluetooth: RFCOMM socket layer initialized
[17179599.484000] Bluetooth: RFCOMM TTY layer initialized
[17179599.484000] Bluetooth: RFCOMM ver 1.7
[17179600.124000] eth0: no IPv6 routers present
[17179791.024000] APIC error on CPU0: 00(40)
[17181248.208000] APIC error on CPU0: 40(40)
[17181279.184000] APIC error on CPU0: 40(40)
[17181338.004000] APIC error on CPU0: 40(40)
[17181353.648000] APIC error on CPU0: 40(40)
[17181398.632000] APIC error on CPU0: 40(40)
[17181405.632000] APIC error on CPU0: 40(40)
[17181408.296000] APIC error on CPU0: 40(40)
[17181416.056000] APIC error on CPU0: 40(40)
[17181439.260000] APIC error on CPU0: 40(40)
[17181545.048000] APIC error on CPU0: 40(40)
[17181568.252000] APIC error on CPU0: 40(40)
[17181670.496000] APIC error on CPU0: 40(40)
[17181702.684000] APIC error on CPU0: 40(40)
[17181707.908000] APIC error on CPU0: 40(40)
[17181720.944000] APIC error on CPU0: 40(40)
[17181723.772000] APIC error on CPU0: 40(40)
[17181725.648000] APIC error on CPU0: 40(40)
[17181739.364000] APIC error on CPU0: 40(40)
[17181789.800000] APIC error on CPU0: 40(40)
[17181812.004000] APIC error on CPU0: 40(40)
[17181838.224000] APIC error on CPU0: 40(40)
[17181841.036000] APIC error on CPU0: 40(40)
[17181860.480000] APIC error on CPU0: 40(40)
[17181863.000000] APIC error on CPU0: 40(40)
[17181863.868000] APIC error on CPU0: 40(40)
[17181867.824000] APIC error on CPU0: 40(40)
[17181886.180000] APIC error on CPU0: 40(40)
[17181886.900000] APIC error on CPU0: 40(40)
[17181907.756000] APIC error on CPU0: 40(40)
[17181910.664000] APIC error on CPU0: 40(40)
[17181927.792000] APIC error on CPU0: 40(40)
[17181928.628000] APIC error on CPU0: 40(40)
[17181941.132000] APIC error on CPU0: 40(40)
[17181959.392000] APIC error on CPU0: 40(40)
[17181959.752000] APIC error on CPU0: 40(40)
[17181989.516000] APIC error on CPU0: 40(40)
[17181997.124000] APIC error on CPU0: 40(40)
[17182004.456000] APIC error on CPU0: 40(40)
[17182004.604000] APIC error on CPU0: 40(40)
[17182030.272000] APIC error on CPU0: 40(40)
[17182046.336000] APIC error on CPU0: 40(40)
[17182052.040000] APIC error on CPU0: 40(40)
[17182062.236000] APIC error on CPU0: 40(40)
[17182064.276000] APIC error on CPU0: 40(40)
[17182077.084000] APIC error on CPU0: 40(40)
[17182082.240000] APIC error on CPU0: 40(40)
[17182086.108000] APIC error on CPU0: 40(40)
[17182097.184000] APIC error on CPU0: 40(40)
[17182097.664000] APIC error on CPU0: 40(40)
[17182128.360000] APIC error on CPU0: 40(40)
[17182142.008000] APIC error on CPU0: 40(40)
[17182163.920000] APIC error on CPU0: 40(40)
[17182169.224000] APIC error on CPU0: 40(40)
[17182172.104000] APIC error on CPU0: 40(40)
[17182186.736000] APIC error on CPU0: 40(40)
[17182189.908000] APIC error on CPU0: 40(40)
[17182197.732000] APIC error on CPU0: 40(40)
[17182215.540000] APIC error on CPU0: 40(40)
[17182222.816000] APIC error on CPU0: 40(40)
[17182232.680000] APIC error on CPU0: 40(40)
[17182250.460000] APIC error on CPU0: 40(40)
[17182252.928000] APIC error on CPU0: 40(40)
[17182279.132000] APIC error on CPU0: 40(40)
[17182324.220000] APIC error on CPU0: 40(40)
[17182327.220000] APIC error on CPU0: 40(40)
[17182335.724000] APIC error on CPU0: 40(40)
[17182339.684000] APIC error on CPU0: 40(40)
[17182409.804000] APIC error on CPU0: 40(40)
[17184332.420000] APIC error on CPU0: 40(40)
[17184348.440000] APIC error on CPU0: 40(40)
[17184367.328000] APIC error on CPU0: 40(40)
[17184379.056000] APIC error on CPU0: 40(40)
[17184391.372000] APIC error on CPU0: 40(40)
[17184396.544000] APIC error on CPU0: 40(40)
[17184434.236000] APIC error on CPU0: 40(40)
****@****:~$
Those are my results.

---

### Post by anony on 2006-06-24
For dmesg /var/log

***@***:~$ dmesg /var/log
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007ff30000 (usable)
[17179569.184000]  BIOS-e820: 000000007ff30000 - 000000007ff40000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007ff40000 - 000000007fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[17179569.184000] 1151MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 524080
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294704 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fadd0
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x05000527 MSFT 0x00000097) @ 0x7ff30000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x05000527 MSFT 0x00000097) @ 0x7ff30200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x05000527 MSFT 0x00000097) @ 0x7ff30390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x05000527 MSFT 0x00000097) @ 0x7ff40040
[17179569.184000] ACPI: DSDT (v001  100XX 100XX001 0x00000001 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:7f7c0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3392.058 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.924000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.928000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.000000] Memory: 2067904k/2096320k available (1976k kernel code, 27132k reserved, 606k data, 288k init, 1178816k highmem)
[17179572.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.084000] Calibrating delay using timer specific routine.. 6788.43 BogoMIPS (lpj=13576863)
[17179572.084000] Security Framework v1.0.0 initialized
[17179572.084000] SELinux:  Disabled at boot.
[17179572.084000] Mount-cache hash table entries: 512
[17179572.084000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.084000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.084000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.084000] CPU: L2 cache: 512K
[17179572.084000] CPU: L3 cache: 2048K
[17179572.084000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.084000] mtrr: v2.0 (20020519)
[17179572.084000] CPU: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 05
[17179572.084000] Enabling fast FPU save and restore... done.
[17179572.084000] Enabling unmasked SIMD FPU exception support... done.
[17179572.084000] Checking 'hlt' instruction... OK.
[17179572.100000] checking if image is initramfs... it is
[17179572.512000] Freeing initrd memory: 6614k freed
[17179572.520000] ACPI: Looking for DSDT ... not found!
[17179572.520000] ENABLING IO-APIC IRQs
[17179572.524000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.664000] NET: Registered protocol family 16
[17179572.664000] EISA bus registered
[17179572.664000] ACPI: bus type pci registered
[17179572.664000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[17179572.664000] PCI: Using configuration type 1
[17179572.664000] ACPI: Subsystem revision 20051216
[17179572.668000] ACPI: Interpreter enabled
[17179572.668000] ACPI: Using IOAPIC for interrupt routing
[17179572.668000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.668000] PCI: Probing PCI hardware (bus 00)
[17179572.672000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179572.672000] Boot video device is 0000:01:00.0
[17179572.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.684000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179572.684000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179572.684000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.684000] pnp: PnP ACPI init
[17179572.688000] pnp: PnP ACPI: found 12 devices
[17179572.688000] PnPBIOS: Disabled by ACPI PNP
[17179572.688000] PCI: Using ACPI for IRQ routing
[17179572.688000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.692000] pnp: 00:06: ioport range 0x290-0x297 has been reserved
[17179572.692000] PCI: Bridge: 0000:00:01.0
[17179572.692000]   IO window: d000-dfff
[17179572.692000]   MEM window: dfe00000-dfefffff
[17179572.692000]   PREFETCH window: bfd00000-dfcfffff
[17179572.692000] audit: initializing netlink socket (disabled)
[17179572.692000] audit(1151169247.692:1): initialized
[17179572.692000] highmem bounce pool size: 64 pages
[17179572.692000] VFS: Disk quotas dquot_6.5.1
[17179572.692000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.692000] Initializing Cryptographic API
[17179572.692000] io scheduler noop registered
[17179572.692000] io scheduler anticipatory registered
[17179572.692000] io scheduler deadline registered
[17179572.692000] io scheduler cfq registered
[17179572.692000] isapnp: Scanning for PnP cards...
[17179573.048000] isapnp: No Plug & Play device found
[17179573.060000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179573.060000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179573.060000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.060000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.060000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.060000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.060000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.060000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.060000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.064000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.064000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.064000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.064000] mice: PS/2 mouse device common for all mice
[17179573.064000] EISA: Probing bus 0 at eisa.0
[17179573.064000] EISA: Detected 0 cards.
[17179573.064000] NET: Registered protocol family 2
[17179573.100000] IP route cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.100000] TCP established hash table entries: 524288 (order: 9, 2097152 bytes)
[17179573.100000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.100000] TCP: Hash tables configured (established 524288 bind 65536)
[17179573.100000] TCP reno registered
[17179573.104000] TCP bic registered
[17179573.104000] NET: Registered protocol family 1
[17179573.104000] NET: Registered protocol family 8
[17179573.104000] NET: Registered protocol family 20
[17179573.104000] Using IPI Shortcut mode
[17179573.104000] ACPI wakeup devices:
[17179573.104000] PS2K UAR1 UAR2 EUSB  USB USB2 USB3 AC97 MC97 PCI1 PCI2 PCI3 RTLL
[17179573.104000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.104000] Freeing unused kernel memory: 288k freed
[17179573.140000] vga16fb: initializing
[17179573.140000] vga16fb: mapped to 0xc00a0000
[17179573.172000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.236000] Console: switching to colour frame buffer device 80x25
[17179573.236000] fb0: VGA16 VGA frame buffer device
[17179574.336000] Capability LSM initialized
[17179574.364000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179574.760000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179574.760000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.760000] SIS5513: chipset revision 1
[17179574.760000] SIS5513: not 100% native mode: will probe irqs later
[17179574.760000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179574.760000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179574.760000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[17179574.760000] Probing IDE interface ide0...
[17179575.500000] hda: DVD DC DQ60, ATAPI CD/DVD-ROM drive
[17179575.836000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.836000] Probing IDE interface ide1...
[17179576.408000] hda: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 1419kB Cache, UDMA(66)
[17179576.408000] Uniform CD-ROM driver Revision: 3.20
[17179576.444000] SCSI subsystem initialized
[17179576.444000] ACPI: bus type scsi registered
[17179576.444000] libata version 1.20 loaded.
[17179576.444000] sata_sis 0000:00:05.0: version 0.5
[17179576.444000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179576.444000] sata_sis 0000:00:05.0: Detected SiS 180/181 chipset in SATA mode
[17179576.444000] ata1: SATA max UDMA/133 cmd 0xEFF0 ctl 0xEFE6 bmdma 0xEF90 irq 177
[17179576.444000] ata2: SATA max UDMA/133 cmd 0xEFA8 ctl 0xEFE2 bmdma 0xEF98 irq 177
[17179576.656000] ata1: dev 0 cfg 00:045a 49:2f00 82:74eb 83:7fea 84:4023 85:74e9 86:3c02 87:4023 88:003f 93:0000
[17179576.656000] ata1: dev 0 ATA-6, max UDMA/100, 488397168 sectors: LBA48
[17179576.656000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0xdffe9f20
[17179576.660000] ata1: dev 0 configured for UDMA/100
[17179576.660000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0xdffe9f20
[17179576.664000] scsi0 : sata_sis
[17179576.868000] ata2: no device found (phy stat 00000000)
[17179576.868000] scsi1 : sata_sis
[17179576.868000]   Vendor: ATA       Model: HDS722525VLSA80   Rev: V36O
[17179576.868000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179576.872000] Driver 'sd' needs updating - please use bus_type methods
[17179576.872000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179576.872000] SCSI device sda: drive cache: write back
[17179576.876000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179576.876000] SCSI device sda: drive cache: write back
[17179576.876000]  sda: sda1 sda2 < sda5 >
[17179576.904000] sd 0:0:0:0: Attached scsi disk sda
[17179577.060000] usbcore: registered new driver usbfs
[17179577.060000] usbcore: registered new driver hub
[17179577.060000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.060000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179577.060000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179577.088000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179577.088000] ohci_hcd 0000:00:03.0: irq 185, io mem 0xdffec000
[17179577.144000] hub 1-0:1.0: USB hub found
[17179577.144000] hub 1-0:1.0: 3 ports detected
[17179577.248000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 193
[17179577.248000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179577.276000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179577.276000] ohci_hcd 0000:00:03.1: irq 193, io mem 0xdffed000
[17179577.332000] hub 2-0:1.0: USB hub found
[17179577.332000] hub 2-0:1.0: 3 ports detected
[17179577.436000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 201
[17179577.436000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[17179577.460000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179577.460000] ohci_hcd 0000:00:03.2: irq 201, io mem 0xdffee000
[17179577.516000] hub 3-0:1.0: USB hub found
[17179577.516000] hub 3-0:1.0: 2 ports detected
[17179577.620000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 209
[17179577.620000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179577.620000] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[17179577.620000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[17179577.620000] ehci_hcd 0000:00:03.3: irq 209, io mem 0xdffef000
[17179577.620000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.620000] hub 4-0:1.0: USB hub found
[17179577.620000] hub 4-0:1.0: 8 ports detected
[17179577.748000] Probing IDE interface ide1...
[17179578.328000] Attempting manual resume
[17179578.336000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179578.336000] EXT3-fs: write access will be enabled during recovery.
[17179578.496000] usb 2-1: new low speed USB device using ohci_hcd and address 3
[17179578.716000] usbcore: registered new driver hiddev
[17179578.728000] input: Logitech Optical USB Mouse as /class/input/input1
[17179578.728000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:03.1-1
[17179578.728000] usbcore: registered new driver usbhid
[17179578.728000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179578.788000] EXT3-fs: recovery complete.
[17179578.788000] kjournald starting.  Commit interval 5 seconds
[17179578.788000] EXT3-fs: mounted filesystem with ordered data mode.
[17179585.568000] ts: Compaq touchscreen protocol output
[17179585.604000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179585.972000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.976000] agpgart: Detected SiS 661 chipset
[17179585.980000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179585.996000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.224000] 8139too Fast Ethernet driver 0.9.27
[17179586.224000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179586.224000] eth0: RealTek RTL8139 at 0xf88c6c00, 00:13:d4:41:05:dd, IRQ 217
[17179586.224000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179586.228000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179586.348000] Real Time Clock Driver v1.12
[17179586.576000] input: PC Speaker as /class/input/input2
[17179586.916000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179586.940000] parport: PnPBIOS parport detected.
[17179586.940000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179587.052000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 225
[17179587.372000] intel8x0_measure_ac97_clock: measured 54850 usecs
[17179587.372000] intel8x0: clocking to 48000
[17179587.656000] lp0: using parport0 (interrupt-driven).
[17179587.696000] Adding 6080560k swap on /dev/sda5.  Priority:-1 extents:1 across:6080560k
[17179587.812000] EXT3 FS on sda1, internal journal
[17179587.924000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179587.924000] md: bitmap version 4.39
[17179588.008000] NET: Registered protocol family 17
[17179588.200000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179588.636000] cdrom: open failed.
[17179589.400000] NET: Registered protocol family 10
[17179589.400000] lo: Disabled Privacy Extensions
[17179589.400000] IPv6 over IPv4 tunneling driver
[17179594.352000] ACPI: Power Button (FF) [PWRF]
[17179594.352000] ACPI: Power Button (CM) [PWRB]
[17179594.420000] ibm_acpi: ec object not found
[17179594.448000] pcc_acpi: loading...
[17179597.196000] [drm] Initialized drm 1.0.1 20051102
[17179597.236000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179597.240000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179597.796000] ppdev: user-space parallel port driver
[17179597.968000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179597.968000] apm: overridden by ACPI.
[17179598.272000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179598.272000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179598.272000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179598.580000] [drm] Setting GART location based on new memory map
[17179598.580000] [drm] Loading R300 Microcode
[17179598.580000] [drm] writeback test succeeded in 1 usecs
[17179599.436000] Bluetooth: Core ver 2.8
[17179599.436000] NET: Registered protocol family 31
[17179599.436000] Bluetooth: HCI device and connection manager initialized
[17179599.436000] Bluetooth: HCI socket layer initialized
[17179599.480000] Bluetooth: L2CAP ver 2.8
[17179599.480000] Bluetooth: L2CAP socket layer initialized
[17179599.484000] Bluetooth: RFCOMM socket layer initialized
[17179599.484000] Bluetooth: RFCOMM TTY layer initialized
[17179599.484000] Bluetooth: RFCOMM ver 1.7
[17179600.124000] eth0: no IPv6 routers present
[17179791.024000] APIC error on CPU0: 00(40)
[17181248.208000] APIC error on CPU0: 40(40)
[17181279.184000] APIC error on CPU0: 40(40)
[17181338.004000] APIC error on CPU0: 40(40)
[17181353.648000] APIC error on CPU0: 40(40)
[17181398.632000] APIC error on CPU0: 40(40)
[17181405.632000] APIC error on CPU0: 40(40)
[17181408.296000] APIC error on CPU0: 40(40)
[17181416.056000] APIC error on CPU0: 40(40)
[17181439.260000] APIC error on CPU0: 40(40)
[17181545.048000] APIC error on CPU0: 40(40)
[17181568.252000] APIC error on CPU0: 40(40)
[17181670.496000] APIC error on CPU0: 40(40)
[17181702.684000] APIC error on CPU0: 40(40)
[17181707.908000] APIC error on CPU0: 40(40)
[17181720.944000] APIC error on CPU0: 40(40)
[17181723.772000] APIC error on CPU0: 40(40)
[17181725.648000] APIC error on CPU0: 40(40)
[17181739.364000] APIC error on CPU0: 40(40)
[17181789.800000] APIC error on CPU0: 40(40)
[17181812.004000] APIC error on CPU0: 40(40)
[17181838.224000] APIC error on CPU0: 40(40)
[17181841.036000] APIC error on CPU0: 40(40)
[17181860.480000] APIC error on CPU0: 40(40)
[17181863.000000] APIC error on CPU0: 40(40)
[17181863.868000] APIC error on CPU0: 40(40)
[17181867.824000] APIC error on CPU0: 40(40)
[17181886.180000] APIC error on CPU0: 40(40)
[17181886.900000] APIC error on CPU0: 40(40)
[17181907.756000] APIC error on CPU0: 40(40)
[17181910.664000] APIC error on CPU0: 40(40)
[17181927.792000] APIC error on CPU0: 40(40)
[17181928.628000] APIC error on CPU0: 40(40)
[17181941.132000] APIC error on CPU0: 40(40)
[17181959.392000] APIC error on CPU0: 40(40)
[17181959.752000] APIC error on CPU0: 40(40)
[17181989.516000] APIC error on CPU0: 40(40)
[17181997.124000] APIC error on CPU0: 40(40)
[17182004.456000] APIC error on CPU0: 40(40)
[17182004.604000] APIC error on CPU0: 40(40)
[17182030.272000] APIC error on CPU0: 40(40)
[17182046.336000] APIC error on CPU0: 40(40)
[17182052.040000] APIC error on CPU0: 40(40)
[17182062.236000] APIC error on CPU0: 40(40)
[17182064.276000] APIC error on CPU0: 40(40)
[17182077.084000] APIC error on CPU0: 40(40)
[17182082.240000] APIC error on CPU0: 40(40)
[17182086.108000] APIC error on CPU0: 40(40)
[17182097.184000] APIC error on CPU0: 40(40)
[17182097.664000] APIC error on CPU0: 40(40)
[17182128.360000] APIC error on CPU0: 40(40)
[17182142.008000] APIC error on CPU0: 40(40)
[17182163.920000] APIC error on CPU0: 40(40)
[17182169.224000] APIC error on CPU0: 40(40)
[17182172.104000] APIC error on CPU0: 40(40)
[17182186.736000] APIC error on CPU0: 40(40)
[17182189.908000] APIC error on CPU0: 40(40)
[17182197.732000] APIC error on CPU0: 40(40)
[17182215.540000] APIC error on CPU0: 40(40)
[17182222.816000] APIC error on CPU0: 40(40)
[17182232.680000] APIC error on CPU0: 40(40)
[17182250.460000] APIC error on CPU0: 40(40)
[17182252.928000] APIC error on CPU0: 40(40)
[17182279.132000] APIC error on CPU0: 40(40)
[17182324.220000] APIC error on CPU0: 40(40)
[17182327.220000] APIC error on CPU0: 40(40)
[17182335.724000] APIC error on CPU0: 40(40)
[17182339.684000] APIC error on CPU0: 40(40)
[17182409.804000] APIC error on CPU0: 40(40)
[17184332.420000] APIC error on CPU0: 40(40)
[17184348.440000] APIC error on CPU0: 40(40)
[17184367.328000] APIC error on CPU0: 40(40)
[17184379.056000] APIC error on CPU0: 40(40)
[17184391.372000] APIC error on CPU0: 40(40)
[17184396.544000] APIC error on CPU0: 40(40)
[17184434.236000] APIC error on CPU0: 40(40)
***@***:~$

---

### Post by ifokkema on 2006-06-24
How do you have your Java and Flash installed? Have you tried a different browser? Else, maybe a different plugin may help.

---

### Post by anony on 2006-06-24
I used automatix

---

### Post by anony on 2006-06-24
That is supposed to install java + flash right?

---

### Post by ifokkema on 2006-06-25
[QUOTE=anony]That is supposed to install java + flash right?[/QUOTE]
Well, yes, but I don't know which packages exactly. There are at least two packages for Flash, and I believe also multiple options for Java.

What's the output of
```
dpkg -l \*flash\* |grep ii
dpkg -l \*j\* |grep -E 'java|j2' |grep ii
```
This shows you the flash and java packages installed.

---

### Post by ohgod on 2006-08-23
I have a friend with the same problem (lockup when browsing gmail with firefox).  He's a new linux convert and I'm trying to make his experience as smooth as possible ;)

Anyway, he had this problem on a fresh install of dapper.  The only thing he did after install was to get all the updates from apt.  So I don't think flash or java is at fault here.

Browsing gmail with opera works great...the problem only occurs with firefox.

Does anyone have any suggestions for debugging this?  I've glanced at the dmesg and syslog files, but couldn't find anything interesting (though I didn't really know what I was looking for).    Any help would be much appreciated.

---

### Post by orb9220 on 2006-08-23
In Firefox type about:plugins in address field then copy paste page here.

---

### Post by ohgod on 2006-08-23
I think I resolved the issue:  My friend has an ati video card, so I decided to install the drivers from ati.com.  Voila!  No more lockups when using gmail with firefox!

---

### Post by ifokkema on 2006-08-25
I personally have the 9200 SE ATi card. It used to freeze my Breezy install. I had to disable DRI and whatnot to keep it from freezing. Installing the ATi  drivers never worked for me (couldn't get GDM to start up properly), but now that I have Dapper I might give it a second try...

---

