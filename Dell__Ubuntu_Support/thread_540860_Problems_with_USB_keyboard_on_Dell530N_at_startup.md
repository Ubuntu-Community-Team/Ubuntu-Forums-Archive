---
title: "Problems with USB keyboard on Dell530N at startup"
date: 2007-09-02
forum: Dell  Ubuntu Support
---

### Post by brianborchers on 2007-09-02
I've got a brand new Dell 530N which has shown the following weird behavior on startup:
 
Using the default kernel, after "Starting up...", if I hit the space bar a few times, the system boots up and goes into X windows normally.  However, if I don't touch the keyboard, after "Starting up...", the system crunches for a few seconds and then reboots.  
 
I went into /boot/grub/menu.lst and removed "quiet splash" so that I might see what was happening.  Unfortunately, the text flashes by so rapidly that it's impossible to see what was going on just before the reboot.  

Any suggestions on how to debug this problem?

---

### Post by brianborchers on 2007-09-02
After running this a few times and looking carefully, it appears that the last message is:
 
  checking if image is initramfs... it is

---

### Post by gbrainin on 2007-09-02
I don't have any suggestions, but I wanted to confirm that this is not normal behavior.  I have two 530Ns in my house, and neither of them do this.  It sounds like something was wrong from the factory (either bad hardware or improper software configuration), and if so Dell should diagnose and fix it.

Don't call the regular support line; they exist in a Windows-only world.  The special line for Ubuntu-preinstalled systems is: 866-622-1947.

---

### Post by Afishionado on 2007-09-02
Once you get it booted, can you run

dmesg

in a terminal and paste the output here?

---

### Post by brianborchers on 2007-09-02
The failed boot up produces no output in dmesg (I'm assuming that's because it hasn't actually mounted any file systems at the point that it fails.)  I do have dmesg output from a successful boot up in which I pressed the space bar early in the process:
 
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009e800 end: 000000000009e800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009e800 size: 0000000000001800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fd90000 end: 000000007fe90000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fe90000 size: 0000000000053000 end: 000000007fee3000 type: 4
[    0.000000] copy_e820_map() start: 000000007fee3000 size: 000000000000d000 end: 000000007fef0000 type: 3
[    0.000000] copy_e820_map() start: 000000007fef0000 size: 0000000000010000 end: 000000007ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe90000 (usable)
[    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3e30
[    0.000000] Entering add_active_range(0, 0, 523920) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523920
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523920
[    0.000000] On node 0 totalpages: 523920
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292243 pages, LIFO batch:31
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP (v002 DELL                                  ) @ 0x000f96c0
[    0.000000] ACPI: XSDT (v001 DELL    FX09    0x42302e31 AWRD 0x00000000) @ 0x7fee3080
[    0.000000] ACPI: FADT (v003 DELL    FX09    0x42302e31 AWRD 0x00000000) @ 0x7fee7200
[    0.000000] ACPI: HPET (v001 DELL    FX09    0x42302e31 AWRD 0x00000098) @ 0x7fee73c0
[    0.000000] ACPI: MCFG (v001 DELL    FX09    0x42302e31 AWRD 0x00000000) @ 0x7fee7400
[    0.000000] ACPI: DMY1 (v001 DELL    FX09    0x42302e31 AWRD 0x00000000) @ 0x7fee7440
[    0.000000] ACPI: DMY2 (v001 DELL    FX09    0x42302e31 AWRD 0x00000000) @ 0x7fee75c0
[    0.000000] ACPI: MADT (v001 DELL    FX09    0x42302e31 AWRD 0x00000000) @ 0x7fee7300
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20041203) @ 0x7fee7ca0
[    0.000000] ACPI: DSDT (v001 DELL   AWRDACPI 0x00001000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] Detected 1795.598 MHz processor.
[   16.253172] Built 1 zonelists.  Total pages: 519827
[   16.253175] Kernel command line: root=UUID=e2f75ab5-0639-4cee-a487-e04bb4bcaf90 ro 
[   16.253293] mapped APIC to ffffd000 (fee00000)
[   16.253295] mapped IOAPIC to ffffc000 (fec00000)
[   16.253298] Enabling fast FPU save and restore... done.
[   16.253300] Enabling unmasked SIMD FPU exception support... done.
[   16.253306] Initializing CPU#0
[   16.253353] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   16.255390] Console: colour VGA+ 80x25
[   16.259013] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.259321] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.336737] Memory: 2066644k/2095680k available (1993k kernel code, 27684k reserved, 900k data, 328k init, 1178176k highmem)
[   16.336808] virtual kernel memory layout:
[   16.336809]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   16.336810]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.336811]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.336812]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.336813]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   16.336814]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   16.336815]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   16.337191] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.337412] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   16.337634] hpet0: 4 64-bit timers, 14318180 Hz
[   16.339239] Using HPET for base-timer
[   16.417371] Calibrating delay using timer specific routine.. 3593.88 BogoMIPS (lpj=7187777)
[   16.417500] Security Framework v1.0.0 initialized
[   16.417552] SELinux:  Disabled at boot.
[   16.418186] Mount-cache hash table entries: 512
[   16.418354] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   16.418361] monitor/mwait feature present.
[   16.418409] using mwait in idle threads.
[   16.418458] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.418541] CPU: L2 cache: 2048K
[   16.418588] CPU: Physical Processor ID: 0
[   16.418634] CPU: Processor Core ID: 0
[   16.418681] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   16.418689] Compat vDSO mapped to ffffe000.
[   16.418738] Remapping vsyscall page to ffffe000
[   16.418796] Checking 'hlt' instruction... OK.
[   16.433523] SMP alternatives: switching to UP code
[   16.434463] Early unpacking initramfs... done
[   16.778297] ACPI: Core revision 20060707
[   16.798565] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.934350] CPU0: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
[   16.934481] SMP alternatives: switching to SMP code
[   16.934589] Booting processor 1/1 eip 3000
[   20.192911] Initializing CPU#1
[   20.271260] Calibrating delay using timer specific routine.. 3591.09 BogoMIPS (lpj=7182184)
[   20.271266] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   20.271270] monitor/mwait feature present.
[   20.271273] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.271275] CPU: L2 cache: 2048K
[   20.271276] CPU: Physical Processor ID: 0
[   20.271278] CPU: Processor Core ID: 1
[   20.271279] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   20.272235] CPU1: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
[   20.272695] Total of 2 processors activated (7184.98 BogoMIPS).
[   20.272885] ENABLING IO-APIC IRQs
[   20.273099] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.419178] checking TSC synchronization across 2 CPUs: passed.
[    0.003962] Brought up 2 CPUs
[    0.163417] migration_cost=604
[    0.163771] Booting paravirtualized kernel on bare hardware
[    0.163890] Time: 16:11:10  Date: 08/02/107
[    0.163960] NET: Registered protocol family 16
[    0.164655] EISA bus registered
[    0.164704] ACPI: bus type pci registered
[    0.204018] PCI: PCI BIOS revision 3.00 entry at 0xfb920, last bus=2
[    0.204648] PCI: Using configuration type 1
[    0.204695] Setting up standard PCI resources
[    0.229968] ACPI: Interpreter enabled
[    0.230016] ACPI: Using IOAPIC for interrupt routing
[    0.230612] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.230664] PCI: Probing PCI hardware (bus 00)
[    0.231685] Boot video device is 0000:01:00.0
[    0.231792] PCI: Transparent bridge - 0000:00:1e.0
[    0.231875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.251723] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.254674] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.255364] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.256711] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.257398] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.258087] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.258772] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.259457] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.260733] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.261424] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.261479] pnp: PnP ACPI init
[    0.263489] pnp: PnP ACPI: found 12 devices
[    0.263538] PnPBIOS: Disabled by ACPI PNP
[    0.263619] PCI: Using ACPI for IRQ routing
[    0.263666] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.282342] NET: Registered protocol family 8
[    0.282390] NET: Registered protocol family 20
[    0.282689] pnp: 00:08: ioport range 0x400-0x4bf could not be reserved
[    0.282987] PCI: Bridge: 0000:00:01.0
[    0.283035]   IO window: c000-cfff
[    0.283083]   MEM window: f8000000-fbffffff
[    0.283131]   PREFETCH window: d0000000-dfffffff
[    0.283180] PCI: Bridge: 0000:00:1e.0
[    0.283227]   IO window: d000-dfff
[    0.283276]   MEM window: fde00000-fdefffff
[    0.283325]   PREFETCH window: fdd00000-fddfffff
[    0.283384] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.283478] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.283488] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.283511] NET: Registered protocol family 2
[    0.332591] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.332729] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.333185] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.333431] TCP: Hash tables configured (established 131072 bind 65536)
[    0.333481] TCP reno registered
[    0.348699] checking if image is initramfs... it is
[    1.025762] Freeing initrd memory: 6746k freed
[    1.026366] audit: initializing netlink socket (disabled)
[    1.026426] audit(1188749469.748:1): initialized
[    1.026556] highmem bounce pool size: 64 pages
[    1.026674] VFS: Disk quotas dquot_6.5.1
[    1.026736] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.026826] io scheduler noop registered
[    1.026906] io scheduler anticipatory registered
[    1.026987] io scheduler deadline registered
[    1.027076] io scheduler cfq registered (default)
[    1.027424] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.027459] assign_interrupt_mode Found MSI capability
[    1.027507] Allocate Port Service[0000:00:01.0:pcie00]
[    1.027645] isapnp: Scanning for PnP cards...
[    1.380546] isapnp: No Plug & Play device found
[    1.399574] Real Time Clock Driver v1.12ac
[    1.399936] hpet_resources: 0xfed00000 is busy
[    1.399953] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.400545] mice: PS/2 mouse device common for all mice
[    1.401069] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.401255] input: Macintosh mouse button emulation as /class/input/input0
[    1.401335] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.401385] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.401656] PNP: No PS/2 controller found. Probing ports directly.
[    1.402061] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.402115] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.403189] EISA: Probing bus 0 at eisa.0
[    1.403263] EISA: Detected 0 cards.
[    1.433370] TCP cubic registered
[    1.433423] NET: Registered protocol family 1
[    1.433486] Starting balanced_irq
[    1.433541] Using IPI No-Shortcut mode
[    1.433659] ACPI: (supports S0 S3 S4 S5)
[    1.433911]   Magic number: 7:480:185
[    1.434164] Freeing unused kernel memory: 328k freed
[    1.435175] Time: tsc clocksource has been installed.
[    1.528844] SCSI subsystem initialized
[    1.533038] libata version 2.20 loaded.
[    1.534241] ata_piix 0000:00:1f.2: version 2.10ac1
[    1.534246] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.534485] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 17
[    1.534589] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    1.534622] ata1: SATA max UDMA/133 cmd 0x0001f800 ctl 0x0001f702 bmdma 0x0001f400 irq 17
[    1.534701] ata2: SATA max UDMA/133 cmd 0x0001f600 ctl 0x0001f502 bmdma 0x0001f408 irq 17
[    1.534768] scsi0 : ata_piix
[    1.697294] ata1.00: ata_hpa_resize 1: sectors = 312500000, hpa_sectors = 312500000
[    1.697360] ata1.00: ATA-7: SAMSUNG HD161HJ, JF100-15, max UDMA7
[    1.697412] ata1.00: 312500000 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.705384] ata1.00: ata_hpa_resize 1: sectors = 312500000, hpa_sectors = 312500000
[    1.705450] ata1.00: configured for UDMA/133
[    1.705504] scsi1 : ata_piix
[    2.181057] ata2.00: ATAPI, max UDMA/100
[    2.346542] ata2.00: configured for UDMA/100
[    2.346683] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD161HJ  JF10 PQ: 0 ANSI: 5
[    2.348832] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-H31N B109 PQ: 0 ANSI: 5
[    2.349246] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[    2.349475] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 17
[    2.349576] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    2.349595] ata3: SATA max UDMA/133 cmd 0x0001f100 ctl 0x0001f002 bmdma 0x0001ed00 irq 17
[    2.349674] ata4: SATA max UDMA/133 cmd 0x0001ef00 ctl 0x0001ee02 bmdma 0x0001ed08 irq 17
[    2.349737] scsi2 : ata_piix
[    2.513871] ATA: abnormal status 0x7F on port 0x0001f107
[    2.513927] scsi3 : ata_piix
[    2.679374] ATA: abnormal status 0x7F on port 0x0001ef07
[    2.769278] Capability LSM initialized
[    2.802414] ACPI: Fan [FAN] (on)
[    2.806212] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.806616] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.806783] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.806915] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.808073] ACPI: Thermal Zone [THRM] (40 C)
[    3.197510] usbcore: registered new interface driver usbfs
[    3.197583] usbcore: registered new interface driver hub
[    3.197656] usbcore: registered new device driver usb
[    3.218437] USB Universal Host Controller Interface driver v3.0
[    3.218529] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.218633] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    3.218637] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.218779] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.218863] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fe00
[    3.219004] usb usb1: configuration #1 chosen from 1 choice
[    3.219077] hub 1-0:1.0: USB hub found
[    3.219128] hub 1-0:1.0: 2 ports detected
[    3.234917] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[    3.234985] sda: Write Protect is off
[    3.235033] sda: Mode Sense: 00 3a 00 00
[    3.235046] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.235144] SCSI device sda: 312500000 512-byte hdwr sectors (160000 MB)
[    3.235201] sda: Write Protect is off
[    3.235249] sda: Mode Sense: 00 3a 00 00
[    3.235262] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.235324]  sda: sda1 sda2 sda3 sda4 < sda5<6>FDC 0 is a post-1991 82077
[    3.259319]  sda6 >
[    3.259588] sd 0:0:0:0: Attached scsi disk sda
[    3.263017] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.263083] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.270745] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.270799] Uniform CD-ROM driver Revision: 3.20
[    3.271001] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.325988] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[    3.326091] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    3.326095] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.326260] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.326344] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000fd00
[    3.326767] usb usb2: configuration #1 chosen from 1 choice
[    3.326949] hub 2-0:1.0: USB hub found
[    3.326999] hub 2-0:1.0: 2 ports detected
[    3.430498] ACPI: PCI Interrupt 0000:00:1a.2[D] -> GSI 19 (level, low) -> IRQ 17
[    3.430612] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[    3.430617] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.430698] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    3.430793] uhci_hcd 0000:00:1a.2: irq 17, io base 0x0000fc00
[    3.430915] usb usb3: configuration #1 chosen from 1 choice
[    3.430984] hub 3-0:1.0: USB hub found
[    3.431034] hub 3-0:1.0: 2 ports detected
[    3.475438] Attempting manual resume
[    3.475486] swsusp: Resume From Partition 8:5
[    3.475488] PM: Checking swsusp image.
[    3.475632] PM: Resume from disk failed.
[    3.536615] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.536719] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.536722] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.536790] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    3.536873] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000fb00
[    3.537002] usb usb4: configuration #1 chosen from 1 choice
[    3.537077] hub 4-0:1.0: USB hub found
[    3.537127] hub 4-0:1.0: 2 ports detected
[    3.566336] kjournald starting.  Commit interval 5 seconds
[    3.566396] EXT3-fs: mounted filesystem with ordered data mode.
[    3.641939] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[    3.642060] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.642064] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.642131] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    3.642210] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000fa00
[    3.642336] usb usb5: configuration #1 chosen from 1 choice
[    3.642405] hub 5-0:1.0: USB hub found
[    3.642454] hub 5-0:1.0: 2 ports detected
[    3.746702] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
[    3.746822] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.746826] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.746893] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    3.746977] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    3.746985] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfdffe000
[    3.750912] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.751032] usb usb6: configuration #1 chosen from 1 choice
[    3.751100] hub 6-0:1.0: USB hub found
[    3.751150] hub 6-0:1.0: 6 ports detected
[    3.774906] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.856223] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.856331] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.856336] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.856415] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.856498] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.856503] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfdffd000
[    3.860443] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.860610] usb usb7: configuration #1 chosen from 1 choice
[    3.860678] hub 7-0:1.0: USB hub found
[    3.860728] hub 7-0:1.0: 6 ports detected
[    3.965431] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[    3.965555] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.965558] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.965633] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.965715] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000f900
[    3.965838] usb usb8: configuration #1 chosen from 1 choice
[    3.965907] hub 8-0:1.0: USB hub found
[    3.965957] hub 8-0:1.0: 2 ports detected
[    4.579240] usb 7-5: new high speed USB device using ehci_hcd and address 2
[    4.790429] usb 7-5: configuration #1 chosen from 1 choice
[    5.161561] usb 3-1: new low speed USB device using uhci_hcd and address 3
[    5.331922] usb 3-1: configuration #1 chosen from 1 choice
[    5.574302] usb 3-2: new low speed USB device using uhci_hcd and address 4
[    5.754663] usb 3-2: configuration #1 chosen from 1 choice
[   10.683997] Linux agpgart interface v0.102 (c) Dave Jones
[   10.685871] agpgart: Detected an Intel G33 Chipset.
[   10.700355] agpgart: AGP aperture is 256M @ 0x0
[   10.736809] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.738490] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.911886] Intel(R) PRO/1000 Network Driver - version 7.5.5.1-NAPI
[   10.911939] Copyright (c) 1999-2007 Intel Corporation.
[   10.912033] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 21
[   10.912134] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   10.958988] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1a:a0:89:e6:cd
[   10.999946] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   11.066374] input: PC Speaker as /class/input/input1
[   11.184205] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[   11.358917] usbcore: registered new interface driver hiddev
[   11.471953] input: USB Optical Mouse as /class/input/input2
[   11.472057] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.2-1
[   11.542017] input: Dell Dell USB Keyboard as /class/input/input3
[   11.542121] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.2-2
[   11.542261] usbcore: registered new interface driver usbhid
[   11.542263] usbcore: registered new interface driver libusual
[   11.542360] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   11.562515] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   11.562625] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   11.574271] Initializing USB Mass Storage driver...
[   11.576922] scsi4 : SCSI emulation for USB Mass Storage devices
[   11.577029] usb-storage: device found at 2
[   11.577031] usb-storage: waiting for device to settle before scanning
[   11.577035] usbcore: registered new interface driver usb-storage
[   11.577089] USB Mass Storage support registered.
[   11.773511] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.073005] lp: driver loaded but no devices found
[   12.108247] Adding 2586424k swap on /dev/disk/by-uuid/51e695ac-1e99-4c7e-8fce-5ad234a5cffa.  Priority:-1 extents:1 across:2586424k
[   12.222267] EXT3 FS on sda6, internal journal
[   12.347573] kjournald starting.  Commit interval 5 seconds
[   12.347584] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   12.347761] EXT3 FS on sda3, internal journal
[   12.347765] EXT3-fs: mounted filesystem with ordered data mode.
[   12.385131] NET: Registered protocol family 17
[   12.673335] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   12.673340] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO

---

