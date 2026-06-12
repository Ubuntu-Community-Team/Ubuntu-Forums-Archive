---
title: "No USB Detected, Ubuntu 10.10"
date: 2010-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Zoltar567 on 2010-11-02
Hello everyone. I am using Ubuntu 10.10 AMD 64 on my Dell Inspiron 1546 laptop.

I initially ran 10.04 using the Windows installer, but it froze often and didnt work properly, so i installed 10.10 to its own partition. 

Inside 10.04 everything worked great when it wasnt freezing. Even when installing 10.10 in Windows, my USB ports would NOT function. 

I have been snooping around the forums a great deal before posting this thread, and nothing can seem to answer my questions. 

I will plug a USB flashdrive into a port, and the light on the flash drive will light up, but nothing is recognized in the system. 

I use ```
sudo fdisk -l
``` and nothing related to USB shows up. This is what i get ```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x983f7c98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       29127   218556600    7  HPFS/NTFS
/dev/sda4           29127       30402    10238977    5  Extended
/dev/sda5           29127       30402    10238976   83  Linux

```I also tried sudo lsusb, and litterally nothing shows up.

I tried my wireless USB mouse to no avail, and a wired mouse, nothing functions.

I looked inside my file system to find there is so /proc/sys/usb or /proc/bus/usb. THe directories dont even exist. 
Any ideas?

---

### Post by P4man on 2010-11-03
can you post the contents of ```
/var/log/dmesg
```  and the output of ```
lspci
```

---

### Post by Zoltar567 on 2010-11-03
Sure.

dsmeg```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-23-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #36-Ubuntu SMP Tue Oct 26 17:13:06 UTC 2010 (Ubuntu 2.6.35-23.36-generic 2.6.35.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=05487332-07e0-4ffe-bd85-d5eaf26a85ee ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfec5400 (usable)
[    0.000000]  BIOS-e820: 00000000cfec5400 - 00000000d4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 00C0000000 mask FFF0000000 write-back
[    0.000000]   3 base 0100000000 mask FF00000000 write-back
[    0.000000]   4 base 00CFF00000 mask FFFFF00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 base 00FFFC8000 mask FFFFFF0000 write-protect
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xcfec5 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfec5400 (usable)
[    0.000000]  modified: 00000000cfec5400 - 00000000d4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfec5000
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfec5000 page 4k
[    0.000000] kernel direct mapping tables up to cfec5000 @ 16000-1c000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 1a000-20000
[    0.000000] RAMDISK: 37570000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fbd20 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000cfec6e00 00054 (v01 DELL    WN09    27DA0201 ASL  00000061)
[    0.000000] ACPI: FACP 00000000cfec6c9c 000F4 (v04 DELL    WN09    27DA0201 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000cfec7400 04E47 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 00000000cfed5800 00040
[    0.000000] ACPI: HPET 00000000cfec6f00 00038 (v01 DELL    WN09    00000001 ASL  00000061)
[    0.000000] ACPI: APIC 00000000cfec7000 00068 (v01 DELL    WN09    27DA0201 ASL  00000047)
[    0.000000] ACPI: MCFG 00000000cfec6fc0 0003E (v16 DELL    WN09    27DA0201 ASL  00000061)
[    0.000000] ACPI: SLIC 00000000cfec709c 00176 (v01 DELL    WN09    27DA0201 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000cfed5c00 00386 (v01 DELL    WN09    27DA0201 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880100200000-ffff880103bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfec5
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048148
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3927 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833277 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x3008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1b000 - 1b7ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfec5000 - 00000000cfec6000
[    0.000000] PM: Registered nosave memory: 00000000cfec6000 - 00000000d4000000
[    0.000000] PM: Registered nosave memory: 00000000d4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
[    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d4000000:2ac00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u1048576
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031124
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=05487332-07e0-4ffe-bd85-d5eaf26a85ee ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (48 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037570000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [000009f000 - 0000100000]   BIOS reserved
[    0.000000]   #4 [0001d18000 - 0001d181e8]             BRK
[    0.000000]   #5 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #6 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #7 [0000016000 - 000001a000]         PGTABLE
[    0.000000]   #8 [000001a000 - 000001b000]         PGTABLE
[    0.000000]   #9 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #10 [0001d18200 - 0001d19200]         BOOTMEM
[    0.000000]   #11 [0001d17140 - 0001d17440]         BOOTMEM
[    0.000000]   #12 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #13 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #14 [0100200000 - 0103c00000]        MEMMAP 0
[    0.000000]   #15 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #16 [0001d19200 - 0001d31200]         BOOTMEM
[    0.000000]   #17 [0001d31200 - 0001d37200]         BOOTMEM
[    0.000000]   #18 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #19 [0001d175c0 - 0001d17601]         BOOTMEM
[    0.000000]   #20 [0001d17640 - 0001d17683]         BOOTMEM
[    0.000000]   #21 [0001d176c0 - 0001d178b8]         BOOTMEM
[    0.000000]   #22 [0001d178c0 - 0001d17928]         BOOTMEM
[    0.000000]   #23 [0001d17940 - 0001d179a8]         BOOTMEM
[    0.000000]   #24 [0001d179c0 - 0001d17a28]         BOOTMEM
[    0.000000]   #25 [0001d17a40 - 0001d17aa8]         BOOTMEM
[    0.000000]   #26 [0001d17ac0 - 0001d17b28]         BOOTMEM
[    0.000000]   #27 [0001d17b40 - 0001d17ba8]         BOOTMEM
[    0.000000]   #28 [0001d17bc0 - 0001d17c28]         BOOTMEM
[    0.000000]   #29 [0001d17c40 - 0001d17ca8]         BOOTMEM
[    0.000000]   #30 [0001d17cc0 - 0001d17ce0]         BOOTMEM
[    0.000000]   #31 [0001d17d00 - 0001d17d20]         BOOTMEM
[    0.000000]   #32 [0001d17d40 - 0001d17daa]         BOOTMEM
[    0.000000]   #33 [0001d17dc0 - 0001d17e2a]         BOOTMEM
[    0.000000]   #34 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #35 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #36 [0001d17e40 - 0001d17e48]         BOOTMEM
[    0.000000]   #37 [0001d17e80 - 0001d17e88]         BOOTMEM
[    0.000000]   #38 [0001d17ec0 - 0001d17ec8]         BOOTMEM
[    0.000000]   #39 [0001d17f00 - 0001d17f10]         BOOTMEM
[    0.000000]   #40 [0001d37200 - 0001d37340]         BOOTMEM
[    0.000000]   #41 [0001d17f40 - 0001d17fa0]         BOOTMEM
[    0.000000]   #42 [0001d37340 - 0001d373a0]         BOOTMEM
[    0.000000]   #43 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #44 [0001f1e000 - 0005f1e000]         BOOTMEM
[    0.000000]   #45 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #46 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #47 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 4042608k/4980736k available (5710k kernel code, 788144k absent, 149984k reserved, 5380k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:512
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2199.985 MHz processor.
[    0.030010] Calibrating delay loop (skipped), value calculated using timer frequency.. 4399.96 BogoMIPS (lpj=21999820)
[    0.030016] pid_max: default: 32768 minimum: 301
[    0.030042] Security Framework initialized
[    0.030063] AppArmor: AppArmor initialized
[    0.030065] Yama: becoming mindful.
[    0.030595] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.040313] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.041567] Mount-cache hash table entries: 256
[    0.041728] Initializing cgroup subsys ns
[    0.041732] Initializing cgroup subsys cpuacct
[    0.041739] Initializing cgroup subsys memory
[    0.041749] Initializing cgroup subsys devices
[    0.041752] Initializing cgroup subsys freezer
[    0.041754] Initializing cgroup subsys net_cls
[    0.041784] tseg: 00cff00000
[    0.041788] CPU: Physical Processor ID: 0
[    0.041790] CPU: Processor Core ID: 0
[    0.041792] mce: CPU supports 5 MCE banks
[    0.041805] Performance Events: AMD PMU driver.
[    0.041811] ... version:                0
[    0.041813] ... bit width:              48
[    0.041815] ... generic registers:      4
[    0.041817] ... value mask:             0000ffffffffffff
[    0.041819] ... max period:             00007fffffffffff
[    0.041822] ... fixed-purpose events:   0
[    0.041823] ... event mask:             000000000000000f
[    0.044219] ACPI: Core revision 20100428
[    0.050015] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.050021] ftrace: allocating 22688 entries in 89 pages
[    0.060102] Setting APIC routing to flat
[    0.060502] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.166485] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-75 stepping 01
[    0.170000] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[    0.170000] Booting Node   0, Processors  #1 Ok.
[    0.330000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.330000] Measured 62712467 cycles TSC warp between CPUs, turning off TSC clock.
[    0.330000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.330009] Brought up 2 CPUs
[    0.330012] Total of 2 processors activated (8800.17 BogoMIPS).
[    0.330153] [Firmware Warn]: MTRR: CPU 1: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[    0.330700] devtmpfs: initialized
[    0.330946] regulator: core version 0.5
[    0.331012] Time:  8:53:18  Date: 11/03/10
[    0.331067] NET: Registered protocol family 16
[    0.331233] TOM: 00000000d0000000 aka 3328M
[    0.331236] Fam 10h mmconf [d0000000, dfffffff]
[    0.331243] TOM2: 0000000130000000 aka 4864M
[    0.331253] ACPI: bus type pci registered
[    0.331368] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xd0000000-0xd3ffffff] (base 0xd0000000)
[    0.331373] PCI: MMCONFIG at [mem 0xd0000000-0xd3ffffff] reserved in E820
[    0.338259] PCI: Using configuration type 1 for base access
[    0.340065] Trying to unpack rootfs image as initramfs...
[    0.350211] bio: create slab <bio-0> at 0
[    0.351512] ACPI: EC: Look up EC in DSDT
[    0.355290] ACPI: BIOS _OSI(Linux) query ignored
[    0.376790] ACPI: Interpreter enabled
[    0.376792] ACPI: (supports S0 S3 S4 S5)
[    0.376812] ACPI: Using IOAPIC for interrupt routing
[    0.420000] ACPI: No dock devices found.
[    0.420000] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.439989] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.485844] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.485847] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.485850] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.485853] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.485856] pci_root PNP0A03:00: host bridge window [mem 0xd4000000-0xfebfffff]
[    0.485858] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff]
[    0.485861] pci_root PNP0A03:00: host bridge window [mem 0xfed00400-0xfedfffff]
[    0.485864] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xff9fffff]
[    0.485867] pci_root PNP0A03:00: host bridge window [mem 0xffc00000-0xffdffbff]
[    0.485869] pci_root PNP0A03:00: host bridge window [mem 0x130000000-0x327ffffff]
[    0.486023] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.486027] pci 0000:00:02.0: PME# disabled
[    0.486117] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.486120] pci 0000:00:05.0: PME# disabled
[    0.486173] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.486177] pci 0000:00:06.0: PME# disabled
[    0.486233] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.486237] pci 0000:00:07.0: PME# disabled
[    0.486328] pci 0000:00:11.0: reg 10: [io  0x6e70-0x6e77]
[    0.486336] pci 0000:00:11.0: reg 14: [io  0x6e78-0x6e7b]
[    0.486345] pci 0000:00:11.0: reg 18: [io  0x6e80-0x6e87]
[    0.486353] pci 0000:00:11.0: reg 1c: [io  0x6e88-0x6e8b]
[    0.486361] pci 0000:00:11.0: reg 20: [io  0x6ea0-0x6eaf]
[    0.486369] pci 0000:00:11.0: reg 24: [mem 0xfed1c800-0xfed1cbff]
[    0.486391] pci 0000:00:11.0: set SATA to AHCI mode
[    0.486445] pci 0000:00:12.0: reg 10: [mem 0xffb00000-0xffb00fff]
[    0.486510] pci 0000:00:12.1: reg 10: [mem 0xffb01000-0xffb01fff]
[    0.486589] pci 0000:00:12.2: reg 10: [mem 0xffa80000-0xffa800ff]
[    0.486651] pci 0000:00:12.2: supports D1 D2
[    0.486654] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.486659] pci 0000:00:12.2: PME# disabled
[    0.486696] pci 0000:00:13.0: reg 10: [mem 0xffb02000-0xffb02fff]
[    0.486761] pci 0000:00:13.1: reg 10: [mem 0xffb03000-0xffb03fff]
[    0.486840] pci 0000:00:13.2: reg 10: [mem 0xffa80400-0xffa804ff]
[    0.486903] pci 0000:00:13.2: supports D1 D2
[    0.486905] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.486910] pci 0000:00:13.2: PME# disabled
[    0.487052] pci 0000:00:14.2: reg 10: [mem 0xf7ffc000-0xf7ffffff 64bit]
[    0.487103] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.487108] pci 0000:00:14.2: PME# disabled
[    0.487474] pci 0000:02:00.0: reg 10: [mem 0xe0000000-0xefffffff pref]
[    0.487481] pci 0000:02:00.0: reg 14: [io  0xee00-0xeeff]
[    0.487488] pci 0000:02:00.0: reg 18: [mem 0xf7df0000-0xf7dfffff]
[    0.487506] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.487529] pci 0000:02:00.0: supports D1 D2
[    0.500017] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    0.500023] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.500027] pci 0000:00:02.0:   bridge window [mem 0xf7d00000-0xf7efffff]
[    0.500032] pci 0000:00:02.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.500095] pci 0000:09:00.0: reg 10: [io  0xde00-0xdeff]
[    0.500113] pci 0000:09:00.0: reg 18: [mem 0xf0010000-0xf0010fff 64bit pref]
[    0.500126] pci 0000:09:00.0: reg 20: [mem 0xf0000000-0xf000ffff 64bit pref]
[    0.500134] pci 0000:09:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.500170] pci 0000:09:00.0: supports D1 D2
[    0.500172] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.500177] pci 0000:09:00.0: PME# disabled
[    0.520012] pci 0000:00:05.0: PCI bridge to [bus 09-09]
[    0.520017] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.520020] pci 0000:00:05.0:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.520025] pci 0000:00:05.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.520130] pci 0000:0b:00.0: reg 10: [mem 0xf7bfc000-0xf7bfffff 64bit]
[    0.520191] pci 0000:0b:00.0: supports D1 D2
[    0.520194] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
[    0.520201] pci 0000:0b:00.0: PME# disabled
[    0.540050] pci 0000:00:06.0: PCI bridge to [bus 0b-0b]
[    0.540055] pci 0000:00:06.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.540059] pci 0000:00:06.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.540064] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.540098] pci 0000:00:07.0: PCI bridge to [bus 0c-0d]
[    0.540103] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
[    0.540106] pci 0000:00:07.0:   bridge window [mem 0xf7800000-0xf7afffff]
[    0.540112] pci 0000:00:07.0:   bridge window [mem 0xf0100000-0xf03fffff 64bit pref]
[    0.540215] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.540221] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.540226] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.540232] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.540235] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.540237] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.540240] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.540243] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.540246] pci 0000:00:14.4:   bridge window [mem 0xd4000000-0xfebfffff] (subtractive decode)
[    0.540249] pci 0000:00:14.4:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.540252] pci 0000:00:14.4:   bridge window [mem 0xfed00400-0xfedfffff] (subtractive decode)
[    0.540254] pci 0000:00:14.4:   bridge window [mem 0xfee10000-0xff9fffff] (subtractive decode)
[    0.540257] pci 0000:00:14.4:   bridge window [mem 0xffc00000-0xffdffbff] (subtractive decode)
[    0.540260] pci 0000:00:14.4:   bridge window [mem 0x130000000-0x327ffffff] (subtractive decode)
[    0.540283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.540441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.540564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RPFX._PRT]
[    0.540639] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.540710] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.540781] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.562758] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.562927] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *0, disabled.
[    0.563103] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.563268] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11) *0, disabled.
[    0.563439] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.563609] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.563780] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.563950] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.564031] HEST: Table is not found!
[    0.564132] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.564135] vgaarb: loaded
[    0.564292] SCSI subsystem initialized
[    0.564398] libata version 3.00 loaded.
[    0.564452] usbcore: registered new interface driver usbfs
[    0.564464] usbcore: registered new interface driver hub
[    0.564491] usbcore: registered new device driver usb
[    0.564783] ACPI: WMI: Mapper loaded
[    0.564786] PCI: Using ACPI for IRQ routing
[    0.564789] PCI: pci_cache_line_size set to 64 bytes
[    0.564847] pci 0000:00:12.0: no compatible bridge window for [mem 0xffb00000-0xffb00fff]
[    0.564853] pci 0000:00:12.1: no compatible bridge window for [mem 0xffb01000-0xffb01fff]
[    0.564859] pci 0000:00:12.2: no compatible bridge window for [mem 0xffa80000-0xffa800ff]
[    0.564864] pci 0000:00:13.0: no compatible bridge window for [mem 0xffb02000-0xffb02fff]
[    0.564870] pci 0000:00:13.1: no compatible bridge window for [mem 0xffb03000-0xffb03fff]
[    0.564876] pci 0000:00:13.2: no compatible bridge window for [mem 0xffa80400-0xffa804ff]
[    0.565056] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.565059] reserve RAM buffer: 00000000cfec5400 - 00000000cfffffff 
[    0.565167] NetLabel: Initializing
[    0.565169] NetLabel:  domain hash size = 128
[    0.565170] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.565187] NetLabel:  unlabeled traffic allowed by default
[    0.565262] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.565267] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.567292] Switching to clocksource hpet
[    0.571084] AppArmor: AppArmor Filesystem Enabled
[    0.571105] pnp: PnP ACPI init
[    0.571127] ACPI: bus type pnp registered
[    0.618585] pnp: PnP ACPI: found 13 devices
[    0.618588] ACPI: ACPI bus type pnp unregistered
[    0.618602] system 00:01: [mem 0xff800000-0xff8fffff] has been reserved
[    0.618605] system 00:01: [mem 0xffc00000-0xffcfffff] has been reserved
[    0.618617] system 00:06: [io  0x0c80-0x0cff] could not be reserved
[    0.618623] system 00:0a: [io  0x0900-0x097f] has been reserved
[    0.618627] system 00:0a: [io  0x0980-0x09ff] has been reserved
[    0.618630] system 00:0a: [io  0x0a00-0x0a7f] has been reserved
[    0.618633] system 00:0a: [io  0x0a80-0x0aff] has been reserved
[    0.618636] system 00:0a: [io  0x0cb0-0x0cff] could not be reserved
[    0.618639] system 00:0a: [io  0x0d00-0x0d7f] has been reserved
[    0.618642] system 00:0a: [io  0x0d80-0x0dff] has been reserved
[    0.618645] system 00:0a: [io  0x0e00-0x0e7f] has been reserved
[    0.618648] system 00:0a: [io  0x0e80-0x0eaf] has been reserved
[    0.618651] system 00:0a: [io  0x0c6c] has been reserved
[    0.618654] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.618657] system 00:0a: [io  0x3000-0x3005] has been reserved
[    0.618660] system 00:0a: [io  0x3008-0x300f] has been reserved
[    0.618663] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.618666] system 00:0a: [io  0x0c14] has been reserved
[    0.618669] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.618672] system 00:0a: [io  0x0c52] has been reserved
[    0.618675] system 00:0a: [io  0x0c6f] has been reserved
[    0.618678] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.618681] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.618684] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.618687] system 00:0a: [io  0x040b] has been reserved
[    0.618690] system 00:0a: [io  0x04d6] has been reserved
[    0.618695] system 00:0b: [io  0xf400-0xf4fe] has been reserved
[    0.618698] system 00:0b: [io  0x3006-0x3007] has been reserved
[    0.618701] system 00:0b: [io  0x300a-0x3059] could not be reserved
[    0.618704] system 00:0b: [io  0x3080-0x30bf] has been reserved
[    0.618707] system 00:0b: [io  0x30c0-0x30df] has been reserved
[    0.618710] system 00:0b: [io  0x3010-0x302f] has been reserved
[    0.618713] system 00:0b: [io  0x0809] has been reserved
[    0.618719] system 00:0c: [mem 0x00000000-0x0009efff] could not be reserved
[    0.618722] system 00:0c: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.618725] system 00:0c: [mem 0x000c0000-0x000cffff] has been reserved
[    0.618728] system 00:0c: [mem 0x000e0000-0x000fffff] has been reserved
[    0.618731] system 00:0c: [mem 0x00100000-0xcfec53ff] could not be reserved
[    0.618735] system 00:0c: [mem 0xcfec5400-0xcfefffff] has been reserved
[    0.618738] system 00:0c: [mem 0xcff00000-0xcfffffff] has been reserved
[    0.618741] system 00:0c: [mem 0xffe00000-0xffffffff] has been reserved
[    0.618744] system 00:0c: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.618747] system 00:0c: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.618750] system 00:0c: [mem 0xfee10000-0xfee103ff] has been reserved
[    0.618754] system 00:0c: [mem 0xfed1c800-0xfed1cfff] could not be reserved
[    0.618757] system 00:0c: [mem 0xd0000000-0xd3ffffff] has been reserved
[    0.625294] pci 0000:00:12.0: BAR 0: assigned [mem 0xd4000000-0xd4000fff]
[    0.625302] pci 0000:00:12.0: BAR 0: set to [mem 0xd4000000-0xd4000fff] (PCI address [0xd4000000-0xd4000fff]
[    0.625306] pci 0000:00:12.1: BAR 0: assigned [mem 0xd4001000-0xd4001fff]
[    0.625312] pci 0000:00:12.1: BAR 0: set to [mem 0xd4001000-0xd4001fff] (PCI address [0xd4001000-0xd4001fff]
[    0.625315] pci 0000:00:13.0: BAR 0: assigned [mem 0xd4002000-0xd4002fff]
[    0.625321] pci 0000:00:13.0: BAR 0: set to [mem 0xd4002000-0xd4002fff] (PCI address [0xd4002000-0xd4002fff]
[    0.625325] pci 0000:00:13.1: BAR 0: assigned [mem 0xd4003000-0xd4003fff]
[    0.625331] pci 0000:00:13.1: BAR 0: set to [mem 0xd4003000-0xd4003fff] (PCI address [0xd4003000-0xd4003fff]
[    0.625334] pci 0000:00:12.2: BAR 0: assigned [mem 0xd4004000-0xd40040ff]
[    0.625340] pci 0000:00:12.2: BAR 0: set to [mem 0xd4004000-0xd40040ff] (PCI address [0xd4004000-0xd40040ff]
[    0.625344] pci 0000:00:13.2: BAR 0: assigned [mem 0xd4004100-0xd40041ff]
[    0.625349] pci 0000:00:13.2: BAR 0: set to [mem 0xd4004100-0xd40041ff] (PCI address [0xd4004100-0xd40041ff]
[    0.625354] pci 0000:02:00.0: BAR 6: assigned [mem 0xf7d00000-0xf7d1ffff pref]
[    0.625357] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    0.625361] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.625365] pci 0000:00:02.0:   bridge window [mem 0xf7d00000-0xf7efffff]
[    0.625369] pci 0000:00:02.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.625375] pci 0000:09:00.0: BAR 6: assigned [mem 0xf0020000-0xf003ffff pref]
[    0.625378] pci 0000:00:05.0: PCI bridge to [bus 09-09]
[    0.625381] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.625385] pci 0000:00:05.0:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.625389] pci 0000:00:05.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.625394] pci 0000:00:06.0: PCI bridge to [bus 0b-0b]
[    0.625396] pci 0000:00:06.0:   bridge window [io  disabled]
[    0.625400] pci 0000:00:06.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.625403] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.625408] pci 0000:00:07.0: PCI bridge to [bus 0c-0d]
[    0.625411] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
[    0.625416] pci 0000:00:07.0:   bridge window [mem 0xf7800000-0xf7afffff]
[    0.625419] pci 0000:00:07.0:   bridge window [mem 0xf0100000-0xf03fffff 64bit pref]
[    0.625425] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.625427] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.625466] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.625471] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.625488] pci 0000:00:02.0: setting latency timer to 64
[    0.625496] pci 0000:00:05.0: setting latency timer to 64
[    0.625504] pci 0000:00:06.0: setting latency timer to 64
[    0.625511] pci 0000:00:07.0: setting latency timer to 64
[    0.625521] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.625523] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.625526] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.625528] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.625531] pci_bus 0000:00: resource 8 [mem 0xd4000000-0xfebfffff]
[    0.625533] pci_bus 0000:00: resource 9 [mem 0xfec10000-0xfecfffff]
[    0.625536] pci_bus 0000:00: resource 10 [mem 0xfed00400-0xfedfffff]
[    0.625538] pci_bus 0000:00: resource 11 [mem 0xfee10000-0xff9fffff]
[    0.625541] pci_bus 0000:00: resource 12 [mem 0xffc00000-0xffdffbff]
[    0.625544] pci_bus 0000:00: resource 13 [mem 0x130000000-0x327ffffff]
[    0.625546] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.625549] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7efffff]
[    0.625551] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.625554] pci_bus 0000:09: resource 0 [io  0xd000-0xdfff]
[    0.625557] pci_bus 0000:09: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.625559] pci_bus 0000:09: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.625562] pci_bus 0000:0b: resource 1 [mem 0xf7b00000-0xf7bfffff]
[    0.625565] pci_bus 0000:0c: resource 0 [io  0xc000-0xcfff]
[    0.625567] pci_bus 0000:0c: resource 1 [mem 0xf7800000-0xf7afffff]
[    0.625570] pci_bus 0000:0c: resource 2 [mem 0xf0100000-0xf03fffff 64bit pref]
[    0.625573] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.625576] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.625578] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.625581] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.625583] pci_bus 0000:03: resource 8 [mem 0xd4000000-0xfebfffff]
[    0.625586] pci_bus 0000:03: resource 9 [mem 0xfec10000-0xfecfffff]
[    0.625588] pci_bus 0000:03: resource 10 [mem 0xfed00400-0xfedfffff]
[    0.625591] pci_bus 0000:03: resource 11 [mem 0xfee10000-0xff9fffff]
[    0.625593] pci_bus 0000:03: resource 12 [mem 0xffc00000-0xffdffbff]
[    0.625596] pci_bus 0000:03: resource 13 [mem 0x130000000-0x327ffffff]
[    0.625641] NET: Registered protocol family 2
[    0.625819] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.627618] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.632619] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.633186] TCP: Hash tables configured (established 524288 bind 65536)
[    0.633189] TCP reno registered
[    0.633206] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.633255] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.633394] NET: Registered protocol family 1
[    0.662153] Freeing initrd memory: 10752k freed
[    1.630255] pci 0000:00:12.0: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
[    2.630253] pci 0000:00:12.1: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
[    2.630282] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630285] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630287] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630289] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630292] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630294] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630296] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630299] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630301] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630303] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630305] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630308] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630310] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630312] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630314] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630317] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630319] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630321] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630323] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630326] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630328] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630330] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630332] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630335] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630337] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630339] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630341] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630344] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630346] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630348] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630350] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630353] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630355] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630357] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630359] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630362] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630364] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630366] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630368] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630371] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630373] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630375] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630378] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630380] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630382] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630384] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630386] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630388] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630390] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630393] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630395] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630397] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630399] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630401] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630403] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630406] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630408] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630410] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630412] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630414] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630416] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630418] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630421] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.630423] pci 0000:00:12.2: EHCI: capability loop?
[    3.630253] pci 0000:00:13.0: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
[    4.630253] pci 0000:00:13.1: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
[    4.630279] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630281] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630283] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630286] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630288] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630290] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630292] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630295] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630297] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630299] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630301] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630304] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630306] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630308] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630311] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630313] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630315] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630317] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630320] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630322] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630324] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630326] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630329] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630331] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630333] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630335] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630338] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630340] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630342] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630344] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630347] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630349] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630351] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630353] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630356] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630358] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630360] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630363] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630365] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630367] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630369] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630372] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630374] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630376] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630378] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630381] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630383] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630385] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630387] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630389] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630391] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630393] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630396] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630398] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630400] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630402] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630404] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630406] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630409] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630411] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630413] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630415] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630417] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.630419] pci 0000:00:13.2: EHCI: capability loop?
[    4.630456] pci 0000:02:00.0: Boot video device
[    4.630504] PCI: CLS 64 bytes, default 64
[    4.630507] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    4.630510] Placing 64MB software IO TLB between ffff880001f1e000 - ffff880005f1e000
[    4.630512] software IO TLB at phys 0x1f1e000 - 0x5f1e000
[    4.630787] Scanning for low memory corruption every 60 seconds
[    4.630959] audit: initializing netlink socket (disabled)
[    4.630972] type=2000 audit(1288774402.630:1): initialized
[    4.644992] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.646826] VFS: Disk quotas dquot_6.5.2
[    4.646888] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    4.647627] fuse init (API version 7.14)
[    4.647749] msgmni has been set to 7916
[    4.651121] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.651125] io scheduler noop registered
[    4.651127] io scheduler deadline registered
[    4.651169] io scheduler cfq registered (default)
[    4.651304] pcieport 0000:00:02.0: setting latency timer to 64
[    4.651340]   alloc irq_desc for 40 on node -1
[    4.651343]   alloc kstat_irqs on node -1
[    4.651355] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    4.651432] pcieport 0000:00:05.0: setting latency timer to 64
[    4.651459]   alloc irq_desc for 41 on node -1
[    4.651462]   alloc kstat_irqs on node -1
[    4.651467] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    4.651533] pcieport 0000:00:06.0: setting latency timer to 64
[    4.651559]   alloc irq_desc for 42 on node -1
[    4.651561]   alloc kstat_irqs on node -1
[    4.651567] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    4.651629] pcieport 0000:00:07.0: setting latency timer to 64
[    4.651655]   alloc irq_desc for 43 on node -1
[    4.651657]   alloc kstat_irqs on node -1
[    4.651663] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    4.651761] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.651824] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.652077] ACPI: AC Adapter [AC] (off-line)
[    4.652167] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    4.653314] ACPI: Lid Switch [LID]
[    4.653358] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    4.653363] ACPI: Power Button [PBTN]
[    4.653409] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    4.653412] ACPI: Sleep Button [SBTN]
[    4.653718] ACPI: acpi_idle registered with cpuidle
[    4.666000] thermal LNXTHERM:01: registered as thermal_zone0
[    4.666009] ACPI: Thermal Zone [THM] (51 C)
[    4.666090] ERST: Table is not found!
[    4.694057] Linux agpgart interface v0.103
[    4.694086] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.697308] brd: module loaded
[    4.698575] loop: module loaded
[    4.699613] Fixed MDIO Bus: probed
[    4.699650] PPP generic driver version 2.4.2
[    4.699853] tun: Universal TUN/TAP device driver, 1.6
[    4.699855] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.699946] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.700007]   alloc irq_desc for 17 on node -1
[    4.700010]   alloc kstat_irqs on node -1
[    4.700188] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.700224] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    4.700258] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    4.700507] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    4.700523] ehci_hcd 0000:00:12.2: debug port 15 IN USE
[    4.701017] ACPI: Battery Slot [BAT0] (battery present)
[    4.722594] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd4004000
[    4.722608] ehci_hcd 0000:00:12.2: startup error -19
[    4.722617] ehci_hcd 0000:00:12.2: USB bus 1 deregistered
[    4.722717] ehci_hcd 0000:00:12.2: PCI INT B disabled
[    4.722721] ehci_hcd 0000:00:12.2: init 0000:00:12.2 fail, -19
[    4.722738]   alloc irq_desc for 20 on node -1
[    4.722740]   alloc kstat_irqs on node -1
[    4.722745] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    4.722765] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.722796] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    4.722817] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    4.722833] ehci_hcd 0000:00:13.2: debug port 15 IN USE
[    4.752769] ehci_hcd 0000:00:13.2: irq 20, io mem 0xd4004100
[    4.752779] ehci_hcd 0000:00:13.2: startup error -19
[    4.752786] ehci_hcd 0000:00:13.2: USB bus 1 deregistered
[    4.752870] ehci_hcd 0000:00:13.2: PCI INT B disabled
[    4.752873] ehci_hcd 0000:00:13.2: init 0000:00:13.2 fail, -19
[    4.752891] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.752906]   alloc irq_desc for 16 on node -1
[    4.752908]   alloc kstat_irqs on node -1
[    4.752913] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.752933] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.752963] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   14.750252] ohci_hcd 0000:00:12.0: USB HC takeover failed!  (BIOS/SMM bug)
[   14.750255] ohci_hcd 0000:00:12.0: can't setup
[   14.750258] ohci_hcd 0000:00:12.0: USB bus 1 deregistered
[   14.750293] ohci_hcd 0000:00:12.0: PCI INT A disabled
[   14.750295] ohci_hcd 0000:00:12.0: init 0000:00:12.0 fail, -16
[   14.750300] ohci_hcd: probe of 0000:00:12.0 failed with error -16
[   14.750312] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.750332] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   14.750362] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 1
[   24.750252] ohci_hcd 0000:00:12.1: USB HC takeover failed!  (BIOS/SMM bug)
[   24.750254] ohci_hcd 0000:00:12.1: can't setup
[   24.750257] ohci_hcd 0000:00:12.1: USB bus 1 deregistered
[   24.750288] ohci_hcd 0000:00:12.1: PCI INT A disabled
[   24.750291] ohci_hcd 0000:00:12.1: init 0000:00:12.1 fail, -16
[   24.750295] ohci_hcd: probe of 0000:00:12.1 failed with error -16
[   24.750306]   alloc irq_desc for 18 on node -1
[   24.750308]   alloc kstat_irqs on node -1
[   24.750313] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.750331] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   24.750365] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   34.750251] ohci_hcd 0000:00:13.0: USB HC takeover failed!  (BIOS/SMM bug)
[   34.750254] ohci_hcd 0000:00:13.0: can't setup
[   34.750256] ohci_hcd 0000:00:13.0: USB bus 1 deregistered
[   34.750288] ohci_hcd 0000:00:13.0: PCI INT A disabled
[   34.750290] ohci_hcd 0000:00:13.0: init 0000:00:13.0 fail, -16
[   34.750294] ohci_hcd: probe of 0000:00:13.0 failed with error -16
[   34.750305] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   34.750324] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   34.750354] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 1
[   44.750251] ohci_hcd 0000:00:13.1: USB HC takeover failed!  (BIOS/SMM bug)
[   44.750254] ohci_hcd 0000:00:13.1: can't setup
[   44.750256] ohci_hcd 0000:00:13.1: USB bus 1 deregistered
[   44.750287] ohci_hcd 0000:00:13.1: PCI INT A disabled
[   44.750290] ohci_hcd 0000:00:13.1: init 0000:00:13.1 fail, -16
[   44.750294] ohci_hcd: probe of 0000:00:13.1 failed with error -16
[   44.750306] uhci_hcd: USB Universal Host Controller Interface driver
[   44.750443] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   44.770030] serio: i8042 KBD port at 0x60,0x64 irq 1
[   44.770039] serio: i8042 AUX port at 0x60,0x64 irq 12
[   44.770111] mice: PS/2 mouse device common for all mice
[   44.770241] rtc_cmos 00:04: RTC can wake from S4
[   44.770284] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[   44.770352] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[   44.770449] device-mapper: uevent: version 1.0.3
[   44.770553] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[   44.770659] device-mapper: multipath: version 1.1.1 loaded
[   44.770662] device-mapper: multipath round-robin: version 1.0.0 loaded
[   44.770987] cpuidle: using governor ladder
[   44.770989] cpuidle: using governor menu
[   44.771309] TCP cubic registered
[   44.771464] NET: Registered protocol family 10
[   44.771890] lo: Disabled Privacy Extensions
[   44.772117] NET: Registered protocol family 17
[   44.772200] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-75 (2 cpu cores) (version 2.20.00)
[   44.772584] powernow-k8:    0 : pstate 0 (2200 MHz)
[   44.772587] powernow-k8:    1 : pstate 1 (1100 MHz)
[   44.772589] powernow-k8:    2 : pstate 2 (550 MHz)
[   44.773974] PM: Resume from disk failed.
[   44.773989] registered taskstats version 1
[   44.774375]   Magic number: 2:441:876
[   44.774523] rtc_cmos 00:04: setting system clock to 2010-11-03 08:54:03 UTC (1288774443)
[   44.774526] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   44.774528] EDD information not available.
[   44.774670] Freeing unused kernel memory: 908k freed
[   44.775090] Write protecting the kernel read-only data: 10240k
[   44.775304] Freeing unused kernel memory: 412k freed
[   44.775676] Freeing unused kernel memory: 1644k freed
[   44.797229] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   44.802102] udev[75]: starting version 163
[   44.978382] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   44.978413] r8169 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   44.978469] r8169 0000:09:00.0: setting latency timer to 64
[   44.978508]   alloc irq_desc for 44 on node -1
[   44.978510]   alloc kstat_irqs on node -1
[   44.978525] r8169 0000:09:00.0: irq 44 for MSI/MSI-X
[   44.979141] r8169 0000:09:00.0: eth0: RTL8102e at 0xffffc90000676000, a4:ba:db:97:54:b9, XID 04c00000 IRQ 44
[   45.021819] ahci 0000:00:11.0: version 3.0
[   45.021851]   alloc irq_desc for 22 on node -1
[   45.021854]   alloc kstat_irqs on node -1
[   45.021864] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   45.021987] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   45.021991] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[   45.022336] scsi0 : ahci
[   45.022486] scsi1 : ahci
[   45.022701] ata1: SATA max UDMA/133 abar m1024@0xfed1c800 port 0xfed1c900 irq 22
[   45.022706] ata2: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 22
[   45.570259] ata1: softreset failed (device not ready)
[   45.570264] ata1: applying SB600 PMP SRST workaround and retrying
[   45.770268] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   45.970255] ata2: softreset failed (device not ready)
[   45.970259] ata2: applying SB600 PMP SRST workaround and retrying
[   46.036077] ata1.00: ATA-8: ST9250315AS, 0003DEM1, max UDMA/133
[   46.036081] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   46.038029] ata1.00: configured for UDMA/133
[   46.050322] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0003 PQ: 0 ANSI: 5
[   46.050516] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   46.050609] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[   46.050757] sd 0:0:0:0: [sda] Write Protect is off
[   46.050761] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.050816] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.051138]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   46.128693] sd 0:0:0:0: [sda] Attached SCSI disk
[   46.170279] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   46.172132] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7700H, 100A, max UDMA/100
[   46.178947] ata2.00: configured for UDMA/100
[   46.220976] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7700H 100A PQ: 0 ANSI: 5
[   46.259610] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   46.259614] Uniform CD-ROM driver Revision: 3.20
[   46.259748] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   46.259818] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   46.737604] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   58.726004] udev[399]: starting version 163
[   58.779800] lp: driver loaded but no devices found
[   58.889809] lib80211: common routines for IEEE802.11 drivers
[   58.889814] lib80211_crypt: registered algorithm 'NULL'
[   58.937327] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x30c0, revision 0
[   58.969566] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   58.969572] Disabling lock debugging due to kernel taint
[   59.030252] EDAC MC: Ver: 2.1.0 Oct 26 2010
[   59.030787] type=1400 audit(1288788857.746:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=589 comm="apparmor_parser"
[   59.031070] type=1400 audit(1288788857.746:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=589 comm="apparmor_parser"
[   59.031230] type=1400 audit(1288788857.746:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=589 comm="apparmor_parser"
[   59.072096] EDAC amd64_edac:  Ver: 3.3.0 Oct 26 2010
[   59.072156] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   59.072165] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   59.072166]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   59.072168]  (Note that use of the override may cause unknown side effects.)
[   59.072175] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   59.156479] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   59.187384] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   59.233279] input: Dell WMI hotkeys as /devices/virtual/input/input4
[   59.236414] wl 0000:0b:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   59.236424] wl 0000:0b:00.0: setting latency timer to 64
[   59.287521] acpi device:34: registered as cooling_device2
[   59.291675] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:31/LNXVIDEO:00/input/input5
[   59.291812] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   59.340102] lib80211_crypt: registered algorithm 'TKIP'
[   59.340396] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   59.412813] [fglrx] Maximum main memory to use for locked dma buffers: 3799 MBytes.
[   59.413114] [fglrx]   vendor: 1002 device: 9552 count: 1
[   59.413580] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[   59.413601] pci 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   59.413607] pci 0000:02:00.0: setting latency timer to 64
[   59.414011] [fglrx] Kernel PAT support is enabled
[   59.414042] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   59.453014] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   59.580575] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   59.580683] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   59.587908] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   59.617543] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   59.770899] type=1400 audit(1288788858.486:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=946 comm="apparmor_parser"
[   59.771190] type=1400 audit(1288788858.486:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=947 comm="apparmor_parser"
[   59.771478] type=1400 audit(1288788858.486:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=947 comm="apparmor_parser"
[   59.771643] type=1400 audit(1288788858.486:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=947 comm="apparmor_parser"
[   59.775665] type=1400 audit(1288788858.486:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=948 comm="apparmor_parser"
[   59.775797] type=1400 audit(1288788858.486:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=950 comm="apparmor_parser"
[   59.776164] type=1400 audit(1288788858.486:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=950 comm="apparmor_parser"
[   59.810574] r8169 0000:09:00.0: eth0: link down
[   59.811189] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

lspci

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

---

### Post by P4man on 2010-11-03
The kernel cant bring up the USB controller and complains about a BIOS bug. Googling further on the issue, it appears its exactly that, and the first thing to do is update your bios. If you have no windows partition anymore, that may require making a bootable DOS cd or USB stick.

As a temporary workaround, you could try adding 

pci=nomsi

to your kernel options in /etc/default/grub (dont forget to run update-grub after that). If Im going too fast for you, feel free to ask, and Ill write out the commands.

---

### Post by Zoltar567 on 2010-11-03
I saw the issue with the BIOS, so i went onto Dell's site and found a BIOS update. Sadly my BIOS as us up to date as it can be, so that wont fix anything.

I know what you speak of with the GRUB.cfg. Where exactly do i drop that line of code you provided? I don't want to fool with grub before without being absolutely sure.

---

### Post by P4man on 2010-11-04
try it first temporarily. In grub menu select the default kernel, and press E to edit. At the end of line that usually ends with "quite splash", add the above parameter.

Boot with control+x

If that does indeed help, make it permanent by

```
gksudo gedit /etc/default/grub
```

modify the default kernel paramneters there (sorry not on ubuntu now, cant give exact line but you should recognise the same parameters). then update grub.cfg:

```
sudo update-grub
```

In grub2 you no longer edit grub.cfg directly, since the file is generated.

---

### Post by Zoltar567 on 2010-11-04
I applied that to my grub file. It reads like this :

```
GRUB_DEFAULT=6
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
pci=nomsi
```

Even with that added in, my USB mouse is not detected.
What exactly does this pci=nomsi do?

---

### Post by P4man on 2010-11-04
Edit it like this:

```
GRUB_DEFAULT=6
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]pci=nomsi[/COLOR]"
GRUB_CMDLINE_LINUX=""

```

And run update-grub again.
and check my sig for more info on boot options

---

### Post by Zoltar567 on 2010-11-04
I applied the commands as you said, and USB is not functional. 

I suppose some progress is being made. 

Now when i flip my wireless USB mouse to on, the light on the top illuminates for a bit, then shuts off. Before there was no activity. 

I attached a flash drive and tried lsusb, and nothing was shown, aswell as fdisk -l.

---

### Post by P4man on 2010-11-04
can you post the contents again of dmesg now?

---

### Post by Zoltar567 on 2010-11-04
```
[    0.623997] pci 0000:00:13.2: BAR 0: assigned [mem 0xd4004100-0xd40041ff]
[    0.624002] pci 0000:00:13.2: BAR 0: set to [mem 0xd4004100-0xd40041ff] (PCI address [0xd4004100-0xd40041ff]
[    0.624007] pci 0000:02:00.0: BAR 6: assigned [mem 0xf7d00000-0xf7d1ffff pref]
[    0.624010] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    0.624014] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.624018] pci 0000:00:02.0:   bridge window [mem 0xf7d00000-0xf7efffff]
[    0.624023] pci 0000:00:02.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.624029] pci 0000:09:00.0: BAR 6: assigned [mem 0xf0020000-0xf003ffff pref]
[    0.624032] pci 0000:00:05.0: PCI bridge to [bus 09-09]
[    0.624035] pci 0000:00:05.0:   bridge window [io  0xd000-0xdfff]
[    0.624039] pci 0000:00:05.0:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.624043] pci 0000:00:05.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.624048] pci 0000:00:06.0: PCI bridge to [bus 0b-0b]
[    0.624050] pci 0000:00:06.0:   bridge window [io  disabled]
[    0.624054] pci 0000:00:06.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.624058] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.624063] pci 0000:00:07.0: PCI bridge to [bus 0c-0d]
[    0.624066] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
[    0.624070] pci 0000:00:07.0:   bridge window [mem 0xf7800000-0xf7afffff]
[    0.624074] pci 0000:00:07.0:   bridge window [mem 0xf0100000-0xf03fffff 64bit pref]
[    0.624079] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.624081] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.624121] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.624125] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.624143] pci 0000:00:02.0: setting latency timer to 64
[    0.624151] pci 0000:00:05.0: setting latency timer to 64
[    0.624159] pci 0000:00:06.0: setting latency timer to 64
[    0.624166] pci 0000:00:07.0: setting latency timer to 64
[    0.624176] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.624178] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.624181] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.624183] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.624186] pci_bus 0000:00: resource 8 [mem 0xd4000000-0xfebfffff]
[    0.624188] pci_bus 0000:00: resource 9 [mem 0xfec10000-0xfecfffff]
[    0.624191] pci_bus 0000:00: resource 10 [mem 0xfed00400-0xfedfffff]
[    0.624194] pci_bus 0000:00: resource 11 [mem 0xfee10000-0xff9fffff]
[    0.624196] pci_bus 0000:00: resource 12 [mem 0xffc00000-0xffdffbff]
[    0.624199] pci_bus 0000:00: resource 13 [mem 0x130000000-0x327ffffff]
[    0.624202] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.624204] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7efffff]
[    0.624207] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.624209] pci_bus 0000:09: resource 0 [io  0xd000-0xdfff]
[    0.624212] pci_bus 0000:09: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.624215] pci_bus 0000:09: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.624218] pci_bus 0000:0b: resource 1 [mem 0xf7b00000-0xf7bfffff]
[    0.624220] pci_bus 0000:0c: resource 0 [io  0xc000-0xcfff]
[    0.624223] pci_bus 0000:0c: resource 1 [mem 0xf7800000-0xf7afffff]
[    0.624225] pci_bus 0000:0c: resource 2 [mem 0xf0100000-0xf03fffff 64bit pref]
[    0.624228] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.624231] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.624234] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.624236] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.624239] pci_bus 0000:03: resource 8 [mem 0xd4000000-0xfebfffff]
[    0.624242] pci_bus 0000:03: resource 9 [mem 0xfec10000-0xfecfffff]
[    0.624244] pci_bus 0000:03: resource 10 [mem 0xfed00400-0xfedfffff]
[    0.624247] pci_bus 0000:03: resource 11 [mem 0xfee10000-0xff9fffff]
[    0.624250] pci_bus 0000:03: resource 12 [mem 0xffc00000-0xffdffbff]
[    0.624252] pci_bus 0000:03: resource 13 [mem 0x130000000-0x327ffffff]
[    0.624295] NET: Registered protocol family 2
[    0.624480] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.626239] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.631214] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.631806] TCP: Hash tables configured (established 524288 bind 65536)
[    0.631809] TCP reno registered
[    0.631828] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.631877] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.632016] NET: Registered protocol family 1
[    0.653281] Freeing initrd memory: 10752k freed
[    1.630255] pci 0000:00:12.0: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
[    2.640253] pci 0000:00:12.1: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
[    2.640280] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640283] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640285] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640287] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640290] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640292] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640295] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640297] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640299] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640302] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640304] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640306] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640309] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640311] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640314] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640316] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640318] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640321] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640323] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640325] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640328] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640330] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640333] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640335] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640337] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640340] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640342] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640344] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640347] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640349] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640352] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640354] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640356] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640359] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640361] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640364] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640366] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640368] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640371] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640373] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640375] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640378] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640380] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640382] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640384] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640387] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640389] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640391] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640393] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640395] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640397] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640400] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640402] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640404] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640406] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640408] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640410] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640413] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640415] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640417] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640419] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640421] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640424] pci 0000:00:12.2: EHCI: unrecognized capability ff
[    2.640426] pci 0000:00:12.2: EHCI: capability loop?
[    3.640253] pci 0000:00:13.0: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
[    4.640252] pci 0000:00:13.1: OHCI: BIOS handoff failed (BIOS bug?) ffffffff
[    4.640279] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640281] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640284] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640286] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640289] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640291] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640293] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640296] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640298] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640301] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640303] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640305] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640308] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640310] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640312] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640315] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640317] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640320] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640322] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640324] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640327] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640329] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640331] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640334] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640336] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640339] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640341] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640343] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640346] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640348] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640350] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640353] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640355] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640358] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640360] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640362] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640365] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640367] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640369] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640372] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640374] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640377] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640379] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640381] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640383] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640385] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640388] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640390] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640392] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640394] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640396] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640399] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640401] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640403] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640405] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640407] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640410] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640412] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640414] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640416] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640418] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640420] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640423] pci 0000:00:13.2: EHCI: unrecognized capability ff
[    4.640425] pci 0000:00:13.2: EHCI: capability loop?
[    4.640462] pci 0000:02:00.0: Boot video device
[    4.640511] PCI: CLS 64 bytes, default 64
[    4.640514] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    4.640518] Placing 64MB software IO TLB between ffff880001f1e000 - ffff880005f1e000
[    4.640522] software IO TLB at phys 0x1f1e000 - 0x5f1e000
[    4.640833] Scanning for low memory corruption every 60 seconds
[    4.641012] audit: initializing netlink socket (disabled)
[    4.641025] type=2000 audit(1288862775.640:1): initialized
[    4.655011] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.656786] VFS: Disk quotas dquot_6.5.2
[    4.656852] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    4.657557] fuse init (API version 7.14)
[    4.657681] msgmni has been set to 7916
[    4.661117] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.661121] io scheduler noop registered
[    4.661123] io scheduler deadline registered
[    4.661164] io scheduler cfq registered (default)
[    4.661297] pcieport 0000:00:02.0: setting latency timer to 64
[    4.661373] pcieport 0000:00:05.0: setting latency timer to 64
[    4.661435] pcieport 0000:00:06.0: setting latency timer to 64
[    4.661500] pcieport 0000:00:07.0: setting latency timer to 64
[    4.661571] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.661596] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.661856] ACPI: AC Adapter [AC] (off-line)
[    4.661945] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    4.662725] ACPI: Lid Switch [LID]
[    4.662779] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    4.662784] ACPI: Power Button [PBTN]
[    4.662835] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    4.662842] ACPI: Sleep Button [SBTN]
[    4.663118] ACPI: acpi_idle registered with cpuidle
[    4.675403] thermal LNXTHERM:01: registered as thermal_zone0
[    4.675412] ACPI: Thermal Zone [THM] (58 C)
[    4.675501] ERST: Table is not found!
[    4.704178] Linux agpgart interface v0.103
[    4.704209] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.707257] brd: module loaded
[    4.708517] loop: module loaded
[    4.709740] Fixed MDIO Bus: probed
[    4.709777] PPP generic driver version 2.4.2
[    4.709812] tun: Universal TUN/TAP device driver, 1.6
[    4.709813] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.710066] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.710095]   alloc irq_desc for 17 on node -1
[    4.710097]   alloc kstat_irqs on node -1
[    4.710106] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.710142] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    4.710178] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    4.710429] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    4.710445] ehci_hcd 0000:00:12.2: debug port 15 IN USE
[    4.711244] ACPI: Battery Slot [BAT0] (battery present)
[    4.742780] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd4004000
[    4.742799] ehci_hcd 0000:00:12.2: startup error -19
[    4.742809] ehci_hcd 0000:00:12.2: USB bus 1 deregistered
[    4.742909] ehci_hcd 0000:00:12.2: PCI INT B disabled
[    4.742913] ehci_hcd 0000:00:12.2: init 0000:00:12.2 fail, -19
[    4.742933]   alloc irq_desc for 20 on node -1
[    4.742935]   alloc kstat_irqs on node -1
[    4.742940] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    4.742960] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.742993] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    4.743015] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    4.743030] ehci_hcd 0000:00:13.2: debug port 15 IN USE
[    4.772766] ehci_hcd 0000:00:13.2: irq 20, io mem 0xd4004100
[    4.772776] ehci_hcd 0000:00:13.2: startup error -19
[    4.772783] ehci_hcd 0000:00:13.2: USB bus 1 deregistered
[    4.772867] ehci_hcd 0000:00:13.2: PCI INT B disabled
[    4.772870] ehci_hcd 0000:00:13.2: init 0000:00:13.2 fail, -19
[    4.772888] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.772903]   alloc irq_desc for 16 on node -1
[    4.772905]   alloc kstat_irqs on node -1
[    4.772910] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.772929] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.772959] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   14.770252] ohci_hcd 0000:00:12.0: USB HC takeover failed!  (BIOS/SMM bug)
[   14.770255] ohci_hcd 0000:00:12.0: can't setup
[   14.770258] ohci_hcd 0000:00:12.0: USB bus 1 deregistered
[   14.770293] ohci_hcd 0000:00:12.0: PCI INT A disabled
[   14.770295] ohci_hcd 0000:00:12.0: init 0000:00:12.0 fail, -16
[   14.770299] ohci_hcd: probe of 0000:00:12.0 failed with error -16
[   14.770311] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.770331] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   14.770361] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 1
[   24.770252] ohci_hcd 0000:00:12.1: USB HC takeover failed!  (BIOS/SMM bug)
[   24.770254] ohci_hcd 0000:00:12.1: can't setup
[   24.770257] ohci_hcd 0000:00:12.1: USB bus 1 deregistered
[   24.770289] ohci_hcd 0000:00:12.1: PCI INT A disabled
[   24.770291] ohci_hcd 0000:00:12.1: init 0000:00:12.1 fail, -16
[   24.770295] ohci_hcd: probe of 0000:00:12.1 failed with error -16
[   24.770308]   alloc irq_desc for 18 on node -1
[   24.770310]   alloc kstat_irqs on node -1
[   24.770315] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.770334] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   24.770364] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   34.770253] ohci_hcd 0000:00:13.0: USB HC takeover failed!  (BIOS/SMM bug)
[   34.770256] ohci_hcd 0000:00:13.0: can't setup
[   34.770259] ohci_hcd 0000:00:13.0: USB bus 1 deregistered
[   34.770290] ohci_hcd 0000:00:13.0: PCI INT A disabled
[   34.770293] ohci_hcd 0000:00:13.0: init 0000:00:13.0 fail, -16
[   34.770296] ohci_hcd: probe of 0000:00:13.0 failed with error -16
[   34.770308] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   34.770327] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   34.770356] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 1
[   44.770251] ohci_hcd 0000:00:13.1: USB HC takeover failed!  (BIOS/SMM bug)
[   44.770255] ohci_hcd 0000:00:13.1: can't setup
[   44.770257] ohci_hcd 0000:00:13.1: USB bus 1 deregistered
[   44.770287] ohci_hcd 0000:00:13.1: PCI INT A disabled
[   44.770289] ohci_hcd 0000:00:13.1: init 0000:00:13.1 fail, -16
[   44.770293] ohci_hcd: probe of 0000:00:13.1 failed with error -16
[   44.770305] uhci_hcd: USB Universal Host Controller Interface driver
[   44.770437] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   44.789439] serio: i8042 KBD port at 0x60,0x64 irq 1
[   44.789448] serio: i8042 AUX port at 0x60,0x64 irq 12
[   44.789518] mice: PS/2 mouse device common for all mice
[   44.789664] rtc_cmos 00:04: RTC can wake from S4
[   44.789709] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[   44.789779] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[   44.789875] device-mapper: uevent: version 1.0.3
[   44.789980] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[   44.790088] device-mapper: multipath: version 1.1.1 loaded
[   44.790091] device-mapper: multipath round-robin: version 1.0.0 loaded
[   44.790328] cpuidle: using governor ladder
[   44.790331] cpuidle: using governor menu
[   44.790620] TCP cubic registered
[   44.790766] NET: Registered protocol family 10
[   44.791182] lo: Disabled Privacy Extensions
[   44.791413] NET: Registered protocol family 17
[   44.791491] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-75 (2 cpu cores) (version 2.20.00)
[   44.791887] powernow-k8:    0 : pstate 0 (2200 MHz)
[   44.791889] powernow-k8:    1 : pstate 1 (1100 MHz)
[   44.791891] powernow-k8:    2 : pstate 2 (550 MHz)
[   44.793517] PM: Resume from disk failed.
[   44.793531] registered taskstats version 1
[   44.793928]   Magic number: 2:657:423
[   44.794073] rtc_cmos 00:04: setting system clock to 2010-11-04 09:26:56 UTC (1288862816)
[   44.794077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   44.794079] EDD information not available.
[   44.794201] Freeing unused kernel memory: 908k freed
[   44.794660] Write protecting the kernel read-only data: 10240k
[   44.794866] Freeing unused kernel memory: 412k freed
[   44.795232] Freeing unused kernel memory: 1644k freed
[   44.816775] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   44.821921] udev[75]: starting version 163
[   44.918116] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   44.918146] r8169 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   44.918203] r8169 0000:09:00.0: setting latency timer to 64
[   44.918220] r8169 0000:09:00.0: no MSI. Back to INTx.
[   44.918796] r8169 0000:09:00.0: eth0: RTL8102e at 0xffffc90000676000, a4:ba:db:97:54:b9, XID 04c00000 IRQ 17
[   45.045590] ahci 0000:00:11.0: version 3.0
[   45.045612]   alloc irq_desc for 22 on node -1
[   45.045615]   alloc kstat_irqs on node -1
[   45.045625] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   45.045786] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   45.045790] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[   45.046132] scsi0 : ahci
[   45.046279] scsi1 : ahci
[   45.046405] ata1: SATA max UDMA/133 irq_stat 0x00400000, PHY RDY changed irq 22
[   45.046409] ata2: SATA max UDMA/133 irq_stat 0x00000040 irq 22, connection status changed
[   45.990258] ata2: softreset failed (device not ready)
[   45.990262] ata2: applying SB600 PMP SRST workaround and retrying
[   45.990293] ata1: softreset failed (device not ready)
[   45.990297] ata1: applying SB600 PMP SRST workaround and retrying
[   46.190267] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   46.190309] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   46.192113] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7700H, 100A, max UDMA/100
[   46.198935] ata2.00: configured for UDMA/100
[   46.432893] ata1.00: ATA-8: ST9250315AS, 0003DEM1, max UDMA/133
[   46.432896] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   46.446568] ata1.00: configured for UDMA/133
[   46.460275] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0003 PQ: 0 ANSI: 5
[   46.460467] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   46.460605] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[   46.460723] sd 0:0:0:0: [sda] Write Protect is off
[   46.460727] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.460776] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.461078]  sda:
[   46.471357] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7700H 100A PQ: 0 ANSI: 5
[   46.499494]  sda1 sda2 sda3 sda4 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   46.509989] Uniform CD-ROM driver Revision: 3.20
[   46.510128] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   46.510204] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   46.524662]  sda5 >
[   46.525087] sd 0:0:0:0: [sda] Attached SCSI disk
[   47.101134] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   59.262662] udev[407]: starting version 163
[   59.349335] lp: driver loaded but no devices found
[   59.426093] lib80211: common routines for IEEE802.11 drivers
[   59.426099] lib80211_crypt: registered algorithm 'NULL'
[   59.467285] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x30c0, revision 0
[   59.474013] EDAC MC: Ver: 2.1.0 Oct 26 2010
[   59.534842] wl: module license 'MIXED/Proprietary' taints kernel.
[   59.534848] Disabling lock debugging due to kernel taint
[   59.666631] EDAC amd64_edac:  Ver: 3.3.0 Oct 26 2010
[   59.666696] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   59.666703] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   59.666705]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   59.666707]  (Note that use of the override may cause unknown side effects.)
[   59.666713] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   59.674832] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   59.716906] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   59.730168] wl 0000:0b:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   59.730180] wl 0000:0b:00.0: setting latency timer to 64
[   59.751060] input: Dell WMI hotkeys as /devices/virtual/input/input4
[   59.759948] type=1400 audit(1288877231.450:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=678 comm="apparmor_parser"
[   59.760277] type=1400 audit(1288877231.460:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=678 comm="apparmor_parser"
[   59.760437] type=1400 audit(1288877231.460:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=678 comm="apparmor_parser"
[   59.836215] acpi device:34: registered as cooling_device2
[   59.837024] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:31/LNXVIDEO:00/input/input5
[   59.837108] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   59.848967] lib80211_crypt: registered algorithm 'TKIP'
[   59.849186] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   59.985201] [fglrx] Maximum main memory to use for locked dma buffers: 3799 MBytes.
[   59.985494] [fglrx]   vendor: 1002 device: 9552 count: 1
[   59.985949] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[   59.985972] pci 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   59.985978] pci 0000:02:00.0: setting latency timer to 64
[   59.986179] [fglrx] Kernel PAT support is enabled
[   59.986212] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   60.003151] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   60.133175] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   60.133285] input: HDA ATI SB HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   60.197108] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   60.224187] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   60.316598] type=1400 audit(1288877232.010:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=939 comm="apparmor_parser"
[   60.317265] type=1400 audit(1288877232.010:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=940 comm="apparmor_parser"
[   60.317553] type=1400 audit(1288877232.010:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=940 comm="apparmor_parser"
[   60.317716] type=1400 audit(1288877232.010:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=940 comm="apparmor_parser"
[   60.322181] type=1400 audit(1288877232.020:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=942 comm="apparmor_parser"
[   60.327767] type=1400 audit(1288877232.020:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=942 comm="apparmor_parser"
[   60.331953] type=1400 audit(1288877232.030:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=942 comm="apparmor_parser"
[   60.362018] r8169 0000:09:00.0: eth0: link down
[   60.362790] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.873685] ppdev: user-space parallel port driver
[   61.273618] [fglrx] Could not enable MSI; System prevented initialization
[   61.274487] [fglrx] Firegl kernel thread PID: 1237
[   61.274768] [fglrx] IRQ 18 Enabled
[   61.982900] [fglrx] Gart USWC size:1240 M.
[   61.982905] [fglrx] Gart cacheable size:491 M.
[   61.982912] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   61.982915] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   61.982917] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   62.072515] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   65.741234] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   70.620022] eth1: no IPv6 routers present

```

Thank you for all the help so far, by the way.

---

### Post by P4man on 2010-11-04
Doesnt seem to have improved a whole lot, if at all.

Again, let me refer to my signature. Try the acpi_osi= option(s) described there, If none of those help, you can try the "nuclear bomb" option of adding ```
acpi=off
``` as kernel option, but that may well cause  a lot things to stop working properly.

Alternatively, see if you have bios settings that you can experiment with regarding acpi, apic and EHCI usb.

---

### Post by Zoltar567 on 2010-11-04
I tried those options, nothing.
Would you like me to post the dsmeg log for each?

I goofed around in my bios and found nothing about acpi, but it was the  SATA configuration, and i know from experience not to mess with that.

This has to be the OS' fault. In 10.04 the mouse worked perfectly and  the boot was fast. In 10.10 the boot is extremely slow and no USB works.  I might just revert back to 10.04, or wait for a much needed update.

---

### Post by P4man on 2010-11-04
Nah, you might want to file a bug report on launchpad and indeed stick to 10.04, though Im rather sure the issue is with the bios primarily and how the kernel has to cope with it.

---

### Post by Zoltar567 on 2010-11-04
I suppose. I just find it so odd that there could be such a huge discrepancy between 10.04 and 10.10, when no changes were made to my BIOS before then. I figured 10.10 would be better, guess not. Ill wait until it gets LTS. If that even happens. Im a linux noob. 
Thank you for all your help my friend. I have learned much.

---

### Post by Billthe4th on 2010-11-07
Hi Zoltar,

I was having exactly the same trouble as you, my usb just stopped working after I updated to 10.10 maverick meerkat - my USB related dmesg entries looked very similar to yours as well. I tried P4man's suggestion of adding "pci=nomsi" to the end of the default boot command line (and then running update-grub) and now usb is working perfectly! Are you sure you ran
```
# sudo update-grup
```
after you had edited /etc/default/grub and before you restarted?

P4man: thank you very much for your help with this, can you tell me any more about what pci=nomsi does? Is it safe to leave that option in? My motherboard is an Asus P5GC...

Thanks again :)

---

### Post by P4man on 2010-11-07
Glad it helped someone then at least :)

As you might have guessed, the nomsi switch disables MSI. That has nothing to do with the MSI brand, but its short for  Message Signaled Interrupts. Techno speak here:
[http://en.wikipedia.org/wiki/Message_Signaled_Interrupts](http://en.wikipedia.org/wiki/Message_Signaled_Interrupts)

Yes its safe to use, but it would be better if you had a bios that didnt require you to disable it.

---

### Post by Zoltar567 on 2010-11-07
I did run the sudo update grub command, i just dont know why it didnt work.

Its okay though my friends, i reverted to 10.04 successfully, my boot is about 10 seconds and my usb works like a charm. I dont really know whats better in 10.10, but i dont need it for all the hastle.

---

### Post by Cpierce on 2010-11-07
I just solved a usb issue, take a look here and hopefully you may find something that helps. 

[http://ubuntuforums.org/showthread.php?t=1610622](http://ubuntuforums.org/showthread.php?t=1610622)

---

### Post by Zoltar567 on 2010-11-07
My BIOS has Legacy. I even tried it with it on or off. Nothing.

This is simply 10.10's fault, considering it works perfectly in 10.04

---

### Post by hazyEgG on 2011-09-11
[B]

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"[/B]

or this just for code cleanliness:

[B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="pci=nomsi"[/B]


This is the correct nomanclature to use on the Grub config. This brought all my USB ports to life. I should have been weary when the USB install of _**Ubuntu 11.04**_ went south right in the middle of the install process on my _Dell Inspiron 1546_. Like the people stated above... just edit and update this file and it addresses a work around bug with Ubuntu and some systems.

---

