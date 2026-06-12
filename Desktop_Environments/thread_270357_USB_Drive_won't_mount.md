---
title: "USB Drive won't mount"
date: 2006-10-03
forum: Desktop Environments
---

### Post by anaoum on 2006-10-03
My usb thumb drive wont mount either automatically or manually.

I have found that there is no sda in /dev

---

### Post by orb9220 on 2006-10-03
usb devices mount in folder /media/
Is your usb device fat32?

---

### Post by anaoum on 2006-10-03
Yes it is fat32, but how will Ubuntu be able to mount it if /dev/sda does not exist?

---

### Post by anaconda on 2006-10-03
> **anaoum said:**
> Yes it is fat32, but how will Ubuntu be able to mount it if /dev/sda does not exist?

It can't. Unless it is sdb or sdc or sdd...
How do you know that sda doesn't exist?

I once had a USB-stick, which had very strange partition-table, but it worked in windows (not in linux) Got it working in linux by correcting the partition table..

---

### Post by anaoum on 2006-10-03
There is no /dev/sd*

---

### Post by anaoum on 2006-10-03
may i also add that no usb drive works; ive tried 4 and none of them work

---

### Post by anaoum on 2006-10-04
double post

---

### Post by Crooksey on 2006-10-04
Plug in in, then imeditaly type "dmesg" and see what it says, post reults back up here.

---

### Post by anaoum on 2006-10-04
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000f56f0
[4294667.296000] On node 0 totalpages: 131056
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126960 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f7170
[4294667.296000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3000
[4294667.296000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3040
[4294667.296000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff6b40
[4294667.296000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:2 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda5 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 2412.503 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.086000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.087000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.099000] Memory: 508596k/524224k available (1976k kernel code, 15024k reserved, 606k data, 288k init, 0k highmem)
[4294669.099000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.159000] Calibrating delay using timer specific routine.. 4827.06 BogoMIPS (lpj=2413532)
[4294669.159000] Security Framework v1.0.0 initialized
[4294669.159000] SELinux:  Disabled at boot.
[4294669.159000] Mount-cache hash table entries: 512
[4294669.159000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[4294669.159000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[4294669.159000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294669.159000] CPU: L2 cache: 512K
[4294669.159000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00000400 00000000 00000000
[4294669.159000] mtrr: v2.0 (20020519)
[4294669.159000] CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[4294669.159000] Enabling fast FPU save and restore... done.
[4294669.159000] Enabling unmasked SIMD FPU exception support... done.
[4294669.159000] Checking 'hlt' instruction... OK.
[4294669.163000] checking if image is initramfs... it is
[4294669.746000] Freeing initrd memory: 6837k freed
[4294669.762000] ACPI: Looking for DSDT ... not found!
[4294669.878000] ENABLING IO-APIC IRQs
[4294669.878000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294669.989000] NET: Registered protocol family 16
[4294669.989000] EISA bus registered
[4294669.989000] ACPI: bus type pci registered
[4294669.995000] PCI: PCI BIOS revision 2.10 entry at 0xfae00, last bus=1
[4294669.995000] PCI: Using configuration type 1
[4294669.995000] ACPI: Subsystem revision 20051216
[4294670.005000] ACPI: Interpreter enabled
[4294670.005000] ACPI: Using IOAPIC for interrupt routing
[4294670.006000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.006000] PCI: Probing PCI hardware (bus 00)
[4294670.006000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.008000] Uncovering SIS962 that hid as a SIS503 (compatible=1)
[4294670.008000] Enabling SiS 96x SMBus.
[4294670.009000] Boot video device is 0000:01:00.0
[4294670.009000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.030000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294670.031000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294670.031000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294670.031000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294670.031000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294670.032000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294670.032000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294670.032000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294670.035000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.035000] pnp: PnP ACPI init
[4294670.040000] pnp: PnP ACPI: found 14 devices
[4294670.040000] PnPBIOS: Disabled by ACPI PNP
[4294670.040000] PCI: Using ACPI for IRQ routing
[4294670.040000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.070000] PCI: Bridge: 0000:00:01.0
[4294670.070000]   IO window: disabled.
[4294670.070000]   MEM window: e4000000-e5ffffff
[4294670.070000]   PREFETCH window: d0000000-dfffffff
[4294670.070000] audit: initializing netlink socket (disabled)
[4294670.070000] audit(1159939710.069:1): initialized
[4294670.070000] VFS: Disk quotas dquot_6.5.1
[4294670.070000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.070000] Initializing Cryptographic API
[4294670.070000] io scheduler noop registered
[4294670.070000] io scheduler anticipatory registered
[4294670.070000] io scheduler deadline registered
[4294670.070000] io scheduler cfq registered
[4294670.070000] isapnp: Scanning for PnP cards...
[4294670.427000] isapnp: No Plug & Play device found
[4294670.442000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.443000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.443000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.443000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294670.443000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.443000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.445000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.445000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.446000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.446000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.446000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.446000] mice: PS/2 mouse device common for all mice
[4294670.446000] EISA: Probing bus 0 at eisa.0
[4294670.446000] Cannot allocate resource for EISA slot 1
[4294670.446000] EISA: Detected 0 cards.
[4294670.446000] NET: Registered protocol family 2
[4294670.456000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294670.456000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.456000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.456000] TCP: Hash tables configured (established 32768 bind 32768)
[4294670.456000] TCP reno registered
[4294670.456000] TCP bic registered
[4294670.456000] NET: Registered protocol family 1
[4294670.456000] NET: Registered protocol family 8
[4294670.456000] NET: Registered protocol family 20
[4294670.456000] Using IPI Shortcut mode
[4294670.456000] ACPI wakeup devices: 
[4294670.456000] PCI0 USB0 USB1 USB2 AMR0 UAR1 UAR2 
[4294670.456000] ACPI: (supports S0 S1 S4 S5)
[4294670.456000] Freeing unused kernel memory: 288k freed
[4294670.474000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294670.506000] vga16fb: initializing
[4294670.506000] vga16fb: mapped to 0xc00a0000
[4294670.630000] Console: switching to colour frame buffer device 80x25
[4294670.630000] fb0: VGA16 VGA frame buffer device
[4294671.736000] Capability LSM initialized
[4294672.317000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294672.317000] SIS5513: chipset revision 0
[4294672.317000] SIS5513: not 100% native mode: will probe irqs later
[4294672.317000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[4294672.317000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294672.317000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[4294672.317000] Probing IDE interface ide0...
[4294672.581000] hda: ST320413A, ATA DISK drive
[4294672.836000] hdb: ST380011A, ATA DISK drive
[4294672.887000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.895000] Probing IDE interface ide1...
[4294673.567000] hdc: SONY DVD-ROM DDU1612, ATAPI CD/DVD-ROM drive
[4294673.873000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.880000] hda: max request size: 128KiB
[4294673.889000] hda: 39102336 sectors (20020 MB) w/512KiB Cache, CHS=38792/16/63, UDMA(100)
[4294673.889000] hda: cache flushes not supported
[4294673.889000]  hda: hda1 hda2 < hda5 >
[4294673.936000] hdb: max request size: 1024KiB
[4294673.936000] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294673.936000] hdb: cache flushes supported
[4294673.936000]  hdb: hdb1 hdb2 < hdb5 >
[4294673.965000] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[4294673.965000] Uniform CD-ROM driver Revision: 3.20
[4294674.533000] Attempting manual resume
[4294674.548000] kjournald starting.  Commit interval 5 seconds
[4294674.548000] EXT3-fs: mounted filesystem with ordered data mode.
[4294689.394000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294689.399000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294689.425000] Linux agpgart interface v0.101 (c) Dave Jones
[4294689.430000] agpgart: Detected SiS 646 chipset
[4294689.434000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294689.987000] i2c-sis96x version 1.0.0
[4294689.988000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1400
[4294690.194000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 169
[4294690.205000] Real Time Clock Driver v1.12
[4294690.217000] input: PC Speaker as /class/input/input1
[4294690.267000] Linux video capture interface: v1.00
[4294690.331000] Floppy drive(s): fd0 is 1.44M
[4294690.346000] FDC 0 is a post-1991 82077
[4294690.368000] parport: PnPBIOS parport detected.
[4294690.368000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294690.389000] logips2pp: Detected unknown logitech mouse model 0
[4294690.397000] nvidia: module license 'NVIDIA' taints kernel.
[4294690.442000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[4294690.493000] 8139too Fast Ethernet driver 0.9.27
[4294690.507000] intel8x0_measure_ac97_clock: measured 50707 usecs
[4294690.507000] intel8x0: clocking to 48000
[4294690.507000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 177
[4294690.508000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[4294690.543000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 169
[4294690.543000] eth0: RealTek RTL8139 at 0xe095a000, 00:e0:4c:e9:1d:21, IRQ 169
[4294690.543000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294690.746000] bttv: driver version 0.9.16 loaded
[4294690.746000] bttv: Bt8xx card found (0).
[4294690.746000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 185
[4294690.746000] bttv0: Bt878 (rev 17) at 0000:00:0b.0, irq: 185, latency: 32, mmio: 0xe7016000
[4294690.746000] bttv0: using: Modular Technology MM201/MM202/MM205/MM210/MM215 PCTV, bt878 [card=23,insmod option]
[4294690.746000] bttv0: gpio config override: mask=0x3f, mux=0x21,0x20,0x23,0x23,0x28
[4294690.751000] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[4294690.751000] bttv0: Modtec: Unknown TunerString: 
[4294690.751000] bttv0: using tuner=18
[4294690.825000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294690.847000] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4294690.847000] tuner 1-0061: type set to 18 (Temic PAL_I (4066 FY5))
[4294690.879000] bttv0: registered device video0
[4294690.879000] bttv0: registered device vbi0
[4294690.879000] bttv0: registered device radio0
[4294691.017000] bt878: AUDIO driver version 0.0.0 loaded
[4294691.017000] bt878: Bt878 AUDIO function found (0).
[4294691.017000] ACPI: PCI Interrupt 0000:00:0b.1[A] -> GSI 19 (level, low) -> IRQ 185
[4294691.017000] bt878(0): Bt878 (rev 17) at 00:0b.1, irq: 185, latency: 32, memory: 0xe7017000
[4294691.350000] ts: Compaq touchscreen protocol output
[4294691.493000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294691.755000] lp0: using parport0 (interrupt-driven).
[4294691.822000] Adding 1510068k swap on /dev/hdb5.  Priority:-1 extents:1 across:1510068k
[4294691.950000] EXT3 FS on hda5, internal journal
[4294692.107000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294692.107000] md: bitmap version 4.39
[4294692.701000] NET: Registered protocol family 17
[4294693.345000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294694.326000] cdrom: open failed.
[4294696.274000] NET: Registered protocol family 10
[4294696.274000] lo: Disabled Privacy Extensions
[4294696.274000] IPv6 over IPv4 tunneling driver
[4294699.983000] kjournald starting.  Commit interval 5 seconds
[4294699.983000] EXT3 FS on hdb1, internal journal
[4294699.983000] EXT3-fs: mounted filesystem with ordered data mode.
[4294706.277000] ACPI: Power Button (FF) [PWRF]
[4294706.277000] ACPI: Power Button (CM) [PWRB]
[4294706.277000] ACPI: Sleep Button (CM) [FUTS]
[4294706.378000] ibm_acpi: ec object not found
[4294706.403000] pcc_acpi: loading...
[4294706.778000] eth0: no IPv6 routers present
[4294712.893000] ppdev: user-space parallel port driver
[4294713.223000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294713.224000] apm: overridden by ACPI.
[4294716.478000] Bluetooth: Core ver 2.8
[4294716.478000] NET: Registered protocol family 31
[4294716.478000] Bluetooth: HCI device and connection manager initialized
[4294716.478000] Bluetooth: HCI socket layer initialized
[4294716.568000] Bluetooth: L2CAP ver 2.8
[4294716.568000] Bluetooth: L2CAP socket layer initialized
[4294716.577000] Bluetooth: RFCOMM socket layer initialized
[4294716.577000] Bluetooth: RFCOMM TTY layer initialized
[4294716.577000] Bluetooth: RFCOMM ver 1.7
[4295061.793000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4295061.793000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4295061.794000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4311602.003000] APIC error on CPU0: 00(40)

---

### Post by Crooksey on 2006-10-04
Dosent look like good news, the drive isnt even recognised as plugged in, is it any diffrent if you wait 30seconds?

---

### Post by anaoum on 2006-10-05
No, there is no difference.

I re-installed Ubuntu, and it still won't work.

It's as though Ubuntu doesn't see any of my USB ports.

---

### Post by Crooksey on 2006-10-05
Try'd getting a new kernel and configuring it yourself?

---

