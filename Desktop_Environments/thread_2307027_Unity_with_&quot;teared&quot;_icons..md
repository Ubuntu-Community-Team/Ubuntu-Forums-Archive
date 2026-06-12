---
title: "Unity with &quot;teared&quot; icons."
date: 2015-12-21
forum: Desktop Environments
---

### Post by rrob on 2015-12-21
Hi, 
pls, can someone help me?

After installing Ubuntu 14.04.3 LTS x86_64 on pc it looks like this:

[IMG]https://photos-2.dropbox.com/t/2/AACRxdmY-e30gVKIT4fe4u2ys0gqe2m_ywqWO4Jvdzv8mw/12/1283494/jpeg/32x32/3/1450731600/0/2/death-unity02.jpg/EOPriwEY8oaUSCABKAE/vpZX2fKsSg2ivLPvMQuMWIHMSC5OwXhp3037BxmKKA8?size_mode=5&size=32x32[/IMG]

[IMG]https://photos-3.dropbox.com/t/2/AACRFVhMICbWAOARMTuXE-0IeadZMTJbt82Vsd1rUzwHpg/12/1283494/jpeg/32x32/3/1450731600/0/2/death-unity03.jpg/EOPriwEY8oaUSCABKAE/rSsFF2UvDBYuc0MF-PVJD6vcPH8RIjTtX0b7jFi-2s4?size_mode=5&size=32x32[/IMG]

dmesg - [http://pastebin.com/fFYunB56](http://pastebin.com/fFYunB56)
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-42-generic (buildd@lgw01-24) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 (Ubuntu 3.19.0-42.48~14.04.1-generic 3.19.8-ckt10)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-42-generic root=UUID=12a413f4-4d91-4fdd-badf-6e6cd28b454f ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] tseg: 0000000000
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003df9ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000003dfa0000-0x000000003dfadfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000003dfae000-0x000000003dfcffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003dfd0000-0x000000003dfddfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000003dfe0000-0x000000003dffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M2A-MX, BIOS 0403    11/26/2007
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x3dfa0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 base 0020000000 mask FFF0000000 write-back
[    0.000000]   2 base 0030000000 mask FFF8000000 write-back
[    0.000000]   3 base 0038000000 mask FFFC000000 write-back
[    0.000000]   4 base 003C000000 mask FFFE000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x3dc00000-0x3ddfffff]
[    0.000000]  [mem 0x3dc00000-0x3ddfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20000000-0x3dbfffff]
[    0.000000]  [mem 0x20000000-0x3dbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x3de00000-0x3df9ffff]
[    0.000000]  [mem 0x3de00000-0x3df9ffff] page 4k
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35a2a000-0x36d0cfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000FB330 000024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 0x000000003DFA0100 000054 (v01 A_M_I_ OEMXSDT  11000726 MSFT 00000097)
[    0.000000] ACPI: FACP 0x000000003DFA0290 0000F4 (v03 A_M_I_ OEMFACP  11000726 MSFT 00000097)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 64/32 (20141107/tbfadt-623)
[    0.000000] ACPI: DSDT 0x000000003DFA05C0 006CD2 (v01 A0877  A0877000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 0x000000003DFAE000 000040
[    0.000000] ACPI: FACS 0x000000003DFAE000 000040
[    0.000000] ACPI: APIC 0x000000003DFA0390 00006C (v01 A_M_I_ OEMAPIC  11000726 MSFT 00000097)
[    0.000000] ACPI: MCFG 0x000000003DFA0400 00003C (v01 A_M_I_ OEMMCFG  11000726 MSFT 00000097)
[    0.000000] ACPI: OEMB 0x000000003DFAE040 000080 (v01 A_M_I_ AMI_OEM  11000726 MSFT 00000097)
[    0.000000] ACPI: HPET 0x000000003DFA72A0 000038 (v01 A_M_I_ OEMHPET  11000726 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x000000003DFA72E0 000248 (v01 A_M_I_ POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000003df9ffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x3df9b000-0x3df9ffff]
[    0.000000]  [ffffea0000000000-ffffea0000ffffff] PMD -> [ffff88003c600000-ffff88003d5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0x3df9ffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x3df9ffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x3df9ffff]
[    0.000000] On node 0 totalpages: 253758
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3903 pages used for memmap
[    0.000000]   DMA32 zone: 249760 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
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
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] e820: [mem 0x3e000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88003dc00000 s86144 r8192 d32640 u524288
[    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 249770
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-42-generic root=UUID=12a413f4-4d91-4fdd-badf-6e6cd28b454f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] AGP: Node 0: aperture [bus addr 0x4800000000-0x4801ffffff] (32MB)
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 962224K/1015032K available (7922K kernel code, 1174K rwdata, 3756K rodata, 1408K init, 1292K bss, 52808K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration failed
[    0.000000] tsc: Unable to calibrate against PIT
[    0.000000] tsc: using HPET reference calibration
[    0.000000] tsc: Detected 2293.933 MHz processor
[    0.000000] tsc: Marking TSC unstable due to TSCs unsynchronized
[    0.016019] Calibrating delay loop (skipped), value calculated using timer frequency.. 4587.86 BogoMIPS (lpj=9175732)
[    0.016023] pid_max: default: 32768 minimum: 301
[    0.016033] ACPI: Core revision 20141107
[    0.024761] ACPI: All ACPI Tables successfully acquired
[    0.024801] Security Framework initialized
[    0.024834] AppArmor: AppArmor initialized
[    0.024835] Yama: becoming mindful.
[    0.024996] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.026007] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.026506] Mount-cache hash table entries: 2048 (order: 2, 16384 bytes)
[    0.026511] Mountpoint-cache hash table entries: 2048 (order: 2, 16384 bytes)
[    0.026941] Initializing cgroup subsys memory
[    0.026957] Initializing cgroup subsys devices
[    0.026963] Initializing cgroup subsys freezer
[    0.026968] Initializing cgroup subsys net_cls
[    0.026972] Initializing cgroup subsys blkio
[    0.026978] Initializing cgroup subsys perf_event
[    0.026983] Initializing cgroup subsys net_prio
[    0.026988] Initializing cgroup subsys hugetlb
[    0.027022] CPU: Physical Processor ID: 0
[    0.027023] CPU: Processor Core ID: 0
[    0.027026] mce: CPU supports 5 MCE banks
[    0.027035] LVT offset 0 assigned for vector 0xf9
[    0.027042] process: using AMD E400 aware idle routine
[    0.027046] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.027046] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4, 1GB 0
[    0.027194] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
[    0.029196] ftrace: allocating 30027 entries in 118 pages
[    0.040584] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081015] smpboot: CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (fam: 0f, model: 6b, stepping: 02)
[    0.084000] Performance Events: AMD PMU driver.
[    0.084000] ... version:                0
[    0.084000] ... bit width:              48
[    0.084000] ... generic registers:      4
[    0.084000] ... value mask:             0000ffffffffffff
[    0.084000] ... max period:             00007fffffffffff
[    0.084000] ... fixed-purpose events:   0
[    0.084000] ... event mask:             000000000000000f
[    0.084000] x86: Booting SMP configuration:
[    0.084000] .... node  #0, CPUs:      #1
[    0.092411] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.172112] x86: Booted up 1 node, 2 CPUs
[    0.172115] smpboot: Total of 2 processors activated (9176.35 BogoMIPS)
[    0.172786] devtmpfs: initialized
[    0.177564] evm: security.selinux
[    0.177566] evm: security.SMACK64
[    0.177567] evm: security.SMACK64EXEC
[    0.177568] evm: security.SMACK64TRANSMUTE
[    0.177570] evm: security.SMACK64MMAP
[    0.177571] evm: security.ima
[    0.177572] evm: security.capability
[    0.177632] PM: Registering ACPI NVS region [mem 0x3dfae000-0x3dfcffff] (139264 bytes)
[    0.177632] pinctrl core: initialized pinctrl subsystem
[    0.177632] RTC time: 13:35:42, date: 12/21/15
[    0.177632] NET: Registered protocol family 16
[    0.184009] cpuidle: using governor ladder
[    0.188016] cpuidle: using governor menu
[    0.188024] node 0 link 0: io port [1000, ffffff]
[    0.188028] TOM: 0000000040000000 aka 1024M
[    0.188031] node 0 link 0: mmio [fc000000, fdfeffff]
[    0.188035] node 0 link 0: mmio [e0000000, efffffff]
[    0.188038] node 0 link 0: mmio [40000000, dfffffff]
[    0.188040] node 0 link 0: mmio [a0000, bffff]
[    0.188043] node 0 link 0: mmio [fdff0000, ffffffff]
[    0.188046] bus: [bus 00-07] on node 0 link 0
[    0.188048] bus: 00 [io  0x0000-0xffff]
[    0.188050] bus: 00 [mem 0xf0000000-0xfcffffffff]
[    0.188051] bus: 00 [mem 0x40000000-0xefffffff]
[    0.188053] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.188147] ACPI: bus type PCI registered
[    0.188151] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.188275] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.188278] PCI: not using MMCONFIG
[    0.188280] PCI: Using configuration type 1 for base access
[    0.188432] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.188434] mtrr: probably your BIOS does not setup all CPUs.
[    0.188436] mtrr: corrected configuration.
[    0.192181] ACPI: Added _OSI(Module Device)
[    0.192185] ACPI: Added _OSI(Processor Device)
[    0.192187] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.192189] ACPI: Added _OSI(Processor Aggregator Device)
[    0.194873] ACPI: Executed 3 blocks of module-level executable AML code
[    0.199881] ACPI: Interpreter enabled
[    0.199897] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.199917] ACPI: (supports S0 S1 S3 S4 S5)
[    0.199919] ACPI: Using IOAPIC for interrupt routing
[    0.199951] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.202103] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.202873] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.212594] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.212605] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.212615] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.213044] PCI host bridge to bus 0000:00
[    0.213048] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.213051] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.213054] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.213056] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.213059] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.213061] pci_bus 0000:00: root bus resource [mem 0x3e000000-0xffffffff]
[    0.213071] pci 0000:00:00.0: [1002:7910] type 00 class 0x060000
[    0.213206] pci 0000:00:01.0: [1002:7912] type 01 class 0x060400
[    0.213340] pci 0000:00:06.0: [1002:7916] type 01 class 0x060400
[    0.213385] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.213444] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.213503] pci 0000:00:07.0: [1002:7917] type 01 class 0x060400
[    0.213549] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.213604] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.213684] pci 0000:00:12.0: [1002:4380] type 00 class 0x01018f
[    0.213709] pci 0000:00:12.0: reg 0x10: [io  0xd000-0xd007]
[    0.213720] pci 0000:00:12.0: reg 0x14: [io  0xc000-0xc003]
[    0.213732] pci 0000:00:12.0: reg 0x18: [io  0xb000-0xb007]
[    0.213743] pci 0000:00:12.0: reg 0x1c: [io  0xa000-0xa003]
[    0.213755] pci 0000:00:12.0: reg 0x20: [io  0x9000-0x900f]
[    0.213767] pci 0000:00:12.0: reg 0x24: [mem 0xfe8ff800-0xfe8ffbff]
[    0.213794] pci 0000:00:12.0: set SATA to AHCI mode
[    0.213932] pci 0000:00:13.0: [1002:4387] type 00 class 0x0c0310
[    0.213948] pci 0000:00:13.0: reg 0x10: [mem 0xfe8fe000-0xfe8fefff]
[    0.214066] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.214125] pci 0000:00:13.1: [1002:4388] type 00 class 0x0c0310
[    0.214141] pci 0000:00:13.1: reg 0x10: [mem 0xfe8fd000-0xfe8fdfff]
[    0.214263] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.214320] pci 0000:00:13.2: [1002:4389] type 00 class 0x0c0310
[    0.214337] pci 0000:00:13.2: reg 0x10: [mem 0xfe8fc000-0xfe8fcfff]
[    0.214457] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.214518] pci 0000:00:13.3: [1002:438a] type 00 class 0x0c0310
[    0.214534] pci 0000:00:13.3: reg 0x10: [mem 0xfe8fb000-0xfe8fbfff]
[    0.214650] pci 0000:00:13.3: System wakeup disabled by ACPI
[    0.214708] pci 0000:00:13.4: [1002:438b] type 00 class 0x0c0310
[    0.214724] pci 0000:00:13.4: reg 0x10: [mem 0xfe8fa000-0xfe8fafff]
[    0.214842] pci 0000:00:13.4: System wakeup disabled by ACPI
[    0.214907] pci 0000:00:13.5: [1002:4386] type 00 class 0x0c0320
[    0.214930] pci 0000:00:13.5: reg 0x10: [mem 0xfe8ff000-0xfe8ff0ff]
[    0.215029] pci 0000:00:13.5: supports D1 D2
[    0.215032] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.215090] pci 0000:00:13.5: System wakeup disabled by ACPI
[    0.215242] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.215599] pci 0000:00:14.0: reg 0x10: [io  0x0b00-0x0b0f]
[    0.218095] pci 0000:00:14.1: [1002:438c] type 00 class 0x01018a
[    0.218115] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.218126] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.218138] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.218149] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.218161] pci 0000:00:14.1: reg 0x20: [io  0xff00-0xff0f]
[    0.218184] pci 0000:00:14.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.218187] pci 0000:00:14.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.218189] pci 0000:00:14.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.218192] pci 0000:00:14.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.218324] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.218352] pci 0000:00:14.2: reg 0x10: [mem 0xfe8f4000-0xfe8f7fff 64bit]
[    0.218445] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.218504] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.218560] pci 0000:00:14.3: [1002:438d] type 00 class 0x060100
[    0.218730] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.218821] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.218890] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.218996] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.219095] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.219195] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.219355] pci 0000:01:05.0: [1002:791e] type 00 class 0x030000
[    0.219369] pci 0000:01:05.0: reg 0x10: [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.219377] pci 0000:01:05.0: reg 0x18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.219382] pci 0000:01:05.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.219388] pci 0000:01:05.0: reg 0x24: [mem 0xfe900000-0xfe9fffff]
[    0.219414] pci 0000:01:05.0: supports D1 D2
[    0.219473] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.219478] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.219481] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.219486] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.219539] pci 0000:00:06.0: PCI bridge to [bus 02]
[    0.219622] pci 0000:03:00.0: [1969:1048] type 00 class 0x020000
[    0.219646] pci 0000:03:00.0: reg 0x10: [mem 0xfebc0000-0xfebfffff 64bit]
[    0.219696] pci 0000:03:00.0: reg 0x30: [mem 0xfeba0000-0xfebbffff pref]
[    0.219756] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.219786] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.219839] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.219849] pci 0000:00:07.0: PCI bridge to [bus 03]
[    0.219854] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.219948] pci 0000:00:14.4: PCI bridge to [bus 04] (subtractive decode)
[    0.219959] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.219962] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.219964] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.219967] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.219970] pci 0000:00:14.4:   bridge window [mem 0x3e000000-0xffffffff] (subtractive decode)
[    0.220022] pci_bus 0000:00: on NUMA node 0
[    0.221649] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.221720] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.221787] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.221854] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.221929] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.221998] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.222063] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.222130] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.222203] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.222402] vgaarb: setting as boot device: PCI:0000:01:05.0
[    0.222402] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.222402] vgaarb: loaded
[    0.222402] vgaarb: bridge control possible 0000:01:05.0
[    0.222402] SCSI subsystem initialized
[    0.222402] libata version 3.00 loaded.
[    0.222402] ACPI: bus type USB registered
[    0.222402] usbcore: registered new interface driver usbfs
[    0.222402] usbcore: registered new interface driver hub
[    0.222402] usbcore: registered new device driver usb
[    0.222402] PCI: Using ACPI for IRQ routing
[    0.233390] PCI: pci_cache_line_size set to 64 bytes
[    0.233946] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.233950] e820: reserve RAM buffer [mem 0x3dfa0000-0x3fffffff]
[    0.234165] NetLabel: Initializing
[    0.234167] NetLabel:  domain hash size = 128
[    0.234168] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.234191] NetLabel:  unlabeled traffic allowed by default
[    0.234232] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.234232] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.236076] Switched to clocksource hpet
[    0.248580] AppArmor: AppArmor Filesystem Enabled
[    0.248726] pnp: PnP ACPI init
[    0.248993] system 00:00: [mem 0x3e000000-0x3fffffff] has been reserved
[    0.249000] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.249096] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.249357] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.249360] system 00:02: [io  0x040b] has been reserved
[    0.249364] system 00:02: [io  0x04d6] has been reserved
[    0.249367] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.249369] system 00:02: [io  0x0c14] has been reserved
[    0.249373] system 00:02: [io  0x0c50-0x0c51] has been reserved
[    0.249375] system 00:02: [io  0x0c52] has been reserved
[    0.249378] system 00:02: [io  0x0c6c] has been reserved
[    0.249382] system 00:02: [io  0x0c6f] has been reserved
[    0.249385] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.249388] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.249391] system 00:02: [io  0x0cd4-0x0cd5] has been reserved
[    0.249394] system 00:02: [io  0x0cd6-0x0cd7] has been reserved
[    0.249397] system 00:02: [io  0x0cd8-0x0cdf] has been reserved
[    0.249400] system 00:02: [io  0x0800-0x089f] could not be reserved
[    0.249403] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    0.249406] system 00:02: [io  0x0900-0x090f] has been reserved
[    0.249409] system 00:02: [io  0x0910-0x091f] has been reserved
[    0.249412] system 00:02: [io  0xfe00-0xfefe] has been reserved
[    0.249415] system 00:02: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.249418] system 00:02: [mem 0xfff00000-0xffffffff] has been reserved
[    0.249422] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.249550] system 00:03: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.249554] system 00:03: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.249557] system 00:03: [mem 0xfef00000-0xfef0001f] has been reserved
[    0.249560] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.249629] pnp 00:04: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.249707] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.250379] pnp 00:06: [dma 2]
[    0.250440] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.250978] system 00:07: [io  0x0230-0x023f] has been reserved
[    0.250981] system 00:07: [io  0x0290-0x029f] has been reserved
[    0.250984] system 00:07: [io  0x0a20-0x0a2f] has been reserved
[    0.250987] system 00:07: [io  0x0a30-0x0a3f] has been reserved
[    0.250990] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.251548] pnp 00:08: [dma 0 disabled]
[    0.251638] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.251727] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.251731] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.252028] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.252031] system 00:0a: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.252034] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.252038] system 00:0a: [mem 0x00100000-0x3dffffff] could not be reserved
[    0.252041] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.252163] pnp: PnP ACPI: found 11 devices
[    0.260240] pci 0000:00:06.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.260246] pci 0000:00:06.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.260249] pci 0000:00:06.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.260267] pci 0000:00:06.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.260269] pci 0000:00:06.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.260272] pci 0000:00:06.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.260281] pci 0000:00:06.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.260288] pci 0000:00:06.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.260293] pci 0000:00:06.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.260297] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.260300] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.260304] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.260307] pci 0000:00:01.0:   bridge window [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.260311] pci 0000:00:06.0: PCI bridge to [bus 02]
[    0.260314] pci 0000:00:06.0:   bridge window [io  0x1000-0x1fff]
[    0.260318] pci 0000:00:06.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.260321] pci 0000:00:06.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.260325] pci 0000:00:07.0: PCI bridge to [bus 03]
[    0.260329] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.260335] pci 0000:00:14.4: PCI bridge to [bus 04]
[    0.260350] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.260352] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.260355] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.260357] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.260360] pci_bus 0000:00: resource 8 [mem 0x3e000000-0xffffffff]
[    0.260363] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.260365] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
[    0.260368] pci_bus 0000:01: resource 2 [mem 0xfc000000-0xfdffffff 64bit pref]
[    0.260371] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.260373] pci_bus 0000:02: resource 1 [mem 0x40000000-0x401fffff]
[    0.260376] pci_bus 0000:02: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.260379] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.260382] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.260384] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.260386] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.260389] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.260391] pci_bus 0000:04: resource 8 [mem 0x3e000000-0xffffffff]
[    0.260445] NET: Registered protocol family 2
[    0.260750] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.260830] TCP bind hash table entries: 8192 (order: 5, 131072 bytes)
[    0.260920] TCP: Hash tables configured (established 8192 bind 8192)
[    0.261023] TCP: reno registered
[    0.261030] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.261046] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.261155] NET: Registered protocol family 1
[    0.672323] pci 0000:01:05.0: Video device with shadowed ROM
[    0.672330] PCI: CLS 64 bytes, default 64
[    0.672452] Trying to unpack rootfs image as initramfs...
[    1.109156] Freeing initrd memory: 19340K (ffff880035a2a000 - ffff880036d0d000)
[    1.109971] microcode: AMD CPU family 0xf not supported
[    1.110038] Scanning for low memory corruption every 60 seconds
[    1.110542] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    1.110603] Initialise system trusted keyring
[    1.110642] audit: initializing netlink subsys (disabled)
[    1.110684] audit: type=2000 audit(1450704943.108:1): initialized
[    1.111132] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.113749] zpool: loaded
[    1.113752] zbud: loaded
[    1.114039] VFS: Disk quotas dquot_6.5.2
[    1.114110] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.115032] fuse init (API version 7.23)
[    1.115321] Key type big_key registered
[    1.116145] Key type asymmetric registered
[    1.116150] Asymmetric key parser 'x509' registered
[    1.116215] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.116292] io scheduler noop registered
[    1.116297] io scheduler deadline registered (default)
[    1.116358] io scheduler cfq registered
[    1.116531] pcieport 0000:00:06.0: enabling device (0104 -> 0107)
[    1.116725] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.116752] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.116810] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    1.116811] vesafb: scrolling: redraw
[    1.116814] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.117330] vesafb: framebuffer at 0xfc000000, mapped to 0xffffc90010280000, using 5824k, total 5824k
[    1.117592] Console: switching to colour frame buffer device 175x65
[    1.117630] fb0: VESA VGA frame buffer device
[    1.117792] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.117799] ACPI: Power Button [PWRB]
[    1.117863] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.117865] ACPI: Power Button [PWRF]
[    1.117913] ACPI: duty_cycle spans bit 4
[    1.118679] GHES: HEST is not enabled!
[    1.118845] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.139442] 00:08: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.142089] Linux agpgart interface v0.103
[    1.144260] brd: module loaded
[    1.145344] loop: module loaded
[    1.145742] libphy: Fixed MDIO Bus: probed
[    1.145746] tun: Universal TUN/TAP device driver, 1.6
[    1.145748] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.145821] PPP generic driver version 2.4.2
[    1.145943] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.145952] ehci-pci: EHCI PCI platform driver
[    1.146210] ehci-pci 0000:00:13.5: EHCI Host Controller
[    1.146224] ehci-pci 0000:00:13.5: new USB bus registered, assigned bus number 1
[    1.146233] ehci-pci 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    1.146250] ehci-pci 0000:00:13.5: debug port 1
[    1.146311] ehci-pci 0000:00:13.5: irq 19, io mem 0xfe8ff000
[    1.156038] ehci-pci 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    1.156114] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.156117] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.156120] usb usb1: Product: EHCI Host Controller
[    1.156122] usb usb1: Manufacturer: Linux 3.19.0-42-generic ehci_hcd
[    1.156124] usb usb1: SerialNumber: 0000:00:13.5
[    1.156314] hub 1-0:1.0: USB hub found
[    1.156328] hub 1-0:1.0: 10 ports detected
[    1.156652] ehci-platform: EHCI generic platform driver
[    1.156672] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.156680] ohci-pci: OHCI PCI platform driver
[    1.156849] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.156857] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 2
[    1.156893] ohci-pci 0000:00:13.0: irq 16, io mem 0xfe8fe000
[    1.216069] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.216072] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.216075] usb usb2: Product: OHCI PCI host controller
[    1.216077] usb usb2: Manufacturer: Linux 3.19.0-42-generic ohci_hcd
[    1.216079] usb usb2: SerialNumber: 0000:00:13.0
[    1.216238] hub 2-0:1.0: USB hub found
[    1.216250] hub 2-0:1.0: 2 ports detected
[    1.216507] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.216517] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.216552] ohci-pci 0000:00:13.1: irq 17, io mem 0xfe8fd000
[    1.276065] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.276068] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.276070] usb usb3: Product: OHCI PCI host controller
[    1.276072] usb usb3: Manufacturer: Linux 3.19.0-42-generic ohci_hcd
[    1.276074] usb usb3: SerialNumber: 0000:00:13.1
[    1.276231] hub 3-0:1.0: USB hub found
[    1.276242] hub 3-0:1.0: 2 ports detected
[    1.276490] ohci-pci 0000:00:13.2: OHCI PCI host controller
[    1.276498] ohci-pci 0000:00:13.2: new USB bus registered, assigned bus number 4
[    1.276534] ohci-pci 0000:00:13.2: irq 18, io mem 0xfe8fc000
[    1.336063] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.336066] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.336068] usb usb4: Product: OHCI PCI host controller
[    1.336070] usb usb4: Manufacturer: Linux 3.19.0-42-generic ohci_hcd
[    1.336072] usb usb4: SerialNumber: 0000:00:13.2
[    1.336273] hub 4-0:1.0: USB hub found
[    1.336289] hub 4-0:1.0: 2 ports detected
[    1.336659] ohci-pci 0000:00:13.3: OHCI PCI host controller
[    1.336669] ohci-pci 0000:00:13.3: new USB bus registered, assigned bus number 5
[    1.336706] ohci-pci 0000:00:13.3: irq 17, io mem 0xfe8fb000
[    1.396097] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.396101] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.396103] usb usb5: Product: OHCI PCI host controller
[    1.396105] usb usb5: Manufacturer: Linux 3.19.0-42-generic ohci_hcd
[    1.396107] usb usb5: SerialNumber: 0000:00:13.3
[    1.396296] hub 5-0:1.0: USB hub found
[    1.396307] hub 5-0:1.0: 2 ports detected
[    1.396565] ohci-pci 0000:00:13.4: OHCI PCI host controller
[    1.396572] ohci-pci 0000:00:13.4: new USB bus registered, assigned bus number 6
[    1.396601] ohci-pci 0000:00:13.4: irq 18, io mem 0xfe8fa000
[    1.456077] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.456080] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.456082] usb usb6: Product: OHCI PCI host controller
[    1.456085] usb usb6: Manufacturer: Linux 3.19.0-42-generic ohci_hcd
[    1.456087] usb usb6: SerialNumber: 0000:00:13.4
[    1.456256] hub 6-0:1.0: USB hub found
[    1.456268] hub 6-0:1.0: 2 ports detected
[    1.456422] ohci-platform: OHCI generic platform driver
[    1.456445] uhci_hcd: USB Universal Host Controller Interface driver
[    1.456559] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.456994] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.457001] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.457232] mousedev: PS/2 mouse device common for all mice
[    1.457467] rtc_cmos 00:01: RTC can wake from S4
[    1.457636] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.457667] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.457684] i2c /dev entries driver
[    1.457820] device-mapper: uevent: version 1.0.3
[    1.457941] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    1.457971] ledtrig-cpu: registered to indicate activity on CPUs
[    1.458211] PCCT header not found.
[    1.458214] ACPI PCC probe failed.
[    1.458363] TCP: cubic registered
[    1.458557] NET: Registered protocol family 10
[    1.458904] NET: Registered protocol family 17
[    1.458923] Key type dns_resolver registered
[    1.459456] Loading compiled-in X.509 certificates
[    1.460699] Loaded X.509 cert 'Magrathea: Glacier signing key: 759bcd6455a9dfaba6111485d04eded53ab83150'
[    1.460730] registered taskstats version 1
[    1.464317] Key type trusted registered
[    1.468043] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.470986] Key type encrypted registered
[    1.471004] AppArmor: AppArmor sha1 policy hashing enabled
[    1.471010] ima: No TPM chip found, activating TPM-bypass!
[    1.471057] evm: HMAC attrs: 0x1
[    1.471568]   Magic number: 11:24:585
[    1.471728] rtc_cmos 00:01: setting system clock to 2015-12-21 13:35:44 UTC (1450704944)
[    1.471968] powernow_k8: fid 0xf (2300 MHz), vid 0xa
[    1.471970] powernow_k8: fid 0xe (2200 MHz), vid 0xb
[    1.471972] powernow_k8: fid 0xc (2000 MHz), vid 0xd
[    1.471974] powernow_k8: fid 0xa (1800 MHz), vid 0xf
[    1.471975] powernow_k8: fid 0x2 (1000 MHz), vid 0x12
[    1.472326] powernow_k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (2 cpu cores) (version 2.20.00)
[    1.472340] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.472341] EDD information not available.
[    1.472431] PM: Hibernation image not present or could not be loaded.
[    1.473761] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    1.473769] Write protecting the kernel read-only data: 12288k
[    1.474225] Freeing unused kernel memory: 256K (ffff8800017c0000 - ffff880001800000)
[    1.474599] Freeing unused kernel memory: 340K (ffff880001bab000 - ffff880001c00000)
[    1.498106] systemd-udevd[102]: starting version 204
[    1.536693] ahci 0000:00:12.0: version 3.0
[    1.536925] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.537045] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.537049] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio ccc
[    1.538227] scsi host0: ahci
[    1.538454] scsi host1: ahci
[    1.539254] scsi host2: ahci
[    1.539768] scsi host3: ahci
[    1.539847] ata1: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff900 irq 22
[    1.539851] ata2: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff980 irq 22
[    1.539855] ata3: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa00 irq 22
[    1.539859] ata4: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa80 irq 22
[    1.554645] atl1 0000:03:00.0: version 2.1.3
[    1.564033] FDC 0 is a post-1991 82077
[    1.564542] scsi host4: pata_atiixp
[    1.565553] scsi host5: pata_atiixp
[    1.565633] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.565636] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.613785] usb 1-1: New USB device found, idVendor=13fe, idProduct=5100
[    1.613792] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.613795] usb 1-1: Product: Patriot Memory
[    1.613797] usb 1-1: Manufacturer:
[    1.613799] usb 1-1: SerialNumber: 07012A335A654F04
[    1.786449] ata5.00: ATA-7: ST3250820A, 3.AAE, max UDMA/100
[    1.786457] ata5.00: 488397168 sectors, multi 16: LBA48
[    1.786465] ata5.01: ATAPI: TSSTcorp CDDVDW SH-S202H, SB00, max UDMA/66
[    1.786470] ata5.00: limited to UDMA/33 due to 40-wire cable
[    1.786473] ata5.01: limited to UDMA/33 due to 40-wire cable
[    1.853023] ata5.00: configured for UDMA/33
[    1.856039] ata1: SATA link down (SStatus 0 SControl 300)
[    1.856073] ata2: SATA link down (SStatus 0 SControl 300)
[    1.860037] ata4: SATA link down (SStatus 0 SControl 300)
[    1.860066] ata3: SATA link down (SStatus 0 SControl 300)
[    1.868411] ata5.01: configured for UDMA/33
[    1.868914] scsi 4:0:0:0: Direct-Access     ATA      ST3250820A       E    PQ: 0 ANSI: 5
[    1.869358] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    1.869863] sd 4:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.869923] sd 4:0:0:0: [sda] Write Protect is off
[    1.869927] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.869953] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.901481] scsi 4:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-S202H  SB00 PQ: 0 ANSI: 5
[    1.923969]  sda: sda1 sda2 < sda5 >
[    1.932488] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.942022] sr 4:0:1:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.942025] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.942226] sr 4:0:1:0: Attached scsi CD-ROM sr0
[    1.942524] sr 4:0:1:0: Attached scsi generic sg1 type 5
[    1.984034] usb 3-2: new full-speed USB device number 2 using ohci-pci
[    2.006060] usb-storage 1-1:1.0: USB Mass Storage device detected
[    2.006701] scsi host6: usb-storage 1-1:1.0
[    2.006839] usbcore: registered new interface driver usb-storage
[    2.009400] usbcore: registered new interface driver uas
[    2.157071] usb 3-2: New USB device found, idVendor=046d, idProduct=c52b
[    2.157078] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.157081] usb 3-2: Product: USB Receiver
[    2.157083] usb 3-2: Manufacturer: Logitech
[    2.165802] hidraw: raw HID events driver (C) Jiri Kosina
[    2.181238] usbcore: registered new interface driver usbhid
[    2.181244] usbhid: USB HID core driver
[    2.191454] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.1-2/input2
[    2.297558] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.944114] random: init urandom read with 78 bits of entropy available
[    3.065260] scsi 6:0:0:0: Direct-Access              Patriot Memory   PMAP PQ: 0 ANSI: 4
[    3.065612] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.735829] sd 6:0:0:0: [sdb] 15466496 512-byte logical blocks: (7.91 GB/7.37 GiB)
[    3.738318] sd 6:0:0:0: [sdb] Write Protect is off
[    3.738322] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    3.740817] sd 6:0:0:0: [sdb] No Caching mode page found
[    3.740821] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.775732] random: nonblocking pool is initialized
[    3.775760]  sdb: sdb1
[    3.782324] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    3.792191] init: plymouth-upstart-bridge main process (178) terminated with status 1
[    3.792216] init: plymouth-upstart-bridge main process ended, respawning
[    3.796886] init: plymouth-upstart-bridge main process (191) terminated with status 1
[    3.796906] init: plymouth-upstart-bridge main process ended, respawning
[    3.801343] init: plymouth-upstart-bridge main process (193) terminated with status 1
[    3.801362] init: plymouth-upstart-bridge main process ended, respawning
[    3.806016] init: plymouth-upstart-bridge main process (194) terminated with status 1
[    3.806037] init: plymouth-upstart-bridge main process ended, respawning
[    3.810925] init: plymouth-upstart-bridge main process (196) terminated with status 1
[    3.810944] init: plymouth-upstart-bridge main process ended, respawning
[    3.819804] init: plymouth-upstart-bridge main process (197) terminated with status 1
[    3.819827] init: plymouth-upstart-bridge main process ended, respawning
[    4.968485] Adding 1013756k swap on /dev/sda5.  Priority:-1 extents:1 across:1013756k FS
[    6.337761] systemd-udevd[300]: starting version 204
[    7.666715] lp: driver loaded but no devices found
[    7.790615] ppdev: user-space parallel port driver
[    8.897418] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.207049] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.240823] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   10.241056] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb10
[   10.569393] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.630624] MCE: In-kernel MCE decoding enabled.
[   10.749603] atl1 0000:03:00.0 eth1: renamed from eth0
[   10.760237] systemd-udevd[362]: renamed network interface eth0 to eth1
[   10.803484] EDAC MC: Ver: 3.0.0
[   10.839633] AMD64 EDAC driver v3.4.0
[   10.839703] EDAC amd64: DRAM ECC disabled.
[   10.839710] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.839710]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.839710]  (Note that use of the override may cause unknown side effects.)
[   11.289369] kvm: Nested Virtualization enabled
[   11.320148] [drm] Initialized drm 1.1.0 20060810
[   12.331815] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   12.331823] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.331827] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.331829] sound hdaudioC0D0:    mono: mono_out=0x0
[   12.331831] sound hdaudioC0D0:    dig-out=0x1e/0x0
[   12.331833] sound hdaudioC0D0:    inputs:
[   12.331837] sound hdaudioC0D0:      Front Mic=0x19
[   12.331839] sound hdaudioC0D0:      Rear Mic=0x18
[   12.331842] sound hdaudioC0D0:      Line=0x1a
[   12.343648] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   12.343765] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   12.343868] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   12.343988] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   12.344178] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   12.440414] [drm] radeon kernel modesetting enabled.
[   12.691364] input: Logitech K400 as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.2/0003:046D:C52B.0003/0003:046D:400E.0004/input/input10
[   12.691708] logitech-hidpp-device 0003:046D:400E.0004: input,hidraw1: USB HID v1.11 Keyboard [Logitech K400] on usb-0000:00:13.1-2:1
[   12.697293] input: Logitech K520 as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.2/0003:046D:C52B.0003/0003:046D:2011.0005/input/input11
[   12.697503] logitech-hidpp-device 0003:046D:2011.0005: input,hidraw2: USB HID v1.11 Keyboard [Logitech K520] on usb-0000:00:13.1-2:2
[   12.787956] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   12.787963] AMD IOMMUv2 functionality not available on this system
[   13.009044] CRAT table not found
[   13.009051] Finished initializing topology ret=0
[   13.009157] kfd kfd: Initialized module
[   13.009687] checking generic (fc000000 5b0000) vs hw (fc000000 2000000)
[   13.009690] fb: switching to radeondrmfb from VESA VGA
[   13.009806] Console: switching to colour dummy device 80x25
[   13.011367] [drm] initializing kernel modesetting (RS690 0x1002:0x791E 0x1043:0x82C8).
[   13.011396] [drm] register mmio base: 0xFEAF0000
[   13.011398] [drm] register mmio size: 65536
[   13.012265] ATOM BIOS: ATI
[   13.012303] radeon 0000:01:05.0: VRAM: 32M 0x000000003E000000 - 0x000000003FFFFFFF (32M used)
[   13.012306] radeon 0000:01:05.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   13.012344] [drm] Detected VRAM RAM=32M, BAR=32M
[   13.012346] [drm] RAM width 128bits DDR
[   13.012958] [TTM] Zone  kernel: Available graphics memory: 491800 kiB
[   13.012963] [TTM] Initializing pool allocator
[   13.012973] [TTM] Initializing DMA pool allocator
[   13.013017] [drm] radeon: 32M of VRAM memory ready
[   13.013019] [drm] radeon: 512M of GTT memory ready.
[   13.013061] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.051847] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   13.051854] [drm] PCIE GART of 512M enabled (table at 0x000000003AB00000).
[   13.051889] radeon 0000:01:05.0: WB enabled
[   13.051894] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x0000000040000000 and cpu addr 0xffff88003a903000
[   13.051897] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   13.051898] [drm] Driver supports precise vblank timestamp query.
[   13.051901] radeon 0000:01:05.0: radeon: MSI limited to 32-bit
[   13.051941] radeon 0000:01:05.0: radeon: using MSI.
[   13.051965] [drm] radeon: irq initialized.
[   13.051981] [drm] Loading RS690/RS740 Microcode
[   13.641745] [drm] radeon: ring at 0x0000000040001000
[   13.641772] [drm] ring test succeeded in 1 usecs
[   13.641926] [drm] ib test succeeded in 0 usecs
[   13.643169] [drm] Radeon Display Connectors
[   13.643174] [drm] Connector 0:
[   13.643175] [drm]   VGA-1
[   13.643177] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[   13.643179] [drm]   Encoders:
[   13.643180] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.643182] [drm] Connector 1:
[   13.643183] [drm]   HDMI-A-1
[   13.643185] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   13.643186] [drm]   Encoders:
[   13.643187] [drm]     DFP3: INTERNAL_LVTM1
[   13.690128] [drm] fb mappable at 0xFC040000
[   13.690130] [drm] vram apper at 0xFC000000
[   13.690131] [drm] size 1884160
[   13.690132] [drm] fb depth is 8
[   13.690133] [drm]    pitch is 1792
[   13.690288] fbcon: radeondrmfb (fb0) is primary device
[   13.690479] Console: switching to colour frame buffer device 210x65
[   13.690528] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[   13.690530] radeon 0000:01:05.0: registered panic notifier
[   13.700059] [drm] Initialized radeon 2.40.0 20080528 for 0000:01:05.0 on minor 0
[   14.403897] audit: type=1400 audit(1450704957.430:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=454 comm="apparmor_parser"
[   14.403911] audit: type=1400 audit(1450704957.430:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=454 comm="apparmor_parser"
[   14.403917] audit: type=1400 audit(1450704957.430:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=454 comm="apparmor_parser"
[   14.404066] audit: type=1400 audit(1450704957.430:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=455 comm="apparmor_parser"
[   14.404083] audit: type=1400 audit(1450704957.430:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=455 comm="apparmor_parser"
[   14.404089] audit: type=1400 audit(1450704957.430:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
[   14.404589] audit: type=1400 audit(1450704957.430:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=454 comm="apparmor_parser"
[   14.404600] audit: type=1400 audit(1450704957.430:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=454 comm="apparmor_parser"
[   14.404712] audit: type=1400 audit(1450704957.430:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=455 comm="apparmor_parser"
[   14.404720] audit: type=1400 audit(1450704957.430:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=455 comm="apparmor_parser"
[   15.585415] init: failsafe main process (516) killed by TERM signal
[   17.870882] init: cups main process (792) killed by HUP signal
[   17.870902] init: cups main process ended, respawning
[   18.025471] Bluetooth: Core ver 2.20
[   18.025515] NET: Registered protocol family 31
[   18.025517] Bluetooth: HCI device and connection manager initialized
[   18.025527] Bluetooth: HCI socket layer initialized
[   18.025532] Bluetooth: L2CAP socket layer initialized
[   18.025541] Bluetooth: SCO socket layer initialized
[   18.199978] Bluetooth: RFCOMM TTY layer initialized
[   18.199995] Bluetooth: RFCOMM socket layer initialized
[   18.200046] Bluetooth: RFCOMM ver 1.11
[   18.301995] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.302002] Bluetooth: BNEP filters: protocol multicast
[   18.302010] Bluetooth: BNEP socket layer initialized
[   21.386835] audit_printk_skb: 165 callbacks suppressed
[   21.386843] audit: type=1400 audit(1450704964.410:67): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=954 comm="apparmor_parser"
[   24.702183] atl1 0000:03:00.0: eth1 link is up 1000 Mbps full duplex
[   30.005333] init: plymouth-upstart-bridge main process ended, respawning
[   47.986178] audit: type=1400 audit(1450704990.352:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1814 comm="apparmor_parser"
[   47.986203] audit: type=1400 audit(1450704990.352:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1814 comm="apparmor_parser"
[   47.986810] audit: type=1400 audit(1450704990.352:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1814 comm="apparmor_parser"
[   52.216136] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[ 9254.723010] audit: type=1400 audit(1450714197.089:71): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/" pid=2509 comm="init" fstype="proc" srcname="proc" flags="rw"
[ 9254.723080] audit: type=1400 audit(1450714197.089:72): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/sys/" pid=2509 comm="init" fstype="sysfs" srcname="sysfs" flags="rw"
[ 9254.888760] audit: type=1400 audit(1450714197.257:73): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/2614/cmdline" pid=2593 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9254.896399] audit: type=1400 audit(1450714197.265:74): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/2611/cmdline" pid=2593 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9254.899401] audit: type=1400 audit(1450714197.265:75): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/2620/cmdline" pid=2593 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9254.919362] audit: type=1400 audit(1450714197.285:76): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/2621/cmdline" pid=2593 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9255.164399] audit: type=1400 audit(1450714197.533:77): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/run/user/116/gvfs/" pid=2674 comm="gvfsd-fuse" fstype="fuse.gvfsd-fuse" srcname="gvfsd-fuse" flags="rw, nosuid, nodev"
[ 9260.946453] audit: type=1400 audit(1450714203.313:78): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/sys/vm/overcommit_memory" pid=2839 comm="pool" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9261.048748] audit: type=1400 audit(1450714203.417:79): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/1/cgroup" pid=2783 comm="gnome-session" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9261.490681] audit: type=1400 audit(1450714203.857:80): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/sys/vm/overcommit_memory" pid=2926 comm="pool" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9261.682629] audit: type=1400 audit(1450714204.049:81): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/1/cgroup" pid=2913 comm="gnome-screensav" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9261.895963] audit: type=1400 audit(1450714204.261:82): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/1/cgroup" pid=2772 comm="unity-settings-" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9261.949513] audit: type=1400 audit(1450714204.317:83): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/1/cgroup" pid=2866 comm="indicator-sound" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9262.090250] audit: type=1400 audit(1450714204.457:84): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/etc/compizconfig/unity.ini" pid=2965 comm="compiz" requested_mask="c" denied_mask="c" fsuid=116 ouid=0
[ 9263.831316] audit: type=1400 audit(1450714206.197:85): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/1/cgroup" pid=2977 comm="polkit-gnome-au" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9264.025168] audit: type=1400 audit(1450714206.393:86): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/1/cgroup" pid=2999 comm="gvfs-udisks2-vo" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9264.321012] audit: type=1400 audit(1450714206.689:87): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/sys/vm/overcommit_memory" pid=2993 comm="pool" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9266.886074] audit: type=1400 audit(1450714209.253:88): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/sys/vm/overcommit_memory" pid=3060 comm="pool" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9276.514617] audit: type=1400 audit(1450714218.881:89): apparmor="DENIED" operation="open" profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/sys/vm/overcommit_memory" pid=2917 comm="pool" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
[ 9510.980405] systemd-hostnamed[4119]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```

lshw - [http://pastebin.com/9Qk2guam](http://pastebin.com/9Qk2guam)
```

msolsovec
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=C0609C84-8DFE-D511-B668-001E8CCA4FFF
  *-core
       description: Motherboard
       product: M2A-MX
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MS6C81B32304407
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0403
          date: 11/26/2007
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          serial: To Be Filled By O.E.M.
          slot: Socket AM2
          size: 1800MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv vmmcall cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 31
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM DDR2 Synchronous 533 MHz (1,9 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fe900000-feafffff ioport:fc000000(size=33554432)
           *-display
                description: VGA compatible controller
                product: RS690 [Radeon X1200]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:27 memory:fc000000-fdffffff memory:feaf0000-feafffff ioport:e000(size=256) memory:fe900000-fe9fffff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: Attansic L1 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: b0
                serial: 00:1e:8c:ca:4f:ff
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full ip=10.77.77.223 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:28 memory:febc0000-febfffff memory:feba0000-febbffff
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:d000(size=8) ioport:c000(size=4) ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=16) memory:fe8ff800-fe8ffbff
        *-usb:0
             description: USB controller
             product: SB600 USB (OHCI0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:fe8fe000-fe8fefff
        *-usb:1
             description: USB controller
             product: SB600 USB (OHCI1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:fe8fd000-fe8fdfff
        *-usb:2
             description: USB controller
             product: SB600 USB (OHCI2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:fe8fc000-fe8fcfff
        *-usb:3
             description: USB controller
             product: SB600 USB (OHCI3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:fe8fb000-fe8fbfff
        *-usb:4
             description: USB controller
             product: SB600 USB (OHCI4)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:fe8fa000-fe8fafff
        *-usb:5
             description: USB controller
             product: SB600 USB Controller (EHCI)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:fe8ff000-fe8ff0ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:26 memory:fe8f4000-fe8f7fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250820A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: E
             serial: 9QE0TC6C
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0006d828
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 12a413f4-4d91-4fdd-badf-6e6cd28b454f
                size: 231GiB
                capacity: 231GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-12-21 12:14:31 filesystem=ext4 lastmountpoint=/ modified=2015-12-21 14:35:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-12-21 14:35:51 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 990MiB
                capacity: 990MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 990MiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S202H
             vendor: TSSTcorp
             physical id: 0.1.0
             bus info: scsi@4:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          bus info: usb@1:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 7552MiB (7918MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=000177a3
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/msolsovec/MODRA
                version: FAT32
                serial: 7a8c-fba0
                size: 7549MiB
                capacity: 7551MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=MODRA mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted

```


lsmod - [http://pastebin.com/fyP7cWSs](http://pastebin.com/fyP7cWSs)
```

Module                  Size  Used by
nls_iso8859_1          16384  1
bnep                   20480  2
rfcomm                 69632  0
bluetooth             491520  10 bnep,rfcomm
amdkfd                 81920  1
amd_iommu_v2           20480  1 amdkfd
joydev                 20480  0
hid_logitech_hidpp     20480  0
radeon               1556480  3
snd_hda_codec_realtek    81920  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_intel          36864  3
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
ttm                    94208  1 radeon
snd_rawmidi            32768  1 snd_seq_midi
drm_kms_helper        126976  1 radeon
drm                   344064  6 ttm,drm_kms_helper,radeon
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
kvm_amd                61440  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm                   479232  1 kvm_amd
snd_timer              32768  2 snd_pcm,snd_seq
i2c_algo_bit           16384  1 radeon
snd                    86016  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
edac_core              53248  0
serio_raw              16384  0
edac_mce_amd           24576  0
k8temp                 16384  0
i2c_piix4              24576  0
shpchp                 40960  0
8250_fintek            16384  0
asus_atk0110           20480  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
hid_logitech_dj        20480  0
usbhid                 53248  0
hid                   110592  3 usbhid,hid_logitech_dj,hid_logitech_hidpp
uas                    24576  0
usb_storage            69632  2 uas
pata_acpi              16384  0
psmouse               114688  0
pata_atiixp            16384  2
atl1                   40960  0
mii                    16384  1 atl1
floppy                 77824  0
ahci                   36864  0
libahci                32768  1 ahci

```


[IMG]https://photos-6.dropbox.com/t/2/AAAmbv0f73OkesinKBfnzrrAETX_GFmqGoGMsrSz-jDY9Q/12/1283494/jpeg/32x32/3/1450731600/0/2/death-unity01.jpg/EOPriwEY7oaUSCABKAE/R0qfdUvOx3JHQ4geVrO2tBCniVcgS6H_HCVKX-f_5Es?size_mode=5&size=32x32[/IMG]

---

### Post by rrob on 2015-12-22
SOLVED
after updating bios.

Directly from booted system:
[https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux)
[http://www.flashrom.org/Supported_hardware](http://www.flashrom.org/Supported_hardware)

---

