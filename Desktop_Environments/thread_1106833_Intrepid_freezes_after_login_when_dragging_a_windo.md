---
title: "Intrepid freezes after login when dragging a window or scrollbar"
date: 2009-03-26
forum: Desktop Environments
---

### Post by jsastrem on 2009-03-26
Just right after booting the system and login into Gnome desktop, sometimes my system completely freezes if I open a window of whatever program and try to move it by clicking on the title bar and moving the mouse without releasing the mouse button, that is, dragging the window's title bar. It also happens when dragging the scrollbar for moving the window content up or down. The window moves a little bit then freezes, like if it couldn't follow my mouse movement; it's almost immediate but I manage to move the window a little bit. If I boot the system and manage to move or scroll a window once, then it doesn't freeze anymore until next reboot, that is, it just happens right after login with the first window/windows I open. When frozen, the system gets completely unresponsive: the mouse pointer does not move anymore and ctrl+alt+backspace does nothing; the only option I have is to reboot the system by pressing the reset button.

My system specs are:
Ubuntu Intrepid 64 bits,
Gnome desktop,
Compiz and Emerald installed, but finally using Metacity window manager,
video driver fglrx-amdcccle 2:8.543-0ubuntu4.1

Intel Core 2 Duo 3.17Mhz
8GB RAM
ATI video card, Sapphire HD 3870
Mobo Asus P5Q Premium

---

### Post by theOtherMarino on 2009-03-26
Hello,

Got a somehow-related issue. May you type a "dmesg > dmesg.txt" in a terminal and attach the file.

Marino
[http://markup.fr/](http://markup.fr/)

---

### Post by jsastrem on 2009-04-08
I thought I had already post the dmesg output. . . well, here you are:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27.2-jsm2 (root@silverlynx) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Jan 7 13:07:01 CET 2009 (Ubuntu 2.6.27-9.19-server)
[    0.000000] Command line: root=UUID=be12d50c-19b7-48bf-ad12-ca083b47a436 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff70000 (usable)
[    0.000000]  BIOS-e820: 00000000cff70000 - 00000000cff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff7e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] last_pfn = 0x230000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xcff70 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff70000 page 4k
[    0.000000] kernel direct mapping tables up to cff70000 @ 8000-e000
[    0.000000] last_map_addr: cff70000 end: cff70000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0230000000 page 2M
[    0.000000] kernel direct mapping tables up to 230000000 @ c000-16000
[    0.000000] last_map_addr: 230000000 end: 230000000
[    0.000000] RAMDISK: 34db1000 - 37fefdc2
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000FB190, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT CFF70100, 0054 (r1 A_M_I_ OEMXSDT   6000818 MSFT       97)
[    0.000000] ACPI: FACP CFF70290, 00F4 (r3 A_M_I_ OEMFACP   6000818 MSFT       97)
[    0.000000] ACPI: DSDT CFF70440, 9DDC (r1  A1039 A1039001        1 INTL 20060113)
[    0.000000] ACPI: FACS CFF7E000, 0040
[    0.000000] ACPI: APIC CFF70390, 006C (r1 A_M_I_ OEMAPIC   6000818 MSFT       97)
[    0.000000] ACPI: MCFG CFF70400, 003C (r1 A_M_I_ OEMMCFG   6000818 MSFT       97)
[    0.000000] ACPI: OEMB CFF7E040, 0081 (r1 A_M_I_ AMI_OEM   6000818 MSFT       97)
[    0.000000] ACPI: HPET CFF7A220, 0038 (r1 A_M_I_ OEMHPET   6000818 MSFT       97)
[    0.000000] ACPI: OSFR CFF7A260, 00B0 (r1 A_M_I_ OEMOSFR   6000818 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000230000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000230000000
[    0.000000]   NODE_DATA [0000000000011000 - 000000000001ffff]
[    0.000000]   bootmap [0000000000020000 -  0000000000065fff] pages 46
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0230000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000918cdc]    TEXT DATA BSS ==> [0000200000 - 0000918cdc]
[    0.000000]   #3 [0034db1000 - 0037fefdc2]          RAMDISK ==> [0034db1000 - 0037fefdc2]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #6 [000000c000 - 0000011000]          PGTABLE ==> [000000c000 - 0000011000]
[    0.000000]  [ffffe20000000000-ffffe20008bfffff] PMD -> [ffff880028200000-ffff8800301fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00230000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000cff70
[    0.000000]     0: 0x00100000 -> 0x00230000
[    0.000000] On node 0 totalpages: 2096909
[    0.000000]   DMA zone: 2007 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 831408 pages, LIFO batch:31
[    0.000000]   Normal zone: 1225728 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff70000 - 00000000cff7e000
[    0.000000] PM: Registered nosave memory: 00000000cff7e000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2ee00000)
[    0.000000] PERCPU: Allocating 48544 bytes of per cpu data
[    0.000000] NR_CPUS: 2, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2059143
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=be12d50c-19b7-48bf-ad12-ca083b47a436 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 3166.292 MHz processor.
[    0.003333] Console: colour VGA+ 80x25
[    0.003333] console [tty0] enabled
[    0.003333] Checking aperture...
[    0.003333] No AGP bridge found
[    0.003333] Calgary: detecting Calgary via BIOS EBDA area
[    0.003333] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.003333] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.003333] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.003333] Memory: 8131416k/9175040k available (3027k kernel code, 256220k reserved, 1525k data, 504k init)
[    0.003333] CPA: page pool initialized 1 of 1 pages preallocated
[    0.003333] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.003333] hpet clockevent registered
[    0.003333] Calibrating delay loop (skipped), value calculated using timer frequency.. 6335.44 BogoMIPS (lpj=10554306)
[    0.003333] Security Framework initialized
[    0.003333] SELinux:  Disabled at boot.
[    0.003333] AppArmor: AppArmor initialized
[    0.003333] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.003399] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004673] Mount-cache hash table entries: 256
[    0.004785] Initializing cgroup subsys ns
[    0.004788] Initializing cgroup subsys cpuacct
[    0.004791] Initializing cgroup subsys memory
[    0.004802] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004804] CPU: L2 cache: 6144K
[    0.004805] CPU 0/0 -> Node 0
[    0.004807] CPU: Physical Processor ID: 0
[    0.004807] CPU: Processor Core ID: 0
[    0.004812] CPU0: Thermal monitoring enabled (TM2)
[    0.004814] using mwait in idle threads.
[    0.006130] ACPI: Core revision 20080609
[    0.008806] ACPI: Checking initramfs for custom DSDT
[    1.570276] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.604317] CPU0: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 0a
[    1.604320] Using local APIC timer interrupts.
[    1.606634] APIC timer calibration result 20830874
[    1.606636] Detected 20.830 MHz APIC timer.
[    1.606712] Booting processor 1/1 ip 6000
[    0.003333] Initializing CPU#1
[    0.003333] Calibrating delay using timer specific routine.. 6335.46 BogoMIPS (lpj=10554339)
[    0.003333] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003333] CPU: L2 cache: 6144K
[    0.003333] CPU 1/1 -> Node 0
[    0.003333] CPU: Physical Processor ID: 0
[    0.003333] CPU: Processor Core ID: 1
[    0.003333] CPU1: Thermal monitoring enabled (TM2)
[    1.700650] CPU1: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 0a
[    1.700664] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    1.703316] Brought up 2 CPUs
[    1.703317] Total of 2 processors activated (12670.90 BogoMIPS).
[    1.703355] CPU0 attaching sched-domain:
[    1.703357]  domain 0: span 0-1 level MC
[    1.703358]   groups: 0 1
[    1.703360]   domain 1: span 0-1 level NODE
[    1.703362]    groups: 0-1
[    1.703364] CPU1 attaching sched-domain:
[    1.703365]  domain 0: span 0-1 level MC
[    1.703367]   groups: 1 0
[    1.703368]   domain 1: span 0-1 level NODE
[    1.703370]    groups: 0-1
[    1.703424] net_namespace: 1552 bytes
[    1.703424] Booting paravirtualized kernel on bare hardware
[    1.703441] Time:  7:09:22  Date: 04/08/09
[    1.703458] NET: Registered protocol family 16
[    1.703470] ACPI: bus type pci registered
[    1.703470] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.703470] PCI: Not using MMCONFIG.
[    1.703470] PCI: Using configuration type 1 for base access
[    1.703879] ACPI: EC: Look up EC in DSDT
[    1.716993] ACPI: Interpreter enabled
[    1.716995] ACPI: (supports S0 S1 S3 S4 S5)
[    1.717005] ACPI: Using IOAPIC for interrupt routing
[    1.717048] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.719355] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    1.723933] PCI: Using MMCONFIG at e0000000 - efffffff
[    1.730059] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.730059] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    1.730059] pci 0000:00:06.0: PME# disabled
[    1.730059] PCI: 0000:00:1a.0 reg 20 io port: [8800, 881f]
[    1.730105] PCI: 0000:00:1a.1 reg 20 io port: [8880, 889f]
[    1.730150] PCI: 0000:00:1a.2 reg 20 io port: [8c00, 8c1f]
[    1.730199] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fe4ffc00, fe4fffff]
[    1.730235] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.730238] pci 0000:00:1a.7: PME# disabled
[    1.730260] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fe4f8000, fe4fbfff]
[    1.730287] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.730289] pci 0000:00:1b.0: PME# disabled
[    1.730322] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.730325] pci 0000:00:1c.0: PME# disabled
[    1.730360] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.730362] pci 0000:00:1c.4: PME# disabled
[    1.730395] PCI: 0000:00:1d.0 reg 20 io port: [8080, 809f]
[    1.730441] PCI: 0000:00:1d.1 reg 20 io port: [8400, 841f]
[    1.730486] PCI: 0000:00:1d.2 reg 20 io port: [8480, 849f]
[    1.730537] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fe4ff800, fe4ffbff]
[    1.730572] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.730575] pci 0000:00:1d.7: PME# disabled
[    1.730689] PCI: 0000:00:1f.2 reg 10 io port: [7c00, 7c07]
[    1.730692] PCI: 0000:00:1f.2 reg 14 io port: [7880, 7883]
[    1.730696] PCI: 0000:00:1f.2 reg 18 io port: [7800, 7807]
[    1.730700] PCI: 0000:00:1f.2 reg 1c io port: [7480, 7483]
[    1.730704] PCI: 0000:00:1f.2 reg 20 io port: [7400, 741f]
[    1.730708] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fe4fe800, fe4fefff]
[    1.730724] pci 0000:00:1f.2: PME# supported from D3hot
[    1.730727] pci 0000:00:1f.2: PME# disabled
[    1.730740] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fe4ff400, fe4ff4ff]
[    1.730750] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    1.730779] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    1.730788] PCI: 0000:01:00.0 reg 18 64bit mmio: [fe5e0000, fe5effff]
[    1.730792] PCI: 0000:01:00.0 reg 20 io port: [9000, 90ff]
[    1.730798] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe5c0000, fe5dffff]
[    1.730809] pci 0000:01:00.0: supports D1
[    1.730810] pci 0000:01:00.0: supports D2
[    1.730827] PCI: 0000:01:00.1 reg 10 64bit mmio: [fe5fc000, fe5fffff]
[    1.730851] pci 0000:01:00.1: supports D1
[    1.730852] pci 0000:01:00.1: supports D2
[    1.730878] PCI: bridge 0000:00:06.0 io port: [9000, 9fff]
[    1.730880] PCI: bridge 0000:00:06.0 32bit mmio: [fe500000, fe5fffff]
[    1.730882] PCI: bridge 0000:00:06.0 64bit mmio pref: [d0000000, dfffffff]
[    1.730938] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.730942] pci 0000:03:00.0: PME# disabled
[    1.730965] PCI: bridge 0000:00:1c.0 io port: [b000, efff]
[    1.730968] PCI: bridge 0000:00:1c.0 32bit mmio: [fe700000, feafffff]
[    1.731032] pci 0000:04:01.0: PME# supported from D0 D3hot D3cold
[    1.731036] pci 0000:04:01.0: PME# disabled
[    1.731090] pci 0000:04:02.0: PME# supported from D0 D3hot D3cold
[    1.731094] pci 0000:04:02.0: PME# disabled
[    1.731148] pci 0000:04:03.0: PME# supported from D0 D3hot D3cold
[    1.731152] pci 0000:04:03.0: PME# disabled
[    1.731206] pci 0000:04:04.0: PME# supported from D0 D3hot D3cold
[    1.731210] pci 0000:04:04.0: PME# disabled
[    1.731264] pci 0000:04:05.0: PME# supported from D0 D3hot D3cold
[    1.731268] pci 0000:04:05.0: PME# disabled
[    1.731322] pci 0000:04:06.0: PME# supported from D0 D3hot D3cold
[    1.731326] pci 0000:04:06.0: PME# disabled
[    1.731359] PCI: bridge 0000:03:00.0 io port: [b000, efff]
[    1.731363] PCI: bridge 0000:03:00.0 32bit mmio: [fe700000, feafffff]
[    1.731485] PCI: 0000:06:00.0 reg 10 64bit mmio: [fe7fc000, fe7fffff]
[    1.731493] PCI: 0000:06:00.0 reg 18 io port: [b800, b8ff]
[    1.731520] PCI: 0000:06:00.0 reg 30 32bit mmio: [fe7c0000, fe7dffff]
[    1.731540] pci 0000:06:00.0: supports D1
[    1.731541] pci 0000:06:00.0: supports D2
[    1.731542] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.731547] pci 0000:06:00.0: PME# disabled
[    1.731586] PCI: bridge 0000:04:02.0 io port: [b000, bfff]
[    1.731590] PCI: bridge 0000:04:02.0 32bit mmio: [fe700000, fe7fffff]
[    1.731659] PCI: 0000:07:00.0 reg 10 64bit mmio: [fe8fc000, fe8fffff]
[    1.731666] PCI: 0000:07:00.0 reg 18 io port: [c800, c8ff]
[    1.731694] PCI: 0000:07:00.0 reg 30 32bit mmio: [fe8c0000, fe8dffff]
[    1.731714] pci 0000:07:00.0: supports D1
[    1.731715] pci 0000:07:00.0: supports D2
[    1.731716] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.731721] pci 0000:07:00.0: PME# disabled
[    1.731760] PCI: bridge 0000:04:03.0 io port: [c000, cfff]
[    1.731764] PCI: bridge 0000:04:03.0 32bit mmio: [fe800000, fe8fffff]
[    1.731833] PCI: 0000:08:00.0 reg 10 64bit mmio: [fe9fc000, fe9fffff]
[    1.731841] PCI: 0000:08:00.0 reg 18 io port: [d800, d8ff]
[    1.731868] PCI: 0000:08:00.0 reg 30 32bit mmio: [fe9c0000, fe9dffff]
[    1.731888] pci 0000:08:00.0: supports D1
[    1.731889] pci 0000:08:00.0: supports D2
[    1.731890] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.731895] pci 0000:08:00.0: PME# disabled
[    1.731934] PCI: bridge 0000:04:04.0 io port: [d000, dfff]
[    1.731938] PCI: bridge 0000:04:04.0 32bit mmio: [fe900000, fe9fffff]
[    1.732007] PCI: 0000:09:00.0 reg 10 64bit mmio: [feafc000, feafffff]
[    1.732014] PCI: 0000:09:00.0 reg 18 io port: [e800, e8ff]
[    1.732042] PCI: 0000:09:00.0 reg 30 32bit mmio: [feac0000, feadffff]
[    1.732062] pci 0000:09:00.0: supports D1
[    1.732063] pci 0000:09:00.0: supports D2
[    1.732064] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.732068] pci 0000:09:00.0: PME# disabled
[    1.732108] PCI: bridge 0000:04:05.0 io port: [e000, efff]
[    1.732112] PCI: bridge 0000:04:05.0 32bit mmio: [fea00000, feafffff]
[    1.732251] PCI: 0000:02:00.0 reg 10 io port: [ac00, ac07]
[    1.732257] PCI: 0000:02:00.0 reg 14 io port: [a880, a883]
[    1.732263] PCI: 0000:02:00.0 reg 18 io port: [a800, a807]
[    1.732269] PCI: 0000:02:00.0 reg 1c io port: [a480, a483]
[    1.732275] PCI: 0000:02:00.0 reg 20 io port: [a400, a40f]
[    1.732281] PCI: 0000:02:00.0 reg 24 32bit mmio: [fe6ffc00, fe6fffff]
[    1.733312] pci 0000:02:00.0: supports D1
[    1.733313] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    1.733316] pci 0000:02:00.0: PME# disabled
[    1.733340] PCI: bridge 0000:00:1c.4 io port: [a000, afff]
[    1.733342] PCI: bridge 0000:00:1c.4 32bit mmio: [fe600000, fe6fffff]
[    1.733373] PCI: 0000:0b:03.0 reg 10 32bit mmio: [febff000, febfffff]
[    1.733406] pci 0000:0b:03.0: supports D1
[    1.733407] pci 0000:0b:03.0: supports D2
[    1.733408] pci 0000:0b:03.0: PME# supported from D0 D1 D2 D3hot
[    1.733411] pci 0000:0b:03.0: PME# disabled
[    1.733439] pci 0000:00:1e.0: transparent bridge
[    1.733443] PCI: bridge 0000:00:1e.0 32bit mmio: [feb00000, febfffff]
[    1.733461] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.733643] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    1.733723] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.733838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    1.733929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.734012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4.P4PB.PBPC._PRT]
[    1.734092] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4.P4PB.PBPD._PRT]
[    1.734171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4.P4PB.PBPE._PRT]
[    1.734251] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4.P4PB.PBPF._PRT]
[    1.734331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4.P4PB.BR10._PRT]
[    1.734411] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4.P4PB.BR11._PRT]
[    1.747401] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.747401] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.747401] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    1.747401] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    1.747401] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.747401] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    1.747401] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.747434] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    1.747478] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 3E, should be 35 [20080609]
[    1.747478] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.747478] pnp: PnP ACPI init
[    1.747478] ACPI: bus type pnp registered
[    1.750436] pnp: PnP ACPI: found 16 devices
[    1.750436] ACPI: ACPI bus type pnp unregistered
[    1.750436] PCI: Using ACPI for IRQ routing
[    1.763308] NET: Registered protocol family 8
[    1.763310] NET: Registered protocol family 20
[    1.763322] NetLabel: Initializing
[    1.763322] NetLabel:  domain hash size = 128
[    1.763322] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.763331] NetLabel:  unlabeled traffic allowed by default
[    1.763353] PCI-GART: No AMD northbridge found.
[    1.763358] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.763362] hpet0: 4 64-bit timers, 14318180 Hz
[    1.765101] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    1.765102]    actual entries 65586
[    1.765149] AppArmor: AppArmor Filesystem Enabled
[    1.765163] ACPI: RTC can wake from S4
[    1.766639] Switched to high resolution mode on CPU 0
[    1.767337] Switched to high resolution mode on CPU 1
[    1.773352] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    1.773360] system 00:07: ioport range 0x290-0x29f has been reserved
[    1.773371] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    1.773373] system 00:08: ioport range 0x800-0x87f has been reserved
[    1.773375] system 00:08: ioport range 0x500-0x57f has been reserved
[    1.773378] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[    1.773381] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.773383] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.773386] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    1.773392] system 00:0b: iomem range 0xffc00000-0xffdfffff has been reserved
[    1.773398] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.773400] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.773405] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    1.773412] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    1.773414] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[    1.773416] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    1.773419] system 00:0f: iomem range 0x100000-0xcfffffff could not be reserved
[    1.778335] pci 0000:00:06.0: PCI bridge, secondary bus 0000:01
[    1.778337] pci 0000:00:06.0:   IO window: 0x9000-0x9fff
[    1.778339] pci 0000:00:06.0:   MEM window: 0xfe500000-0xfe5fffff
[    1.778341] pci 0000:00:06.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.778344] pci 0000:04:01.0: PCI bridge, secondary bus 0000:05
[    1.778346] pci 0000:04:01.0:   IO window: disabled
[    1.778351] pci 0000:04:01.0:   MEM window: disabled
[    1.778355] pci 0000:04:01.0:   PREFETCH window: disabled
[    1.778362] pci 0000:04:02.0: PCI bridge, secondary bus 0000:06
[    1.778365] pci 0000:04:02.0:   IO window: 0xb000-0xbfff
[    1.778370] pci 0000:04:02.0:   MEM window: 0xfe700000-0xfe7fffff
[    1.778374] pci 0000:04:02.0:   PREFETCH window: disabled
[    1.778381] pci 0000:04:03.0: PCI bridge, secondary bus 0000:07
[    1.778384] pci 0000:04:03.0:   IO window: 0xc000-0xcfff
[    1.778389] pci 0000:04:03.0:   MEM window: 0xfe800000-0xfe8fffff
[    1.778393] pci 0000:04:03.0:   PREFETCH window: disabled
[    1.778401] pci 0000:04:04.0: PCI bridge, secondary bus 0000:08
[    1.778403] pci 0000:04:04.0:   IO window: 0xd000-0xdfff
[    1.778409] pci 0000:04:04.0:   MEM window: 0xfe900000-0xfe9fffff
[    1.778413] pci 0000:04:04.0:   PREFETCH window: disabled
[    1.778420] pci 0000:04:05.0: PCI bridge, secondary bus 0000:09
[    1.778422] pci 0000:04:05.0:   IO window: 0xe000-0xefff
[    1.778428] pci 0000:04:05.0:   MEM window: 0xfea00000-0xfeafffff
[    1.778432] pci 0000:04:05.0:   PREFETCH window: disabled
[    1.778439] pci 0000:04:06.0: PCI bridge, secondary bus 0000:0a
[    1.778440] pci 0000:04:06.0:   IO window: disabled
[    1.778445] pci 0000:04:06.0:   MEM window: disabled
[    1.778449] pci 0000:04:06.0:   PREFETCH window: disabled
[    1.778456] pci 0000:03:00.0: PCI bridge, secondary bus 0000:04
[    1.778458] pci 0000:03:00.0:   IO window: 0xb000-0xefff
[    1.778464] pci 0000:03:00.0:   MEM window: 0xfe700000-0xfeafffff
[    1.778468] pci 0000:03:00.0:   PREFETCH window: disabled
[    1.778475] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    1.778477] pci 0000:00:1c.0:   IO window: 0xb000-0xefff
[    1.778480] pci 0000:00:1c.0:   MEM window: 0xfe700000-0xfeafffff
[    1.778483] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.778487] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:02
[    1.778488] pci 0000:00:1c.4:   IO window: 0xa000-0xafff
[    1.778492] pci 0000:00:1c.4:   MEM window: 0xfe600000-0xfe6fffff
[    1.778494] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.778498] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0b
[    1.778499] pci 0000:00:1e.0:   IO window: disabled
[    1.778502] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    1.778505] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.778513] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.778515] pci 0000:00:06.0: setting latency timer to 64
[    1.778520] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.778523] pci 0000:00:1c.0: setting latency timer to 64
[    1.778532] pci 0000:03:00.0: setting latency timer to 64
[    1.778542] pci 0000:04:01.0: setting latency timer to 64
[    1.778551] pci 0000:04:02.0: setting latency timer to 64
[    1.778561] pci 0000:04:03.0: setting latency timer to 64
[    1.778571] pci 0000:04:04.0: setting latency timer to 64
[    1.778581] pci 0000:04:05.0: setting latency timer to 64
[    1.778590] pci 0000:04:06.0: setting latency timer to 64
[    1.778595] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.778598] pci 0000:00:1c.4: setting latency timer to 64
[    1.778602] pci 0000:00:1e.0: setting latency timer to 64
[    1.778604] bus: 00 index 0 io port: [0, ffff]
[    1.778606] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    1.778607] bus: 01 index 0 io port: [9000, 9fff]
[    1.778608] bus: 01 index 1 mmio: [fe500000, fe5fffff]
[    1.778609] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    1.778610] bus: 01 index 3 mmio: [0, 0]
[    1.778611] bus: 03 index 0 io port: [b000, efff]
[    1.778612] bus: 03 index 1 mmio: [fe700000, feafffff]
[    1.778613] bus: 03 index 2 mmio: [0, 0]
[    1.778614] bus: 03 index 3 mmio: [0, 0]
[    1.778615] bus: 04 index 0 io port: [b000, efff]
[    1.778616] bus: 04 index 1 mmio: [fe700000, feafffff]
[    1.778617] bus: 04 index 2 mmio: [0, 0]
[    1.778618] bus: 04 index 3 mmio: [0, 0]
[    1.778619] bus: 05 index 0 mmio: [0, 0]
[    1.778620] bus: 05 index 1 mmio: [0, 0]
[    1.778621] bus: 05 index 2 mmio: [0, 0]
[    1.778622] bus: 05 index 3 mmio: [0, 0]
[    1.778623] bus: 06 index 0 io port: [b000, bfff]
[    1.778624] bus: 06 index 1 mmio: [fe700000, fe7fffff]
[    1.778625] bus: 06 index 2 mmio: [0, 0]
[    1.778626] bus: 06 index 3 mmio: [0, 0]
[    1.778627] bus: 07 index 0 io port: [c000, cfff]
[    1.778628] bus: 07 index 1 mmio: [fe800000, fe8fffff]
[    1.778629] bus: 07 index 2 mmio: [0, 0]
[    1.778630] bus: 07 index 3 mmio: [0, 0]
[    1.778631] bus: 08 index 0 io port: [d000, dfff]
[    1.778632] bus: 08 index 1 mmio: [fe900000, fe9fffff]
[    1.778633] bus: 08 index 2 mmio: [0, 0]
[    1.778634] bus: 08 index 3 mmio: [0, 0]
[    1.778635] bus: 09 index 0 io port: [e000, efff]
[    1.778637] bus: 09 index 1 mmio: [fea00000, feafffff]
[    1.778638] bus: 09 index 2 mmio: [0, 0]
[    1.778639] bus: 09 index 3 mmio: [0, 0]
[    1.778640] bus: 0a index 0 mmio: [0, 0]
[    1.778640] bus: 0a index 1 mmio: [0, 0]
[    1.778641] bus: 0a index 2 mmio: [0, 0]
[    1.778642] bus: 0a index 3 mmio: [0, 0]
[    1.778643] bus: 02 index 0 io port: [a000, afff]
[    1.778644] bus: 02 index 1 mmio: [fe600000, fe6fffff]
[    1.778646] bus: 02 index 2 mmio: [0, 0]
[    1.778646] bus: 02 index 3 mmio: [0, 0]
[    1.778648] bus: 0b index 0 mmio: [0, 0]
[    1.778649] bus: 0b index 1 mmio: [feb00000, febfffff]
[    1.778650] bus: 0b index 2 mmio: [0, 0]
[    1.778651] bus: 0b index 3 io port: [0, ffff]
[    1.778652] bus: 0b index 4 mmio: [0, ffffffffffffffff]
[    1.778658] NET: Registered protocol family 2
[    1.810215] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.811068] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.813275] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.813612] TCP: Hash tables configured (established 524288 bind 65536)
[    1.813614] TCP reno registered
[    1.823414] NET: Registered protocol family 1
[    1.823510] checking if image is initramfs... it is
[    4.996019] Freeing initrd memory: 51451k freed
[    5.010797] audit: initializing netlink socket (disabled)
[    5.010810] type=2000 audit(1239174565.007:1): initialized
[    5.014724] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    5.016162] VFS: Disk quotas dquot_6.5.1
[    5.016210] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    5.016267] msgmni has been set to 15982
[    5.016335] io scheduler noop registered
[    5.016336] io scheduler anticipatory registered
[    5.016337] io scheduler deadline registered (default)
[    5.016406] io scheduler cfq registered
[    5.016509] pci 0000:01:00.0: Boot video device
[    5.016596] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    5.016614] pcieport-driver 0000:00:06.0: found MSI capability
[    5.016631] pci_express 0000:00:06.0:pcie00: allocate port service
[    5.016654] pci_express 0000:00:06.0:pcie03: allocate port service
[    5.016703] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    5.016725] pcieport-driver 0000:00:1c.0: found MSI capability
[    5.016748] pci_express 0000:00:1c.0:pcie00: allocate port service
[    5.016772] pci_express 0000:00:1c.0:pcie02: allocate port service
[    5.016794] pci_express 0000:00:1c.0:pcie03: allocate port service
[    5.016850] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    5.016873] pcieport-driver 0000:00:1c.4: found MSI capability
[    5.016895] pci_express 0000:00:1c.4:pcie00: allocate port service
[    5.016917] pci_express 0000:00:1c.4:pcie02: allocate port service
[    5.016942] pci_express 0000:00:1c.4:pcie03: allocate port service
[    5.017005] pcieport-driver 0000:03:00.0: setting latency timer to 64
[    5.017044] pci_express 0000:03:00.0:pcie11: allocate port service
[    5.017066] pci_express 0000:03:00.0:pcie13: allocate port service
[    5.017147] pcieport-driver 0000:04:01.0: setting latency timer to 64
[    5.017190] pcieport-driver 0000:04:01.0: found MSI capability
[    5.017246] pci_express 0000:04:01.0:pcie21: allocate port service
[    5.017271] pci_express 0000:04:01.0:pcie23: allocate port service
[    5.017356] pcieport-driver 0000:04:02.0: setting latency timer to 64
[    5.017398] pcieport-driver 0000:04:02.0: found MSI capability
[    5.017452] pci_express 0000:04:02.0:pcie21: allocate port service
[    5.017475] pci_express 0000:04:02.0:pcie23: allocate port service
[    5.017562] pcieport-driver 0000:04:03.0: setting latency timer to 64
[    5.017604] pcieport-driver 0000:04:03.0: found MSI capability
[    5.017658] pci_express 0000:04:03.0:pcie21: allocate port service
[    5.017683] pci_express 0000:04:03.0:pcie23: allocate port service
[    5.017767] pcieport-driver 0000:04:04.0: setting latency timer to 64
[    5.017809] pcieport-driver 0000:04:04.0: found MSI capability
[    5.017863] pci_express 0000:04:04.0:pcie21: allocate port service
[    5.017886] pci_express 0000:04:04.0:pcie23: allocate port service
[    5.017969] pcieport-driver 0000:04:05.0: setting latency timer to 64
[    5.018011] pcieport-driver 0000:04:05.0: found MSI capability
[    5.018065] pci_express 0000:04:05.0:pcie21: allocate port service
[    5.018089] pci_express 0000:04:05.0:pcie23: allocate port service
[    5.018171] pcieport-driver 0000:04:06.0: setting latency timer to 64
[    5.018213] pcieport-driver 0000:04:06.0: found MSI capability
[    5.018267] pci_express 0000:04:06.0:pcie21: allocate port service
[    5.018291] pci_express 0000:04:06.0:pcie23: allocate port service
[    5.036323] hpet_resources: 0xfed00000 is busy
[    5.036370] Linux agpgart interface v0.103
[    5.036373] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    5.036470] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    5.036875] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    5.037841] brd: module loaded
[    5.037883] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    5.037979] PNP: No PS/2 controller found. Probing ports directly.
[    5.040251] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.040255] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.057598] mice: PS/2 mouse device common for all mice
[    5.057696] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    5.057715] rtc0: alarms up to one month, y3k, hpet irqs
[    5.057740] cpuidle: using governor ladder
[    5.057741] cpuidle: using governor menu
[    5.057961] TCP cubic registered
[    5.058069] registered taskstats version 1
[    5.058166]   Magic number: 5:942:166
[    5.058178] tty ttyq6: hash matches
[    5.058232] rtc_cmos 00:03: setting system clock to 2009-04-08 07:09:25 UTC (1239174565)
[    5.058234] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.058235] EDD information not available.
[    5.058258] Freeing unused kernel memory: 504k freed
[    5.058383] Write protecting the kernel read-only data: 4208k
[    5.150098] fuse init (API version 7.9)
[    5.169614] processor ACPI0007:00: registered as cooling_device0
[    5.169828] processor ACPI0007:01: registered as cooling_device1
[    5.341866] usbcore: registered new interface driver usbfs
[    5.341879] usbcore: registered new interface driver hub
[    5.345759] usbcore: registered new device driver usb
[    5.347275] USB Universal Host Controller Interface driver v3.0
[    5.347303] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.347310] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.347312] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.347336] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    5.347361] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00008800
[    5.347451] usb usb1: configuration #1 chosen from 1 choice
[    5.347467] hub 1-0:1.0: USB hub found
[    5.347471] hub 1-0:1.0: 2 ports detected
[    5.381260] No dock devices found.
[    5.389674] SCSI subsystem initialized
[    5.409984] libata version 3.00 loaded.
[    5.553504] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.553512] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.553514] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.553529] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    5.553555] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00008880
[    5.553608] usb usb2: configuration #1 chosen from 1 choice
[    5.553625] hub 2-0:1.0: USB hub found
[    5.553629] hub 2-0:1.0: 2 ports detected
[    5.656856] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.656863] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    5.656865] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    5.656880] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    5.656904] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00008c00
[    5.656957] usb usb3: configuration #1 chosen from 1 choice
[    5.656973] hub 3-0:1.0: USB hub found
[    5.656977] hub 3-0:1.0: 2 ports detected
[    5.660010] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    5.813444] usb 1-2: configuration #1 chosen from 1 choice
[    5.863499] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.863509] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.863511] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.863526] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    5.867425] ehci_hcd 0000:00:1a.7: debug port 1
[    5.867429] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    5.867432] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe4ffc00
[    5.970010] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    5.980840] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.980902] usb usb4: configuration #1 chosen from 1 choice
[    5.980933] hub 4-0:1.0: USB hub found
[    5.980939] hub 4-0:1.0: 6 ports detected
[    6.034207] hub 3-0:1.0: unable to enumerate USB device on port 1
[    6.096701] usb 1-2: USB disconnect, address 2
[    6.186967] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    6.186971] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    6.186973] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.186988] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    6.187010] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00008080
[    6.187058] usb usb5: configuration #1 chosen from 1 choice
[    6.187072] hub 5-0:1.0: USB hub found
[    6.187076] hub 5-0:1.0: 2 ports detected
[    6.290334] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    6.290338] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    6.290340] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.290356] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    6.290378] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00008400
[    6.290432] usb usb6: configuration #1 chosen from 1 choice
[    6.290447] hub 6-0:1.0: USB hub found
[    6.290450] hub 6-0:1.0: 2 ports detected
[    6.430008] usb 4-5: new high speed USB device using ehci_hcd and address 3
[    6.497025] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.497029] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    6.497031] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.497046] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    6.497064] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008480
[    6.497112] usb usb7: configuration #1 chosen from 1 choice
[    6.497129] hub 7-0:1.0: USB hub found
[    6.497133] hub 7-0:1.0: 2 ports detected
[    6.554728] usb 4-5: configuration #1 chosen from 1 choice
[    6.555098] hub 4-5:1.0: USB hub found
[    6.555246] hub 4-5:1.0: 4 ports detected
[    6.600170] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    6.600175] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    6.600177] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.600191] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    6.604075] ehci_hcd 0000:00:1d.7: debug port 1
[    6.604079] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    6.604081] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe4ff800
[    6.617506] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.617764] usb usb8: configuration #1 chosen from 1 choice
[    6.617934] hub 8-0:1.0: USB hub found
[    6.617938] hub 8-0:1.0: 6 ports detected
[    6.824878] ahci 0000:00:1f.2: version 3.0
[    6.824885] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    6.824951] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    6.824953] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    6.824956] ahci 0000:00:1f.2: setting latency timer to 64
[    6.825146] scsi0 : ahci
[    6.825205] scsi1 : ahci
[    6.825241] scsi2 : ahci
[    6.825275] scsi3 : ahci
[    6.825310] scsi4 : ahci
[    6.825346] scsi5 : ahci
[    6.825422] ata1: SATA max UDMA/133 abar m2048@0xfe4fe800 port 0xfe4fe900 irq 310
[    6.825424] ata2: SATA max UDMA/133 abar m2048@0xfe4fe800 port 0xfe4fe980 irq 310
[    6.825425] ata3: SATA max UDMA/133 abar m2048@0xfe4fe800 port 0xfe4fea00 irq 310
[    6.825427] ata4: SATA max UDMA/133 abar m2048@0xfe4fe800 port 0xfe4fea80 irq 310
[    6.825429] ata5: SATA max UDMA/133 abar m2048@0xfe4fe800 port 0xfe4feb00 irq 310
[    6.825430] ata6: SATA max UDMA/133 abar m2048@0xfe4fe800 port 0xfe4feb80 irq 310
[    6.986676] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    7.139656] usb 1-2: configuration #1 chosen from 1 choice
[    7.143347] ata1: SATA link down (SStatus 0 SControl 300)
[    7.463508] usb 4-5.2: new high speed USB device using ehci_hcd and address 4
[    7.476680] ata2: SATA link down (SStatus 0 SControl 300)
[    7.560568] usb 4-5.2: configuration #1 chosen from 1 choice
[    7.560808] hub 4-5.2:1.0: USB hub found
[    7.560877] hub 4-5.2:1.0: 4 ports detected
[    7.810011] ata3: SATA link down (SStatus 0 SControl 300)
[    8.060132] usb 4-5.2.3: new high speed USB device using ehci_hcd and address 5
[    8.143347] ata4: SATA link down (SStatus 0 SControl 300)
[    8.204649] usb 4-5.2.3: configuration #1 chosen from 1 choice
[    8.286759] usb 4-5.2.4: new high speed USB device using ehci_hcd and address 6
[    8.383950] usb 4-5.2.4: configuration #1 chosen from 1 choice
[    8.384186] hub 4-5.2.4:1.0: USB hub found
[    8.384255] hub 4-5.2.4:1.0: 2 ports detected
[    8.476678] ata5: SATA link down (SStatus 0 SControl 300)
[    8.810011] ata6: SATA link down (SStatus 0 SControl 300)
[    8.816675] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    8.823602] sky2 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.823612] sky2 0000:06:00.0: setting latency timer to 64
[    8.823629] sky2 0000:06:00.0: v1.22 addr 0xfe7fc000 irq 18 Yukon-2 EC Ultra rev 3
[    8.824357] sky2 eth0: addr 00:22:15:4b:92:d1
[    8.824373] sky2 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.824380] sky2 0000:07:00.0: setting latency timer to 64
[    8.824393] sky2 0000:07:00.0: v1.22 addr 0xfe8fc000 irq 19 Yukon-2 EC Ultra rev 3
[    8.824667] sky2 eth1: addr 00:22:15:4b:92:d2
[    8.824682] sky2 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.824688] sky2 0000:08:00.0: setting latency timer to 64
[    8.824701] sky2 0000:08:00.0: v1.22 addr 0xfe9fc000 irq 16 Yukon-2 EC Ultra rev 3
[    8.824969] sky2 eth2: addr 00:22:15:4b:92:d3
[    8.824984] sky2 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.824990] sky2 0000:09:00.0: setting latency timer to 64
[    8.825004] sky2 0000:09:00.0: v1.22 addr 0xfeafc000 irq 17 Yukon-2 EC Ultra rev 3
[    8.825283] sky2 eth3: addr 00:22:15:4b:92:d4
[    8.825298] ohci1394 0000:0b:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.877389] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    8.884784] pata_acpi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.884802] pata_acpi 0000:02:00.0: setting latency timer to 64
[    8.884812] pata_acpi 0000:02:00.0: PCI INT A disabled
[    8.885980] pata_marvell 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.886000] pata_marvell 0000:02:00.0: setting latency timer to 64
[    8.887486] scsi6 : pata_marvell
[    8.887543] scsi7 : pata_marvell
[    8.887566] ata7: PATA max UDMA/100 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 16
[    8.887568] ata8: PATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 16
[    9.012509] usb 6-1: configuration #1 chosen from 1 choice
[    9.236421] ata8.00: ATA-8: WDC WD1500HLFS-01G6U0, 04.04V01, max UDMA/133
[    9.236424] ata8.00: 293046768 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    9.243341] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    9.247694] ata8.00: configured for UDMA/133
[    9.247771] scsi 7:0:0:0: Direct-Access     ATA      WDC WD1500HLFS-0 04.0 PQ: 0 ANSI: 5
[    9.247876] scsi 7:0:0:0: Attached scsi generic sg0 type 0
[    9.255949] Driver 'sd' needs updating - please use bus_type methods
[    9.255999] sd 7:0:0:0: [sda] 293046768 512-byte hardware sectors (150040 MB)
[    9.256008] sd 7:0:0:0: [sda] Write Protect is off
[    9.256010] sd 7:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.256025] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.256063] sd 7:0:0:0: [sda] 293046768 512-byte hardware sectors (150040 MB)
[    9.256072] sd 7:0:0:0: [sda] Write Protect is off
[    9.256073] sd 7:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.256088] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.256090]  sda: sda1 sda2
[    9.263892] sd 7:0:0:0: [sda] Attached SCSI disk
[    9.416639] usb 6-2: configuration #1 chosen from 1 choice
[    9.419448] hub 6-2:1.0: USB hub found
[    9.421416] hub 6-2:1.0: 3 ports detected
[    9.713391] usb 4-5.2.4.2: new high speed USB device using ehci_hcd and address 7
[    9.812565] usb 4-5.2.4.2: configuration #1 chosen from 1 choice
[    9.881425] usb 6-2.2: new full speed USB device using uhci_hcd and address 4
[   10.025478] usb 6-2.2: configuration #1 chosen from 1 choice
[   10.101425] usb 6-2.3: new full speed USB device using uhci_hcd and address 5
[   10.150098] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00015f071e]
[   10.245477] usb 6-2.3: configuration #1 chosen from 1 choice
[   10.252450] usbcore: registered new interface driver libusual
[   10.252451] usbcore: registered new interface driver hiddev
[   10.256966] Initializing USB Mass Storage driver...
[   10.260478] input: Logitech G9 Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input1
[   10.280110] input,hidraw0: USB HID v1.11 Mouse [Logitech G9 Laser Mouse] on usb-0000:00:1d.1-1
[   10.289534] input: Logitech G9 Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input2
[   10.300910] input,hiddev96,hidraw1: USB HID v1.11 Keyboard [Logitech G9 Laser Mouse] on usb-0000:00:1d.1-1
[   10.301001] scsi8 : SCSI emulation for USB Mass Storage devices
[   10.301046] usb-storage: device found at 7
[   10.301048] usb-storage: waiting for device to settle before scanning
[   10.306493] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2.2/6-2.2:1.0/input/input3
[   10.323373] input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.1-2.2
[   10.333511] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2.3/6-2.3:1.0/input/input4
[   10.354252] input,hiddev97,hidraw3: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.1-2.3
[   10.354282] usbcore: registered new interface driver usb-storage
[   10.354285] USB Mass Storage support registered.
[   10.354459] usbcore: registered new interface driver usbhid
[   10.354461] usbhid: v2.6:USB HID core driver
[   10.396905] PM: Starting manual resume from disk
[   10.396907] PM: Resume from partition 8:1
[   10.396908] PM: Checking hibernation image.
[   10.397043] PM: Resume from disk failed.
[   10.423688] kjournald starting.  Commit interval 5 seconds
[   10.423699] EXT3-fs: mounted filesystem with ordered data mode.
[   14.816276] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.887827] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.887898] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   14.887900] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   14.887901] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   15.012628] udevd version 124 started
[   15.165849] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.221160] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   15.237512] ACPI: Power Button (FF) [PWRF]
[   15.237591] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   15.264719] ACPI: Power Button (CM) [PWRB]
[   15.264879] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.319549] usb-storage: device scan complete
[   15.320301] scsi 8:0:0:0: Direct-Access     HP       DPF              0001 PQ: 0 ANSI: 2
[   15.321174] scsi 8:0:0:1: Direct-Access     HP       DPF              0001 PQ: 0 ANSI: 2
[   15.322044] scsi 8:0:0:2: Direct-Access     HP       DPF              0001 PQ: 0 ANSI: 2
[   15.323728] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[   15.323827] sd 8:0:0:0: Attached scsi generic sg1 type 0
[   15.325343] sd 8:0:0:1: [sdc] Attached SCSI removable disk
[   15.325391] sd 8:0:0:1: Attached scsi generic sg2 type 0
[   15.326841] sd 8:0:0:2: [sdd] Attached SCSI removable disk
[   15.326895] sd 8:0:0:2: Attached scsi generic sg3 type 0
[   15.523004] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.535333] [fglrx] Maximum main memory to use for locked dma buffers: 7758 MBytes.
[   15.535705] [fglrx]   vendor: 1002 device: 9501 count: 1
[   15.536357] [fglrx] ioport: bar 4, base 0x9000, size: 0x100
[   15.536365] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.536368] pci 0000:01:00.0: setting latency timer to 64
[   15.538757] [fglrx] PAT is enabled successfully!
[   15.538777] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   15.726622] usbcore: registered new interface driver usbserial
[   15.726631] usbserial: USB Serial support registered for generic
[   15.726664] usbcore: registered new interface driver usbserial_generic
[   15.726665] usbserial: USB Serial Driver core
[   16.030664] usbserial: USB Serial support registered for pl2303
[   16.030684] pl2303 1-2:1.0: pl2303 converter detected
[   16.042533] usb 1-2: pl2303 converter now attached to ttyUSB0
[   16.042554] usbcore: registered new interface driver pl2303
[   16.042555] pl2303: Prolific PL2303 USB to serial adaptor driver
[   16.133128] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   16.240414] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.240433] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.258328] Linux video capture interface: v2.00
[   16.270933] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[   16.372894] uvcvideo: Found UVC 1.00 device CNF8215 (03f0:b116)
[   16.390011] input: CNF8215 as /devices/pci0000:00/0000:00:1a.7/usb4/4-5/4-5.2/4-5.2.3/4-5.2.3:1.0/input/input8
[   16.407783] usbcore: registered new interface driver uvcvideo
[   16.407785] USB Video Class driver (v0.1.0)
[   16.450421] 5:3:1: cannot get freq at ep 0x84
[   16.464082] usbcore: registered new interface driver snd-usb-audio
[   16.643389] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.643411] HDA Intel 0000:01:00.1: setting latency timer to 64
[   17.641983] loop: module loaded
[   17.696656] lp: driver loaded but no devices found
[   17.772775] coretemp coretemp.0: Using relative temperature scale!
[   17.772803] coretemp coretemp.1: Using relative temperature scale!
[   17.850502] Adding 15623172k swap on /dev/sda1.  Priority:-1 extents:1 across:15623172k
[   18.381573] EXT3 FS on sda2, internal journal
[   19.219499] type=1505 audit(1239174579.621:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4605
[   19.296376] type=1505 audit(1239174579.697:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4610
[   19.296474] type=1505 audit(1239174579.697:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4610
[   19.372420] sky2 eth0: enabling interface
[   20.391472] NET: Registered protocol family 10
[   20.392047] lo: Disabled Privacy Extensions
[   20.392374] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.095373] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   21.096247] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.155620] ACPI: WMI: Mapper loaded
[   21.675210] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   26.767102] ppdev: user-space parallel port driver
[   31.977547] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   31.977551] vboxdrv: Successfully done.
[   31.977552] vboxdrv: Found 2 processor cores.
[   31.978759] VBoxDrv: dbg - g_abExecMemory=ffffffffa0604f00
[   31.978772] vboxdrv: fAsync=0 offMin=0x185 offMax=0xe07
[   31.979361] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.979364] vboxdrv: Successfully loaded version 2.1.4 (interface 0x000a0009).
[   32.086668] eth0: no IPv6 routers present
[   32.187226] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa07a0d80
[   33.060467] Bluetooth: Core ver 2.13
[   33.060774] NET: Registered protocol family 31
[   33.060777] Bluetooth: HCI device and connection manager initialized
[   33.060779] Bluetooth: HCI socket layer initialized
[   33.071925] Bluetooth: L2CAP ver 2.11
[   33.071927] Bluetooth: L2CAP socket layer initialized
[   33.088456] Bluetooth: RFCOMM socket layer initialized
[   33.088465] Bluetooth: RFCOMM TTY layer initialized
[   33.088466] Bluetooth: RFCOMM ver 1.10
[   33.104323] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.104327] Bluetooth: BNEP filters: protocol multicast
[   33.472376] Bridge firewalling registered
[   33.472699] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   33.483862] Bluetooth: SCO (Voice Link) ver 0.6
[   33.483865] Bluetooth: SCO socket layer initialized
[   36.733604] [fglrx] CMM init INV FB MC:0xd0000000, length:0x10000000
[   36.733612] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   36.733613] [fglrx] Reserved FB block: Unshared offset:ff77000, size:88000 
[   37.206853] sky2 eth3: enabling interface
[   37.210689] ADDRCONF(NETDEV_UP): eth3: link is not ready
[   37.211375] sky2 eth2: enabling interface
[   37.215236] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   37.215526] sky2 eth1: enabling interface
[   37.219313] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   39.834579] usbcore: registered new interface driver wacom
[   39.835105] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
[  125.031662] 5:3:1: cannot get freq at ep 0x84
[  214.543258] type=1503 audit(1239174775.325:5): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=8237 profile="/usr/sbin/cupsd"
```

---

### Post by jsastrem on 2009-04-08
By the way, I have Compiz and Emerald installed, but finally set Metacity as window manager and GTK as window decorator due to flickering problems in OpenGL windows and video windows.

---

