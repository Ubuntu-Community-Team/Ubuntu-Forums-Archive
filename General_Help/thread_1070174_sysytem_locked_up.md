---
title: "sysytem locked up"
date: 2009-02-14
forum: General Help
---

### Post by unix1adm on 2009-02-14
Ok several time now I have seen some strangeness with Ubuntu

I was in Mozilla reading  a forum and the system just locked up witha blinking A., The one that indicates caps lock was just blinking and the mouse would not move. I had to power off the system. 

Also I noticed that If I leave it for a while from time to time it is like there is a process taking up the cpu and wont release it. It takes for ever to do anything and the shutdown command takes for ever to come up. I endup powering off with the button. 

Any ideas?

---

### Post by unix1adm on 2009-02-14
Not sure if this will help log file info


Feb 14 19:56:56 cj454-lt syslogd 1.5.0#2ubuntu6: restart.
Feb 14 19:56:56 cj454-lt kernel: Inspecting /boot/System.map-2.6.27-7-generic
Feb 14 19:56:56 cj454-lt kernel: Cannot find map file.
Feb 14 19:56:56 cj454-lt kernel: Loaded 51808 symbols from 98 modules.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff60000 (usable)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff77000 (ACPI data)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 000000005ff77000 - 000000005ff79000 (ACPI NVS)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 000000005ff80000 - 0000000060000000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] last_pfn = 0x5ff60 max_arch_pfn = 0x100000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] RAMDISK: 3781e000 - 37fef98a
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] DMI present.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: RSDP 000F6DF0, 0024 (r2 IBM   )
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: XSDT 5FF6A6CD, 004C (r1 IBM    TP-1R        3150  LTP        0)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: FACP 5FF6A800, 00F4 (r3 IBM    TP-1R        3150 IBM         1)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080609]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: DSDT 5FF6A9E7, C4D5 (r1 IBM    TP-1R        3150 MSFT  100000E)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: FACS 5FF78000, 0040
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: SSDT 5FF6A9B4, 0033 (r1 IBM    TP-1R        3150 MSFT  100000E)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: ECDT 5FF76EBC, 0052 (r1 IBM    TP-1R        3150 IBM         1)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: TCPA 5FF76F0E, 0032 (r1 IBM    TP-1R        3150 PTL         1)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: BOOT 5FF76FD8, 0028 (r1 IBM    TP-1R        3150  LTP        1)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] 639MB HIGHMEM available.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] 896MB LOWMEM available.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   mapped low ram: 0 - 38000000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   low ram: 00000000 - 38000000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   bootmap 00008000 - 0000f000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #4 [003781e000 - 0037fef98a]          RAMDISK ==> [003781e000 - 0037fef98a]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Zone PFN ranges:
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   HighMem  0x00038000 -> 0x0005ff60
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Movable zone start PFN for each node
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]     0: 0x00000100 -> 0x0005ff60
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9f800000)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389504
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Kernel command line: root=UUID=befc8a95-e59a-4adc-aab0-2c5c3b6dacbd ro quiet splash 
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Initializing CPU#0
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Extended CMOS year: 2000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] TSC: using PMTIMER calibration value
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Detected 1598.640 MHz processor.
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Console: colour VGA+ 80x25
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] console [tty0] enabled
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Memory: 1543388k/1572224k available (2572k kernel code, 27612k reserved, 1160k data, 424k init, 654720k highmem)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] virtual kernel memory layout:
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Feb 14 19:56:56 cj454-lt kernel: [    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 3197.28 BogoMIPS (lpj=6394560)
Feb 14 19:56:56 cj454-lt kernel: [    0.004052] Security Framework initialized
Feb 14 19:56:56 cj454-lt kernel: [    0.004069] SELinux:  Disabled at boot.
Feb 14 19:56:56 cj454-lt kernel: [    0.004103] AppArmor: AppArmor initialized
Feb 14 19:56:56 cj454-lt kernel: [    0.004116] Mount-cache hash table entries: 512
Feb 14 19:56:56 cj454-lt kernel: [    0.004358] Initializing cgroup subsys ns
Feb 14 19:56:56 cj454-lt kernel: [    0.004367] Initializing cgroup subsys cpuacct
Feb 14 19:56:56 cj454-lt kernel: [    0.004370] Initializing cgroup subsys memory
Feb 14 19:56:56 cj454-lt kernel: [    0.004393] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 14 19:56:56 cj454-lt kernel: [    0.004396] CPU: L2 cache: 2048K
Feb 14 19:56:56 cj454-lt kernel: [    0.004419] Checking 'hlt' instruction... OK.
Feb 14 19:56:56 cj454-lt kernel: [    0.020584] SMP alternatives: switching to UP code
Feb 14 19:56:56 cj454-lt kernel: [    0.027025] Freeing SMP alternatives: 11k freed
Feb 14 19:56:56 cj454-lt kernel: [    0.027029] ACPI: Core revision 20080609
Feb 14 19:56:56 cj454-lt kernel: [    0.032608] ACPI: Checking initramfs for custom DSDT
Feb 14 19:56:56 cj454-lt kernel: [    0.460323] ACPI: setting ELCR to 0200 (from 0800)
Feb 14 19:56:56 cj454-lt kernel: [    0.464085] weird, boot CPU (#0) not listedby the BIOS.
Feb 14 19:56:56 cj454-lt kernel: [    0.464089] SMP motherboard not detected.
Feb 14 19:56:56 cj454-lt kernel: [    0.464092] Local APIC not detected. Using dummy APIC emulation.
Feb 14 19:56:56 cj454-lt kernel: [    0.464095] SMP disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.464168] Brought up 1 CPUs
Feb 14 19:56:56 cj454-lt kernel: [    0.464171] Total of 1 processors activated (3197.28 BogoMIPS).
Feb 14 19:56:56 cj454-lt kernel: [    0.464469] net_namespace: 840 bytes
Feb 14 19:56:56 cj454-lt kernel: [    0.464478] Booting paravirtualized kernel on bare hardware
Feb 14 19:56:56 cj454-lt kernel: [    0.464699] Time:  0:56:28  Date: 02/15/09
Feb 14 19:56:56 cj454-lt kernel: [    0.464731] NET: Registered protocol family 16
Feb 14 19:56:56 cj454-lt kernel: [    0.465081] EISA bus registered
Feb 14 19:56:56 cj454-lt kernel: [    0.465098] ACPI: bus type pci registered
Feb 14 19:56:56 cj454-lt kernel: [    0.468126] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=5
Feb 14 19:56:56 cj454-lt kernel: [    0.468129] PCI: Using configuration type 1 for base access
Feb 14 19:56:56 cj454-lt kernel: [    0.470646] ACPI: EC: EC description table is found, configuring boot EC
Feb 14 19:56:56 cj454-lt kernel: [    0.480632] ACPI: EC: non-query interrupt received, switching to interrupt mode
Feb 14 19:56:56 cj454-lt kernel: [    0.501900] ACPI: Interpreter enabled
Feb 14 19:56:56 cj454-lt kernel: [    0.501904] ACPI: (supports S0 S3 S4 S5)
Feb 14 19:56:56 cj454-lt kernel: [    0.501923] ACPI: Using PIC for interrupt routing
Feb 14 19:56:56 cj454-lt kernel: [    0.517218] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Feb 14 19:56:56 cj454-lt kernel: [    0.517221] ACPI: EC: driver started in interrupt mode
Feb 14 19:56:56 cj454-lt kernel: [    0.517286] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 14 19:56:56 cj454-lt kernel: [    0.517682] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.517687] pci 0000:00:1d.7: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.517761] HPET not enabled in BIOS. You might try hpet=force boot option
Feb 14 19:56:56 cj454-lt kernel: [    0.517769] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Feb 14 19:56:56 cj454-lt kernel: [    0.517774] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
Feb 14 19:56:56 cj454-lt kernel: [    0.517969] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.517974] pci 0000:00:1f.5: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.518041] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.518046] pci 0000:00:1f.6: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.518215] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.518220] pci 0000:02:00.0: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.518372] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.518377] pci 0000:02:08.0: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.518404] pci 0000:00:1e.0: transparent bridge
Feb 14 19:56:56 cj454-lt kernel: [    0.524560] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.524845] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.525126] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.525407] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.525687] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.525946] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Feb 14 19:56:56 cj454-lt kernel: [    0.526205] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Feb 14 19:56:56 cj454-lt kernel: [    0.526492] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.526684] ACPI: Power Resource [PUBS] (on)
Feb 14 19:56:56 cj454-lt kernel: [    0.526684] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 14 19:56:56 cj454-lt kernel: [    0.526684] pnp: PnP ACPI init
Feb 14 19:56:56 cj454-lt kernel: [    0.526684] ACPI: bus type pnp registered
Feb 14 19:56:56 cj454-lt kernel: [    0.532522] pnp: PnP ACPI: found 13 devices
Feb 14 19:56:56 cj454-lt kernel: [    0.532525] ACPI: ACPI bus type pnp unregistered
Feb 14 19:56:56 cj454-lt kernel: [    0.532528] PnPBIOS: Disabled by ACPI PNP
Feb 14 19:56:56 cj454-lt kernel: [    0.532931] PCI: Using ACPI for IRQ routing
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NET: Registered protocol family 8
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NET: Registered protocol family 20
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NetLabel: Initializing
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NetLabel:  domain hash size = 128
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NetLabel:  unlabeled traffic allowed by default
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] tracer: 772 pages allocated for 65536 entries of 48 bytes
Feb 14 19:56:56 cj454-lt kernel: [    0.533052]    actual entries 65620
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] AppArmor: AppArmor Filesystem Enabled
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] ACPI: RTC can wake from S4
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xec000-0xeffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0x100000-0x5fffffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1000-0x107f has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1180-0x11bf has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x15e0-0x15ef has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1600-0x162f has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1632-0x167f has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1630-0x1631 has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.568862] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Feb 14 19:56:56 cj454-lt kernel: [    0.568866] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
Feb 14 19:56:56 cj454-lt kernel: [    0.568871] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568875] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000e7ffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568884] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
Feb 14 19:56:56 cj454-lt kernel: [    0.568887] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
Feb 14 19:56:56 cj454-lt kernel: [    0.568892] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
Feb 14 19:56:56 cj454-lt kernel: [    0.568897] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568902] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568907] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Feb 14 19:56:56 cj454-lt kernel: [    0.568911] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
Feb 14 19:56:56 cj454-lt kernel: [    0.568917] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568922] pci 0000:00:1e.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.569462] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    0.569471] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    0.569478] bus: 00 index 0 io port: [0, ffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569480] bus: 00 index 1 mmio: [0, ffffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569483] bus: 01 index 0 io port: [3000, 3fff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569486] bus: 01 index 1 mmio: [c0100000, c01fffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569489] bus: 01 index 2 mmio: [e0000000, e7ffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569491] bus: 01 index 3 mmio: [0, 0]
Feb 14 19:56:56 cj454-lt kernel: [    0.569494] bus: 02 index 0 io port: [4000, 8fff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569497] bus: 02 index 1 mmio: [c0200000, cfffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569500] bus: 02 index 2 mmio: [e8000000, efffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569502] bus: 02 index 3 io port: [0, ffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569505] bus: 02 index 4 mmio: [0, ffffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569507] bus: 03 index 0 io port: [4000, 40ff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569510] bus: 03 index 1 io port: [4400, 44ff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569513] bus: 03 index 2 mmio: [e8000000, ebffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569516] bus: 03 index 3 mmio: [c4000000, c7ffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569526] NET: Registered protocol family 2
Feb 14 19:56:56 cj454-lt kernel: [    0.569674] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.569965] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.570890] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.571539] TCP: Hash tables configured (established 131072 bind 65536)
Feb 14 19:56:56 cj454-lt kernel: [    0.571544] TCP reno registered
Feb 14 19:56:56 cj454-lt kernel: [    0.571716] NET: Registered protocol family 1
Feb 14 19:56:56 cj454-lt kernel: [    0.571874] checking if image is initramfs... it is
Feb 14 19:56:56 cj454-lt kernel: [    1.438205] Freeing initrd memory: 8006k freed
Feb 14 19:56:56 cj454-lt kernel: [    1.438507] Simple Boot Flag at 0x35 set to 0x1
Feb 14 19:56:56 cj454-lt kernel: [    1.439022] audit: initializing netlink socket (disabled)
Feb 14 19:56:56 cj454-lt kernel: [    1.439046] type=2000 audit(1234659388.436:1): initialized
Feb 14 19:56:56 cj454-lt kernel: [    1.446851] highmem bounce pool size: 64 pages
Feb 14 19:56:56 cj454-lt kernel: [    1.446861] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Feb 14 19:56:56 cj454-lt kernel: [    1.449750] VFS: Disk quotas dquot_6.5.1
Feb 14 19:56:56 cj454-lt kernel: [    1.449861] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    1.450001] msgmni has been set to 1752
Feb 14 19:56:56 cj454-lt kernel: [    1.450159] io scheduler noop registered
Feb 14 19:56:56 cj454-lt kernel: [    1.450162] io scheduler anticipatory registered
Feb 14 19:56:56 cj454-lt kernel: [    1.450165] io scheduler deadline registered
Feb 14 19:56:56 cj454-lt kernel: [    1.450180] io scheduler cfq registered (default)
Feb 14 19:56:56 cj454-lt kernel: [    1.450286] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
Feb 14 19:56:56 cj454-lt kernel: [    1.450687] isapnp: Scanning for PnP cards...
Feb 14 19:56:56 cj454-lt kernel: [    1.803665] isapnp: No Plug & Play device found
Feb 14 19:56:56 cj454-lt kernel: [    1.845937] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Feb 14 19:56:56 cj454-lt kernel: [    1.847282] serial 00:0a: activated
Feb 14 19:56:56 cj454-lt kernel: [    1.847542] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Feb 14 19:56:56 cj454-lt kernel: [    1.848280] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    1.848285] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    1.848294] serial 0000:00:1f.6: PCI INT B disabled
Feb 14 19:56:56 cj454-lt kernel: [    1.850193] brd: module loaded
Feb 14 19:56:56 cj454-lt kernel: [    1.850286] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Feb 14 19:56:56 cj454-lt kernel: [    1.850436] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Feb 14 19:56:56 cj454-lt kernel: [    1.856380] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 14 19:56:56 cj454-lt kernel: [    1.856394] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 14 19:56:56 cj454-lt kernel: [    1.856804] mice: PS/2 mouse device common for all mice
Feb 14 19:56:56 cj454-lt kernel: [    1.856973] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Feb 14 19:56:56 cj454-lt kernel: [    1.856990] rtc0: alarms up to one month, y3k
Feb 14 19:56:56 cj454-lt kernel: [    1.857131] EISA: Probing bus 0 at eisa.0
Feb 14 19:56:56 cj454-lt kernel: [    1.857138] Cannot allocate resource for EISA slot 1
Feb 14 19:56:56 cj454-lt kernel: [    1.857142] Cannot allocate resource for EISA slot 2
Feb 14 19:56:56 cj454-lt kernel: [    1.857145] Cannot allocate resource for EISA slot 3
Feb 14 19:56:56 cj454-lt kernel: [    1.857148] Cannot allocate resource for EISA slot 4
Feb 14 19:56:56 cj454-lt kernel: [    1.857151] Cannot allocate resource for EISA slot 5
Feb 14 19:56:56 cj454-lt kernel: [    1.857153] Cannot allocate resource for EISA slot 6
Feb 14 19:56:56 cj454-lt kernel: [    1.857156] Cannot allocate resource for EISA slot 7
Feb 14 19:56:56 cj454-lt kernel: [    1.857159] Cannot allocate resource for EISA slot 8
Feb 14 19:56:56 cj454-lt kernel: [    1.857161] EISA: Detected 0 cards.
Feb 14 19:56:56 cj454-lt kernel: [    1.857166] cpuidle: using governor ladder
Feb 14 19:56:56 cj454-lt kernel: [    1.857169] cpuidle: using governor menu
Feb 14 19:56:56 cj454-lt kernel: [    1.857810] TCP cubic registered
Feb 14 19:56:56 cj454-lt kernel: [    1.857843] Using IPI No-Shortcut mode
Feb 14 19:56:56 cj454-lt kernel: [    1.858070] registered taskstats version 1
Feb 14 19:56:56 cj454-lt kernel: [    1.858196]   Magic number: 13:986:910
Feb 14 19:56:56 cj454-lt kernel: [    1.858265] tty ptyz6: hash matches
Feb 14 19:56:56 cj454-lt kernel: [    1.858355] rtc_cmos 00:06: setting system clock to 2009-02-15 00:56:29 UTC (1234659389)
Feb 14 19:56:56 cj454-lt kernel: [    1.858360] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 14 19:56:56 cj454-lt kernel: [    1.858362] EDD information not available.
Feb 14 19:56:56 cj454-lt kernel: [    1.858693] Freeing unused kernel memory: 424k freed
Feb 14 19:56:56 cj454-lt kernel: [    1.858751] Write protecting the kernel text: 2576k
Feb 14 19:56:56 cj454-lt kernel: [    1.858784] Write protecting the kernel read-only data: 936k
Feb 14 19:56:56 cj454-lt kernel: [    1.861744] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Feb 14 19:56:56 cj454-lt kernel: [    2.099619] fuse init (API version 7.9)
Feb 14 19:56:56 cj454-lt kernel: [    2.335428] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Feb 14 19:56:56 cj454-lt kernel: [    2.340456] processor ACPI0007:00: registered as cooling_device0
Feb 14 19:56:56 cj454-lt kernel: [    2.340461] ACPI: Processor [CPU] (supports 8 throttling states)
Feb 14 19:56:56 cj454-lt kernel: [    2.369300] thermal LNXTHERM:01: registered as thermal_zone0
Feb 14 19:56:56 cj454-lt kernel: [    2.370993] ACPI: Thermal Zone [THM0] (68 C)
Feb 14 19:56:56 cj454-lt kernel: [    3.259005] ACPI: ACPI Dock Station Driver
Feb 14 19:56:56 cj454-lt kernel: [    3.413285] usbcore: registered new interface driver usbfs
Feb 14 19:56:56 cj454-lt kernel: [    3.413319] usbcore: registered new interface driver hub
Feb 14 19:56:56 cj454-lt kernel: [    3.413371] usbcore: registered new device driver usb
Feb 14 19:56:56 cj454-lt kernel: [    3.416512] USB Universal Host Controller Interface driver v3.0
Feb 14 19:56:56 cj454-lt kernel: [    3.420189] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Feb 14 19:56:56 cj454-lt kernel: [    3.420202] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.420218] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [    3.420272] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Feb 14 19:56:56 cj454-lt kernel: [    3.420299] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
Feb 14 19:56:56 cj454-lt kernel: [    3.420523] usb usb1: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [    3.420557] hub 1-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [    3.420565] hub 1-0:1.0: 2 ports detected
Feb 14 19:56:56 cj454-lt kernel: [    3.515062] SCSI subsystem initialized
Feb 14 19:56:56 cj454-lt kernel: [    3.518335] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Feb 14 19:56:56 cj454-lt kernel: [    3.518338] e100: Copyright(c) 1999-2006 Intel Corporation
Feb 14 19:56:56 cj454-lt kernel: [    3.541468] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Feb 14 19:56:56 cj454-lt kernel: [    3.541976] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.541981] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.541997] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [    3.542028] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Feb 14 19:56:56 cj454-lt kernel: [    3.542055] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
Feb 14 19:56:56 cj454-lt kernel: [    3.542173] usb usb2: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [    3.542206] hub 2-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [    3.542214] hub 2-0:1.0: 2 ports detected
Feb 14 19:56:56 cj454-lt kernel: [    3.644982] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.644988] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.645004] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [    3.645043] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Feb 14 19:56:56 cj454-lt kernel: [    3.645070] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
Feb 14 19:56:56 cj454-lt kernel: [    3.645181] usb usb3: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [    3.645213] hub 3-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [    3.645223] hub 3-0:1.0: 2 ports detected
Feb 14 19:56:56 cj454-lt kernel: [    3.749949] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Feb 14 19:56:56 cj454-lt kernel: [    3.750458] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.750463] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.750487] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [    3.750520] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Feb 14 19:56:56 cj454-lt kernel: [    3.754422] ehci_hcd 0000:00:1d.7: debug port 1
Feb 14 19:56:56 cj454-lt kernel: [    3.754440] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
Feb 14 19:56:56 cj454-lt kernel: [    3.768056] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb 14 19:56:56 cj454-lt kernel: [    3.768230] usb usb4: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [    3.768264] hub 4-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [    3.768274] hub 4-0:1.0: 6 ports detected
Feb 14 19:56:56 cj454-lt kernel: [    3.874082] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.874089] e100 0000:02:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.898295] e100 0000:02:08.0: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    3.899754] e100: eth0: e100_probe: addr 0xc0210000, irq 11, MAC addr 00:11:25:86:3d:04
Feb 14 19:56:56 cj454-lt kernel: [    3.903444] pata_acpi 0000:00:1f.1: enabling device (0005 -> 0007)
Feb 14 19:56:56 cj454-lt kernel: [    3.903453] pata_acpi 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.903507] pata_acpi 0000:00:1f.1: PCI INT A disabled
Feb 14 19:56:56 cj454-lt kernel: [    3.907860] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.909388] scsi0 : ata_piix
Feb 14 19:56:56 cj454-lt kernel: [    3.909824] scsi1 : ata_piix
Feb 14 19:56:56 cj454-lt kernel: [    3.911182] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
Feb 14 19:56:56 cj454-lt kernel: [    3.911186] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
Feb 14 19:56:56 cj454-lt kernel: [    4.124111] ata1.00: ATA-8: WDC WD2500BEVE-00WZT0, 01.01A01, max UDMA/100
Feb 14 19:56:56 cj454-lt kernel: [    4.124118] ata1.00: 488397168 sectors, multi 16: LBA48 
Feb 14 19:56:56 cj454-lt kernel: [    4.141057] ata1.00: configured for UDMA/100
Feb 14 19:56:56 cj454-lt kernel: [    4.264442] Marking TSC unstable due to TSC halts in idle
Feb 14 19:56:56 cj454-lt kernel: [    4.304344] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0202, max UDMA/33
Feb 14 19:56:56 cj454-lt kernel: [    4.320269] ata2.00: configured for UDMA/33
Feb 14 19:56:56 cj454-lt kernel: [    4.320419] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVE-0 01.0 PQ: 0 ANSI: 5
Feb 14 19:56:56 cj454-lt kernel: [    4.325625] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0202 PQ: 0 ANSI: 5
Feb 14 19:56:56 cj454-lt kernel: [    4.337939] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Feb 14 19:56:56 cj454-lt kernel: [    4.337982] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Feb 14 19:56:56 cj454-lt kernel: [    4.359351] Driver 'sd' needs updating - please use bus_type methods
Feb 14 19:56:56 cj454-lt kernel: [    4.359485] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Feb 14 19:56:56 cj454-lt kernel: [    4.359514] sd 0:0:0:0: [sda] Write Protect is off
Feb 14 19:56:56 cj454-lt kernel: [    4.359565] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 19:56:56 cj454-lt kernel: [    4.359662] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Feb 14 19:56:56 cj454-lt kernel: [    4.359688] sd 0:0:0:0: [sda] Write Protect is off
Feb 14 19:56:56 cj454-lt kernel: [    4.359740] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 19:56:56 cj454-lt kernel: [    4.359745]  sda: sda1 sda2 sda3 sda4
Feb 14 19:56:56 cj454-lt kernel: [    4.372378] Driver 'sr' needs updating - please use bus_type methods
Feb 14 19:56:56 cj454-lt kernel: [    4.398467] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 14 19:56:56 cj454-lt kernel: [    4.413851] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Feb 14 19:56:56 cj454-lt kernel: [    4.413856] Uniform CD-ROM driver Revision: 3.20
Feb 14 19:56:56 cj454-lt kernel: [    5.068116] Clocksource tsc unstable (delta = -93862065 ns)
Feb 14 19:56:56 cj454-lt kernel: [    9.850352] EXT3-fs: INFO: recovery required on readonly filesystem.
Feb 14 19:56:56 cj454-lt kernel: [    9.850356] EXT3-fs: write access will be enabled during recovery.
Feb 14 19:56:56 cj454-lt kernel: [   11.891062] kjournald starting.  Commit interval 5 seconds
Feb 14 19:56:56 cj454-lt kernel: [   11.891082] EXT3-fs: sda1: orphan cleanup on readonly fs
Feb 14 19:56:56 cj454-lt kernel: [   11.891134] EXT3-fs: sda1: 1 orphan inode deleted
Feb 14 19:56:56 cj454-lt kernel: [   11.891137] EXT3-fs: recovery complete.
Feb 14 19:56:56 cj454-lt kernel: [   11.894917] EXT3-fs: mounted filesystem with ordered data mode.
Feb 14 19:56:56 cj454-lt kernel: [   18.057184] udevd version 124 started
Feb 14 19:56:56 cj454-lt kernel: [   18.878114] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 14 19:56:56 cj454-lt kernel: [   18.966658] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 14 19:56:56 cj454-lt kernel: [   19.044922] Linux agpgart interface v0.103
Feb 14 19:56:56 cj454-lt kernel: [   19.113411] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
Feb 14 19:56:56 cj454-lt kernel: [   19.184337] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Feb 14 19:56:56 cj454-lt kernel: [   19.191969] iTCO_vendor_support: vendor-support=0
Feb 14 19:56:56 cj454-lt kernel: [   19.256278] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Feb 14 19:56:56 cj454-lt kernel: [   19.256442] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
Feb 14 19:56:56 cj454-lt kernel: [   19.256629] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Feb 14 19:56:56 cj454-lt kernel: [   19.333511] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Feb 14 19:56:56 cj454-lt kernel: [   19.345006] ACPI: Power Button (FF) [PWRF]
Feb 14 19:56:56 cj454-lt kernel: [   19.345151] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Feb 14 19:56:56 cj454-lt kernel: [   19.353040] ACPI: Lid Switch [LID]
Feb 14 19:56:56 cj454-lt kernel: [   19.353151] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
Feb 14 19:56:56 cj454-lt kernel: [   19.364050] ACPI: Sleep Button (CM) [SLPB]
Feb 14 19:56:56 cj454-lt kernel: [   19.513569] intel_rng: FWH not detected
Feb 14 19:56:56 cj454-lt kernel: [   20.396034] NET: Registered protocol family 23
Feb 14 19:56:56 cj454-lt kernel: [   20.476798] nsc-ircc 00:0c: activated
Feb 14 19:56:56 cj454-lt kernel: [   20.476985] nsc-ircc, chip->init
Feb 14 19:56:56 cj454-lt kernel: [   20.476994] nsc-ircc, Found chip at base=0x02e
Feb 14 19:56:56 cj454-lt kernel: [   20.477018] nsc-ircc, driver loaded (Dag Brattli)
Feb 14 19:56:56 cj454-lt kernel: [   20.477445] IrDA: Registered device irda0
Feb 14 19:56:56 cj454-lt kernel: [   20.477449] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Feb 14 19:56:56 cj454-lt kernel: [   20.606781] parport_pc 00:0b: reported by Plug and Play ACPI
Feb 14 19:56:56 cj454-lt kernel: [   20.606824] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Feb 14 19:56:56 cj454-lt kernel: [   20.738471] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input5
Feb 14 19:56:56 cj454-lt kernel: [   20.752070] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Feb 14 19:56:56 cj454-lt kernel: [   20.767396] ACPI: Error installing bay notify handler
Feb 14 19:56:56 cj454-lt kernel: [   21.042798] ath_hal: module license 'Proprietary' taints kernel.
Feb 14 19:56:56 cj454-lt kernel: [   21.126066] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Feb 14 19:56:56 cj454-lt kernel: [   21.304974] wlan: 0.9.4
Feb 14 19:56:56 cj454-lt kernel: [   21.415794] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
Feb 14 19:56:56 cj454-lt kernel: [   21.415814] Yenta: Using INTVAL to route CSC interrupts to PCI
Feb 14 19:56:56 cj454-lt kernel: [   21.415817] Yenta: Routing CardBus interrupts to PCI
Feb 14 19:56:56 cj454-lt kernel: [   21.415823] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
Feb 14 19:56:56 cj454-lt kernel: [   21.461570] ACPI: AC Adapter [AC] (on-line)
Feb 14 19:56:56 cj454-lt kernel: [   21.462390] ath_pci: 0.9.4
Feb 14 19:56:56 cj454-lt kernel: [   21.530497] ACPI: Battery Slot [BAT0] (battery present)
Feb 14 19:56:56 cj454-lt kernel: [   21.644615] Yenta: ISA IRQ mask 0x0430, PCI irq 11
Feb 14 19:56:56 cj454-lt kernel: [   21.644620] Socket status: 30000020
Feb 14 19:56:56 cj454-lt kernel: [   21.644625] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
Feb 14 19:56:56 cj454-lt kernel: [   21.644628] cs: IO port probe 0x4000-0x8fff: clean.
Feb 14 19:56:56 cj454-lt kernel: [   21.646029] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
Feb 14 19:56:56 cj454-lt kernel: [   21.646032] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
Feb 14 19:56:56 cj454-lt kernel: [   21.679302] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [   22.776053] pccard: CardBus card inserted into slot 0
Feb 14 19:56:56 cj454-lt kernel: [   22.776150] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
Feb 14 19:56:56 cj454-lt kernel: [   22.776156] pci 0000:03:00.0: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [   22.776243] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot
Feb 14 19:56:56 cj454-lt kernel: [   22.776248] pci 0000:03:00.1: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [   22.828960] input: PC Speaker as /devices/platform/pcspkr/input/input6
Feb 14 19:56:56 cj454-lt kernel: [   22.890117] ath_rate_sample: 1.2 (0.9.4)
Feb 14 19:56:56 cj454-lt kernel: [   22.890716] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Feb 14 19:56:56 cj454-lt kernel: [   22.890726] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Feb 14 19:56:56 cj454-lt kernel: [   22.890732] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Feb 14 19:56:56 cj454-lt kernel: [   22.890762] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Feb 14 19:56:56 cj454-lt kernel: [   22.890768] wifi0: mac 5.9 phy 4.3 radio 3.6
Feb 14 19:56:56 cj454-lt kernel: [   22.890773] wifi0: Use hw queue 1 for WME_AC_BE traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890776] wifi0: Use hw queue 0 for WME_AC_BK traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890778] wifi0: Use hw queue 2 for WME_AC_VI traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890781] wifi0: Use hw queue 3 for WME_AC_VO traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890783] wifi0: Use hw queue 8 for CAB traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890786] wifi0: Use hw queue 9 for beacons
Feb 14 19:56:56 cj454-lt kernel: [   22.898775] wifi0: Atheros 5212: mem=0xc0200000, irq=11
Feb 14 19:56:56 cj454-lt kernel: [   23.220390] Non-volatile memory driver v1.2
Feb 14 19:56:56 cj454-lt kernel: [   23.282122] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [   23.483084] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
Feb 14 19:56:56 cj454-lt kernel: [   23.483092] serio: Synaptics pass-through port at isa0060/serio1/input0
Feb 14 19:56:56 cj454-lt kernel: [   23.521410] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Feb 14 19:56:56 cj454-lt kernel: [   23.543425] thinkpad_acpi: ThinkPad ACPI Extras v0.21
Feb 14 19:56:56 cj454-lt kernel: [   23.543430] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Feb 14 19:56:56 cj454-lt kernel: [   23.543433] thinkpad_acpi: ThinkPad BIOS 1RETDJWW (3.15 ), EC 1RHT71WW-3.04
Feb 14 19:56:56 cj454-lt kernel: [   23.543436] thinkpad_acpi: IBM ThinkPad R51, model 1830WCW
Feb 14 19:56:56 cj454-lt kernel: [   23.548985] Registered led device: tpacpi::thinklight
Feb 14 19:56:56 cj454-lt kernel: [   23.549250] thinkpad_acpi: another device driver is already handling bay events
Feb 14 19:56:56 cj454-lt kernel: [   23.549254] thinkpad_acpi: disabling subdriver bay
Feb 14 19:56:56 cj454-lt kernel: [   23.549309] Registered led device: tpacpi::power
Feb 14 19:56:56 cj454-lt kernel: [   23.549349] Registered led device: tpacpi:orange:batt
Feb 14 19:56:56 cj454-lt kernel: [   23.549388] Registered led device: tpacpi:green:batt
Feb 14 19:56:56 cj454-lt kernel: [   23.549428] Registered led device: tpacpi::dock_active
Feb 14 19:56:56 cj454-lt kernel: [   23.549471] Registered led device: tpacpi::bay_active
Feb 14 19:56:56 cj454-lt kernel: [   23.549511] Registered led device: tpacpi::dock_batt
Feb 14 19:56:56 cj454-lt kernel: [   23.549550] Registered led device: tpacpi::unknown_led
Feb 14 19:56:56 cj454-lt kernel: [   23.549589] Registered led device: tpacpi::standby
Feb 14 19:56:56 cj454-lt kernel: [   23.552273] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
Feb 14 19:56:56 cj454-lt kernel: [   24.208058] intel8x0_measure_ac97_clock: measured 55450 usecs
Feb 14 19:56:56 cj454-lt kernel: [   24.208063] intel8x0: clocking to 48000
Feb 14 19:56:56 cj454-lt kernel: [   24.784042] ohci_hcd 0000:03:00.0: enabling device (0000 -> 0002)
Feb 14 19:56:56 cj454-lt kernel: [   24.784056] ohci_hcd 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [   24.784079] ohci_hcd 0000:03:00.0: OHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [   24.784185] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 5
Feb 14 19:56:56 cj454-lt kernel: [   24.784208] ohci_hcd 0000:03:00.0: irq 11, io mem 0xc4000000
Feb 14 19:56:56 cj454-lt kernel: [   24.918155] cs: IO port probe 0x100-0x3af: clean.
Feb 14 19:56:56 cj454-lt kernel: [   24.919152] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Feb 14 19:56:56 cj454-lt kernel: [   24.919597] cs: IO port probe 0x820-0x8ff: clean.
Feb 14 19:56:56 cj454-lt kernel: [   24.920000] cs: IO port probe 0xc00-0xcf7: clean.
Feb 14 19:56:56 cj454-lt kernel: [   24.920541] cs: IO port probe 0xa00-0xaff: clean.
Feb 14 19:56:56 cj454-lt kernel: [   24.930416] usb usb5: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [   24.930487] hub 5-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [   24.930501] hub 5-0:1.0: 1 port detected
Feb 14 19:56:56 cj454-lt kernel: [   25.032477] ohci_hcd 0000:03:00.1: enabling device (0000 -> 0002)
Feb 14 19:56:56 cj454-lt kernel: [   25.032492] ohci_hcd 0000:03:00.1: PCI INT B -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [   25.032515] ohci_hcd 0000:03:00.1: OHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [   25.032604] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 6
Feb 14 19:56:56 cj454-lt kernel: [   25.032627] ohci_hcd 0000:03:00.1: irq 11, io mem 0xc4001000
Feb 14 19:56:56 cj454-lt kernel: [   25.170420] usb usb6: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [   25.170506] hub 6-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [   25.170520] hub 6-0:1.0: 1 port detected
Feb 14 19:56:56 cj454-lt kernel: [   26.016528] lp0: using parport0 (interrupt-driven).
Feb 14 19:56:56 cj454-lt kernel: [   26.456863] EXT3 FS on sda1, internal journal
Feb 14 19:56:56 cj454-lt kernel: [   26.934941] type=1505 audit(1234659415.059:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3985
Feb 14 19:56:56 cj454-lt kernel: [   27.183837] type=1505 audit(1234659415.307:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3990
Feb 14 19:56:56 cj454-lt kernel: [   27.184277] type=1505 audit(1234659415.311:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3990
Feb 14 19:56:56 cj454-lt kernel: [   27.323681] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 14 19:56:56 cj454-lt kernel: [   27.489691] usb 5-1: new full speed USB device using ohci_hcd and address 2
Feb 14 19:56:56 cj454-lt kernel: [   27.709895] usb 5-1: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [   27.905808] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
Feb 14 19:56:56 cj454-lt kernel: [   27.910234] usbcore: registered new interface driver cdc_acm
Feb 14 19:56:56 cj454-lt kernel: [   27.910240] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Feb 14 19:56:56 cj454-lt kernel: [   27.932710] ACPI: WMI: Mapper loaded
Feb 14 19:56:56 cj454-lt kernel: [   27.994476] ACPI: Error installing bay notify handler
Feb 14 19:56:56 cj454-lt kernel: [   28.824077] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Feb 14 19:56:57 cj454-lt kernel: [   28.946366] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Feb 14 19:56:57 cj454-lt kernel: [   29.002505] IBM machine detected. Enabling interrupts during APM calls.
Feb 14 19:56:57 cj454-lt kernel: [   29.002515] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Feb 14 19:56:57 cj454-lt kernel: [   29.002519] apm: overridden by ACPI.
Feb 14 19:56:57 cj454-lt kernel: [   29.065959] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
Feb 14 19:56:57 cj454-lt kernel: [   29.203988] ppdev: user-space parallel port driver
Feb 14 19:57:00 cj454-lt kernel: [   32.425117] Bluetooth: Core ver 2.13
Feb 14 19:57:00 cj454-lt kernel: [   32.427911] NET: Registered protocol family 31
Feb 14 19:57:00 cj454-lt kernel: [   32.427921] Bluetooth: HCI device and connection manager initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.427926] Bluetooth: HCI socket layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.470088] Bluetooth: L2CAP ver 2.11
Feb 14 19:57:00 cj454-lt kernel: [   32.470099] Bluetooth: L2CAP socket layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.520897] Bluetooth: SCO (Voice Link) ver 0.6
Feb 14 19:57:00 cj454-lt kernel: [   32.520909] Bluetooth: SCO socket layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.556973] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 14 19:57:00 cj454-lt kernel: [   32.556984] Bluetooth: BNEP filters: protocol multicast
Feb 14 19:57:00 cj454-lt kernel: [   32.594350] Bridge firewalling registered
Feb 14 19:57:00 cj454-lt kernel: [   32.687017] Bluetooth: RFCOMM socket layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.687375] Bluetooth: RFCOMM TTY layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.687385] Bluetooth: RFCOMM ver 1.10
Feb 14 19:57:01 cj454-lt kernel: [   33.542868] pci 0000:01:00.0: power state changed by ACPI to D0
Feb 14 19:57:01 cj454-lt kernel: [   33.545010] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:57:02 cj454-lt kernel: [   34.088649] [drm] Initialized drm 1.1.0 20060810
Feb 14 19:57:02 cj454-lt kernel: [   34.168752] [drm] Initialized radeon 1.29.0 20080528 on minor 0
Feb 14 19:57:02 cj454-lt kernel: [   34.397794] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Feb 14 19:57:02 cj454-lt kernel: [   34.397827] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Feb 14 19:57:02 cj454-lt kernel: [   34.397865] pci 0000:01:00.0: putting AGP V2 device into 4x mode
Feb 14 19:57:02 cj454-lt kernel: [   34.650331] [drm] Setting GART location based on new memory map
Feb 14 19:57:02 cj454-lt kernel: [   34.650346] [drm] Loading R100 Microcode
Feb 14 19:57:02 cj454-lt kernel: [   34.650401] [drm] writeback test succeeded in 2 usecs
Feb 14 19:57:05 cj454-lt kernel: [   36.934717] NET: Registered protocol family 17
Feb 14 19:57:15 cj454-lt pulseaudio[5351]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 14 19:57:15 cj454-lt pulseaudio[5353]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 14 19:57:15 cj454-lt pulseaudio[5353]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 14 19:58:11 cj454-lt kernel: [  102.940056] NET: Registered protocol family 10
Feb 14 19:58:11 cj454-lt kernel: [  102.949376] lo: Disabled Privacy Extensions
Feb 14 19:58:11 cj454-lt kernel: [  102.951054] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by unix1adm on 2009-02-14
Not sure if this will help log file info


Feb 14 19:56:56 cj454-lt syslogd 1.5.0#2ubuntu6: restart.
Feb 14 19:56:56 cj454-lt kernel: Inspecting /boot/System.map-2.6.27-7-generic
Feb 14 19:56:56 cj454-lt kernel: Cannot find map file.
Feb 14 19:56:56 cj454-lt kernel: Loaded 51808 symbols from 98 modules.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005ff60000 (usable)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff77000 (ACPI data)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 000000005ff77000 - 000000005ff79000 (ACPI NVS)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 000000005ff80000 - 0000000060000000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] last_pfn = 0x5ff60 max_arch_pfn = 0x100000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] RAMDISK: 3781e000 - 37fef98a
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] DMI present.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: RSDP 000F6DF0, 0024 (r2 IBM   )
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: XSDT 5FF6A6CD, 004C (r1 IBM    TP-1R        3150  LTP        0)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: FACP 5FF6A800, 00F4 (r3 IBM    TP-1R        3150 IBM         1)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080609]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: DSDT 5FF6A9E7, C4D5 (r1 IBM    TP-1R        3150 MSFT  100000E)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: FACS 5FF78000, 0040
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: SSDT 5FF6A9B4, 0033 (r1 IBM    TP-1R        3150 MSFT  100000E)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: ECDT 5FF76EBC, 0052 (r1 IBM    TP-1R        3150 IBM         1)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: TCPA 5FF76F0E, 0032 (r1 IBM    TP-1R        3150 PTL         1)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: BOOT 5FF76FD8, 0028 (r1 IBM    TP-1R        3150  LTP        1)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] 639MB HIGHMEM available.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] 896MB LOWMEM available.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   mapped low ram: 0 - 38000000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   low ram: 00000000 - 38000000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   bootmap 00008000 - 0000f000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #4 [003781e000 - 0037fef98a]          RAMDISK ==> [003781e000 - 0037fef98a]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Zone PFN ranges:
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]   HighMem  0x00038000 -> 0x0005ff60
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Movable zone start PFN for each node
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Feb 14 19:56:56 cj454-lt kernel: [    0.000000]     0: 0x00000100 -> 0x0005ff60
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9f800000)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389504
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Kernel command line: root=UUID=befc8a95-e59a-4adc-aab0-2c5c3b6dacbd ro quiet splash 
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Initializing CPU#0
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Extended CMOS year: 2000
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] TSC: using PMTIMER calibration value
Feb 14 19:56:56 cj454-lt kernel: [    0.000000] Detected 1598.640 MHz processor.
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Console: colour VGA+ 80x25
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] console [tty0] enabled
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Memory: 1543388k/1572224k available (2572k kernel code, 27612k reserved, 1160k data, 424k init, 654720k highmem)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] virtual kernel memory layout:
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb 14 19:56:56 cj454-lt kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Feb 14 19:56:56 cj454-lt kernel: [    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 3197.28 BogoMIPS (lpj=6394560)
Feb 14 19:56:56 cj454-lt kernel: [    0.004052] Security Framework initialized
Feb 14 19:56:56 cj454-lt kernel: [    0.004069] SELinux:  Disabled at boot.
Feb 14 19:56:56 cj454-lt kernel: [    0.004103] AppArmor: AppArmor initialized
Feb 14 19:56:56 cj454-lt kernel: [    0.004116] Mount-cache hash table entries: 512
Feb 14 19:56:56 cj454-lt kernel: [    0.004358] Initializing cgroup subsys ns
Feb 14 19:56:56 cj454-lt kernel: [    0.004367] Initializing cgroup subsys cpuacct
Feb 14 19:56:56 cj454-lt kernel: [    0.004370] Initializing cgroup subsys memory
Feb 14 19:56:56 cj454-lt kernel: [    0.004393] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 14 19:56:56 cj454-lt kernel: [    0.004396] CPU: L2 cache: 2048K
Feb 14 19:56:56 cj454-lt kernel: [    0.004419] Checking 'hlt' instruction... OK.
Feb 14 19:56:56 cj454-lt kernel: [    0.020584] SMP alternatives: switching to UP code
Feb 14 19:56:56 cj454-lt kernel: [    0.027025] Freeing SMP alternatives: 11k freed
Feb 14 19:56:56 cj454-lt kernel: [    0.027029] ACPI: Core revision 20080609
Feb 14 19:56:56 cj454-lt kernel: [    0.032608] ACPI: Checking initramfs for custom DSDT
Feb 14 19:56:56 cj454-lt kernel: [    0.460323] ACPI: setting ELCR to 0200 (from 0800)
Feb 14 19:56:56 cj454-lt kernel: [    0.464085] weird, boot CPU (#0) not listedby the BIOS.
Feb 14 19:56:56 cj454-lt kernel: [    0.464089] SMP motherboard not detected.
Feb 14 19:56:56 cj454-lt kernel: [    0.464092] Local APIC not detected. Using dummy APIC emulation.
Feb 14 19:56:56 cj454-lt kernel: [    0.464095] SMP disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.464168] Brought up 1 CPUs
Feb 14 19:56:56 cj454-lt kernel: [    0.464171] Total of 1 processors activated (3197.28 BogoMIPS).
Feb 14 19:56:56 cj454-lt kernel: [    0.464469] net_namespace: 840 bytes
Feb 14 19:56:56 cj454-lt kernel: [    0.464478] Booting paravirtualized kernel on bare hardware
Feb 14 19:56:56 cj454-lt kernel: [    0.464699] Time:  0:56:28  Date: 02/15/09
Feb 14 19:56:56 cj454-lt kernel: [    0.464731] NET: Registered protocol family 16
Feb 14 19:56:56 cj454-lt kernel: [    0.465081] EISA bus registered
Feb 14 19:56:56 cj454-lt kernel: [    0.465098] ACPI: bus type pci registered
Feb 14 19:56:56 cj454-lt kernel: [    0.468126] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=5
Feb 14 19:56:56 cj454-lt kernel: [    0.468129] PCI: Using configuration type 1 for base access
Feb 14 19:56:56 cj454-lt kernel: [    0.470646] ACPI: EC: EC description table is found, configuring boot EC
Feb 14 19:56:56 cj454-lt kernel: [    0.480632] ACPI: EC: non-query interrupt received, switching to interrupt mode
Feb 14 19:56:56 cj454-lt kernel: [    0.501900] ACPI: Interpreter enabled
Feb 14 19:56:56 cj454-lt kernel: [    0.501904] ACPI: (supports S0 S3 S4 S5)
Feb 14 19:56:56 cj454-lt kernel: [    0.501923] ACPI: Using PIC for interrupt routing
Feb 14 19:56:56 cj454-lt kernel: [    0.517218] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Feb 14 19:56:56 cj454-lt kernel: [    0.517221] ACPI: EC: driver started in interrupt mode
Feb 14 19:56:56 cj454-lt kernel: [    0.517286] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 14 19:56:56 cj454-lt kernel: [    0.517682] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.517687] pci 0000:00:1d.7: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.517761] HPET not enabled in BIOS. You might try hpet=force boot option
Feb 14 19:56:56 cj454-lt kernel: [    0.517769] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Feb 14 19:56:56 cj454-lt kernel: [    0.517774] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
Feb 14 19:56:56 cj454-lt kernel: [    0.517969] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.517974] pci 0000:00:1f.5: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.518041] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.518046] pci 0000:00:1f.6: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.518215] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.518220] pci 0000:02:00.0: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.518372] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 19:56:56 cj454-lt kernel: [    0.518377] pci 0000:02:08.0: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    0.518404] pci 0000:00:1e.0: transparent bridge
Feb 14 19:56:56 cj454-lt kernel: [    0.524560] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.524845] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.525126] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.525407] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.525687] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.525946] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Feb 14 19:56:56 cj454-lt kernel: [    0.526205] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
Feb 14 19:56:56 cj454-lt kernel: [    0.526492] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Feb 14 19:56:56 cj454-lt kernel: [    0.526684] ACPI: Power Resource [PUBS] (on)
Feb 14 19:56:56 cj454-lt kernel: [    0.526684] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 14 19:56:56 cj454-lt kernel: [    0.526684] pnp: PnP ACPI init
Feb 14 19:56:56 cj454-lt kernel: [    0.526684] ACPI: bus type pnp registered
Feb 14 19:56:56 cj454-lt kernel: [    0.532522] pnp: PnP ACPI: found 13 devices
Feb 14 19:56:56 cj454-lt kernel: [    0.532525] ACPI: ACPI bus type pnp unregistered
Feb 14 19:56:56 cj454-lt kernel: [    0.532528] PnPBIOS: Disabled by ACPI PNP
Feb 14 19:56:56 cj454-lt kernel: [    0.532931] PCI: Using ACPI for IRQ routing
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NET: Registered protocol family 8
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NET: Registered protocol family 20
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NetLabel: Initializing
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NetLabel:  domain hash size = 128
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] NetLabel:  unlabeled traffic allowed by default
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] tracer: 772 pages allocated for 65536 entries of 48 bytes
Feb 14 19:56:56 cj454-lt kernel: [    0.533052]    actual entries 65620
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] AppArmor: AppArmor Filesystem Enabled
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] ACPI: RTC can wake from S4
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xec000-0xeffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0x100000-0x5fffffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1000-0x107f has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1180-0x11bf has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x15e0-0x15ef has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1600-0x162f has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1632-0x167f has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.533052] system 00:02: ioport range 0x1630-0x1631 has been reserved
Feb 14 19:56:56 cj454-lt kernel: [    0.568862] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Feb 14 19:56:56 cj454-lt kernel: [    0.568866] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
Feb 14 19:56:56 cj454-lt kernel: [    0.568871] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568875] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000e7ffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568884] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
Feb 14 19:56:56 cj454-lt kernel: [    0.568887] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
Feb 14 19:56:56 cj454-lt kernel: [    0.568892] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
Feb 14 19:56:56 cj454-lt kernel: [    0.568897] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568902] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568907] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
Feb 14 19:56:56 cj454-lt kernel: [    0.568911] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
Feb 14 19:56:56 cj454-lt kernel: [    0.568917] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.568922] pci 0000:00:1e.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
Feb 14 19:56:56 cj454-lt kernel: [    0.569462] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    0.569471] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    0.569478] bus: 00 index 0 io port: [0, ffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569480] bus: 00 index 1 mmio: [0, ffffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569483] bus: 01 index 0 io port: [3000, 3fff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569486] bus: 01 index 1 mmio: [c0100000, c01fffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569489] bus: 01 index 2 mmio: [e0000000, e7ffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569491] bus: 01 index 3 mmio: [0, 0]
Feb 14 19:56:56 cj454-lt kernel: [    0.569494] bus: 02 index 0 io port: [4000, 8fff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569497] bus: 02 index 1 mmio: [c0200000, cfffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569500] bus: 02 index 2 mmio: [e8000000, efffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569502] bus: 02 index 3 io port: [0, ffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569505] bus: 02 index 4 mmio: [0, ffffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569507] bus: 03 index 0 io port: [4000, 40ff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569510] bus: 03 index 1 io port: [4400, 44ff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569513] bus: 03 index 2 mmio: [e8000000, ebffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569516] bus: 03 index 3 mmio: [c4000000, c7ffffff]
Feb 14 19:56:56 cj454-lt kernel: [    0.569526] NET: Registered protocol family 2
Feb 14 19:56:56 cj454-lt kernel: [    0.569674] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.569965] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.570890] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    0.571539] TCP: Hash tables configured (established 131072 bind 65536)
Feb 14 19:56:56 cj454-lt kernel: [    0.571544] TCP reno registered
Feb 14 19:56:56 cj454-lt kernel: [    0.571716] NET: Registered protocol family 1
Feb 14 19:56:56 cj454-lt kernel: [    0.571874] checking if image is initramfs... it is
Feb 14 19:56:56 cj454-lt kernel: [    1.438205] Freeing initrd memory: 8006k freed
Feb 14 19:56:56 cj454-lt kernel: [    1.438507] Simple Boot Flag at 0x35 set to 0x1
Feb 14 19:56:56 cj454-lt kernel: [    1.439022] audit: initializing netlink socket (disabled)
Feb 14 19:56:56 cj454-lt kernel: [    1.439046] type=2000 audit(1234659388.436:1): initialized
Feb 14 19:56:56 cj454-lt kernel: [    1.446851] highmem bounce pool size: 64 pages
Feb 14 19:56:56 cj454-lt kernel: [    1.446861] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Feb 14 19:56:56 cj454-lt kernel: [    1.449750] VFS: Disk quotas dquot_6.5.1
Feb 14 19:56:56 cj454-lt kernel: [    1.449861] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 14 19:56:56 cj454-lt kernel: [    1.450001] msgmni has been set to 1752
Feb 14 19:56:56 cj454-lt kernel: [    1.450159] io scheduler noop registered
Feb 14 19:56:56 cj454-lt kernel: [    1.450162] io scheduler anticipatory registered
Feb 14 19:56:56 cj454-lt kernel: [    1.450165] io scheduler deadline registered
Feb 14 19:56:56 cj454-lt kernel: [    1.450180] io scheduler cfq registered (default)
Feb 14 19:56:56 cj454-lt kernel: [    1.450286] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
Feb 14 19:56:56 cj454-lt kernel: [    1.450687] isapnp: Scanning for PnP cards...
Feb 14 19:56:56 cj454-lt kernel: [    1.803665] isapnp: No Plug & Play device found
Feb 14 19:56:56 cj454-lt kernel: [    1.845937] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Feb 14 19:56:56 cj454-lt kernel: [    1.847282] serial 00:0a: activated
Feb 14 19:56:56 cj454-lt kernel: [    1.847542] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Feb 14 19:56:56 cj454-lt kernel: [    1.848280] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    1.848285] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    1.848294] serial 0000:00:1f.6: PCI INT B disabled
Feb 14 19:56:56 cj454-lt kernel: [    1.850193] brd: module loaded
Feb 14 19:56:56 cj454-lt kernel: [    1.850286] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Feb 14 19:56:56 cj454-lt kernel: [    1.850436] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Feb 14 19:56:56 cj454-lt kernel: [    1.856380] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 14 19:56:56 cj454-lt kernel: [    1.856394] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 14 19:56:56 cj454-lt kernel: [    1.856804] mice: PS/2 mouse device common for all mice
Feb 14 19:56:56 cj454-lt kernel: [    1.856973] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Feb 14 19:56:56 cj454-lt kernel: [    1.856990] rtc0: alarms up to one month, y3k
Feb 14 19:56:56 cj454-lt kernel: [    1.857131] EISA: Probing bus 0 at eisa.0
Feb 14 19:56:56 cj454-lt kernel: [    1.857138] Cannot allocate resource for EISA slot 1
Feb 14 19:56:56 cj454-lt kernel: [    1.857142] Cannot allocate resource for EISA slot 2
Feb 14 19:56:56 cj454-lt kernel: [    1.857145] Cannot allocate resource for EISA slot 3
Feb 14 19:56:56 cj454-lt kernel: [    1.857148] Cannot allocate resource for EISA slot 4
Feb 14 19:56:56 cj454-lt kernel: [    1.857151] Cannot allocate resource for EISA slot 5
Feb 14 19:56:56 cj454-lt kernel: [    1.857153] Cannot allocate resource for EISA slot 6
Feb 14 19:56:56 cj454-lt kernel: [    1.857156] Cannot allocate resource for EISA slot 7
Feb 14 19:56:56 cj454-lt kernel: [    1.857159] Cannot allocate resource for EISA slot 8
Feb 14 19:56:56 cj454-lt kernel: [    1.857161] EISA: Detected 0 cards.
Feb 14 19:56:56 cj454-lt kernel: [    1.857166] cpuidle: using governor ladder
Feb 14 19:56:56 cj454-lt kernel: [    1.857169] cpuidle: using governor menu
Feb 14 19:56:56 cj454-lt kernel: [    1.857810] TCP cubic registered
Feb 14 19:56:56 cj454-lt kernel: [    1.857843] Using IPI No-Shortcut mode
Feb 14 19:56:56 cj454-lt kernel: [    1.858070] registered taskstats version 1
Feb 14 19:56:56 cj454-lt kernel: [    1.858196]   Magic number: 13:986:910
Feb 14 19:56:56 cj454-lt kernel: [    1.858265] tty ptyz6: hash matches
Feb 14 19:56:56 cj454-lt kernel: [    1.858355] rtc_cmos 00:06: setting system clock to 2009-02-15 00:56:29 UTC (1234659389)
Feb 14 19:56:56 cj454-lt kernel: [    1.858360] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 14 19:56:56 cj454-lt kernel: [    1.858362] EDD information not available.
Feb 14 19:56:56 cj454-lt kernel: [    1.858693] Freeing unused kernel memory: 424k freed
Feb 14 19:56:56 cj454-lt kernel: [    1.858751] Write protecting the kernel text: 2576k
Feb 14 19:56:56 cj454-lt kernel: [    1.858784] Write protecting the kernel read-only data: 936k
Feb 14 19:56:56 cj454-lt kernel: [    1.861744] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Feb 14 19:56:56 cj454-lt kernel: [    2.099619] fuse init (API version 7.9)
Feb 14 19:56:56 cj454-lt kernel: [    2.335428] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Feb 14 19:56:56 cj454-lt kernel: [    2.340456] processor ACPI0007:00: registered as cooling_device0
Feb 14 19:56:56 cj454-lt kernel: [    2.340461] ACPI: Processor [CPU] (supports 8 throttling states)
Feb 14 19:56:56 cj454-lt kernel: [    2.369300] thermal LNXTHERM:01: registered as thermal_zone0
Feb 14 19:56:56 cj454-lt kernel: [    2.370993] ACPI: Thermal Zone [THM0] (68 C)
Feb 14 19:56:56 cj454-lt kernel: [    3.259005] ACPI: ACPI Dock Station Driver
Feb 14 19:56:56 cj454-lt kernel: [    3.413285] usbcore: registered new interface driver usbfs
Feb 14 19:56:56 cj454-lt kernel: [    3.413319] usbcore: registered new interface driver hub
Feb 14 19:56:56 cj454-lt kernel: [    3.413371] usbcore: registered new device driver usb
Feb 14 19:56:56 cj454-lt kernel: [    3.416512] USB Universal Host Controller Interface driver v3.0
Feb 14 19:56:56 cj454-lt kernel: [    3.420189] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Feb 14 19:56:56 cj454-lt kernel: [    3.420202] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.420218] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [    3.420272] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Feb 14 19:56:56 cj454-lt kernel: [    3.420299] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
Feb 14 19:56:56 cj454-lt kernel: [    3.420523] usb usb1: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [    3.420557] hub 1-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [    3.420565] hub 1-0:1.0: 2 ports detected
Feb 14 19:56:56 cj454-lt kernel: [    3.515062] SCSI subsystem initialized
Feb 14 19:56:56 cj454-lt kernel: [    3.518335] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Feb 14 19:56:56 cj454-lt kernel: [    3.518338] e100: Copyright(c) 1999-2006 Intel Corporation
Feb 14 19:56:56 cj454-lt kernel: [    3.541468] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Feb 14 19:56:56 cj454-lt kernel: [    3.541976] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.541981] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.541997] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [    3.542028] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Feb 14 19:56:56 cj454-lt kernel: [    3.542055] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
Feb 14 19:56:56 cj454-lt kernel: [    3.542173] usb usb2: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [    3.542206] hub 2-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [    3.542214] hub 2-0:1.0: 2 ports detected
Feb 14 19:56:56 cj454-lt kernel: [    3.644982] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.644988] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.645004] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [    3.645043] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Feb 14 19:56:56 cj454-lt kernel: [    3.645070] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
Feb 14 19:56:56 cj454-lt kernel: [    3.645181] usb usb3: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [    3.645213] hub 3-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [    3.645223] hub 3-0:1.0: 2 ports detected
Feb 14 19:56:56 cj454-lt kernel: [    3.749949] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Feb 14 19:56:56 cj454-lt kernel: [    3.750458] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.750463] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.750487] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [    3.750520] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Feb 14 19:56:56 cj454-lt kernel: [    3.754422] ehci_hcd 0000:00:1d.7: debug port 1
Feb 14 19:56:56 cj454-lt kernel: [    3.754440] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
Feb 14 19:56:56 cj454-lt kernel: [    3.768056] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb 14 19:56:56 cj454-lt kernel: [    3.768230] usb usb4: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [    3.768264] hub 4-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [    3.768274] hub 4-0:1.0: 6 ports detected
Feb 14 19:56:56 cj454-lt kernel: [    3.874082] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.874089] e100 0000:02:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.898295] e100 0000:02:08.0: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [    3.899754] e100: eth0: e100_probe: addr 0xc0210000, irq 11, MAC addr 00:11:25:86:3d:04
Feb 14 19:56:56 cj454-lt kernel: [    3.903444] pata_acpi 0000:00:1f.1: enabling device (0005 -> 0007)
Feb 14 19:56:56 cj454-lt kernel: [    3.903453] pata_acpi 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.903507] pata_acpi 0000:00:1f.1: PCI INT A disabled
Feb 14 19:56:56 cj454-lt kernel: [    3.907860] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [    3.909388] scsi0 : ata_piix
Feb 14 19:56:56 cj454-lt kernel: [    3.909824] scsi1 : ata_piix
Feb 14 19:56:56 cj454-lt kernel: [    3.911182] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
Feb 14 19:56:56 cj454-lt kernel: [    3.911186] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
Feb 14 19:56:56 cj454-lt kernel: [    4.124111] ata1.00: ATA-8: WDC WD2500BEVE-00WZT0, 01.01A01, max UDMA/100
Feb 14 19:56:56 cj454-lt kernel: [    4.124118] ata1.00: 488397168 sectors, multi 16: LBA48 
Feb 14 19:56:56 cj454-lt kernel: [    4.141057] ata1.00: configured for UDMA/100
Feb 14 19:56:56 cj454-lt kernel: [    4.264442] Marking TSC unstable due to TSC halts in idle
Feb 14 19:56:56 cj454-lt kernel: [    4.304344] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0202, max UDMA/33
Feb 14 19:56:56 cj454-lt kernel: [    4.320269] ata2.00: configured for UDMA/33
Feb 14 19:56:56 cj454-lt kernel: [    4.320419] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVE-0 01.0 PQ: 0 ANSI: 5
Feb 14 19:56:56 cj454-lt kernel: [    4.325625] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0202 PQ: 0 ANSI: 5
Feb 14 19:56:56 cj454-lt kernel: [    4.337939] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Feb 14 19:56:56 cj454-lt kernel: [    4.337982] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Feb 14 19:56:56 cj454-lt kernel: [    4.359351] Driver 'sd' needs updating - please use bus_type methods
Feb 14 19:56:56 cj454-lt kernel: [    4.359485] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Feb 14 19:56:56 cj454-lt kernel: [    4.359514] sd 0:0:0:0: [sda] Write Protect is off
Feb 14 19:56:56 cj454-lt kernel: [    4.359565] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 19:56:56 cj454-lt kernel: [    4.359662] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Feb 14 19:56:56 cj454-lt kernel: [    4.359688] sd 0:0:0:0: [sda] Write Protect is off
Feb 14 19:56:56 cj454-lt kernel: [    4.359740] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 19:56:56 cj454-lt kernel: [    4.359745]  sda: sda1 sda2 sda3 sda4
Feb 14 19:56:56 cj454-lt kernel: [    4.372378] Driver 'sr' needs updating - please use bus_type methods
Feb 14 19:56:56 cj454-lt kernel: [    4.398467] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 14 19:56:56 cj454-lt kernel: [    4.413851] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Feb 14 19:56:56 cj454-lt kernel: [    4.413856] Uniform CD-ROM driver Revision: 3.20
Feb 14 19:56:56 cj454-lt kernel: [    5.068116] Clocksource tsc unstable (delta = -93862065 ns)
Feb 14 19:56:56 cj454-lt kernel: [    9.850352] EXT3-fs: INFO: recovery required on readonly filesystem.
Feb 14 19:56:56 cj454-lt kernel: [    9.850356] EXT3-fs: write access will be enabled during recovery.
Feb 14 19:56:56 cj454-lt kernel: [   11.891062] kjournald starting.  Commit interval 5 seconds
Feb 14 19:56:56 cj454-lt kernel: [   11.891082] EXT3-fs: sda1: orphan cleanup on readonly fs
Feb 14 19:56:56 cj454-lt kernel: [   11.891134] EXT3-fs: sda1: 1 orphan inode deleted
Feb 14 19:56:56 cj454-lt kernel: [   11.891137] EXT3-fs: recovery complete.
Feb 14 19:56:56 cj454-lt kernel: [   11.894917] EXT3-fs: mounted filesystem with ordered data mode.
Feb 14 19:56:56 cj454-lt kernel: [   18.057184] udevd version 124 started
Feb 14 19:56:56 cj454-lt kernel: [   18.878114] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 14 19:56:56 cj454-lt kernel: [   18.966658] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 14 19:56:56 cj454-lt kernel: [   19.044922] Linux agpgart interface v0.103
Feb 14 19:56:56 cj454-lt kernel: [   19.113411] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
Feb 14 19:56:56 cj454-lt kernel: [   19.184337] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Feb 14 19:56:56 cj454-lt kernel: [   19.191969] iTCO_vendor_support: vendor-support=0
Feb 14 19:56:56 cj454-lt kernel: [   19.256278] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Feb 14 19:56:56 cj454-lt kernel: [   19.256442] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
Feb 14 19:56:56 cj454-lt kernel: [   19.256629] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Feb 14 19:56:56 cj454-lt kernel: [   19.333511] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Feb 14 19:56:56 cj454-lt kernel: [   19.345006] ACPI: Power Button (FF) [PWRF]
Feb 14 19:56:56 cj454-lt kernel: [   19.345151] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Feb 14 19:56:56 cj454-lt kernel: [   19.353040] ACPI: Lid Switch [LID]
Feb 14 19:56:56 cj454-lt kernel: [   19.353151] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
Feb 14 19:56:56 cj454-lt kernel: [   19.364050] ACPI: Sleep Button (CM) [SLPB]
Feb 14 19:56:56 cj454-lt kernel: [   19.513569] intel_rng: FWH not detected
Feb 14 19:56:56 cj454-lt kernel: [   20.396034] NET: Registered protocol family 23
Feb 14 19:56:56 cj454-lt kernel: [   20.476798] nsc-ircc 00:0c: activated
Feb 14 19:56:56 cj454-lt kernel: [   20.476985] nsc-ircc, chip->init
Feb 14 19:56:56 cj454-lt kernel: [   20.476994] nsc-ircc, Found chip at base=0x02e
Feb 14 19:56:56 cj454-lt kernel: [   20.477018] nsc-ircc, driver loaded (Dag Brattli)
Feb 14 19:56:56 cj454-lt kernel: [   20.477445] IrDA: Registered device irda0
Feb 14 19:56:56 cj454-lt kernel: [   20.477449] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Feb 14 19:56:56 cj454-lt kernel: [   20.606781] parport_pc 00:0b: reported by Plug and Play ACPI
Feb 14 19:56:56 cj454-lt kernel: [   20.606824] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Feb 14 19:56:56 cj454-lt kernel: [   20.738471] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input5
Feb 14 19:56:56 cj454-lt kernel: [   20.752070] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Feb 14 19:56:56 cj454-lt kernel: [   20.767396] ACPI: Error installing bay notify handler
Feb 14 19:56:56 cj454-lt kernel: [   21.042798] ath_hal: module license 'Proprietary' taints kernel.
Feb 14 19:56:56 cj454-lt kernel: [   21.126066] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Feb 14 19:56:56 cj454-lt kernel: [   21.304974] wlan: 0.9.4
Feb 14 19:56:56 cj454-lt kernel: [   21.415794] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
Feb 14 19:56:56 cj454-lt kernel: [   21.415814] Yenta: Using INTVAL to route CSC interrupts to PCI
Feb 14 19:56:56 cj454-lt kernel: [   21.415817] Yenta: Routing CardBus interrupts to PCI
Feb 14 19:56:56 cj454-lt kernel: [   21.415823] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
Feb 14 19:56:56 cj454-lt kernel: [   21.461570] ACPI: AC Adapter [AC] (on-line)
Feb 14 19:56:56 cj454-lt kernel: [   21.462390] ath_pci: 0.9.4
Feb 14 19:56:56 cj454-lt kernel: [   21.530497] ACPI: Battery Slot [BAT0] (battery present)
Feb 14 19:56:56 cj454-lt kernel: [   21.644615] Yenta: ISA IRQ mask 0x0430, PCI irq 11
Feb 14 19:56:56 cj454-lt kernel: [   21.644620] Socket status: 30000020
Feb 14 19:56:56 cj454-lt kernel: [   21.644625] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
Feb 14 19:56:56 cj454-lt kernel: [   21.644628] cs: IO port probe 0x4000-0x8fff: clean.
Feb 14 19:56:56 cj454-lt kernel: [   21.646029] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
Feb 14 19:56:56 cj454-lt kernel: [   21.646032] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
Feb 14 19:56:56 cj454-lt kernel: [   21.679302] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [   22.776053] pccard: CardBus card inserted into slot 0
Feb 14 19:56:56 cj454-lt kernel: [   22.776150] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
Feb 14 19:56:56 cj454-lt kernel: [   22.776156] pci 0000:03:00.0: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [   22.776243] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot
Feb 14 19:56:56 cj454-lt kernel: [   22.776248] pci 0000:03:00.1: PME# disabled
Feb 14 19:56:56 cj454-lt kernel: [   22.828960] input: PC Speaker as /devices/platform/pcspkr/input/input6
Feb 14 19:56:56 cj454-lt kernel: [   22.890117] ath_rate_sample: 1.2 (0.9.4)
Feb 14 19:56:56 cj454-lt kernel: [   22.890716] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Feb 14 19:56:56 cj454-lt kernel: [   22.890726] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Feb 14 19:56:56 cj454-lt kernel: [   22.890732] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Feb 14 19:56:56 cj454-lt kernel: [   22.890762] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Feb 14 19:56:56 cj454-lt kernel: [   22.890768] wifi0: mac 5.9 phy 4.3 radio 3.6
Feb 14 19:56:56 cj454-lt kernel: [   22.890773] wifi0: Use hw queue 1 for WME_AC_BE traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890776] wifi0: Use hw queue 0 for WME_AC_BK traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890778] wifi0: Use hw queue 2 for WME_AC_VI traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890781] wifi0: Use hw queue 3 for WME_AC_VO traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890783] wifi0: Use hw queue 8 for CAB traffic
Feb 14 19:56:56 cj454-lt kernel: [   22.890786] wifi0: Use hw queue 9 for beacons
Feb 14 19:56:56 cj454-lt kernel: [   22.898775] wifi0: Atheros 5212: mem=0xc0200000, irq=11
Feb 14 19:56:56 cj454-lt kernel: [   23.220390] Non-volatile memory driver v1.2
Feb 14 19:56:56 cj454-lt kernel: [   23.282122] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [   23.483084] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
Feb 14 19:56:56 cj454-lt kernel: [   23.483092] serio: Synaptics pass-through port at isa0060/serio1/input0
Feb 14 19:56:56 cj454-lt kernel: [   23.521410] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Feb 14 19:56:56 cj454-lt kernel: [   23.543425] thinkpad_acpi: ThinkPad ACPI Extras v0.21
Feb 14 19:56:56 cj454-lt kernel: [   23.543430] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Feb 14 19:56:56 cj454-lt kernel: [   23.543433] thinkpad_acpi: ThinkPad BIOS 1RETDJWW (3.15 ), EC 1RHT71WW-3.04
Feb 14 19:56:56 cj454-lt kernel: [   23.543436] thinkpad_acpi: IBM ThinkPad R51, model 1830WCW
Feb 14 19:56:56 cj454-lt kernel: [   23.548985] Registered led device: tpacpi::thinklight
Feb 14 19:56:56 cj454-lt kernel: [   23.549250] thinkpad_acpi: another device driver is already handling bay events
Feb 14 19:56:56 cj454-lt kernel: [   23.549254] thinkpad_acpi: disabling subdriver bay
Feb 14 19:56:56 cj454-lt kernel: [   23.549309] Registered led device: tpacpi::power
Feb 14 19:56:56 cj454-lt kernel: [   23.549349] Registered led device: tpacpi:orange:batt
Feb 14 19:56:56 cj454-lt kernel: [   23.549388] Registered led device: tpacpi:green:batt
Feb 14 19:56:56 cj454-lt kernel: [   23.549428] Registered led device: tpacpi::dock_active
Feb 14 19:56:56 cj454-lt kernel: [   23.549471] Registered led device: tpacpi::bay_active
Feb 14 19:56:56 cj454-lt kernel: [   23.549511] Registered led device: tpacpi::dock_batt
Feb 14 19:56:56 cj454-lt kernel: [   23.549550] Registered led device: tpacpi::unknown_led
Feb 14 19:56:56 cj454-lt kernel: [   23.549589] Registered led device: tpacpi::standby
Feb 14 19:56:56 cj454-lt kernel: [   23.552273] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
Feb 14 19:56:56 cj454-lt kernel: [   24.208058] intel8x0_measure_ac97_clock: measured 55450 usecs
Feb 14 19:56:56 cj454-lt kernel: [   24.208063] intel8x0: clocking to 48000
Feb 14 19:56:56 cj454-lt kernel: [   24.784042] ohci_hcd 0000:03:00.0: enabling device (0000 -> 0002)
Feb 14 19:56:56 cj454-lt kernel: [   24.784056] ohci_hcd 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [   24.784079] ohci_hcd 0000:03:00.0: OHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [   24.784185] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 5
Feb 14 19:56:56 cj454-lt kernel: [   24.784208] ohci_hcd 0000:03:00.0: irq 11, io mem 0xc4000000
Feb 14 19:56:56 cj454-lt kernel: [   24.918155] cs: IO port probe 0x100-0x3af: clean.
Feb 14 19:56:56 cj454-lt kernel: [   24.919152] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Feb 14 19:56:56 cj454-lt kernel: [   24.919597] cs: IO port probe 0x820-0x8ff: clean.
Feb 14 19:56:56 cj454-lt kernel: [   24.920000] cs: IO port probe 0xc00-0xcf7: clean.
Feb 14 19:56:56 cj454-lt kernel: [   24.920541] cs: IO port probe 0xa00-0xaff: clean.
Feb 14 19:56:56 cj454-lt kernel: [   24.930416] usb usb5: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [   24.930487] hub 5-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [   24.930501] hub 5-0:1.0: 1 port detected
Feb 14 19:56:56 cj454-lt kernel: [   25.032477] ohci_hcd 0000:03:00.1: enabling device (0000 -> 0002)
Feb 14 19:56:56 cj454-lt kernel: [   25.032492] ohci_hcd 0000:03:00.1: PCI INT B -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:56:56 cj454-lt kernel: [   25.032515] ohci_hcd 0000:03:00.1: OHCI Host Controller
Feb 14 19:56:56 cj454-lt kernel: [   25.032604] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 6
Feb 14 19:56:56 cj454-lt kernel: [   25.032627] ohci_hcd 0000:03:00.1: irq 11, io mem 0xc4001000
Feb 14 19:56:56 cj454-lt kernel: [   25.170420] usb usb6: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [   25.170506] hub 6-0:1.0: USB hub found
Feb 14 19:56:56 cj454-lt kernel: [   25.170520] hub 6-0:1.0: 1 port detected
Feb 14 19:56:56 cj454-lt kernel: [   26.016528] lp0: using parport0 (interrupt-driven).
Feb 14 19:56:56 cj454-lt kernel: [   26.456863] EXT3 FS on sda1, internal journal
Feb 14 19:56:56 cj454-lt kernel: [   26.934941] type=1505 audit(1234659415.059:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3985
Feb 14 19:56:56 cj454-lt kernel: [   27.183837] type=1505 audit(1234659415.307:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3990
Feb 14 19:56:56 cj454-lt kernel: [   27.184277] type=1505 audit(1234659415.311:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3990
Feb 14 19:56:56 cj454-lt kernel: [   27.323681] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 14 19:56:56 cj454-lt kernel: [   27.489691] usb 5-1: new full speed USB device using ohci_hcd and address 2
Feb 14 19:56:56 cj454-lt kernel: [   27.709895] usb 5-1: configuration #1 chosen from 1 choice
Feb 14 19:56:56 cj454-lt kernel: [   27.905808] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
Feb 14 19:56:56 cj454-lt kernel: [   27.910234] usbcore: registered new interface driver cdc_acm
Feb 14 19:56:56 cj454-lt kernel: [   27.910240] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Feb 14 19:56:56 cj454-lt kernel: [   27.932710] ACPI: WMI: Mapper loaded
Feb 14 19:56:56 cj454-lt kernel: [   27.994476] ACPI: Error installing bay notify handler
Feb 14 19:56:56 cj454-lt kernel: [   28.824077] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Feb 14 19:56:57 cj454-lt kernel: [   28.946366] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Feb 14 19:56:57 cj454-lt kernel: [   29.002505] IBM machine detected. Enabling interrupts during APM calls.
Feb 14 19:56:57 cj454-lt kernel: [   29.002515] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Feb 14 19:56:57 cj454-lt kernel: [   29.002519] apm: overridden by ACPI.
Feb 14 19:56:57 cj454-lt kernel: [   29.065959] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
Feb 14 19:56:57 cj454-lt kernel: [   29.203988] ppdev: user-space parallel port driver
Feb 14 19:57:00 cj454-lt kernel: [   32.425117] Bluetooth: Core ver 2.13
Feb 14 19:57:00 cj454-lt kernel: [   32.427911] NET: Registered protocol family 31
Feb 14 19:57:00 cj454-lt kernel: [   32.427921] Bluetooth: HCI device and connection manager initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.427926] Bluetooth: HCI socket layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.470088] Bluetooth: L2CAP ver 2.11
Feb 14 19:57:00 cj454-lt kernel: [   32.470099] Bluetooth: L2CAP socket layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.520897] Bluetooth: SCO (Voice Link) ver 0.6
Feb 14 19:57:00 cj454-lt kernel: [   32.520909] Bluetooth: SCO socket layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.556973] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 14 19:57:00 cj454-lt kernel: [   32.556984] Bluetooth: BNEP filters: protocol multicast
Feb 14 19:57:00 cj454-lt kernel: [   32.594350] Bridge firewalling registered
Feb 14 19:57:00 cj454-lt kernel: [   32.687017] Bluetooth: RFCOMM socket layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.687375] Bluetooth: RFCOMM TTY layer initialized
Feb 14 19:57:00 cj454-lt kernel: [   32.687385] Bluetooth: RFCOMM ver 1.10
Feb 14 19:57:01 cj454-lt kernel: [   33.542868] pci 0000:01:00.0: power state changed by ACPI to D0
Feb 14 19:57:01 cj454-lt kernel: [   33.545010] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 14 19:57:02 cj454-lt kernel: [   34.088649] [drm] Initialized drm 1.1.0 20060810
Feb 14 19:57:02 cj454-lt kernel: [   34.168752] [drm] Initialized radeon 1.29.0 20080528 on minor 0
Feb 14 19:57:02 cj454-lt kernel: [   34.397794] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Feb 14 19:57:02 cj454-lt kernel: [   34.397827] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Feb 14 19:57:02 cj454-lt kernel: [   34.397865] pci 0000:01:00.0: putting AGP V2 device into 4x mode
Feb 14 19:57:02 cj454-lt kernel: [   34.650331] [drm] Setting GART location based on new memory map
Feb 14 19:57:02 cj454-lt kernel: [   34.650346] [drm] Loading R100 Microcode
Feb 14 19:57:02 cj454-lt kernel: [   34.650401] [drm] writeback test succeeded in 2 usecs
Feb 14 19:57:05 cj454-lt kernel: [   36.934717] NET: Registered protocol family 17
Feb 14 19:57:15 cj454-lt pulseaudio[5351]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 14 19:57:15 cj454-lt pulseaudio[5353]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 14 19:57:15 cj454-lt pulseaudio[5353]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 14 19:58:11 cj454-lt kernel: [  102.940056] NET: Registered protocol family 10
Feb 14 19:58:11 cj454-lt kernel: [  102.949376] lo: Disabled Privacy Extensions
Feb 14 19:58:11 cj454-lt kernel: [  102.951054] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by primus454 on 2009-02-14
I can't help with  you actual situation, but to make rebooting easier on the system you can try to go to TTY1 with CTRL+ALT+F1 and type ```
sudo shutdown now -r
```

---

### Post by 3rdalbum on 2009-02-14
In Gnome System Log, can you give us the "messages" or "kern.log" from the time when the caps lock light started blinking?

When the keyboard lights blink, that indicates a kernel panic. A kernel panic is when your system has detected an error that it can't recover from.

Kernel panics are most often caused by proprietary drivers or bad RAM, although some programs can unwittingly cause them. Try running Memtest and disabling any proprietary graphics card drivers. The kernel messages from the times when you have a kernel panic might yield some useful information too.

---

### Post by unix1adm on 2009-02-14
> **primus454 said:**
> I can't help with  you actual situation, but to make rebooting easier on the system you can try to go to TTY1 with CTRL+ALT+F1 and type ```
sudo shutdown now -r
```


tried thisbut the system would not respond

---

### Post by unix1adm on 2009-02-14
> **3rdalbum said:**
> In Gnome System Log, can you give us the "messages" or "kern.log" from the time when the caps lock light started blinking?

When the keyboard lights blink, that indicates a kernel panic. A kernel panic is when your system has detected an error that it can't recover from.

Kernel panics are most often caused by proprietary drivers or bad RAM, although some programs can unwittingly cause them. Try running Memtest and disabling any proprietary graphics card drivers. The kernel messages from the times when you have a kernel panic might yield some useful information too.


I did post the messages file see above.

I tried to upload it but the site says its an invalid file... so I dont know how to post the kern.log file

---

### Post by Pbethe on 2009-05-01
> **unix1adm said:**
> I did post the messages file see above.

I tried to upload it but the site says its an invalid file... so I dont know how to post the kern.log file

Try compressing kern.log and posting the archive.  I think the size limit for text files is 20k.

I turned up your post in a search because you have the same "weird" messages as I do. You have "weird, boot CPU (#0) not listedby the BIOS."  Also, I get "Driver 'sd' needs updating - please use bus_type methods
Apr 24 23:40:49 ubuntu kernel: [    5.525628] Driver 'sr' needs updating - please use bus_type methods".  I don't know if I get kernel panics; mostly, my system just grinds to a halt.

Does anyone know what these messages mean, and if they might result in a panic?

---

