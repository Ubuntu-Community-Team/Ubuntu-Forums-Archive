---
title: "Computer doesn't turn off after shut down..."
date: 2005-09-30
forum: Desktop Environments
---

### Post by tyttuz on 2005-09-30
is there a way to change this setting. when I write "halt" ou click in "Turn off Computer" show me the list of process turning off... and stop in "Power off" or "Power down", and I have to power off in button.
I want that when stop in "Power off" or "Power down", the machine turn off.
Is that possible?
Someone have the same problem???


Best Regards,
Tito Duarte

---

### Post by adwait on 2005-09-30
That depends on type of cabinet/setup you have. Does the machine auto power off in any other OS?

---

### Post by tyttuz on 2005-09-30
[QUOTE=adwait]That depends on type of cabinet/setup you have. Does the machine auto power off in any other OS?[/QUOTE]
Yes, I have windows installed and auto power off

---

### Post by az on 2005-09-30
From a terminal ty;pe
dmesg

and scroll up and look for messages regarding apm or acpi.  These are power management options.  Post the relevant lines....


You can always force the kernel to use one or the other, but that should be taken care of automatically.

---

### Post by bobyang on 2006-01-19
I have exactly the same problem, here is my dmesg output:
```
[4294667.296000] ACPI: RSDT (v001 ASUS   A7S333   0x42302e31 MSFT 0x31313031) @ 0x1fffc000
[4294667.296000] ACPI: FADT (v001 ASUS   A7S333   0x42302e31 MSFT 0x31313031) @ 0x1fffc0b2
[4294667.296000] ACPI: BOOT (v001 ASUS   A7S333   0x42302e31 MSFT 0x31313031) @ 0x1fffc030
[4294667.296000] ACPI: MADT (v001 ASUS   A7S333   0x42302e31 MSFT 0x31313031) @ 0x1fffc058
[4294667.296000] ACPI: DSDT (v001   ASUS A7S333   0x00001000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0xe408
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:6 APIC version 16
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1662.752 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.769000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.771000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.790000] Memory: 510460k/524272k available (1632k kernel code, 13216k reserved, 740k data, 168k init, 0k highmem)
[4294667.790000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.791000] Calibrating delay loop... 3301.37 BogoMIPS (lpj=1650688)
[4294667.814000] Security Framework v1.0.0 initialized
[4294667.814000] SELinux:  Disabled at boot.
[4294667.814000] Mount-cache hash table entries: 512
[4294667.814000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[4294667.814000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[4294667.814000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294667.814000] CPU: L2 Cache: 256K (64 bytes/line)
[4294667.814000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000020 00000000 00000000 00000000
[4294667.814000] Intel machine check architecture supported.
[4294667.814000] Intel machine check reporting enabled on CPU#0.
[4294667.814000] CPU: AMD Athlon(TM) XP 2000+ stepping 02
[4294667.814000] Enabling fast FPU save and restore... done.
[4294667.814000] Enabling unmasked SIMD FPU exception support... done.
[4294667.814000] Checking 'hlt' instruction... OK.
[4294667.818000] checking if image is initramfs... it is
[4294668.383000] Freeing initrd memory: 5511k freed
[4294668.385000] ACPI: Looking for DSDT in initrd... not found!
[4294668.454000]  not found!
[4294668.458000] ENABLING IO-APIC IRQs
[4294668.458000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.569000] NET: Registered protocol family 16
[4294668.569000] ACPI: bus type pci registered
[4294668.570000] PCI: PCI BIOS revision 2.10 entry at 0xf19a0, last bus=1
[4294668.570000] PCI: Using configuration type 1
[4294668.570000] mtrr: v2.0 (20020519)
[4294668.570000] ACPI: Subsystem revision 20050729
[4294668.576000] ACPI: Interpreter enabled
[4294668.576000] ACPI: Using IOAPIC for interrupt routing
[4294668.577000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294668.577000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.577000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.577000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.578000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.578000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.578000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.578000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[4294668.578000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.578000] PCI: Probing PCI hardware (bus 00)
[4294668.579000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.579000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294668.581000] Enabling SiS 96x SMBus.
[4294668.582000] Boot video device is 0000:01:00.0
[4294668.582000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.583000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294668.588000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.588000] pnp: PnP ACPI init
[4294668.592000] pnp: PnP ACPI: found 16 devices
[4294668.592000] PnPBIOS: Disabled by ACPI PNP
[4294668.592000] PCI: Using ACPI for IRQ routing
[4294668.592000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.598000] pnp: 00:01: ioport range 0xe400-0xe47f could not be reserved
[4294668.598000] pnp: 00:01: ioport range 0xe480-0xe4ff has been reserved
[4294668.598000] pnp: 00:01: ioport range 0xe600-0xe61f has been reserved
[4294668.598000] pnp: 00:01: ioport range 0x480-0x48f has been reserved
[4294668.598000] pnp: 00:0f: ioport range 0x290-0x297 has been reserved
[4294668.598000] pnp: 00:0f: ioport range 0x500-0x507 has been reserved
[4294668.598000] Simple Boot Flag at 0x3a set to 0x1
[4294668.599000] audit: initializing netlink socket (disabled)
[4294668.599000] audit: initialized
[4294668.599000] VFS: Disk quotas dquot_6.5.1
[4294668.599000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.599000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.599000] devfs: boot_options: 0x0
[4294668.599000] Initializing Cryptographic API
[4294668.599000] isapnp: Scanning for PnP cards...
[4294668.953000] isapnp: No Plug & Play device found
[4294668.972000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294668.972000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.972000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.972000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294668.972000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.972000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.974000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.974000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.974000] io scheduler noop registered
[4294668.974000] io scheduler anticipatory registered
[4294668.974000] io scheduler deadline registered
[4294668.974000] io scheduler cfq registered
[4294668.975000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.975000] NET: Registered protocol family 2
[4294668.985000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294668.985000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294668.985000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.986000] TCP: Hash tables configured (established 32768 bind 32768)
[4294668.986000] NET: Registered protocol family 8
[4294668.986000] NET: Registered protocol family 20
[4294668.986000] ACPI wakeup devices:
[4294668.986000] PCI0 PCI1 PS2K PS2M USB0 USB1 MC97
[4294668.986000] ACPI: (supports S0 S1 S4 S5)
[4294668.986000] Freeing unused kernel memory: 168k freed
[4294669.004000] vga16fb: initializing
[4294669.004000] vga16fb: mapped to 0xc00a0000
[4294669.142000] Console: switching to colour frame buffer device 80x30
[4294669.142000] fb0: VGA16 VGA frame buffer device
[4294669.145000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.275000] Capability LSM initialized
[4294670.288000] NET: Registered protocol family 1
[4294670.303000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.303000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.303000] ACPI: bus type ide registered
[4294670.308000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294670.308000] SIS5513: chipset revision 208
[4294670.308000] SIS5513: not 100% native mode: will probe irqs later
[4294670.308000] SIS5513: SiS745 ATA 100 (2nd gen) controller
[4294670.308000]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:pio
[4294670.308000]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:DMA, hdd:pio
[4294670.308000] Probing IDE interface ide0...
[4294670.572000] hda: Maxtor 6Y080L0, ATA DISK drive
[4294671.184000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.184000] Probing IDE interface ide1...
[4294671.856000] hdc: HL-DT-ST GCE-8523B, ATAPI CD/DVD-ROM drive
[4294672.468000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.468000] Probing IDE interface ide2...
[4294672.981000] Probing IDE interface ide3...
[4294673.493000] Probing IDE interface ide4...
[4294674.005000] Probing IDE interface ide5...
[4294674.521000] hda: max request size: 128KiB
[4294674.526000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294674.526000] hda: cache flushes supported
[4294674.527000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
[4294674.552000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294674.552000] Uniform CD-ROM driver Revision: 3.20
[4294674.819000] Attempting manual resume
[4294674.819000] swsusp: Suspend partition has wrong signature?
[4294674.865000] usbcore: registered new driver usbfs
[4294674.865000] usbcore: registered new driver hub
[4294674.866000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294674.866000] ACPI: PCI Interrupt 0000:00:02.2[D] -> GSI 19 (level, low) -> IRQ 19
[4294674.866000] ohci_hcd 0000:00:02.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
[4294674.867000] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[4294674.867000] ohci_hcd 0000:00:02.2: irq 19, io mem 0xe6800000
[4294674.920000] hub 1-0:1.0: USB hub found
[4294674.920000] hub 1-0:1.0: 3 ports detected
[4294674.923000] ACPI: PCI Interrupt 0000:00:02.3[A] -> GSI 23 (level, low) -> IRQ 23
[4294674.923000] ohci_hcd 0000:00:02.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
[4294674.923000] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[4294674.923000] ohci_hcd 0000:00:02.3: irq 23, io mem 0xe6000000
[4294674.976000] hub 2-0:1.0: USB hub found
[4294674.976000] hub 2-0:1.0: 3 ports detected
[4294675.015000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294675.015000] 8139cp: pci dev 0000:00:0b.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294675.015000] 8139cp: Try the "8139too" driver instead.
[4294675.017000] 8139too Fast Ethernet driver 0.9.27
[4294675.017000] PCI: Enabling device 0000:00:0b.0 (0004 -> 0007)
[4294675.017000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294675.017000] eth0: RealTek RTL8139 at 0xa800, 00:0a:eb:7f:b5:de, IRQ 19
[4294675.017000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294677.422000] ACPI: CPU0 (power states: C1[C1])
[4294677.626000] Attempting manual resume
[4294677.626000] swsusp: Suspend partition has wrong signature?
[4294677.644000] kjournald starting.  Commit interval 5 seconds
[4294677.644000] EXT3-fs: mounted filesystem with ordered data mode.
[4294678.589000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294681.344000] Adding 441776k swap on /dev/hda4.  Priority:-1 extents:1
[4294681.533000] EXT3 FS on hda1, internal journal
[4294687.739000] parport: PnPBIOS parport detected.
[4294687.739000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294687.824000] lp0: using parport0 (interrupt-driven).
[4294687.841000] mice: PS/2 mouse device common for all mice
[4294687.862000] Linux agpgart interface v0.101 (c) Dave Jones
[4294687.897000] nvidia: module license 'NVIDIA' taints kernel.
[4294687.905000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294687.905000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4294688.111000] logips2pp: Detected unknown logitech mouse model 56
[4294688.161000] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[4294688.699000] ts: Compaq touchscreen protocol output
[4294692.137000] kjournald starting.  Commit interval 5 seconds
[4294692.137000] EXT3 FS on hda3, internal journal
[4294692.137000] EXT3-fs: mounted filesystem with ordered data mode.
[4294692.155000] kjournald starting.  Commit interval 5 seconds
[4294692.155000] EXT3 FS on hda2, internal journal
[4294692.155000] EXT3-fs: mounted filesystem with ordered data mode.
[4294694.440000] agpgart: Detected SiS 745 chipset
[4294694.453000] agpgart: AGP aperture is 64M @ 0xe8000000
[4294694.707000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.716000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294694.716000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294694.860000] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[4294694.974000] i2c-sis96x version 1.0.0
[4294694.979000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
[4294695.452000] PCI: Enabling device 0000:00:05.0 (0084 -> 0085)
[4294695.452000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294697.335000] Real Time Clock Driver v1.12
[4294697.457000] input: PC Speaker
[4294697.586000] Floppy drive(s): fd0 is 1.44M
[4294697.617000] FDC 0 is a post-1991 82077
[4294698.870000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294700.783000] ACPI: Power Button (FF) [PWRF]
[4294700.783000] ACPI: Power Button (CM) [PWRB]
[4294700.914000] ibm_acpi: ec object not found
[4294707.178000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294707.178000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294707.178000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294707.381000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294707.381000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294707.381000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294718.354000] /dev/vmmon[6847]: Module vmmon: registered with major=10 minor=165
[4294718.354000] /dev/vmmon[6847]: Module vmmon: initialized
[4294718.780000] /dev/vmnet: open called by PID 6881 (vmnet-bridge)
[4294718.780000] /dev/vmnet: hub 0 does not exist, allocating memory.
[4294718.780000] /dev/vmnet: port on hub 0 successfully opened
[4294718.780000] bridge-eth0: enabling the bridge
[4294718.780000] bridge-eth0: up
[4294718.780000] bridge-eth0: already up
[4294718.780000] bridge-eth0: attached
[4294719.278000] NET: Registered protocol family 10
[4294719.278000] Disabled Privacy Extensions on device c0321b80(lo)
[4294719.279000] IPv6 over IPv4 tunneling driver
[4294730.120000] eth0: no IPv6 routers present
[4306049.599000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4306050.096000] cdrom: open failed.
[4306070.575000] cdrom: open failed.

```

---

### Post by az on 2006-01-19
Can you upgrade to Breesy?

If not, give apm a shot.  When you boot, go into the grub menu and press "e" to edit the ubuntu selection.  Edit the kernel like by pressing "e" again.  Go to the end of the line and add "apm=force" and hit enter.  Then press "b" to boot.

If that fixes it, add "apm=force" to the line in /boot/grub/menu.list

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash apm=force

Then run

sudo update-grub.

You can also see what your bios is set to (apm or acpi)

---

### Post by mr_ed on 2006-01-23
Heh.  With my PC, it depends on what kernel I use.  The latest kernel (2.6.12-10?) doesn't power off my box, but the one before it (2.6.12-9?) did.

Thanks azz for the tip.

---

