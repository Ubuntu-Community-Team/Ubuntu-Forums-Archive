---
title: "Soft reset failed ---&gt; totally dead"
date: 2009-06-24
forum: General Help
---

### Post by ph0 on 2009-06-24
Hi there.

I'm definitely not the first one to ask this - 

9.04 worked fine - except for "soft reset failed" that increased the startup time to 2.5 minutes instead of 30 seconds but has not been a big issue otherwise. Because right now I've got a new thing - in the very end of the startup, when Ubuntu logo with a progress indicator is seen, it dies for good, the screen becomes pixelated mess and it does not respond to keyboard.

RAM was the only thing that was different in the original 'stable' config (used to be some old Kingston stuff, 2x1 GB).

XP SP3 is perfectly stable. 

_________________________
Intel Q9550
Gigabyte EP45-DQ6
**Mushkin DDR2 1066 (2x2GB)**
Sapphire HD4850 1GB
Samsung T200HD
WD Black 640 GB
CORSAIR CMPSU-650TX

---

### Post by HavocXphere on 2009-06-24
Sounds like a graphics driver issue. What graphics card are you using?

---

### Post by ph0 on 2009-06-24
I've seen other people having problems with the same motherboard, as well as with other relatively new boards. Should I update BIOS (currently v. F5)? [http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=2831](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=2831) 

Just in case,
RAM latency: 5-5-5-15, 5-5-5-18 @ 400MHz, 4-4-4-12 @ 266 MHz
For some reason, Everest sees RAM as DDR2-800MHz while it should be 1066.

---

### Post by ph0 on 2009-06-24
'soft reset' thing was solved by disabling Onboard SATA/IDE Device (under Integrated Peripherals). Now it boots super fast but still dies in the end. :)

---

### Post by ph0 on 2009-06-25
ATI driver update helped. Got some help with the shell from a local guru here. Moving on! :)

---

### Post by bluzit on 2009-06-30
Still have error message at boot. Ata 1, Ata 2, softreset failed Device Not Ready. Can't this be fixed? I run an AMD pc with an Invidia graphics card. Thanks,  bluzit

---

### Post by QIII on 2009-06-30
> **bluzit said:**
> Still have error message at boot. Ata 1, Ata 2, softreset failed Device Not Ready. Can't this be fixed? I run an AMD pc with an Invidia graphics card. Thanks,  bluzit

Does your machine run after you get that message?


Edit --  Don't know if you'll get back to this tonight, bluzit, so here are some additional points to ponder.

If you are having no performance problems at startup or while running, I wouldn't worry about it.  There are bug reports about this issue with some AMD chipsets.  Personally, I think it probably has to do with the OS probing your SATA headers on your motherboard and finding nothing there, hence the "Device Not Ready" message.

I have an AMD machine with 4 SATA headers.  (The DVD drive is on an IDE header, strangely.)  I have two hdds for dual booting Vista (hack, cough) and Jaunty.  So I have two open SATA headers.  I get two "soft test failed" messages on startup, and my machine boots right up.

---

### Post by Slywire on 2009-07-31
I have an LG LW20 Express laptop that I'm trying to install ubuntu-9.04 from a live CD. I have absolutely no hard drives installed (Can't find any to replace my defective drive) so I'm running Ubuntu from a 8GB SD card. On Kubuntu Gutsy(8.10) I had no problems  on booting. When trying to boot from the cd without any flash drives or memory card inserted, I get the ata1 softreset failed (device not ready) error and the laptop refuses to do anything more. I get this message about 5 times before the laptop just turns off. Any suggestions? i have tried disabling the entire IDE channel in the bios, and only keep the CD drive live, but no success. Any suggestions? I'm at a dead end

---

### Post by Zyprexa on 2011-05-24
When i upgraded my serverbox to natty, i started getting this error sometimes when i boot. And i usually don't have a screen, or keyboard, connected to it so its frustrating when the computer wont come up again after reboot.

I have a MSI K9A2GM-F V3 motherboard with 4 sata disks. Please tell me what info i should include if someone could help me. :(

I've included a dmesg log in case that helps, but i'm not sure if it's from when it fails to boot but the errors are present on line #659 - #664. I've already reinstalled ubuntu on it but it didnt help. I've run fsck, changed filesystem to ext3, but still it doesnt help.

I'm not sure if this error was present on maveric, but i think it was working flawlessly under it until i upgraded to natty. Only times it wouldnt boot was when i messed something up myself :)

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-server (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 (Ubuntu 2.6.38-8.42-server 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-server root=UUID=eac5613e-37bd-4b3e-8c1b-d3d1fd582484 ro quiet
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7fa0000 (usable)
[    0.000000]  BIOS-e820: 00000000d7fa0000 - 00000000d7fae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d7fae000 - 00000000d7ff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000d7ff0000 - 00000000d7ffe000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: MICRO-STAR INTERANTONAL CO.,LTD MS-7302/MS-7302, BIOS V2.0 04/16/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000120000000 aka 4608M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xd7fa0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000d7fa0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00d7e00000 page 2M
[    0.000000]  00d7e00000 - 00d7fa0000 page 4k
[    0.000000] kernel direct mapping tables up to d7fa0000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ d7f9e000-d7fa0000
[    0.000000] RAMDISK: 364da000 - 37265000
[    0.000000] ACPI: RSDP 00000000000fa030 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000d7fa0000 0003C (v01 7302MS A7302200 20080416 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000d7fa0200 00084 (v02 7302MS A7302200 20080416 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000d7fa05c0 048E0 (v01  A7302 A7302200 00000200 INTL 20051117)
[    0.000000] ACPI: FACS 00000000d7fae000 00040
[    0.000000] ACPI: APIC 00000000d7fa0390 0006C (v01 7302MS A7302200 20080416 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000d7fa0400 0003C (v01 7302MS OEMMCFG  20080416 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000d7fa0440 00176 (v01 7302MS A7302200 20080416 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000d7fae040 00071 (v01 7302MS A7302200 20080416 MSFT 00000097)
[    0.000000] ACPI: TEPH 00000000d7fa4ea0 00038 (v01 7302MS OEMHPET  20080416 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [000000011fffb000 - 000000011fffffff]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff88011c000000-ffff88011f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000d7fa0
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 1015599
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 866264 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000d7fa0000 - 00000000d7fae000
[    0.000000] PM: Registered nosave memory: 00000000d7fae000 - 00000000d7ff0000
[    0.000000] PM: Registered nosave memory: 00000000d7ff0000 - 00000000d7ffe000
[    0.000000] PM: Registered nosave memory: 00000000d7ffe000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d7ffe000 (gap: d7ffe000:27f02000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800d7c00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 999465
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-server root=UUID=eac5613e-37bd-4b3e-8c1b-d3d1fd582484 ro quiet
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 879c000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ cc000000
[    0.000000] PM: Registered nosave memory: 00000000cc000000 - 00000000d0000000
[    0.000000] Memory: 3845512k/4718592k available (6023k kernel code, 656196k absent, 216884k reserved, 5025k data, 880k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 40632320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2699.664 MHz processor.
[    0.020004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5399.32 BogoMIPS (lpj=26996640)
[    0.020008] pid_max: default: 32768 minimum: 301
[    0.020029] Security Framework initialized
[    0.020045] AppArmor: AppArmor initialized
[    0.020046] Yama: becoming mindful.
[    0.020461] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.022135] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.022878] Mount-cache hash table entries: 256
[    0.023009] Initializing cgroup subsys ns
[    0.023012] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.023015] Initializing cgroup subsys cpuacct
[    0.023019] Initializing cgroup subsys memory
[    0.023027] Initializing cgroup subsys devices
[    0.023029] Initializing cgroup subsys freezer
[    0.023031] Initializing cgroup subsys net_cls
[    0.023033] Initializing cgroup subsys blkio
[    0.023064] tseg: 0000000000
[    0.023078] CPU: Physical Processor ID: 0
[    0.023079] CPU: Processor Core ID: 0
[    0.023081] mce: CPU supports 6 MCE banks
[    0.023091] using C1E aware idle routine
[    0.024558] ACPI: Core revision 20110112
[    0.028205] ftrace: allocating 24611 entries in 97 pages
[    0.030075] Setting APIC routing to flat
[    0.030385] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.136550] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.140000] Performance Events: AMD PMU driver.
[    0.140000] ... version:                0
[    0.140000] ... bit width:              48
[    0.140000] ... generic registers:      4
[    0.140000] ... value mask:             0000ffffffffffff
[    0.140000] ... max period:             00007fffffffffff
[    0.140000] ... fixed-purpose events:   0
[    0.140000] ... event mask:             000000000000000f
[    0.140000] Booting Node   0, Processors  #1
[    0.300009] Brought up 2 CPUs
[    0.300011] Total of 2 processors activated (10799.67 BogoMIPS).
[    0.300387] devtmpfs: initialized
[    0.301063] print_constraints: dummy: 
[    0.301063] Time: 13:21:13  Date: 05/24/11
[    0.301063] NET: Registered protocol family 16
[    0.301063] node 0 link 0: io port [1000, ffffff]
[    0.301063] TOM: 00000000e0000000 aka 3584M
[    0.301063] Fam 10h mmconf [e0000000, e00fffff]
[    0.301063] node 0 link 0: mmio [f0000000, f7feffff]
[    0.301063] node 0 link 0: mmio [e0000000, efffffff] ==> [e0100000, efffffff]
[    0.301063] node 0 link 0: mmio [e0000000, ffff] ==> none
[    0.301063] node 0 link 0: mmio [a0000, bffff]
[    0.301063] node 0 link 0: mmio [f7ff0000, ffffffff]
[    0.301063] TOM2: 0000000120000000 aka 4608M
[    0.301063] bus: [00, 07] on node 0 link 0
[    0.301063] bus: 00 index 0 [io  0x0000-0xffff]
[    0.301063] bus: 00 index 1 [mem 0xe0100000-0xffffffff]
[    0.301063] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.301063] bus: 00 index 3 [mem 0x120000000-0xfcffffffff]
[    0.301063] Extended Config Space enabled on 1 nodes
[    0.301063] ACPI: bus type pci registered
[    0.301063] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.301063] PCI: not using MMCONFIG
[    0.301063] PCI: Using configuration type 1 for base access
[    0.301063] PCI: Using configuration type 1 for extended access
[    0.301676] Trying to unpack rootfs image as initramfs...
[    0.301755] bio: create slab <bio-0> at 0
[    0.302440] ACPI: EC: Detected MSI hardware, enabling workarounds.
[    0.302442] ACPI: EC: Look up EC in DSDT
[    0.303336] ACPI: Executed 3 blocks of module-level executable AML code
[    0.330391] ACPI: Interpreter enabled
[    0.330394] ACPI: (supports S0 S1 S4 S5)
[    0.330410] ACPI: Using IOAPIC for interrupt routing
[    0.330429] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.331035] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.430075] ACPI: No dock devices found.
[    0.430078] HEST: Table not found.
[    0.430081] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.430150] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.430289] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.430291] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.430293] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.430295] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.430297] pci_root PNP0A03:00: host bridge window [mem 0xd8000000-0xdfffffff]
[    0.430299] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfed44fff]
[    0.430311] pci 0000:00:00.0: [1002:7911] type 0 class 0x000600
[    0.430339] pci 0000:00:01.0: [1002:7912] type 1 class 0x000604
[    0.430371] pci 0000:00:05.0: [1002:7915] type 1 class 0x000604
[    0.430396] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.430399] pci 0000:00:05.0: PME# disabled
[    0.430435] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.430458] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.430468] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.430478] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.430488] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.430498] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.430508] pci 0000:00:11.0: reg 24: [mem 0xfe8ffc00-0xfe8fffff]
[    0.430529] pci 0000:00:11.0: set SATA to AHCI mode
[    0.430572] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.430586] pci 0000:00:12.0: reg 10: [mem 0xfe8fe000-0xfe8fefff]
[    0.430652] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.430666] pci 0000:00:12.1: reg 10: [mem 0xfe8fd000-0xfe8fdfff]
[    0.430738] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.430758] pci 0000:00:12.2: reg 10: [mem 0xfe8ff800-0xfe8ff8ff]
[    0.430831] pci 0000:00:12.2: supports D1 D2
[    0.430833] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.430837] pci 0000:00:12.2: PME# disabled
[    0.430858] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.430872] pci 0000:00:13.0: reg 10: [mem 0xfe8fc000-0xfe8fcfff]
[    0.430941] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.430954] pci 0000:00:13.1: reg 10: [mem 0xfe8fb000-0xfe8fbfff]
[    0.431026] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.431046] pci 0000:00:13.2: reg 10: [mem 0xfe8ff400-0xfe8ff4ff]
[    0.431119] pci 0000:00:13.2: supports D1 D2
[    0.431121] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.431125] pci 0000:00:13.2: PME# disabled
[    0.431150] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.431247] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.431264] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.431274] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.431283] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.431293] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.431303] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.431354] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.431377] pci 0000:00:14.2: reg 10: [mem 0xfe8f4000-0xfe8f7fff 64bit]
[    0.431437] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.431441] pci 0000:00:14.2: PME# disabled
[    0.431454] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.431532] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.431574] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.431588] pci 0000:00:14.5: reg 10: [mem 0xfe8fa000-0xfe8fafff]
[    0.431659] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.431673] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.431685] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.431697] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.431712] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.431750] pci 0000:01:05.0: [1002:796e] type 0 class 0x000300
[    0.431760] pci 0000:01:05.0: reg 10: [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.431766] pci 0000:01:05.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.431771] pci 0000:01:05.0: reg 20: [io  0xd000-0xd0ff]
[    0.431775] pci 0000:01:05.0: reg 24: [mem 0xfe900000-0xfe9fffff]
[    0.431786] pci 0000:01:05.0: supports D1 D2
[    0.431800] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.431803] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.431806] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.431809] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.431845] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.431858] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.431879] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.431892] pci 0000:02:00.0: reg 20: [mem 0xfdfe0000-0xfdfeffff 64bit pref]
[    0.431902] pci 0000:02:00.0: reg 30: [mem 0xfebf0000-0xfebfffff pref]
[    0.431931] pci 0000:02:00.0: supports D1 D2
[    0.431933] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.431936] pci 0000:02:00.0: PME# disabled
[    0.450012] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.450015] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.450018] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.450021] pci 0000:00:05.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.450083] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.450088] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.450092] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.450096] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.450098] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.450100] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.450102] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.450104] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.450106] pci 0000:00:14.4:   bridge window [mem 0xd8000000-0xdfffffff] (subtractive decode)
[    0.450108] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfed44fff] (subtractive decode)
[    0.450120] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.450236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.450265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.450302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.450348]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.453184] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.453217] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.453247] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.453277] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.453306] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.453336] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.453366] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.453396] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.453500] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.453502] vgaarb: loaded
[    0.453659] SCSI subsystem initialized
[    0.453722] libata version 3.00 loaded.
[    0.453758] usbcore: registered new interface driver usbfs
[    0.453766] usbcore: registered new interface driver hub
[    0.453791] usbcore: registered new device driver usb
[    0.453871] wmi: Mapper loaded
[    0.453872] PCI: Using ACPI for IRQ routing
[    0.453875] PCI: pci_cache_line_size set to 64 bytes
[    0.453941] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
[    0.453943] reserve RAM buffer: 00000000d7fa0000 - 00000000d7ffffff 
[    0.454026] NetLabel: Initializing
[    0.454027] NetLabel:  domain hash size = 128
[    0.454028] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.454039] NetLabel:  unlabeled traffic allowed by default
[    0.459898] AppArmor: AppArmor Filesystem Enabled
[    0.459929] pnp: PnP ACPI init
[    0.459948] ACPI: bus type pnp registered
[    0.460096] pnp 00:00: [bus 00-ff]
[    0.460099] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.460101] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.460102] pnp 00:00: [io  0x0d00-0xffff window]
[    0.460104] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.460106] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.460108] pnp 00:00: [mem 0xd8000000-0xdfffffff window]
[    0.460112] pnp 00:00: [mem 0xf0000000-0xfed44fff window]
[    0.460168] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.460198] pnp 00:01: [dma 4]
[    0.460200] pnp 00:01: [io  0x0000-0x000f]
[    0.460201] pnp 00:01: [io  0x0081-0x0083]
[    0.460203] pnp 00:01: [io  0x0087]
[    0.460204] pnp 00:01: [io  0x0089-0x008b]
[    0.460205] pnp 00:01: [io  0x008f]
[    0.460207] pnp 00:01: [io  0x00c0-0x00df]
[    0.460230] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.460238] pnp 00:02: [io  0x0070-0x0071]
[    0.460251] pnp 00:02: [irq 8]
[    0.460271] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.460277] pnp 00:03: [io  0x0061]
[    0.460298] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.460304] pnp 00:04: [io  0x00f0-0x00ff]
[    0.460308] pnp 00:04: [irq 13]
[    0.460327] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.460518] pnp 00:05: [io  0x03f8-0x03ff]
[    0.460522] pnp 00:05: [irq 4]
[    0.460524] pnp 00:05: [dma 0 disabled]
[    0.460571] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.460744] pnp 00:06: [io  0x02f8-0x02ff]
[    0.460749] pnp 00:06: [irq 3]
[    0.460750] pnp 00:06: [dma 0 disabled]
[    0.460813] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.461110] pnp 00:07: [io  0x0378-0x037f]
[    0.461114] pnp 00:07: [irq 7]
[    0.461116] pnp 00:07: [dma 0 disabled]
[    0.461204] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.461224] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.461245] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.461282] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.461283] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.461344] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.461346] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.461349] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.461406] pnp 00:0a: [io  0x0010-0x001f]
[    0.461408] pnp 00:0a: [io  0x0022-0x003f]
[    0.461409] pnp 00:0a: [io  0x0062-0x0063]
[    0.461410] pnp 00:0a: [io  0x0065-0x006f]
[    0.461412] pnp 00:0a: [io  0x0072-0x007f]
[    0.461413] pnp 00:0a: [io  0x0080]
[    0.461415] pnp 00:0a: [io  0x0084-0x0086]
[    0.461416] pnp 00:0a: [io  0x0088]
[    0.461417] pnp 00:0a: [io  0x008c-0x008e]
[    0.461419] pnp 00:0a: [io  0x0090-0x009f]
[    0.461420] pnp 00:0a: [io  0x00a2-0x00bf]
[    0.461422] pnp 00:0a: [io  0x00b1]
[    0.461423] pnp 00:0a: [io  0x00e0-0x00ef]
[    0.461424] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.461426] pnp 00:0a: [io  0x040b]
[    0.461427] pnp 00:0a: [io  0x04d6]
[    0.461428] pnp 00:0a: [io  0x0c00-0x0c01]
[    0.461430] pnp 00:0a: [io  0x0c14]
[    0.461431] pnp 00:0a: [io  0x0c50-0x0c51]
[    0.461433] pnp 00:0a: [io  0x0c52]
[    0.461434] pnp 00:0a: [io  0x0c6c]
[    0.461438] pnp 00:0a: [io  0x0c6f]
[    0.461439] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    0.461441] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    0.461442] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    0.461443] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    0.461445] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    0.461446] pnp 00:0a: [io  0x0800-0x089f]
[    0.461448] pnp 00:0a: [io  0x0b20-0x0b2f]
[    0.461449] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.461451] pnp 00:0a: [io  0x0900-0x090f]
[    0.461452] pnp 00:0a: [io  0x0910-0x091f]
[    0.461454] pnp 00:0a: [io  0xfe00-0xfefe]
[    0.461456] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.461457] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
[    0.461518] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.461520] system 00:0a: [io  0x040b] has been reserved
[    0.461522] system 00:0a: [io  0x04d6] has been reserved
[    0.461524] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.461526] system 00:0a: [io  0x0c14] has been reserved
[    0.461528] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.461529] system 00:0a: [io  0x0c52] has been reserved
[    0.461531] system 00:0a: [io  0x0c6c] has been reserved
[    0.461533] system 00:0a: [io  0x0c6f] has been reserved
[    0.461535] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.461537] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.461539] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.461543] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.461545] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.461547] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.461549] system 00:0a: [io  0x0b20-0x0b2f] has been reserved
[    0.461551] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.461553] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.461555] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.461558] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.461560] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.461563] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.461647] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    0.461649] pnp 00:0b: [io  0x0600-0x06df]
[    0.461650] pnp 00:0b: [io  0x0ae0-0x0aef]
[    0.461688] system 00:0b: [io  0x0600-0x06df] has been reserved
[    0.461690] system 00:0b: [io  0x0ae0-0x0aef] has been reserved
[    0.461693] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.461724] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.461758] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.461760] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.461843] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.461844] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.461846] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.461848] pnp 00:0d: [mem 0x00100000-0xd7ffffff]
[    0.461849] pnp 00:0d: [mem 0xfed45000-0xffffffff]
[    0.461891] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.461893] system 00:0d: [mem 0x000c0000-0x000cffff] has been reserved
[    0.461895] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.461897] system 00:0d: [mem 0x00100000-0xd7ffffff] could not be reserved
[    0.461899] system 00:0d: [mem 0xfed45000-0xffffffff] could not be reserved
[    0.461902] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.461979] pnp: PnP ACPI: found 14 devices
[    0.461980] ACPI: ACPI bus type pnp unregistered
[    0.467760] Switching to clocksource acpi_pm
[    0.467911] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.467914] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.467917] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.467920] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.467924] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.467926] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.467929] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.467931] pci 0000:00:05.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.467935] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.467936] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.467941] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.467945] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.467958] pci 0000:00:05.0: setting latency timer to 64
[    0.467965] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.467968] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.467970] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.467972] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.467974] pci_bus 0000:00: resource 8 [mem 0xd8000000-0xdfffffff]
[    0.467976] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.467978] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.467980] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
[    0.467982] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.467984] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.467986] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.467988] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.467990] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.467992] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.467994] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.467996] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.467998] pci_bus 0000:03: resource 8 [mem 0xd8000000-0xdfffffff]
[    0.468000] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.468033] NET: Registered protocol family 2
[    0.468170] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.469279] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.469279] Switched to NOHz mode on CPU #0
[    0.467870] Switched to NOHz mode on CPU #1
[    0.469279] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.469279] TCP: Hash tables configured (established 524288 bind 65536)
[    0.469279] TCP reno registered
[    0.469279] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.469279] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.469279] NET: Registered protocol family 1
[    0.566709] Freeing initrd memory: 13868k freed
[    0.600043] pci 0000:01:05.0: Boot video device
[    0.600048] PCI: CLS 64 bytes, default 64
[    0.601305] PCI-DMA: Disabling AGP.
[    0.601418] PCI-DMA: aperture base @ cc000000 size 65536 KB
[    0.601420] PCI-DMA: using GART IOMMU.
[    0.601423] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.605177] audit: initializing netlink socket (disabled)
[    0.605196] type=2000 audit(1306243273.599:1): initialized
[    0.615896] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.617370] VFS: Disk quotas dquot_6.5.2
[    0.617416] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.617945] fuse init (API version 7.16)
[    0.618024] msgmni has been set to 7666
[    0.618328] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.618368] io scheduler noop registered
[    0.618370] io scheduler deadline registered (default)
[    0.618407] io scheduler cfq registered
[    0.618615] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.618636] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.618750] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.670026] ACPI: Power Button [PWRB]
[    0.670065] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.670067] ACPI: Power Button [PWRF]
[    0.670189] ACPI: acpi_idle registered with cpuidle
[    0.671311] ERST: Table is not found!
[    0.671387] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.692036] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.760658] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.080753] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.110701] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.120242] hpet_acpi_add: no address or irqs in _CRS
[    1.120253] Linux agpgart interface v0.103
[    1.121128] brd: module loaded
[    1.121525] loop: module loaded
[    1.121601] i2c-core: driver [adp5520] using legacy suspend method
[    1.121603] i2c-core: driver [adp5520] using legacy resume method
[    1.121772] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.121800] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.122086] Fixed MDIO Bus: probed
[    1.122107] PPP generic driver version 2.4.2
[    1.122136] tun: Universal TUN/TAP device driver, 1.6
[    1.122138] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.122203] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.122250] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.122272] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.122312] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.150049] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.150064] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.150077] ehci_hcd 0000:00:12.2: debug port 1
[    1.150099] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
[    1.170020] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.170113] hub 1-0:1.0: USB hub found
[    1.170117] hub 1-0:1.0: 6 ports detected
[    1.170231] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.170240] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.170273] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.170301] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.170313] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.170326] ehci_hcd 0000:00:13.2: debug port 1
[    1.170343] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
[    1.190024] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.190097] hub 2-0:1.0: USB hub found
[    1.190100] hub 2-0:1.0: 6 ports detected
[    1.190172] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.190214] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.190223] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.190253] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.190295] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
[    1.254107] hub 3-0:1.0: USB hub found
[    1.254113] hub 3-0:1.0: 3 ports detected
[    1.254215] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.254224] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.254253] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.254286] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
[    1.314104] hub 4-0:1.0: USB hub found
[    1.314109] hub 4-0:1.0: 3 ports detected
[    1.314217] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.314226] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.314256] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.314295] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
[    1.374105] hub 5-0:1.0: USB hub found
[    1.374110] hub 5-0:1.0: 3 ports detected
[    1.374211] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.374219] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.374251] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.374283] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8fb000
[    1.434107] hub 6-0:1.0: USB hub found
[    1.434112] hub 6-0:1.0: 3 ports detected
[    1.434211] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.434219] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.434255] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.434287] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8fa000
[    1.494099] hub 7-0:1.0: USB hub found
[    1.494104] hub 7-0:1.0: 2 ports detected
[    1.494168] uhci_hcd: USB Universal Host Controller Interface driver
[    1.494242] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.496294] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.496298] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.496352] mousedev: PS/2 mouse device common for all mice
[    1.496437] rtc_cmos 00:02: RTC can wake from S4
[    1.510062] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.510084] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.510160] device-mapper: uevent: version 1.0.3
[    1.510221] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.510304] device-mapper: multipath: version 1.2.0 loaded
[    1.510306] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.510437] cpuidle: using governor ladder
[    1.510438] cpuidle: using governor menu
[    1.510629] TCP cubic registered
[    1.510733] NET: Registered protocol family 10
[    1.511128] NET: Registered protocol family 17
[    1.511140] Registering the dns_resolver key type
[    1.511161] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor (2 cpu cores) (version 2.20.00)
[    1.511174] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.511175] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.511265] PM: Hibernation image not present or could not be loaded.
[    1.511280] registered taskstats version 1
[    1.511470]   Magic number: 11:996:382
[    1.511552] rtc_cmos 00:02: setting system clock to 2011-05-24 13:21:14 UTC (1306243274)
[    1.511555] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.511556] EDD information not available.
[    1.512850] Freeing unused kernel memory: 880k freed
[    1.513150] Write protecting the kernel read-only data: 10240k
[    1.513566] Freeing unused kernel memory: 104k freed
[    1.517598] Freeing unused kernel memory: 1416k freed
[    1.534305] <30>udev[97]: starting version 167
[    1.575417] xor: automatically using best checksumming function: generic_sse
[    1.610037] Refined TSC clocksource calibration: 2700.095 MHz.
[    1.610041] Switching to clocksource tsc
[    1.620035]    generic_sse: 10962.400 MB/sec
[    1.620037] xor: using function: generic_sse (10962.400 MB/sec)
[    1.624192] device-mapper: dm-raid45: initialized v0.2594b
[    1.640768] scsi0 : pata_atiixp
[    1.641465] scsi1 : pata_atiixp
[    1.641991] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.641993] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.643363] ahci 0000:00:11.0: version 3.0
[    1.643386] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.643451] ahci 0000:00:11.0: irq 40 for MSI/MSI-X
[    1.643538] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.643542] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.644091] scsi2 : ahci
[    1.645870] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.645893] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.645934] r8169 0000:02:00.0: setting latency timer to 64
[    1.645979] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
[    1.646356] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xffffc90000662000, 00:24:21:54:ef:d9, XID 1c4000c0 IRQ 41
[    1.646695] scsi3 : ahci
[    1.648452] scsi4 : ahci
[    1.650562] scsi5 : ahci
[    1.650634] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 40
[    1.650638] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 40
[    1.650641] ata5: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 40
[    1.650644] ata6: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 40
[    2.200012] ata5: softreset failed (device not ready)
[    2.200016] ata5: applying SB600 PMP SRST workaround and retrying
[    2.200033] ata3: softreset failed (device not ready)
[    2.200037] ata3: applying SB600 PMP SRST workaround and retrying
[    2.200053] ata6: softreset failed (device not ready)
[    2.200056] ata6: applying SB600 PMP SRST workaround and retrying
[    2.200071] ata4: softreset failed (device not ready)
[    2.200074] ata4: applying SB600 PMP SRST workaround and retrying
[    2.400020] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.400043] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.400066] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.400084] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.401117] ata6.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    2.401119] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.401244] ata5.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    2.401246] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.401309] ata4.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    2.401311] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.402515] ata5.00: configured for UDMA/133
[    2.402861] ata6.00: configured for UDMA/133
[    2.403590] ata4.00: configured for UDMA/133
[    2.426858] ata3.00: ATA-8: ST3250318AS, CC44, max UDMA/133
[    2.426860] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.466242] ata3.00: configured for UDMA/133
[    2.466359] scsi 2:0:0:0: Direct-Access     ATA      ST3250318AS      CC44 PQ: 0 ANSI: 5
[    2.466478] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.466505] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.466513] sd 2:0:0:0: [sda] Write Protect is off
[    2.466515] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.466530] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.466589] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    2.466695] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.466781] scsi 4:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    2.466894] sd 4:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.466912] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.466970] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.467001] sd 3:0:0:0: [sdb] Write Protect is off
[    2.467004] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.467017] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.467042] scsi 5:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    2.467134] sd 5:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.467161] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    2.467164] sd 5:0:0:0: [sdd] Write Protect is off
[    2.467166] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.467180] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.467200] sd 4:0:0:0: [sdc] Write Protect is off
[    2.467202] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.467221] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.508179]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.508449] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.927134]  sdc: sdc1
[    2.927291] sd 4:0:0:0: [sdc] Attached SCSI disk
[    2.942845]  sdd: sdd1
[    2.943003] sd 5:0:0:0: [sdd] Attached SCSI disk
[    2.952736]  sdb: sdb1
[    2.952905] sd 3:0:0:0: [sdb] Attached SCSI disk
[    3.341480] EXT3-fs: barriers not enabled
[    3.356854] kjournald starting.  Commit interval 5 seconds
[    3.356885] EXT3-fs (sda2): mounted filesystem with ordered data mode
[    8.399922] <30>udev[415]: starting version 167
[    8.427145] Adding 9735352k swap on /dev/sda1.  Priority:-1 extents:1 across:9735352k 
[    8.441141] lp: driver loaded but no devices found
[    8.522335] MCE: In-kernel MCE decoding enabled.
[    8.529501] parport_pc 00:07: reported by Plug and Play ACPI
[    8.529557] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.536169] EDAC MC: Ver: 2.1.0 Apr 11 2011
[    8.538368] EDAC amd64_edac: v3.3.0
[    8.575525] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.578796] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
[    8.582219] EDAC amd64: DRAM ECC disabled.
[    8.582229] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    8.582230]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    8.582231]  (Note that use of the override may cause unknown side effects.)
[    8.584040] type=1400 audit(1306243281.559:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
[    8.584339] type=1400 audit(1306243281.559:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
[    8.584527] type=1400 audit(1306243281.559:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[    8.587222] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    8.588037] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    8.588107] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[    8.595349] Bridge firewalling registered
[    8.598561] device eth0 entered promiscuous mode
[    8.603341] r8169 0000:02:00.0: eth0: link down
[    8.603350] r8169 0000:02:00.0: eth0: link down
[    8.603873] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.619029] [drm] Initialized drm 1.1.0 20060810
[    8.622478] lp0: using parport0 (interrupt-driven).
[    8.698386] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.833876] ppdev: user-space parallel port driver
[    8.857689] [drm] radeon defaulting to kernel modesetting.
[    8.857692] [drm] radeon kernel modesetting enabled.
[    8.860302] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.862284] [drm] initializing kernel modesetting (RS740 0x1002:0x796E).
[    8.862321] [drm] register mmio base: 0xFEAF0000
[    8.862322] [drm] register mmio size: 65536
[    8.863086] ATOM BIOS: ATI
[    8.863101] radeon 0000:01:05.0: VRAM: 128M 0x00000000D8000000 - 0x00000000DFFFFFFF (128M used)
[    8.863104] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    8.863121] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.863122] [drm] Driver supports precise vblank timestamp query.
[    8.863132] [drm] radeon: irq initialized.
[    8.872669] [drm] Detected VRAM RAM=128M, BAR=128M
[    8.872673] [drm] RAM width 128bits DDR
[    8.878492] [TTM] Zone  kernel: Available graphics memory: 1963866 kiB.
[    8.878494] [TTM] Initializing pool allocator.
[    8.878516] [drm] radeon: 128M of VRAM memory ready
[    8.878517] [drm] radeon: 512M of GTT memory ready.
[    8.878536] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    8.884976] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[    8.899666] radeon 0000:01:05.0: WB enabled
[    8.899758] [drm] Loading RS690/RS740 Microcode
[    8.899807] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.922198] [drm] radeon: ring at 0x00000000A0001000
[    8.922218] [drm] ring test succeeded in 1 usecs
[    8.922335] [drm] radeon: ib pool ready.
[    8.922397] [drm] ib test succeeded in 0 usecs
[    8.922399] [drm] Enabling audio support
[    8.922406] failed to evaluate ATIF got AE_BAD_PARAMETER
[    8.922552] [drm] Radeon Display Connectors
[    8.922554] [drm] Connector 0:
[    8.922555] [drm]   VGA
[    8.922557] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[    8.922558] [drm]   Encoders:
[    8.922559] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    8.961790] hda_codec: ALC888: BIOS auto-probing.
[    8.973145] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input2
[    9.020073] No connectors reported connected with modes
[    9.020079] [drm] Cannot find any crtc or sizes - going 1024x768
[    9.027352] [drm] fb mappable at 0xF0040000
[    9.027353] [drm] vram apper at 0xF0000000
[    9.027354] [drm] size 3145728
[    9.027355] [drm] fb depth is 24
[    9.027357] [drm]    pitch is 4096
[    9.027606] Console: switching to colour frame buffer device 128x48
[    9.034679] fb0: radeondrmfb frame buffer device
[    9.034680] drm: registered panic notifier
[    9.034687] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[    9.437042] EXT3-fs (sda2): using internal journal
[    9.640939] EXT3-fs: barriers not enabled
[    9.641144] kjournald starting.  Commit interval 5 seconds
[    9.642360] EXT3-fs (dm-0): using internal journal
[    9.642364] EXT3-fs (dm-0): mounted filesystem with ordered data mode
[   10.237678] EXT3-fs: barriers not enabled
[   10.237945] kjournald starting.  Commit interval 5 seconds
[   10.238215] EXT3-fs (sda6): using internal journal
[   10.238219] EXT3-fs (sda6): mounted filesystem with ordered data mode
[   10.269531] r8169 0000:02:00.0: eth0: link up
[   10.269979] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   10.270823] bru0: port 1(eth0) entering forwarding state
[   10.270825] bru0: port 1(eth0) entering forwarding state
[   19.070006] bru0: no IPv6 routers present
[   20.750012] eth0: no IPv6 routers present
[   34.948277] EXT3-fs: barriers not enabled
[   34.968135] kjournald starting.  Commit interval 5 seconds
[   34.968368] EXT3-fs (sda5): using internal journal
[   34.968373] EXT3-fs (sda5): mounted filesystem with ordered data mode
[   35.046484] type=1400 audit(1306243308.054:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/libvirt/virt-aa-helper" pid=1036 comm="apparmor_parser"
[   35.049366] type=1400 audit(1306243308.054:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1035 comm="apparmor_parser"
[   35.049679] type=1400 audit(1306243308.054:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1035 comm="apparmor_parser"
[   35.049873] type=1400 audit(1306243308.054:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1035 comm="apparmor_parser"
[   35.051667] type=1400 audit(1306243308.064:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/libvirtd" pid=1037 comm="apparmor_parser"
[   35.053324] type=1400 audit(1306243308.064:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1038 comm="apparmor_parser"
[   35.148381] kvm: Nested Virtualization enabled
[   35.148387] kvm: Nested Paging enabled
```

---

