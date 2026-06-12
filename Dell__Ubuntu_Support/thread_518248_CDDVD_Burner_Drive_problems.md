---
title: "CD/DVD Burner Drive problems"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by circuz_phreak on 2007-08-05
I currently have a dual boot system with Windows Vista (installed first).  My CD/DVD Burner works fine in vista, but doesn't work at all in Ubuntu 7.04.  It doesn't show up in Device Manager, there's no trace of it anywhere else on the system.  And form the fstab output I assume it's not really recognizing it fully?  It doesn't autoplay or read anything, when I attempt to mount it through terminal or from the explorer window it says dev/hda does not exist (or something along those lines).  Is it possible to resolve this problem, or am I doomed?  Are the drivers for it no good in ubuntu?  Strange that the Ubuntu install went smoothly and now it's like the drive doesn't exist.

fstab output:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=2254cf8c-f4f5-4662-bf8b-f7fcf95443b6 / ext3 defaults,erro$
# /dev/sda7
UUID=13497107-d3af-45f6-8e64-b7a938c91833 none swap sw $
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by bogolisk on 2007-08-05
> **circuz_phreak said:**
> I currently have a dual boot system with Windows Vista (installed first).  My CD/DVD Burner works fine in vista, but doesn't work at all in Ubuntu 7.04.  It doesn't show up in Device Manager, there's no trace of it anywhere else on the system.  And form the fstab output I assume it's not really recognizing it fully?  It doesn't autoplay or read anything, when I attempt to mount it through terminal or from the explorer window it says dev/hda does not exist (or something along those lines).  Is it possible to resolve this problem, or am I doomed?  Are the drivers for it no good in ubuntu?  Strange that the Ubuntu install went smoothly and now it's like the drive doesn't exist.

fstab output:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=2254cf8c-f4f5-4662-bf8b-f7fcf95443b6 / ext3 defaults,erro$
# /dev/sda7
UUID=13497107-d3af-45f6-8e64-b7a938c91833 none swap sw $
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0


What happen if you insert a disc in to the drive?

It would help if you go into a terminal and type:

   dmesg

post the output here so we decipher what the kernel says about the drive. Another thing to try is, in a terminal, type:

   sudo hdparm -iI /dev/hda

post the output as well. We shall see what driver think about the drive.

---

### Post by circuz_phreak on 2007-08-06
dmesg...ALOT of output (also shows wireless card drivers aren´t working..but one problem at a time ).  When i insert a disc into the drive nothing at all happens, the drive spins and sounds like it´s reading the cd...but fails to produce any results.  I don´t believe there is anything wrong with the drive because it is a dual boot system and the drive functions 100% in windows vista.

```


7fe93fc0
[    0.000000] ACPI: SLIC (v001 DELL    M08     0x27d70510 ASL  0x00000061) @ 0x7fe9409c
[    0.000000] ACPI: BOOT (v001 DELL    M08     0x27d70510 ASL  0x00000061) @ 0x7fe93bc0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x7fe926eb
[    0.000000] ACPI: DSDT (v002 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:74000000)
[    0.000000] Detected 1994.633 MHz processor.
[   11.211833] Built 1 zonelists.  Total pages: 519829
[   11.211838] Kernel command line: root=UUID=644532b1-4720-45d2-8dd2-c9198544a36f ro quiet splash
[   11.212030] mapped APIC to ffffd000 (fee00000)
[   11.212034] mapped IOAPIC to ffffc000 (fec00000)
[   11.212037] Enabling fast FPU save and restore... done.
[   11.212040] Enabling unmasked SIMD FPU exception support... done.
[   11.212049] Initializing CPU#0
[   11.212124] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   11.215365] Console: colour VGA+ 80x25
[   11.215700] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.216091] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.305781] Memory: 2066656k/2095688k available (1992k kernel code, 27712k reserved, 893k data, 328k init, 1178184k highmem)
[   11.305793] virtual kernel memory layout:
[   11.305794]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   11.305796]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.305798]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   11.305799]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   11.305801]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   11.305802]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   11.305804]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   11.305808] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.306008] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.306015] hpet0: 3 64-bit timers, 14318180 Hz
[   11.307021] Using HPET for base-timer
[   11.385945] Calibrating delay using timer specific routine.. 3993.97 BogoMIPS (lpj=7987943)
[   11.385996] Security Framework v1.0.0 initialized
[   11.386003] SELinux:  Disabled at boot.
[   11.386022] Mount-cache hash table entries: 512
[   11.386183] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   11.386193] monitor/mwait feature present.
[   11.386195] using mwait in idle threads.
[   11.386201] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.386204] CPU: L2 cache: 4096K
[   11.386207] CPU: Physical Processor ID: 0
[   11.386210] CPU: Processor Core ID: 0
[   11.386212] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   11.386225] Compat vDSO mapped to ffffe000.
[   11.386229] Remapping vsyscall page to ffffe000
[   11.386244] Checking 'hlt' instruction... OK.
[   11.402054] SMP alternatives: switching to UP code
[   11.402487] Early unpacking initramfs... done
[   11.842470] ACPI: Core revision 20060707
[   11.848298] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   11.853098] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   11.853119] SMP alternatives: switching to SMP code
[   11.853193] Booting processor 1/1 eip 3000
[   11.864042] Initializing CPU#1
[   11.941479] Calibrating delay using timer specific routine.. 3988.96 BogoMIPS (lpj=7977938)
[   11.941488] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   11.941494] monitor/mwait feature present.
[   11.941498] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.941501] CPU: L2 cache: 4096K
[   11.941503] CPU: Physical Processor ID: 0
[   11.941505] CPU: Processor Core ID: 1
[   11.941507] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   11.942455] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   11.942484] Total of 2 processors activated (7982.94 BogoMIPS).
[   11.942686] ENABLING IO-APIC IRQs
[   11.942901] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.089355] checking TSC synchronization across 2 CPUs: passed.
[    0.003999] Brought up 2 CPUs
[    0.081613] migration_cost=35
[    0.081924] Booting paravirtualized kernel on bare hardware
[    0.082039] Time: 23:46:13  Date: 07/05/107
[    0.082073] NET: Registered protocol family 16
[    0.082169] EISA bus registered
[    0.082175] ACPI: bus type pci registered
[    0.092817] PCI: PCI BIOS revision 2.10 entry at 0xfad46, last bus=14
[    0.092820] PCI: Using configuration type 1
[    0.092822] Setting up standard PCI resources
[    0.153191] ACPI: Interpreter enabled
[    0.153194] ACPI: Using IOAPIC for interrupt routing
[    0.153557] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.153569] PCI: Probing PCI hardware (bus 00)
[    0.153589] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.183028] Boot video device is 0000:01:00.0
[    0.184332] PCI: Transparent bridge - 0000:00:1e.0
[    0.184439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.202756] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.228302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.230131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.230480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.230927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.231752] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.232149] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.232539] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.232926] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.233312] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.233703] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.234095] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.234470] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.235607] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.235618] pnp: PnP ACPI init
[    0.297785] pnp: PnP ACPI: found 12 devices
[    0.297790] PnPBIOS: Disabled by ACPI PNP
[    0.297844] PCI: Using ACPI for IRQ routing
[    0.297847] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.366938] NET: Registered protocol family 8
[    0.366941] NET: Registered protocol family 20
[    0.398810] pnp: 00:05: ioport range 0xc80-0xcff could not be reserved
[    0.398825] pnp: 00:09: ioport range 0x900-0x97f has been reserved
[    0.398829] pnp: 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.398834] pnp: 00:09: ioport range 0x1000-0x1005 could not be reserved
[    0.398837] pnp: 00:09: ioport range 0x1008-0x100f could not be reserved
[    0.398845] pnp: 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    0.398848] pnp: 00:0a: ioport range 0x1006-0x1007 has been reserved
[    0.398852] pnp: 00:0a: ioport range 0x100a-0x1059 could not be reserved
[    0.398856] pnp: 00:0a: ioport range 0x1060-0x107f has been reserved
[    0.398859] pnp: 00:0a: ioport range 0x1080-0x10bf has been reserved
[    0.398863] pnp: 00:0a: ioport range 0x10c0-0x10df has been reserved
[    0.398867] pnp: 00:0a: ioport range 0x1010-0x102f could not be reserved
[    0.399230] PCI: Bridge: 0000:00:01.0
[    0.399233]   IO window: e000-efff
[    0.399239]   MEM window: fa000000-feafffff
[    0.399243]   PREFETCH window: e0000000-efffffff
[    0.399248] PCI: Bridge: 0000:00:1c.0
[    0.399250]   IO window: disabled.
[    0.399257]   MEM window: disabled.
[    0.399262]   PREFETCH window: disabled.
[    0.399270] PCI: Bridge: 0000:00:1c.1
[    0.399271]   IO window: disabled.
[    0.399279]   MEM window: f9f00000-f9ffffff
[    0.399285]   PREFETCH window: disabled.
[    0.399292] PCI: Bridge: 0000:00:1c.3
[    0.399296]   IO window: d000-dfff
[    0.399304]   MEM window: f9c00000-f9efffff
[    0.399310]   PREFETCH window: f0000000-f01fffff
[    0.399318] PCI: Bridge: 0000:00:1e.0
[    0.399319]   IO window: disabled.
[    0.399327]   MEM window: f9b00000-f9bfffff
[    0.399333]   PREFETCH window: disabled.
[    0.399353] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.399360] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.399388] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.399396] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.399425] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    0.399433] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.399463] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[    0.399470] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.399488] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.399519] NET: Registered protocol family 2
[    0.443684] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.443794] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.444330] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.444597] TCP: Hash tables configured (established 131072 bind 65536)
[    0.444600] TCP reno registered
[    0.459759] checking if image is initramfs... it is
[    1.328995] Freeing initrd memory: 6780k freed
[    1.329189] Simple Boot Flag at 0x79 set to 0x1
[    1.329733] audit: initializing netlink socket (disabled)
[    1.329751] audit(1186357574.192:1): initialized
[    1.329867] highmem bounce pool size: 64 pages
[    1.329966] VFS: Disk quotas dquot_6.5.1
[    1.329988] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.330046] io scheduler noop registered
[    1.330049] io scheduler anticipatory registered
[    1.330052] io scheduler deadline registered
[    1.330066] io scheduler cfq registered (default)
[    1.330407] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.330458] assign_interrupt_mode Found MSI capability
[    1.330461] Allocate Port Service[0000:00:01.0:pcie00]
[    1.330505] Allocate Port Service[0000:00:01.0:pcie02]
[    1.330624] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.330695] assign_interrupt_mode Found MSI capability
[    1.330698] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.330739] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.330903] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.330973] assign_interrupt_mode Found MSI capability
[    1.330976] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.331017] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.331168] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    1.331239] assign_interrupt_mode Found MSI capability
[    1.331242] Allocate Port Service[0000:00:1c.3:pcie00]
[    1.331282] Allocate Port Service[0000:00:1c.3:pcie02]
[    1.331509] isapnp: Scanning for PnP cards...
[    1.685709] isapnp: No Plug & Play device found
[    1.712601] Real Time Clock Driver v1.12ac
[    1.712676] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.713426] mice: PS/2 mouse device common for all mice
[    1.714119] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.714377] input: Macintosh mouse button emulation as /class/input/input0
[    1.714420] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.714425] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.714791] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.718523] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.718528] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.718646] EISA: Probing bus 0 at eisa.0
[    1.718713] EISA: Mainboard @O_FFFF detected.
[    1.718752] Cannot allocate resource for EISA slot 1
[    1.718792] EISA: Detected 0 cards.
[    1.724056] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.748876] TCP cubic registered
[    1.748886] NET: Registered protocol family 1
[    1.748911] Starting balanced_irq
[    1.748918] Using IPI No-Shortcut mode
[    1.748998] ACPI: (supports S0 S3 S4 S5)
[    1.749058]   Magic number: 3:65:807
[    1.749099]   hash matches device ptys1
[    1.749115]   hash matches device snapshot
[    1.749277] Freeing unused kernel memory: 328k freed
[    1.750540] Time: tsc clocksource has been installed.
[    3.021510] Capability LSM initialized
[    3.098909] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.099223] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.099687] Monitor-Mwait will be used to enter C-1 state
[    3.099690] Monitor-Mwait will be used to enter C-2 state
[    3.099694] Monitor-Mwait will be used to enter C-3 state
[    3.099701] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.099707] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.100328] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.100586] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.102997] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.103005] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.792000] Time: hpet clocksource has been installed.
[    3.792000] ACPI: Thermal Zone [THM] (25 C)
[    4.308000] SCSI subsystem initialized
[    4.312000] usbcore: registered new interface driver usbfs
[    4.312000] usbcore: registered new interface driver hub
[    4.312000] usbcore: registered new device driver usb
[    4.316000] libata version 2.20 loaded.
[    4.316000] ieee1394: Initialized config rom entry `ip1394'
[    4.320000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[    4.384000] USB Universal Host Controller Interface driver v3.0
[    4.396000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.432000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
[    4.432000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    4.432000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.432000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.432000] uhci_hcd 0000:00:1a.0: irq 19, io base 0x00006f20
[    4.432000] usb usb1: configuration #1 chosen from 1 choice
[    4.432000] hub 1-0:1.0: USB hub found
[    4.432000] hub 1-0:1.0: 2 ports detected
[    4.536000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[    4.536000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    4.536000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.536000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    4.536000] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00006f00
[    4.536000] usb usb2: configuration #1 chosen from 1 choice
[    4.536000] hub 2-0:1.0: USB hub found
[    4.536000] hub 2-0:1.0: 2 ports detected
[    4.640000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    4.640000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.640000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.640000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    4.640000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00006f80
[    4.640000] usb usb3: configuration #1 chosen from 1 choice
[    4.640000] hub 3-0:1.0: USB hub found
[    4.640000] hub 3-0:1.0: 2 ports detected
[    4.744000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
[    4.744000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    4.744000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.744000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    4.744000] ehci_hcd 0000:00:1a.7: debug port 1
[    4.744000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    4.744000] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xfed1c400
[    4.748000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.748000] usb usb4: configuration #1 chosen from 1 choice
[    4.748000] hub 4-0:1.0: USB hub found
[    4.748000] hub 4-0:1.0: 4 ports detected
[    4.852000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    4.852000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.852000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.852000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.852000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.852000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.852000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfed1c000
[    4.856000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.856000] usb usb5: configuration #1 chosen from 1 choice
[    4.856000] hub 5-0:1.0: USB hub found
[    4.856000] hub 5-0:1.0: 6 ports detected
[    4.960000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[    4.960000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.960000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.960000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.960000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00006f60
[    4.960000] usb usb6: configuration #1 chosen from 1 choice
[    4.960000] hub 6-0:1.0: USB hub found
[    4.960000] hub 6-0:1.0: 2 ports detected
[    5.064000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[    5.064000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    5.064000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.064000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.064000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006f40
[    5.064000] usb usb7: configuration #1 chosen from 1 choice
[    5.064000] hub 7-0:1.0: USB hub found
[    5.064000] hub 7-0:1.0: 2 ports detected
[    5.168000] ahci 0000:00:1f.2: version 2.1
[    5.168000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[    5.200000] usb 5-6: new high speed USB device using ehci_hcd and address 2
[    5.336000] usb 5-6: configuration #1 chosen from 1 choice
[    5.672000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc0001c12a981]
[    6.172000] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match
[    6.172000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    6.172000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    6.172000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    6.172000] ata1: SATA max UDMA/133 cmd 0xf882a900 ctl 0x00000000 bmdma 0x00000000 irq 17
[    6.172000] ata2: DUMMY
[    6.172000] ata3: SATA max UDMA/133 cmd 0xf882aa00 ctl 0x00000000 bmdma 0x00000000 irq 17
[    6.172000] scsi0 : ahci
[    6.656000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.660000] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[    6.660000] ata1.00: ATA-8: SAMSUNG HM250JI, HS100-06, max UDMA7
[    6.660000] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    6.668000] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[    6.668000] ata1.00: configured for UDMA/133
[    6.668000] scsi1 : ahci
[    6.668000] scsi2 : ahci
[    6.980000] ata3: SATA link down (SStatus 0 SControl 300)
[    6.980000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250JI  HS10 PQ: 0 ANSI: 5
[    6.980000] b44.c:v1.01 (Jun 16, 2006)
[    6.980000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    6.984000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:7b:a1:0d
[    6.992000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    6.992000] sda: Write Protect is off
[    6.992000] sda: Mode Sense: 00 3a 00 00
[    6.992000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.992000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    6.992000] sda: Write Protect is off
[    6.992000] sda: Mode Sense: 00 3a 00 00
[    6.992000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.992000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    7.628000] sd 0:0:0:0: Attached scsi disk sda
[    7.632000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    8.136000] Attempting manual resume
[    8.136000] swsusp: Resume From Partition 8:7
[    8.136000] PM: Checking swsusp image.
[    8.136000] PM: Resume from disk failed.
[    8.168000] kjournald starting.  Commit interval 5 seconds
[    8.168000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.924000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.948000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.084000] input: PC Speaker as /class/input/input2
[   20.744000] sdhci: Secure Digital Host Controller Interface driver
[   20.744000] sdhci: Copyright(c) Pierre Ossman
[   20.744000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   20.744000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
[   20.744000] mmc0: SDHCI at 0xf9bfd400 irq 22 DMA
[   20.816000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.848000] ieee80211_crypt: registered algorithm 'NULL'
[   20.852000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.852000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.868000] input: PS/2 Generic Mouse as /class/input/input3
[   20.908000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   20.908000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.964000] Linux video capture interface: v2.00
[   20.968000] bcm43xx driver
[   21.064000] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   21.064000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   21.064000] uvcvideo: Failed to initialize the device (-5).
[   21.064000] usbcore: registered new interface driver uvcvideo
[   21.064000] USB Video Class driver (v0.1.0)
[   22.136000] hda_intel: azx_get_response timeout, switching to polling mode...
[   23.140000] hda_intel: azx_get_response timeout, switching to single_cmd mode...
[   23.172000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   23.172000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   23.412000] lp: driver loaded but no devices found
[   23.480000] Adding 1124508k swap on /dev/disk/by-uuid/874af833-afb7-469b-9dfe-16af5cffdf93.  Priority:-1 extents:1 across:1124508k
[   23.596000] EXT3 FS on sda6, internal journal
[   24.352000] ACPI: AC Adapter [AC] (off-line)
[   24.396000] ACPI: Battery Slot [BAT0] (battery present)
[   24.476000] No dock devices found.
[   24.508000] Using specific hotkey driver
[   24.540000] ibm_acpi: ec object not found
[   24.576000] input: Lid Switch as /class/input/input4
[   24.576000] ACPI: Lid Switch [LID]
[   24.576000] input: Power Button (CM) as /class/input/input5
[   24.576000] ACPI: Power Button (CM) [PBTN]
[   24.576000] input: Sleep Button (CM) as /class/input/input6
[   24.576000] ACPI: Sleep Button (CM) [SBTN]
[   24.700000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   24.708000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   24.708000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   24.740000] pcc_acpi: loading...
[   27.740000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   30.220000] ppdev: user-space parallel port driver
[   30.840000] apm: BIOS not found.
[   30.976000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   31.052000] Bluetooth: Core ver 2.11
[   31.052000] NET: Registered protocol family 31
[   31.052000] Bluetooth: HCI device and connection manager initialized
[   31.052000] Bluetooth: HCI socket layer initialized
[   31.072000] Bluetooth: L2CAP ver 2.8
[   31.072000] Bluetooth: L2CAP socket layer initialized
[   31.276000] Bluetooth: RFCOMM socket layer initialized
[   31.276000] Bluetooth: RFCOMM TTY layer initialized
[   31.276000] Bluetooth: RFCOMM ver 1.8
[   50.932000] NET: Registered protocol family 10
[   50.932000] lo: Disabled Privacy Extensions
[   50.932000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.212000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   77.436000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  100.660000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  124.492000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  147.712000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


```

sudo hdparm -iI /dev/hda   (gives ¨/dev/hda no such file or directory¨)  not familiar with this command sorry, but makes sense if the drive doesn´t exist i.e. the system doesn´t read the drive at all...for the command i used a lower case  i  and an uppercase  i  after the - , is that correct?

Hope this helps...thanks

---

### Post by bogolisk on 2007-08-06
circuz_phreak,

thanx for posting the dmesg results. The kernel seems to ignore/not-recognize your IDE controller. Do you have an IDE controller? or is DVD drive a sata-burnner?

If your DVD drive is an IDE drive do you know what IDE controller you have? What motherboard do you have?

Try post the output of
```

sudo lspci -v

```

That would show how the kernel see hardware (thru the southbridge).


Another thing you can try is to boot with the Ubuntu-7.04 live-cd. Don't install just boot the live-cd up and go into a terminal. Capture the output of "dmesg" again to see how the kernel-on-the-livecd detected your DVD drive (vs the installed kernel which failed to detect your drive.) In this case it's not really the drive but the the installed-kernel seems to ignore/not-recognized the IDE controller.

---

### Post by circuz_phreak on 2007-08-06
I probably should have mentioned my system, sorry.  I have a dell inspiron 1720 laptop.  The drive that came with it isn´t detailed, but it is an IDE 8x CD/DVD/CD-RW Burner.  The system has a Mobile IDE Controller and a Intel Crestline G965 / P965 chipset.  I don´t know much more about the controller, all they said was that it was a standard IDE Controller.  Hope this all helps...thanks again.

sudo lspci -v

```

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fa000000-feafffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: [88] Subsystem: Dell Unknown device 01f2
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Dell Unknown device 01f2
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f9f00000-f9ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Dell Unknown device 01f2
        Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f9c00000-f9efffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Dell Unknown device 01f2
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: f9b00000-f9bfffff
        Capabilities: [50] Subsystem: Dell Unknown device 01f2

00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=32]
        Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 01f2
        Flags: medium devsel, IRQ 10
        Memory at febfb700 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0407 (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at ef00 [size=128]
        Expansion ROM at fea00000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at f9bfe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f9bfd800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f9bfd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0c:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Express Legacy Endpoint IRQ 0



```

Unfortunately I am unable to boot from the live cd, which is what forced me to install from the alternate cd.  Here is the error I get when trying to boot from live cd, and selecting ¨start or install ubuntu¨.  Is this going to be a problem, or is running ´dmesg´ from there not really matter?  I get limited commands and when i type ´ls´ i see all the folders in the directory that are needed....Also pressing F6 displays "Boot option______________" at the bottom of the screen for me to enter something (or something like that).......perhaps it wouldn't say that if i didn't have ubuntu already installed?  Anyways, i've asked somebody who has the same system as me and used a live cd if he had this drive problem with his kernel...he also used wubi though (if that matters)....i would like to fix the situation from where I am now if possible, but figuring out how to fix the live cd, then doing a fresh installing is always an option too.

```

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter ´help´ for a list of built-in commands.
/bin/sh: can´t access tty; job control turned off (initramfs)

```

P.S.  If my kernel isn't recognizing my IDE controller, is there an up to date one that would?  Can I do that with linux, switch kernels, or update the kernel?  I'm guessing there's probably no way I can edit the kernel to recognize my device?  I thought the IDE Controller was also for my hard drives, so how come only my CD/DVD Burner wouldn't be seen?  This is a pretty serious compatability issue for this laptop....

---

### Post by bogolisk on 2007-08-07
```

00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01f2
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]

```

The kernel **found** the IDE controller but it seems that the standard Ubuntu kernel doesn't load the appropriate driver for it.
[list]
[*] The first thing to try is when you boot, try to press "ESC" at the Grub prompt, then move the selection bar the first kernel choice and presse "e" for edit. Add a "all-generic-ide" to the end of the command line. Since you're there, delete the "quiet" and the "splash" options. Boot the system and wish for the best.

[*] Boot the altenate-cd, once it's up and ask the first question. Try to go to another terminal (Alt-F2 or Alt-F3). In the shell type
```

mount

```
to see if your IDE drive is using the old ide driver or the new libata's pata driver.

If you see something like /dev/hdX (e.g. hdd, hdb, etc.) then it's the old ide driver. If it's /dev/sdX  (e.g. sda1, sda2, sb6, etc.) and no /dev/hdX then the kernel is using the new libata driver for the ide controller.

If you had a /dev/hdX (e.g. /dev/hdd) then type:
```

ls -lA /sys/module/*/drivers/*/0000:00:1f.1

```

Because your IDE controller is at 00:1f.1. On my machine, the ide controller is at 00:0d.0, and the above command would show:
```

ls -lA  /sys/module/*/drivers/*/0000:00:0d.0 lrwxrwxrwx 1 root root 0 2007-08-06 23:39 /sys/module/**amd74xx**/drivers/pci:AMD_IDE/0000:00:0d.0 -> ../../../../devices/pci0000:00/0000:00:0d.0

```
that the driver module amd74xx is assigned to the IDE controller by the kernel.


Once you know the name of the driver. Assuming it's  piix (old ide driver), Then boot the your previously installed system. In a shell type:

```

sudo modprobe piix
ls -ld /sys/module/*/drivers/*/0000:00:1f.1
ls -ld /sys/module/*/drivers/*/0000:00:1f.1/ide*/*/block:hd*
dmesg

```

the 2nd "ls ..." command should tell which /dev/hdX is your DVD drive.


If the driver was an libata pata driver such as pata_marvell. Then type
```

sudo modprobe pata_marvell
ls -ld /sys/module/*/drivers/*/0000:00:1f.1
ls -ld /sys/module/*/drivers/*/0000:00:1f.1/host0/target*/*/block:sd*
dmesg

```
capture and post the output so we can debug further. The 2nd "ls", if successful would tell you what "/dev/sdX" is your DVD drive.

From this point on, you'll have to help me and try different things because I've never used libata's for IDE before. In either case, you should probably add the module name (piix, pata_marvell, etc.) into the file /etc/modules.

Good luck.
[/list]

---

### Post by bogolisk on 2007-08-07
According to [http://ubuntuforums.org/showthread.php?t=512576](http://ubuntuforums.org/showthread.php?t=512576)

All you would need is to add a line
```

piix

```

into the file /etc/modules.

Good luck.

---

### Post by circuz_phreak on 2007-08-07
LOL, after bringing up the driver myself in the terminal it worked fine, a reboot completely resolved it because I still had both a cd-rom and the proper burner drive showing up.  Now it works great, auto mounts upon insertion of media, can be read no problem...not sure about burning but that´s for another time.  Right now i´m gonna fix my wireless issue and get some drivers for my Nvidia card.  I think it´s hilarious how a couple lines of short code was the fix to a problem that was driving me nuts.  Thanks so much for all your help, and I can´t thank you enough for all the effort you put in reading the output from my terminal.  I never woulda got this fixed without your help....THANKS!!!

---

