---
title: "Help my hd performance and kde suck"
date: 2006-08-12
forum: Desktop Environments
---

### Post by joefie on 2006-08-12
hello all,

I'm running ubuntu drapper, kubuntu actually. Freshly Installed, Let me give you some hw info.


Kde is slow! firefox takes ages to load, this wasn't the case with breezy.




> 

$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Celeron(R) CPU 2.13GHz
stepping        : 1
cpu MHz         : 2133.743
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid xtpr
bogomips        : 4273.95


--------------------------------------------------------(dmesg)


[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000bfb0000 (usable)
[17179569.184000]  BIOS-e820: 000000000bfb0000 - 000000000bfc0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000bfc0000 - 000000000bff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000bff0000 - 000000000c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 191MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 49072
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 44976 pages, LIFO batch:7
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fabf0
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x02000614 MSFT 0x00000097) @ 0x0bfb0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x02000614 MSFT 0x00000097) @ 0x0bfb0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x02000614 MSFT 0x00000097) @ 0x0bfb0390
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x02000614 MSFT 0x00000097) @ 0x0bfc0040
[17179569.184000] ACPI: DSDT (v001  P4V80 P4V80000 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f2e00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 2133.743 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.812000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.812000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179569.816000] Memory: 183256k/196288k available (2110k kernel code, 12488k reserved, 595k data, 332k init, 0k highmem)
[17179569.816000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.896000] Calibrating delay using timer specific routine.. 4273.95 BogoMIPS (lpj=8547906)
[17179569.896000] Security Framework v1.0.0 initialized
[17179569.896000] SELinux:  Disabled at boot.
[17179569.896000] Mount-cache hash table entries: 512
[17179569.896000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179569.896000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179569.896000] monitor/mwait feature present.
[17179569.896000] using mwait in idle threads.
[17179569.896000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179569.896000] CPU: L2 cache: 256K
[17179569.896000] CPU: Hyper-Threading is disabled
[17179569.896000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[17179569.896000] mtrr: v2.0 (20020519)
[17179569.896000] Enabling fast FPU save and restore... done.
[17179569.896000] Enabling unmasked SIMD FPU exception support... done.
[17179569.896000] Checking 'hlt' instruction... OK.
[17179569.912000] SMP alternatives: switching to UP code
[17179569.912000] checking if image is initramfs... it is
[17179570.612000] Freeing initrd memory: 6807k freed
[17179570.628000] ACPI: Looking for DSDT ... not found!
[17179570.628000] CPU0: Intel(R) Celeron(R) CPU 2.13GHz stepping 01
[17179570.628000] Total of 1 processors activated (4273.95 BogoMIPS).
[17179570.628000] ENABLING IO-APIC IRQs
[17179570.632000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.772000] Brought up 1 CPUs
[17179570.772000] NET: Registered protocol family 16
[17179570.772000] EISA bus registered
[17179570.772000] ACPI: bus type pci registered
[17179570.772000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[17179570.772000] PCI: Using configuration type 1
[17179570.772000] ACPI: Subsystem revision 20051216
[17179570.776000] ACPI: Interpreter enabled
[17179570.776000] ACPI: Using IOAPIC for interrupt routing
[17179570.780000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.780000] PCI: Probing PCI hardware (bus 00)
[17179570.784000] Boot video device is 0000:01:00.0
[17179570.784000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.804000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179570.816000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.816000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.816000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.816000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.816000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.816000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.816000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.820000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.820000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.820000] pnp: PnP ACPI init
[17179570.824000] pnp: PnP ACPI: found 13 devices
[17179570.824000] PnPBIOS: Disabled by ACPI PNP
[17179570.824000] PCI: Using ACPI for IRQ routing
[17179570.824000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.832000] PCI: Bridge: 0000:00:01.0
[17179570.832000]   IO window: disabled.
[17179570.832000]   MEM window: fca00000-feafffff
[17179570.832000]   PREFETCH window: eff00000-f7efffff
[17179570.832000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.832000] audit: initializing netlink socket (disabled)
[17179570.836000] audit(1155406540.832:1): initialized
[17179570.836000] VFS: Disk quotas dquot_6.5.1
[17179570.836000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.836000] Initializing Cryptographic API
[17179570.836000] io scheduler noop registered
[17179570.836000] io scheduler anticipatory registered
[17179570.836000] io scheduler deadline registered
[17179570.836000] io scheduler cfq registered
[17179570.836000] PCI: Bypassing VIA 8237 APIC De-Assert Message
[17179570.836000] isapnp: Scanning for PnP cards...
[17179571.188000] isapnp: No Plug & Play device found
[17179571.228000] Real Time Clock Driver v1.12
[17179571.228000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179571.228000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.228000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.228000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.228000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.228000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.232000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.236000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.236000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.236000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.236000] mice: PS/2 mouse device common for all mice
[17179571.236000] EISA: Probing bus 0 at eisa.0
[17179571.236000] EISA: Detected 0 cards.
[17179571.236000] NET: Registered protocol family 2
[17179571.260000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.272000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179571.272000] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[17179571.272000] TCP bind hash table entries: 8192 (order: 4, 98304 bytes)
[17179571.272000] TCP: Hash tables configured (established 8192 bind 8192)
[17179571.272000] TCP reno registered
[17179571.272000] TCP bic registered
[17179571.272000] NET: Registered protocol family 1
[17179571.272000] NET: Registered protocol family 8
[17179571.272000] NET: Registered protocol family 20
[17179571.272000] Using IPI No-Shortcut mode
[17179571.272000] ACPI wakeup devices: 
[17179571.272000] PCI0 PS2K PS2M UAR1 MC97 USB1 USB2 USB3 USB4 EHCI ILAN 
[17179571.272000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.272000] Freeing unused kernel memory: 332k freed
[17179571.344000] vga16fb: initializing
[17179571.344000] vga16fb: mapped to 0xc00a0000
[17179571.480000] Console: switching to colour frame buffer device 80x25
[17179571.480000] fb0: VGA16 VGA frame buffer device
[17179572.600000] Capability LSM initialized
[17179573.664000] SCSI subsystem initialized
[17179573.668000] ACPI: bus type scsi registered
[17179573.668000] libata version 1.20 loaded.
[17179573.672000] sata_via 0000:00:0f.0: version 1.1
[17179573.672000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 169
[17179573.672000] sata_via 0000:00:0f.0: routed to hard irq line 11
[17179573.672000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 169
[17179573.672000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 169
[17179574.848000] scsi0 : sata_via
[17179576.024000] scsi1 : sata_via
[17179576.056000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[17179576.056000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 169
[17179576.056000] PCI: VIA IRQ fixup for 0000:00:0f.1, from 255 to 9
[17179576.056000] VP_IDE: chipset revision 6
[17179576.056000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.056000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[17179576.056000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[17179576.056000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[17179576.056000] Probing IDE interface ide0...
[17179576.472000] hda: Maxtor 2F040L0, ATA DISK drive
[17179576.920000] hdb: HL-DT-STDVD-ROM GDR8163B, ATAPI CD/DVD-ROM drive
[17179576.980000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.004000] Probing IDE interface ide1...
[17179577.584000] hda: max request size: 1024KiB
[17179577.596000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(133)
[17179577.600000] hda: cache flushes supported
[17179577.600000]  hda: hda1 hda2 < hda5 >
[17179577.648000] hdb: ATAPI 32X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179577.648000] Uniform CD-ROM driver Revision: 3.20
[17179577.944000] usbcore: registered new driver usbfs
[17179577.944000] usbcore: registered new driver hub
[17179577.948000] USB Universal Host Controller Interface driver v2.3
[17179577.948000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 177
[17179577.948000] PCI: VIA IRQ fixup for 0000:00:10.0, from 10 to 1
[17179577.948000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179577.952000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179577.952000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000c000
[17179577.952000] hub 1-0:1.0: USB hub found
[17179577.952000] hub 1-0:1.0: 2 ports detected
[17179578.056000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 177
[17179578.056000] PCI: VIA IRQ fixup for 0000:00:10.1, from 10 to 1
[17179578.056000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.056000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.056000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000c400
[17179578.056000] hub 2-0:1.0: USB hub found
[17179578.056000] hub 2-0:1.0: 2 ports detected
[17179578.160000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 177
[17179578.160000] PCI: VIA IRQ fixup for 0000:00:10.2, from 11 to 1
[17179578.160000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.160000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179578.160000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000c800
[17179578.160000] hub 3-0:1.0: USB hub found
[17179578.160000] hub 3-0:1.0: 2 ports detected
[17179578.264000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 177
[17179578.264000] PCI: VIA IRQ fixup for 0000:00:10.3, from 11 to 1
[17179578.264000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179578.264000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179578.264000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000cc00
[17179578.264000] hub 4-0:1.0: USB hub found
[17179578.264000] hub 4-0:1.0: 2 ports detected
[17179578.372000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 177
[17179578.372000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179578.372000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179578.372000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xfebff800
[17179578.372000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.372000] hub 5-0:1.0: USB hub found
[17179578.372000] hub 5-0:1.0: 8 ports detected
[17179578.504000] Probing IDE interface ide1...
[17179579.104000] Attempting manual resume
[17179579.156000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.192000] kjournald starting.  Commit interval 5 seconds
[17179592.320000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.324000] agpgart: Detected VIA P4M800CE chipset
[17179592.328000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179592.996000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.296000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179593.296000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179593.300000] eth0: VIA Rhine II at 0x1d400, 00:13:8f:8e:6a:3c, IRQ 185.
[17179593.300000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179593.556000] FDC 0 is a post-1991 82077
[17179593.700000] logips2pp: Detected unknown logitech mouse model 0
[17179593.760000] parport: PnPBIOS parport detected.
[17179593.760000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179593.916000] input: PC Speaker as /class/input/input1
[17179594.064000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[17179594.124000] ts: Compaq touchscreen protocol output
[17179594.156000] irda_init()
[17179594.156000] NET: Registered protocol family 23
[17179594.308000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179594.512000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 193
[17179594.512000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179595.352000] NET: Registered protocol family 17
[17179595.596000] lp0: using parport0 (interrupt-driven).
[17179595.676000] Adding 562232k swap on /dev/hda5.  Priority:-1 extents:1 across:562232k
[17179595.816000] EXT3 FS on hda1, internal journal
[17179596.048000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179596.048000] md: bitmap version 4.39
[17179596.740000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179597.572000] cdrom: open failed.
[17179598.808000] NET: Registered protocol family 10
[17179598.808000] lo: Disabled Privacy Extensions
[17179598.808000] IPv6 over IPv4 tunneling driver
[17179607.560000] ppdev: user-space parallel port driver
[17179609.548000] eth0: no IPv6 routers present
[17179617.864000] [drm] Initialized drm 1.0.1 20051102
[17179617.884000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[17179617.884000] [drm] Initialized via 2.7.4 20051116 on minor 0
[17179617.952000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179617.952000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[17179617.952000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179617.952000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179629.260000] eth0: no IPv6 routers present
[17179732.324000] Bluetooth: Core ver 2.8
[17179732.324000] NET: Registered protocol family 31
[17179732.324000] Bluetooth: HCI device and connection manager initialized
[17179732.324000] Bluetooth: HCI socket layer initialized
[17180154.708000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17180154.708000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[17180154.708000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17180154.712000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17180164.752000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17180164.752000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[17180164.752000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17180164.752000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17180173.388000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17180173.388000] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[17180173.388000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17180173.392000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
--------------------------------------------------------------------(lsmod)

Module                  Size  Used by
bluetooth              54084  0 
via                    50496  1 
drm                    78484  2 via
ppdev                   9668  0 
ipv6                  286976  24 
dm_mod                 63256  1 
md_mod                 76052  0 
lp                     12356  0 
af_packet              24520  2 
snd_seq_dummy           3908  0 
snd_seq_oss            37216  0 
snd_seq_midi            9600  0 
snd_seq_midi_event      7520  2 snd_seq_oss,snd_seq_midi
snd_seq                58160  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            31128  1 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100224  1 snd_via82xx
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0 
snd_mixer_oss          20544  1 snd_pcm_oss
irtty_sir               9312  0 
sir_dev                21356  1 irtty_sir
snd_pcm                96708  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_seq,snd_pcm
snd_page_alloc         11304  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8640  1 snd_via82xx
irda                  217980  2 irtty_sir,sir_dev
tsdev                   8032  0 
snd_rawmidi            26848  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
crc_ccitt               2240  1 irda
snd                    60004  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10784  1 snd
pcspkr                  2244  0 
i2c_viapro              9108  0 
parport_pc             37988  1 
parport                39400  3 ppdev,lp,parport_pc
i2c_core               22848  1 i2c_viapro
psmouse                40004  0 
floppy                 64676  0 
via_rhine              25988  0 
mii                     6176  1 via_rhine
serio_raw               7748  0 
shpchp                 49504  0 
pci_hotplug            30788  1 shpchp
via_agp                10304  1 
agpgart                36784  2 drm,via_agp
evdev                  10176  1 
ext3                  148104  1 
jbd                    65876  1 ext3
ide_generic             1504  0 
ehci_hcd               36104  0 
uhci_hcd               35408  0 
usbcore               139076  3 ehci_hcd,uhci_hcd
ide_cd                 35780  0 
cdrom                  41408  1 ide_cd
ide_disk               19136  3 
via82cxxx               9796  0 [permanent]
generic                 5124  0 
sata_via               10340  0 
libata                 83440  1 sata_via
scsi_mod              145960  1 libata
thermal                13768  0 
processor              26888  1 thermal
fan                     4836  0 
capability              4968  0 
commoncap               7328  1 capability
vga16fb                13992  1 
vgastate               10208  1 vga16fb
fbcon                  43904  76 
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit
---------------------------------------------------------------------(hdparm output)

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

# hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   868 MB in  2.00 seconds = 433.97 MB/sec
 Timing buffered disk reads:   28 MB in  3.15 seconds =   8.88 MB/sec



# hdparm -i /dev/hda

/dev/hda:

 Model=Maxtor 2F040L0, FwRev=VAM51JJ0, SerialNo=F1F4125E
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=80293248
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode







---

### Post by joefie on 2006-08-12
help!

---

### Post by schou on 2006-08-16
Hi there,
Your HD seems to be running in UDMA2-mode which kind of explains at least part of your problem.

Does your controller support faster speeds? (have you tried enabling for instance UDMA6-support in BIOS?)
Also, you need to ensure that you are using a 80-pin cable between the HD and the MB - otherwise you cannot get faster speeds.

Moving your optical drive away from the controller used by the HD could possibly also be beneficial.

A lot to try - I know.. hope some of it helps.

Best regards
Jakob

P.s. The disc is only designed to run at 5400 RPM - right? (that may also explain some of it).

---

