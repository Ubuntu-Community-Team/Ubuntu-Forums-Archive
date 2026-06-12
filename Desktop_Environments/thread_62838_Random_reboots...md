---
title: "Random reboots.."
date: 2005-09-06
forum: Desktop Environments
---

### Post by mcduck on 2005-09-06
Well, I left my computer running last night when I went to sleep, and this morning I was greeted with login screen..  Which is interesting, as I was logged in when I left the computer. I of course started looking through the system logs to find out what has happened, and it seems Ubuntu has booted itself at 08.04 this morning, and I woke up at about ten minutes later so something is not right.

Then I realised that this is not the first time. It happened last week also, only then I just thought that I must have logged myself out before leaving the machine, so I didn't even check the logs.

There sure is something wrong, and I have no idea where to look to find out what's wrong.

from messages: 
```

Sep  6 05:10:58 localhost -- MARK --
Sep  6 05:30:58 localhost -- MARK --
Sep  6 05:50:58 localhost -- MARK --
Sep  6 06:10:58 localhost -- MARK --
Sep  6 06:30:58 localhost -- MARK --
Sep  6 06:50:58 localhost -- MARK --
Sep  6 07:10:58 localhost -- MARK --
Sep  6 07:30:58 localhost -- MARK --
Sep  6 07:36:03 localhost exiting on signal 15
Sep  6 07:36:04 localhost syslogd 1.4.1#16ubuntu6: restart.
Sep  6 07:56:04 localhost -- MARK --
Sep  6 08:04:07 localhost syslogd 1.4.1#16ubuntu6: restart.
Sep  6 08:04:07 localhost kernel: Inspecting /boot/System.map-2.6.10-5-k7
Sep  6 08:04:08 localhost kernel: Loaded 26825 symbols from /boot/System.map-2.6.10-5-k7.
Sep  6 08:04:08 localhost kernel: Symbols match kernel version 2.6.10.
Sep  6 08:04:08 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Sep  6 08:04:08 localhost kernel: VR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  6 08:04:08 localhost kernel: ACPI: BIOS IRQ0 pin2 override ignored.
Sep  6 08:04:08 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  6 08:04:08 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Sep  6 08:04:08 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Sep  6 08:04:08 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  6 08:04:08 localhost kernel: Using ACPI (MADT) for SMP configuration information
Sep  6 08:04:08 localhost kernel: Built 1 zonelists
Sep  6 08:04:08 localhost kernel: Kernel command line: root=/dev/hdc2 ro quiet splash vga=792 
Sep  6 08:04:08 localhost kernel: Initializing CPU#0
Sep  6 08:04:08 localhost kernel: PID hash table entries: 4096 (order: 12, 65536 bytes)
Sep  6 08:04:08 localhost kernel: Detected 2304.420 MHz processor.
Sep  6 08:04:08 localhost kernel: Using pmtmr for high-res timesource
Sep  6 08:04:08 localhost kernel: Console: colour dummy device 80x25
Sep  6 08:04:08 localhost kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  6 08:04:08 localhost kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  6 08:04:08 localhost kernel: Memory: 1031516k/1048512k available (1595k kernel code, 16340k reserved, 721k data, 164k init, 131008k highmem)
Sep  6 08:04:08 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  6 08:04:08 localhost kernel: Security Framework v1.0.0 initialized
Sep  6 08:04:08 localhost kernel: SELinux:  Disabled at boot.
Sep  6 08:04:08 localhost kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Sep  6 08:04:08 localhost kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Sep  6 08:04:08 localhost kernel: CPU: L2 Cache: 512K (64 bytes/line)
Sep  6 08:04:08 localhost kernel: Intel machine check architecture supported.
Sep  6 08:04:08 localhost kernel: Intel machine check reporting enabled on CPU#0.
Sep  6 08:04:08 localhost kernel: CPU: AMD Athlon(tm) XP 2800+ stepping 00
Sep  6 08:04:08 localhost kernel: Enabling fast FPU save and restore... done.
Sep  6 08:04:08 localhost kernel: Enabling unmasked SIMD FPU exception support... done.
Sep  6 08:04:08 localhost kernel: Checking 'hlt' instruction... OK.
Sep  6 08:04:08 localhost kernel: ACPI: Looking for DSDT in initrd... not found!
Sep  6 08:04:08 localhost kernel: ENABLING IO-APIC IRQs
Sep  6 08:04:08 localhost kernel: ..TIMER: vector=0x31 pin1=0 pin2=-1
Sep  6 08:04:08 localhost kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Sep  6 08:04:08 localhost kernel: Freeing initrd memory: 4540k freed
Sep  6 08:04:08 localhost kernel: NET: Registered protocol family 16
Sep  6 08:04:08 localhost kernel: PCI: PCI BIOS revision 2.10 entry at 0xfb410, last bus=3
Sep  6 08:04:08 localhost kernel: PCI: Using configuration type 1
Sep  6 08:04:08 localhost kernel: mtrr: v2.0 (20020519)
Sep  6 08:04:08 localhost kernel: ACPI: Subsystem revision 20050211
Sep  6 08:04:08 localhost kernel: ACPI: Interpreter enabled
Sep  6 08:04:08 localhost kernel: ACPI: Using IOAPIC for interrupt routing
Sep  6 08:04:08 localhost kernel: ACPI: PCI Root Bridge [PCI0] (00:00)
Sep  6 08:04:08 localhost kernel: PCI: Probing PCI hardware (bus 00)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Sep  6 08:04:08 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  6 08:04:08 localhost kernel: pnp: PnP ACPI init
Sep  6 08:04:08 localhost kernel: pnp: PnP ACPI: found 15 devices
Sep  6 08:04:08 localhost kernel: PnPBIOS: Disabled by ACPI PNP
Sep  6 08:04:08 localhost kernel: PCI: Using ACPI for IRQ routing
Sep  6 08:04:08 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
Sep  6 08:04:08 localhost kernel: ** causes a device to stop working, it is probably because the
Sep  6 08:04:08 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
Sep  6 08:04:08 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
Sep  6 08:04:08 localhost kernel: ** behavior.  If this argument makes the device work again,
Sep  6 08:04:08 localhost kernel: ** please email the output of "lspci" to bjorn.helgaas@hp.com
Sep  6 08:04:08 localhost kernel: ** so I can fix the driver.
Sep  6 08:04:08 localhost kernel: pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
Sep  6 08:04:08 localhost kernel: pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
Sep  6 08:04:08 localhost kernel: pnp: 00:00: ioport range 0x4400-0x447f has been reserved
Sep  6 08:04:08 localhost kernel: pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
Sep  6 08:04:08 localhost kernel: pnp: 00:00: ioport range 0x4200-0x427f has been reserved
Sep  6 08:04:08 localhost kernel: pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
Sep  6 08:04:08 localhost kernel: pnp: 00:01: ioport range 0x5000-0x503f has been reserved
Sep  6 08:04:08 localhost kernel: pnp: 00:01: ioport range 0x5500-0x553f has been reserved
Sep  6 08:04:08 localhost kernel: audit: initializing netlink socket (disabled)
Sep  6 08:04:08 localhost kernel: highmem bounce pool size: 64 pages
Sep  6 08:04:08 localhost kernel: VFS: Disk quotas dquot_6.5.1
Sep  6 08:04:08 localhost kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  6 08:04:08 localhost kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Sep  6 08:04:08 localhost kernel: devfs: boot_options: 0x0
Sep  6 08:04:08 localhost kernel: Initializing Cryptographic API
Sep  6 08:04:08 localhost kernel: isapnp: Scanning for PnP cards...
Sep  6 08:04:08 localhost kernel: isapnp: No Plug & Play device found
Sep  6 08:04:08 localhost kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  6 08:04:08 localhost kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  6 08:04:08 localhost kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Sep  6 08:04:08 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  6 08:04:08 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep  6 08:04:08 localhost kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  6 08:04:08 localhost kernel: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Sep  6 08:04:08 localhost kernel: io scheduler noop registered
Sep  6 08:04:08 localhost kernel: io scheduler anticipatory registered
Sep  6 08:04:08 localhost kernel: io scheduler deadline registered
Sep  6 08:04:08 localhost kernel: io scheduler cfq registered
Sep  6 08:04:08 localhost kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Sep  6 08:04:08 localhost kernel: input: AT Translated Set 2 keyboard on isa0060/serio0
Sep  6 08:04:08 localhost kernel: NET: Registered protocol family 2
Sep  6 08:04:08 localhost kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Sep  6 08:04:08 localhost kernel: TCP: Hash tables configured (established 262144 bind 65536)
Sep  6 08:04:08 localhost kernel: NET: Registered protocol family 8
Sep  6 08:04:08 localhost kernel: NET: Registered protocol family 20
Sep  6 08:04:08 localhost kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
Sep  6 08:04:08 localhost kernel:  Strange, kseriod not stopped
Sep  6 08:04:08 localhost kernel:  done
Sep  6 08:04:08 localhost kernel: ACPI wakeup devices: 
Sep  6 08:04:08 localhost kernel: HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI UAR1 
Sep  6 08:04:08 localhost kernel: ACPI: (supports S0 S1 S3 S4 S4bios S5)
Sep  6 08:04:08 localhost kernel: RAMDISK: cramfs filesystem found at block 0
Sep  6 08:04:08 localhost kernel: RAMDISK: Loading 4540KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^Hdone.
Sep  6 08:04:08 localhost kernel: VFS: Mounted root (cramfs filesystem) readonly.
Sep  6 08:04:08 localhost kernel: Freeing unused kernel memory: 164k freed
Sep  6 08:04:08 localhost kernel: vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 4608k, total 16384k
Sep  6 08:04:08 localhost kernel: vesafb: mode is 1024x768x24, linelength=3072, pages=6
Sep  6 08:04:08 localhost kernel: vesafb: protected mode interface info at c000:5812
Sep  6 08:04:08 localhost kernel: vesafb: scrolling: redraw
Sep  6 08:04:08 localhost kernel: vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Sep  6 08:04:08 localhost kernel: fb0: VESA VGA frame buffer device
Sep  6 08:04:08 localhost kernel: Console: switching to colour frame buffer device 128x48
Sep  6 08:04:08 localhost kernel: NET: Registered protocol family 1
Sep  6 08:04:08 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Sep  6 08:04:08 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Sep  6 08:04:08 localhost kernel: NFORCE2: IDE controller at PCI slot 0000:00:09.0
Sep  6 08:04:08 localhost kernel: NFORCE2: chipset revision 162
Sep  6 08:04:08 localhost kernel: NFORCE2: not 100%% native mode: will probe irqs later
Sep  6 08:04:08 localhost kernel: NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
Sep  6 08:04:08 localhost kernel: NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
Sep  6 08:04:08 localhost kernel:     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Sep  6 08:04:08 localhost kernel:     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Sep  6 08:04:08 localhost kernel: hda: HL-DT-ST RW/DVD GCC-4521B, ATAPI CD/DVD-ROM drive
Sep  6 08:04:08 localhost kernel: elevator: using anticipatory as default io scheduler
Sep  6 08:04:08 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Sep  6 08:04:08 localhost kernel: hdc: SAMSUNG SP1213N, ATA DISK drive
Sep  6 08:04:08 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Sep  6 08:04:08 localhost kernel: hdc: max request size: 1024KiB
Sep  6 08:04:08 localhost kernel: hdc: 234493056 sectors (120060 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
Sep  6 08:04:08 localhost kernel:  /dev/ide/host0/bus1/target0/lun0: p1 p2 p3
Sep  6 08:04:08 localhost kernel: Stopping tasks: ==|
Sep  6 08:04:08 localhost kernel: Freeing memory...  ^H-^H\^H|^H/^Hdone (453 pages freed)
Sep  6 08:04:08 localhost kernel: Restarting tasks... done
Sep  6 08:04:08 localhost kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  6 08:04:08 localhost kernel: EXT3-fs: write access will be enabled during recovery.
Sep  6 08:04:08 localhost kernel: EXT3-fs: recovery complete.
Sep  6 08:04:08 localhost kernel: kjournald starting.  Commit interval 5 seconds
Sep  6 08:04:08 localhost kernel: EXT3-fs: mounted filesystem with ordered data mode.
Sep  6 08:04:08 localhost kernel: Adding 1951888k swap on /dev/hdc3.  Priority:-1 extents:1
Sep  6 08:04:08 localhost kernel: EXT3 FS on hdc2, internal journal
Sep  6 08:04:08 localhost kernel: hda: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache
Sep  6 08:04:08 localhost kernel: Uniform CD-ROM driver Revision: 3.20
Sep  6 08:04:08 localhost kernel: parport: PnPBIOS parport detected.
Sep  6 08:04:08 localhost kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Sep  6 08:04:08 localhost kernel: lp0: using parport0 (interrupt-driven).
Sep  6 08:04:08 localhost kernel: mice: PS/2 mouse device common for all mice
Sep  6 08:04:08 localhost kernel: input: PS2++ Logitech MX Mouse on isa0060/serio1
Sep  6 08:04:08 localhost kernel: SCSI subsystem initialized
Sep  6 08:04:08 localhost kernel: sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Sep  6 08:04:08 localhost kernel: i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
Sep  6 08:04:08 localhost kernel: i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5500
Sep  6 08:04:08 localhost kernel: ts: Compaq touchscreen protocol output
Sep  6 08:04:08 localhost kernel: Capability LSM initialized
Sep  6 08:04:08 localhost kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
Sep  6 08:04:08 localhost kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Sep  6 08:04:08 localhost kernel: cdrom: open failed.
Sep  6 08:04:08 localhost kernel: Real Time Clock Driver v1.12
Sep  6 08:04:08 localhost kernel: input: PC Speaker
Sep  6 08:04:08 localhost kernel: Linux agpgart interface v0.100 (c) Dave Jones
Sep  6 08:04:08 localhost kernel: agpgart: Detected NVIDIA nForce2 chipset
Sep  6 08:04:08 localhost kernel: agpgart: Maximum main memory to use for agp memory: 941M
Sep  6 08:04:08 localhost kernel: agpgart: AGP aperture is 128M @ 0xe0000000
Sep  6 08:04:08 localhost kernel: usbcore: registered new driver usbfs
Sep  6 08:04:08 localhost kernel: usbcore: registered new driver hub
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 22 (level, high) -> IRQ 22
Sep  6 08:04:08 localhost kernel: ohci_hcd 0000:00:02.0: nVidia Corporation nForce2 USB Controller
Sep  6 08:04:08 localhost kernel: ohci_hcd 0000:00:02.0: irq 22, pci mem 0xed087000
Sep  6 08:04:08 localhost kernel: ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Sep  6 08:04:08 localhost kernel: hub 1-0:1.0: USB hub found
Sep  6 08:04:08 localhost kernel: hub 1-0:1.0: 3 ports detected
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:00:02.1[B] -> GSI 21 (level, high) -> IRQ 21
Sep  6 08:04:08 localhost kernel: ohci_hcd 0000:00:02.1: nVidia Corporation nForce2 USB Controller (#2)
Sep  6 08:04:08 localhost kernel: ohci_hcd 0000:00:02.1: irq 21, pci mem 0xed082000
Sep  6 08:04:08 localhost kernel: ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Sep  6 08:04:08 localhost kernel: hub 2-0:1.0: USB hub found
Sep  6 08:04:08 localhost kernel: hub 2-0:1.0: 3 ports detected
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:00:02.2[C] -> GSI 20 (level, high) -> IRQ 20
Sep  6 08:04:08 localhost kernel: ehci_hcd 0000:00:02.2: nVidia Corporation nForce2 USB Controller
Sep  6 08:04:08 localhost kernel: ehci_hcd 0000:00:02.2: irq 20, pci mem 0xed083000
Sep  6 08:04:08 localhost kernel: ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
Sep  6 08:04:08 localhost kernel: ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
Sep  6 08:04:08 localhost kernel: hub 3-0:1.0: USB hub found
Sep  6 08:04:08 localhost kernel: hub 3-0:1.0: 6 ports detected
Sep  6 08:04:08 localhost kernel: forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.30.
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:00:04.0[A] -> GSI 22 (level, high) -> IRQ 22
Sep  6 08:04:08 localhost kernel: eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 21 (level, high) -> IRQ 21
Sep  6 08:04:08 localhost kernel: intel8x0_measure_ac97_clock: measured 49608 usecs
Sep  6 08:04:08 localhost kernel: intel8x0: clocking to 47466
Sep  6 08:04:08 localhost kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Sep  6 08:04:08 localhost kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  6 08:04:08 localhost kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  6 08:04:08 localhost kernel: ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:00:0d.0[A] -> GSI 20 (level, high) -> IRQ 20
Sep  6 08:04:08 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[ed084000-ed0847ff]  Max Packet=[2048]
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:01:04.0[A] -> GSI 17 (level, high) -> IRQ 17
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:01:04.0[A] -> GSI 17 (level, high) -> IRQ 17
Sep  6 08:04:08 localhost kernel: ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 18 (level, high) -> IRQ 18
Sep  6 08:04:08 localhost kernel: ata1: SATA max UDMA/100 cmd 0xF902E080 ctl 0xF902E08A bmdma 0xF902E000 irq 18
Sep  6 08:04:08 localhost kernel: ata2: SATA max UDMA/100 cmd 0xF902E0C0 ctl 0xF902E0CA bmdma 0xF902E008 irq 18
Sep  6 08:04:08 localhost kernel: ata1: dev 0 ATA, max UDMA/133, 240121728 sectors:
Sep  6 08:04:08 localhost kernel: ata1: dev 0 configured for UDMA/100
Sep  6 08:04:08 localhost kernel: scsi0 : sata_sil
Sep  6 08:04:08 localhost kernel: ata2: no device found (phy stat 00000000)
Sep  6 08:04:08 localhost kernel: scsi1 : sata_sil
Sep  6 08:04:08 localhost kernel:   Vendor: ATA       Model: Maxtor 6Y120M0    Rev: YAR5
Sep  6 08:04:08 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
Sep  6 08:04:08 localhost kernel: SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
Sep  6 08:04:08 localhost kernel: SCSI device sda: drive cache: write back
Sep  6 08:04:08 localhost kernel: SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
Sep  6 08:04:08 localhost kernel: SCSI device sda: drive cache: write back
Sep  6 08:04:08 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0: [LDM] p1 p2
Sep  6 08:04:08 localhost kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Sep  6 08:04:08 localhost kernel: NET: Registered protocol family 17
Sep  6 08:04:08 localhost kernel: eth1: network connection up using port A
Sep  6 08:04:08 localhost kernel:     speed:           100
Sep  6 08:04:08 localhost kernel:     autonegotiation: yes
Sep  6 08:04:08 localhost kernel:     duplex mode:     full
Sep  6 08:04:08 localhost kernel:     flowctrl:        symmetric
Sep  6 08:04:08 localhost kernel:     irq moderation:  disabled
Sep  6 08:04:08 localhost kernel:     scatter-gather:  enabled
Sep  6 08:04:08 localhost kernel: NET: Registered protocol family 10
Sep  6 08:04:08 localhost kernel: Disabled Privacy Extensions on device c0315d40(lo)
Sep  6 08:04:08 localhost kernel: IPv6 over IPv4 tunneling driver
Sep  6 08:04:09 localhost kernel: ACPI: Power Button (FF) [PWRF]
Sep  6 08:04:10 localhost kernel: apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Sep  6 08:04:10 localhost kernel: apm: overridden by ACPI.
Sep  6 08:04:10 localhost hal.hotplug[5257]: timout(10000 ms) waiting for /bus/pci/slots 
Sep  6 08:04:10 localhost pci.agent[7037]: Bad PCI agent invocation
Sep  6 08:04:10 localhost kernel: fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Sep  6 08:04:10 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
Sep  6 08:04:10 localhost kernel: ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Sep  6 08:04:10 localhost kernel: ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 19 (level, high) -> IRQ 19
Sep  6 08:04:10 localhost kernel: [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
Sep  6 08:04:10 localhost kernel: [fglrx] Kernel AGP support doesn't provide agplock functionality.
Sep  6 08:04:10 localhost kernel: [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
Sep  6 08:04:10 localhost kernel: agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Sep  6 08:04:10 localhost kernel: agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Sep  6 08:04:10 localhost kernel: agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
Sep  6 08:04:10 localhost kernel: [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
Sep  6 08:04:10 localhost kernel: [fglrx] free  AGP = 121909248
Sep  6 08:04:10 localhost kernel: [fglrx] max   AGP = 121909248
Sep  6 08:04:10 localhost kernel: [fglrx] free  LFB = 119533568
Sep  6 08:04:10 localhost kernel: [fglrx] max   LFB = 119533568
Sep  6 08:04:10 localhost kernel: [fglrx] free  Inv = 0
Sep  6 08:04:10 localhost kernel: [fglrx] max   Inv = 0
Sep  6 08:04:10 localhost kernel: [fglrx] total Inv = 0
Sep  6 08:04:10 localhost kernel: [fglrx] total TIM = 0
Sep  6 08:04:10 localhost kernel: [fglrx] total FB  = 0
Sep  6 08:04:10 localhost kernel: [fglrx] total AGP = 32768
Sep  6 08:04:11 localhost kernel: ip_tables: (C) 2000-2002 Netfilter core team
Sep  6 08:04:11 localhost kernel: ip_conntrack version 2.1 (8191 buckets, 65528 max) - 336 bytes per conntrack
Sep  6 08:18:21 localhost gconfd (mcduck-8027): starting (version 2.10.0), pid 8027 user 'mcduck'

```
You can see the reboot at 08.04, and me logging in at 08.18

And this is from syslog:
```

Sep  6 07:36:04 localhost syslogd 1.4.1#16ubuntu6: restart.
Sep  6 07:36:04 localhost anacron[2374]: Job `cron.daily' terminated (mailing output)
Sep  6 07:36:04 localhost anacron[2374]: Normal exit (1 job run)
Sep  6 07:36:04 localhost postfix/cleanup[2731]: 9B05C84B0: message-id=<20050906043604.9B05C84B0@localhost.localdomain>
Sep  6 07:36:04 localhost postfix/local[2733]: 9B05C84B0: to=<mcduck@localhost.localdomain>, orig_to=<root>, relay=local, delay=0, status=sent (delivered to mailbox)
Sep  6 07:56:04 localhost -- MARK --
Sep  6 07:58:42 localhost dhclient: DHCPREQUEST on eth1 to 192.168.1.1 port 67
Sep  6 07:58:42 localhost dhclient: DHCPACK from 192.168.1.1
Sep  6 07:58:42 localhost dhclient: bound to 192.168.1.39 -- renewal in 1640 seconds.
Sep  6 08:04:07 localhost syslogd 1.4.1#16ubuntu6: restart.
Sep  6 08:04:07 localhost kernel: Inspecting /boot/System.map-2.6.10-5-k7
Sep  6 08:04:08 localhost kernel: Loaded 26825 symbols from /boot/System.map-2.6.10-5-k7.
Sep  6 08:04:08 localhost kernel: Symbols match kernel version 2.6.10.

```

And here are some specs of the machine:
Amd Athlon XP 2800+ @ 2300MHz
2*512 MB of PC3200 RAM, on dual channels
Asus A7N8X-E Deluxe motherboard (yes, nForce2)
Ati Radeon 9600 XT
Samsung 120GB PATA harddisk
Maxtor 120GB SATA hd, not mounted at the time.
Nexus NX3500 SE 350W power

The machine itself is stable as a rock, it's been tested with memtest, cpuburn, prime95, superpi and of course over a year of heavy use including 3D-rendering with no problems. That's why I posted this on Desktop Support and not hardware..

If anybody has any idea what caused this reboot, please help. Also, if you need any more information, just ask and i'll post it here..

edit: I found this from user.log. Seems like it could be related to this problem (or not, as this this would have happened 2secs _after_ that reboot)
```
 
Sep  5 22:04:30 localhost gconfd (mcduck-20722): Resolved address "xml:readwrite:/home/mcduck/.gconf" to a writable configuration source at position 0
Sep  6 08:04:10 localhost hal.hotplug[5257]: timout(10000 ms) waiting for /bus/pci/slots 
Sep  6 08:04:10 localhost pci.agent[7037]: Bad PCI agent invocation
Sep  6 08:18:21 localhost gconfd (mcduck-8027): starting (version 2.10.0), pid 8027 user 'mcduck'

```

---

### Post by Tiede on 2005-09-06
You must have set a specific reboot time for the system... Just make sure no automatic sleep/wake time for the system is set and you problem shall go away :)

---

### Post by mcduck on 2005-09-06
[QUOTE=Tiede]You must have set a specific reboot time for the system... Just make sure no automatic sleep/wake time for the system is set and you problem shall go away :)[/QUOTE]No, that couldn't be it as this machine had been running from last week's thursday with no reboots.. (other than this morning, of course..)

Anyway, I wouldn't even know how to set a  reboot time for linux ;)

---

