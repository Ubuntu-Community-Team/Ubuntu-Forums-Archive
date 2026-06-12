---
title: "Boot hang on Enterprise Volume Manager"
date: 2005-07-28
forum: Desktop Environments
---

### Post by ghostintheshell on 2005-07-28
Hello,

Time to time, my boot hang on the Enterprise Volume Manager sequence.

It's hang again tonight, I had to reboot twice to boot normally :/
And sometimes I had to reboot 3 or 4 times :(

And that really freeze the boot-up sequence (the "CTRL-C" tip does nothing like for the [Configure Network Interfaces sequence problem]("http://www.ubuntuguide.org/#configuringnetwoktooslow")).

Do you know this problem? -> Have you got a solution?

Many thanks.

---

### Post by strikeforce on 2005-07-28
Need more information e.g. log files dmesg and things like that.

Look under /var/log for an error in the files there.

---

### Post by ghostintheshell on 2005-07-29
I don't see any particular error but I'm far to be an expert in the log files ...

Then here's the /var/log/dmesg file:

 ```
      0 - 0000000100000000 (reserved)
0MB HIGHMEM available.
511MB LOWMEM available.
On node 0 totalpages: 131051
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 126955 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 ASUS                                  ) @ 0x000f6b20
ACPI: RSDT (v001 ASUS   P4T-E    0x30303031 MSFT 0x31313031) @ 0x1ffeb000
ACPI: FADT (v001 ASUS   P4T-E    0x30303031 MSFT 0x31313031) @ 0x1ffeb100
ACPI: BOOT (v001 ASUS   P4T-E    0x30303031 MSFT 0x31313031) @ 0x1ffeb040
ACPI: MADT (v001 ASUS   P4T-E    0x30303031 MSFT 0x31313031) @ 0x1ffeb080
ACPI: DSDT (v001   ASUS P4T-E    0x00001000 MSFT 0x0100000b) @ 0x00000000
ACPI: PM-Timer IO Port: 0xe408
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:2 APIC version 20
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda4 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 2008.958 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 511440k/524204k available (1587k kernel code, 12156k reserved, 714k data, 164k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3981.31 BogoMIPS (lpj=1990656)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
CPU0: Thermal monitoring enabled
CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4524k freed
NET: Registered protocol family 16
PCI: PCI BIOS revision 2.10 entry at 0xf0ea0, last bus=2
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
pnp: 00:02: ioport range 0xec00-0xec3f has been reserved
pnp: 00:02: ioport range 0x370-0x372 has been reserved
Simple Boot Flag at 0x3a set to 0x1
audit: initializing netlink socket (disabled)
audit(1122589711.259:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
PCI0 PCI1 PCI2 UAR1 UAR2 USB0 USB1 AC97 
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4524KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH2: IDE controller at PCI slot 0000:00:1f.1
ICH2: chipset revision 4
ICH2: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: ST3120026A, ATA DISK drive
hdb: ST3160023A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 p7 > p3 p4
hdb: max request size: 1024KiB
hdb: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
hdb: cache flushes supported
 /dev/ide/host0/bus0/target1/lun0: p1 p2 p4
Probing IDE interface ide1...
hdc: PLEXTOR DVDR PX-716A, ATAPI CD/DVD-ROM drive
hdd: SAMSUNG DVD-ROM SD-616E, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  -\|/done (464 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 514072k swap on /dev/hda3.  Priority:-1 extents:1
EXT3 FS on hda4, internal journal
hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X DVD-ROM drive, 512kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Linux agpgart interface v0.100 (c) Dave Jones
nvidia: module license 'NVIDIA' taints kernel.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda7, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
NTFS volume version 3.1.
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-686
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
agpgart: Detected an Intel i850 Chipset.
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 64M @ 0xf8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
hw_random: RNG not detected
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1f.2: Intel Corp. 82801BA/BAM USB (Hub #1)
PCI: Setting latency timer of device 0000:00:1f.2 to 64
uhci_hcd 0000:00:1f.2: irq 19, io base 0xb400
uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1f.4: Intel Corp. 82801BA/BAM USB (Hub #2)
PCI: Setting latency timer of device 0000:00:1f.4 to 64
uhci_hcd 0000:00:1f.4: irq 23, io base 0xb000
uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using uhci_hcd and address 2
hub 1-1:1.0: USB hub found
hub 1-1:1.0: 4 ports detected
sundance.c:v1.01+LK1.09a 10-Jul-2003  Written by Donald Becker
  http://www.scyld.com/network/sundance.html
PCI: Enabling device 0000:02:0b.0 (0014 -> 0017)
ACPI: PCI interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 23
eth0: D-Link DFE-550TX FAST Ethernet Adapter at 0xd800, 00:05:5d:1a:67:f0, IRQ 23.
eth0: MII PHY found at address 1, status 0x7829 advertising 01e1.
usb 1-2: new low speed USB device using uhci_hcd and address 3
eth0: Link changed: 
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1f.2-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
PCI: Enabling device 0000:02:0c.0 (0014 -> 0016)
ACPI: PCI interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 20
ohci_hcd 0000:02:0c.0: NEC Corporation USB
ohci_hcd 0000:02:0c.0: irq 20, pci mem 0xdd000000
ohci_hcd 0000:02:0c.0: new USB bus registered, assigned bus number 3
NET: Registered protocol family 17
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 3 ports detected
PCI: Enabling device 0000:02:0c.1 (0014 -> 0016)
ACPI: PCI interrupt 0000:02:0c.1[B] -> GSI 21 (level, low) -> IRQ 21
ohci_hcd 0000:02:0c.1: NEC Corporation USB (#2)
ohci_hcd 0000:02:0c.1: irq 21, pci mem 0xdc800000
ohci_hcd 0000:02:0c.1: new USB bus registered, assigned bus number 4
usb 3-2: new full speed USB device using ohci_hcd and address 2
usb 3-3: new full speed USB device using ohci_hcd and address 3
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0C17
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
Bluetooth: Core ver 2.7
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: HCI USB driver ver 2.7
usbcore: registered new driver hci_usb
usb 4-1: new full speed USB device using ohci_hcd and address 2
PCI: Enabling device 0000:02:0c.2 (0014 -> 0016)
ACPI: PCI interrupt 0000:02:0c.2[C] -> GSI 22 (level, low) -> IRQ 22
ehci_hcd 0000:02:0c.2: NEC Corporation USB 2.0
ehci_hcd 0000:02:0c.2: irq 22, pci mem 0xdc000000
ehci_hcd 0000:02:0c.2: new USB bus registered, assigned bus number 5
ehci_hcd 0000:02:0c.2: USB 2.0 initialized, EHCI 0.95, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 5 ports detected
usb 5-2: new high speed USB device using ehci_hcd and address 2
PCI: Enabling device 0000:02:0d.0 (0004 -> 0005)
ACPI: PCI interrupt 0000:02:0d.0[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Enabling device 0000:02:0d.1 (0004 -> 0005)
gameport: pci0000:02:0d.1 speed 978 kHz
usb 3-2: USB disconnect, address 2
drivers/usb/class/usblp.c: usblp0: removed
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0000:02:0d.2 (0014 -> 0016)
ACPI: PCI interrupt 0000:02:0d.2[B] -> GSI 19 (level, low) -> IRQ 19
usb 3-2: new full speed USB device using ohci_hcd and address 4
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[db800000-db8007ff]  Max Packet=[2048]
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0C17
usb 3-3: USB disconnect, address 3
usb 3-3: new full speed USB device using ohci_hcd and address 5
usb 4-2: new full speed USB device using ohci_hcd and address 3
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0151079d03]
usbcore: registered new driver snd-usb-audio

``` 

Do you see something strange which could be the source of the problem?

---

