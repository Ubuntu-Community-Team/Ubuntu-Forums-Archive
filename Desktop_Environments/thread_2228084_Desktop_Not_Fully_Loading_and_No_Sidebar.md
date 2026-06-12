---
title: "Desktop Not Fully Loading and No Sidebar"
date: 2014-06-05
forum: Desktop Environments
---

### Post by ap0ll0uk2 on 2014-06-05
Evening All

I've switched on my Ubuntu 14.04 box this evening only to be greeted with a desktop wallpaper and not much else! There's no sidebar, no taskbar, only the wallpaper. 

I can right click on the desktop and am presented with the right click context menu and I can create a new folder. I can browse the folder but there is no window title, no minimise, maximise or close buttons.

I can SSH into the machine, and apps that run from the web server all run fine and are accesible.

Does anyone have any idea what might have caused this, or how I can troubleshoot it please?

I've included below the info from the Syslog:-

```

Jun  5 20:37:45 hermes rsyslogd: rsyslogd's groupid changed to 103
Jun  5 20:37:45 hermes rsyslogd: rsyslogd's userid changed to 101
Jun  5 20:37:45 hermes kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  5 20:37:45 hermes kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  5 20:37:45 hermes kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jun  5 20:37:45 hermes kernel: [    0.000000] Linux version 3.13.0-24-generic (buildd@batsu) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 (Ubuntu 3.13.0-24.47-generic 3.13.9)
Jun  5 20:37:45 hermes kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=d9145a00-ca82-40b5-b8b0-bffde6061aa7 ro quiet splash
Jun  5 20:37:45 hermes kernel: [    0.000000] KERNEL supported cpus:
Jun  5 20:37:45 hermes kernel: [    0.000000]   Intel GenuineIntel
Jun  5 20:37:45 hermes kernel: [    0.000000]   AMD AuthenticAMD
Jun  5 20:37:45 hermes kernel: [    0.000000]   Centaur CentaurHauls
Jun  5 20:37:45 hermes kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f3ff] usable
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f400-0x000000000009ffff] reserved
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000afedffff] usable
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x00000000afee0000-0x00000000afee2fff] ACPI NVS
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x00000000afee3000-0x00000000afeeffff] ACPI data
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x00000000afef0000-0x00000000afefffff] reserved
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
Jun  5 20:37:45 hermes kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024fffffff] usable
Jun  5 20:37:45 hermes kernel: [    0.000000] NX (Execute Disable) protection: active
Jun  5 20:37:45 hermes kernel: [    0.000000] SMBIOS 2.2 present.
Jun  5 20:37:45 hermes kernel: [    0.000000] DMI: OEM OEM/AB9/AB9RPO(Intel965+ICH8), BIOS 6.00 PG 12/20/2007
Jun  5 20:37:45 hermes kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jun  5 20:37:45 hermes kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jun  5 20:37:45 hermes kernel: [    0.000000] No AGP bridge found
Jun  5 20:37:45 hermes kernel: [    0.000000] e820: last_pfn = 0x250000 max_arch_pfn = 0x400000000
Jun  5 20:37:45 hermes kernel: [    0.000000] MTRR default type: uncachable
Jun  5 20:37:45 hermes kernel: [    0.000000] MTRR fixed ranges enabled:
Jun  5 20:37:45 hermes kernel: [    0.000000]   00000-9FFFF write-back
Jun  5 20:37:45 hermes kernel: [    0.000000]   A0000-BFFFF uncachable
Jun  5 20:37:45 hermes kernel: [    0.000000]   C0000-CDFFF write-protect
Jun  5 20:37:45 hermes kernel: [    0.000000]   CE000-EFFFF uncachable
Jun  5 20:37:45 hermes kernel: [    0.000000]   F0000-FFFFF write-through
Jun  5 20:37:45 hermes kernel: [    0.000000] MTRR variable ranges enabled:
Jun  5 20:37:45 hermes kernel: [    0.000000]   0 base 100000000 mask F00000000 write-back
Jun  5 20:37:45 hermes kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
Jun  5 20:37:45 hermes kernel: [    0.000000]   2 base 240000000 mask FF0000000 write-back
Jun  5 20:37:45 hermes kernel: [    0.000000]   3 base 000000000 mask F80000000 write-back
Jun  5 20:37:45 hermes kernel: [    0.000000]   4 base 080000000 mask FE0000000 write-back
Jun  5 20:37:45 hermes kernel: [    0.000000]   5 base 0A0000000 mask FF0000000 write-back
Jun  5 20:37:45 hermes kernel: [    0.000000]   6 base 0AFF00000 mask FFFF00000 uncachable
Jun  5 20:37:45 hermes kernel: [    0.000000]   7 disabled
Jun  5 20:37:45 hermes kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun  5 20:37:45 hermes kernel: [    0.000000] original variable MTRRs
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 0, base: 4GB, range: 4GB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 1, base: 8GB, range: 1GB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 2, base: 9GB, range: 256MB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 3, base: 0GB, range: 2GB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 4, base: 2GB, range: 512MB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 5, base: 2560MB, range: 256MB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 6, base: 2815MB, range: 1MB, type UC
Jun  5 20:37:45 hermes kernel: [    0.000000] total RAM covered: 8191M
Jun  5 20:37:45 hermes kernel: [    0.000000] Found optimal setting for mtrr clean up
Jun  5 20:37:45 hermes kernel: [    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 7      lose cover RAM: 0G
Jun  5 20:37:45 hermes kernel: [    0.000000] New variable MTRRs
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 1, base: 2GB, range: 512MB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 3, base: 2815MB, range: 1MB, type UC
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 4, base: 4GB, range: 4GB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 5, base: 8GB, range: 1GB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] reg 6, base: 9GB, range: 256MB, type WB
Jun  5 20:37:45 hermes kernel: [    0.000000] e820: update [mem 0xaff00000-0xffffffff] usable ==> reserved
Jun  5 20:37:45 hermes kernel: [    0.000000] e820: last_pfn = 0xafee0 max_arch_pfn = 0x400000000
Jun  5 20:37:45 hermes kernel: [    0.000000] found SMP MP-table at [mem 0x000f3590-0x000f359f] mapped at [ffff8800000f3590]
Jun  5 20:37:45 hermes kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jun  5 20:37:45 hermes kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Jun  5 20:37:45 hermes kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jun  5 20:37:45 hermes kernel: [    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
Jun  5 20:37:45 hermes kernel: [    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
Jun  5 20:37:45 hermes kernel: [    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
Jun  5 20:37:45 hermes kernel: [    0.000000] init_memory_mapping: [mem 0x24fe00000-0x24fffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]  [mem 0x24fe00000-0x24fffffff] page 2M
Jun  5 20:37:45 hermes kernel: [    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
Jun  5 20:37:45 hermes kernel: [    0.000000] init_memory_mapping: [mem 0x24c000000-0x24fdfffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]  [mem 0x24c000000-0x24fdfffff] page 2M
Jun  5 20:37:45 hermes kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x24bffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]  [mem 0x200000000-0x24bffffff] page 2M
Jun  5 20:37:45 hermes kernel: [    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
Jun  5 20:37:45 hermes kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xafedffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jun  5 20:37:45 hermes kernel: [    0.000000]  [mem 0x00200000-0xafdfffff] page 2M
Jun  5 20:37:45 hermes kernel: [    0.000000]  [mem 0xafe00000-0xafedffff] page 4k
Jun  5 20:37:45 hermes kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
Jun  5 20:37:45 hermes kernel: [    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
Jun  5 20:37:45 hermes kernel: [    0.000000] RAMDISK: [mem 0x35b86000-0x36dbafff]
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: RSDP 00000000000f7740 000014 (v00 IntelR)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: RSDT 00000000afee3000 000034 (v01 IntelR AWRDACPI 42302E31 AWRD 00000000)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: FACP 00000000afee3080 000074 (v01 IntelR AWRDACPI 42302E31 AWRD 00000000)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: DSDT 00000000afee3100 004C43 (v01 INTELR AWRDACPI 00001000 MSFT 03000000)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: FACS 00000000afee0000 000040
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: MCFG 00000000afee7e40 00003C (v01 IntelR AWRDACPI 42302E31 AWRD 00000000)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: APIC 00000000afee7d80 000084 (v01 IntelR AWRDACPI 42302E31 AWRD 00000000)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: SSDT 00000000afee84e0 000380 (v01  PmRef    CpuPm 00003000 INTL 20041203)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  5 20:37:45 hermes kernel: [    0.000000] No NUMA configuration found
Jun  5 20:37:45 hermes kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024fffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x24fffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]   NODE_DATA [mem 0x24fff5000-0x24fff9fff]
Jun  5 20:37:45 hermes kernel: [    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880247600000-ffff88024f5fffff] on node 0
Jun  5 20:37:45 hermes kernel: [    0.000000] Zone ranges:
Jun  5 20:37:45 hermes kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]   Normal   [mem 0x100000000-0x24fffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] Movable zone start for each node
Jun  5 20:37:45 hermes kernel: [    0.000000] Early memory node ranges
Jun  5 20:37:45 hermes kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009efff]
Jun  5 20:37:45 hermes kernel: [    0.000000]   node   0: [mem 0x00100000-0xafedffff]
Jun  5 20:37:45 hermes kernel: [    0.000000]   node   0: [mem 0x100000000-0x24fffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] On node 0 totalpages: 2096766
Jun  5 20:37:45 hermes kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun  5 20:37:45 hermes kernel: [    0.000000]   DMA zone: 21 pages reserved
Jun  5 20:37:45 hermes kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Jun  5 20:37:45 hermes kernel: [    0.000000]   DMA32 zone: 11196 pages used for memmap
Jun  5 20:37:45 hermes kernel: [    0.000000]   DMA32 zone: 716512 pages, LIFO batch:31
Jun  5 20:37:45 hermes kernel: [    0.000000]   Normal zone: 21504 pages used for memmap
Jun  5 20:37:45 hermes kernel: [    0.000000]   Normal zone: 1376256 pages, LIFO batch:31
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun  5 20:37:45 hermes kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun  5 20:37:45 hermes kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun  5 20:37:45 hermes kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  5 20:37:45 hermes kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Jun  5 20:37:45 hermes kernel: [    0.000000] nr_irqs_gsi: 40
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0xafee0000-0xafee2fff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0xafee3000-0xafeeffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0xafef0000-0xafefffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0xaff00000-0xdfffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
Jun  5 20:37:45 hermes kernel: [    0.000000] e820: [mem 0xaff00000-0xdfffffff] available for PCI devices
Jun  5 20:37:45 hermes kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun  5 20:37:45 hermes kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Jun  5 20:37:45 hermes kernel: [    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88024fc00000 s86336 r8192 d24256 u524288
Jun  5 20:37:45 hermes kernel: [    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
Jun  5 20:37:45 hermes kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jun  5 20:37:45 hermes kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2063981
Jun  5 20:37:45 hermes kernel: [    0.000000] Policy zone: Normal
Jun  5 20:37:45 hermes kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=d9145a00-ca82-40b5-b8b0-bffde6061aa7 ro quiet splash
Jun  5 20:37:45 hermes kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun  5 20:37:45 hermes kernel: [    0.000000] Checking aperture...
Jun  5 20:37:45 hermes kernel: [    0.000000] No AGP bridge found
Jun  5 20:37:45 hermes kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jun  5 20:37:45 hermes kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun  5 20:37:45 hermes kernel: [    0.000000] Memory: 8154188K/8387064K available (7338K kernel code, 1138K rwdata, 3388K rodata, 1332K init, 1440K bss, 232876K reserved)
Jun  5 20:37:45 hermes kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jun  5 20:37:45 hermes kernel: [    0.000000] Hierarchical RCU implementation.
Jun  5 20:37:45 hermes kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jun  5 20:37:45 hermes kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Jun  5 20:37:45 hermes kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Jun  5 20:37:45 hermes kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Jun  5 20:37:45 hermes kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Jun  5 20:37:45 hermes kernel: [    0.000000] Console: colour VGA+ 80x25
Jun  5 20:37:45 hermes kernel: [    0.000000] console [tty0] enabled
Jun  5 20:37:45 hermes kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Jun  5 20:37:45 hermes kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun  5 20:37:45 hermes kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jun  5 20:37:45 hermes kernel: [    0.000000] tsc: Detected 2447.907 MHz processor
Jun  5 20:37:45 hermes kernel: [    0.008003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4895.81 BogoMIPS (lpj=9791628)
Jun  5 20:37:45 hermes kernel: [    0.008007] pid_max: default: 32768 minimum: 301
Jun  5 20:37:45 hermes kernel: [    0.008035] Security Framework initialized
Jun  5 20:37:45 hermes kernel: [    0.008057] AppArmor: AppArmor initialized
Jun  5 20:37:45 hermes kernel: [    0.008059] Yama: becoming mindful.
Jun  5 20:37:45 hermes kernel: [    0.012651] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jun  5 20:37:45 hermes kernel: [    0.016210] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun  5 20:37:45 hermes kernel: [    0.017883] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jun  5 20:37:45 hermes kernel: [    0.017897] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jun  5 20:37:45 hermes kernel: [    0.018239] Initializing cgroup subsys memory
Jun  5 20:37:45 hermes kernel: [    0.018248] Initializing cgroup subsys devices
Jun  5 20:37:45 hermes kernel: [    0.018251] Initializing cgroup subsys freezer
Jun  5 20:37:45 hermes kernel: [    0.018253] Initializing cgroup subsys blkio
Jun  5 20:37:45 hermes kernel: [    0.018255] Initializing cgroup subsys perf_event
Jun  5 20:37:45 hermes kernel: [    0.018258] Initializing cgroup subsys hugetlb
Jun  5 20:37:45 hermes kernel: [    0.018282] CPU: Physical Processor ID: 0
Jun  5 20:37:45 hermes kernel: [    0.018284] CPU: Processor Core ID: 0
Jun  5 20:37:45 hermes kernel: [    0.018286] mce: CPU supports 6 MCE banks
Jun  5 20:37:45 hermes kernel: [    0.018293] CPU0: Thermal monitoring enabled (TM2)
Jun  5 20:37:45 hermes kernel: [    0.018301] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
Jun  5 20:37:45 hermes kernel: [    0.018301] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
Jun  5 20:37:45 hermes kernel: [    0.018301] tlb_flushall_shift: -1
Jun  5 20:37:45 hermes kernel: [    0.018397] Freeing SMP alternatives memory: 32K (ffffffff81e6b000 - ffffffff81e73000)
Jun  5 20:37:45 hermes kernel: [    0.019837] ACPI: Core revision 20131115
Jun  5 20:37:45 hermes kernel: [    0.022015] ACPI: All ACPI Tables successfully acquired
Jun  5 20:37:45 hermes kernel: [    0.024012] ftrace: allocating 28408 entries in 111 pages
Jun  5 20:37:45 hermes kernel: [    0.032446] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun  5 20:37:45 hermes kernel: [    0.074367] smpboot: CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (fam: 06, model: 0f, stepping: 06)
Jun  5 20:37:45 hermes kernel: [    0.076000] Performance Events: PEBS fmt0-, 4-deep LBR, Core2 events, Intel PMU driver.
Jun  5 20:37:45 hermes kernel: [    0.076000] perf_event_intel: PEBS disabled due to CPU errata
Jun  5 20:37:45 hermes kernel: [    0.076000] ... version:                2
Jun  5 20:37:45 hermes kernel: [    0.076000] ... bit width:              40
Jun  5 20:37:45 hermes kernel: [    0.076000] ... generic registers:      2
Jun  5 20:37:45 hermes kernel: [    0.076000] ... value mask:             000000ffffffffff
Jun  5 20:37:45 hermes kernel: [    0.076000] ... max period:             000000007fffffff
Jun  5 20:37:45 hermes kernel: [    0.076000] ... fixed-purpose events:   3
Jun  5 20:37:45 hermes kernel: [    0.076000] ... event mask:             0000000700000003
Jun  5 20:37:45 hermes kernel: [    0.076737] x86: Booting SMP configuration:
Jun  5 20:37:45 hermes kernel: [    0.076740] .... node  #0, CPUs:      #1
Jun  5 20:37:45 hermes kernel: [    0.088050] x86: Booted up 1 node, 2 CPUs
Jun  5 20:37:45 hermes kernel: [    0.088054] smpboot: Total of 2 processors activated (9791.62 BogoMIPS)
Jun  5 20:37:45 hermes kernel: [    0.088151] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jun  5 20:37:45 hermes kernel: [    0.089952] devtmpfs: initialized
Jun  5 20:37:45 hermes kernel: [    0.093542] EVM: security.selinux
Jun  5 20:37:45 hermes kernel: [    0.093544] EVM: security.SMACK64
Jun  5 20:37:45 hermes kernel: [    0.093545] EVM: security.ima
Jun  5 20:37:45 hermes kernel: [    0.093547] EVM: security.capability
Jun  5 20:37:45 hermes kernel: [    0.093572] PM: Registering ACPI NVS region [mem 0xafee0000-0xafee2fff] (12288 bytes)
Jun  5 20:37:45 hermes kernel: [    0.093572] pinctrl core: initialized pinctrl subsystem
Jun  5 20:37:45 hermes kernel: [    0.093572] regulator-dummy: no parameters
Jun  5 20:37:45 hermes kernel: [    0.093572] RTC time: 19:37:40, date: 06/05/14
Jun  5 20:37:45 hermes kernel: [    0.093572] NET: Registered protocol family 16
Jun  5 20:37:45 hermes kernel: [    0.093572] cpuidle: using governor ladder
Jun  5 20:37:45 hermes kernel: [    0.093572] cpuidle: using governor menu
Jun  5 20:37:45 hermes kernel: [    0.093572] ACPI: bus type PCI registered
Jun  5 20:37:45 hermes kernel: [    0.093572] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jun  5 20:37:45 hermes kernel: [    0.093572] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun  5 20:37:45 hermes kernel: [    0.093572] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jun  5 20:37:45 hermes kernel: [    0.113381] PCI: Using configuration type 1 for base access
Jun  5 20:37:45 hermes kernel: [    0.116069] bio: create slab <bio-0> at 0
Jun  5 20:37:45 hermes kernel: [    0.116089] ACPI: Added _OSI(Module Device)
Jun  5 20:37:45 hermes kernel: [    0.116091] ACPI: Added _OSI(Processor Device)
Jun  5 20:37:45 hermes kernel: [    0.116093] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun  5 20:37:45 hermes kernel: [    0.116095] ACPI: Added _OSI(Processor Aggregator Device)
Jun  5 20:37:45 hermes kernel: [    0.118776] ACPI: SSDT 00000000afee7ec0 00022A (v01  PmRef  Cpu0Ist 00003000 INTL 20041203)
Jun  5 20:37:45 hermes kernel: [    0.119007] ACPI: Dynamic OEM Table Load:
Jun  5 20:37:45 hermes kernel: [    0.119010] ACPI: SSDT           (null) 00022A (v01  PmRef  Cpu0Ist 00003000 INTL 20041203)
Jun  5 20:37:45 hermes kernel: [    0.119107] ACPI: SSDT 00000000afee8380 000152 (v01  PmRef  Cpu1Ist 00003000 INTL 20041203)
Jun  5 20:37:45 hermes kernel: [    0.119332] ACPI: Dynamic OEM Table Load:
Jun  5 20:37:45 hermes kernel: [    0.119335] ACPI: SSDT           (null) 000152 (v01  PmRef  Cpu1Ist 00003000 INTL 20041203)
Jun  5 20:37:45 hermes kernel: [    0.119472] ACPI: Interpreter enabled
Jun  5 20:37:45 hermes kernel: [    0.119477] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
Jun  5 20:37:45 hermes rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jun  5 20:37:45 hermes kernel: [    0.119482] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Jun  5 20:37:45 hermes kernel: [    0.119496] ACPI: (supports S0 S3 S4 S5)
Jun  5 20:37:45 hermes kernel: [    0.119497] ACPI: Using IOAPIC for interrupt routing
Jun  5 20:37:45 hermes kernel: [    0.119518] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Jun  5 20:37:45 hermes kernel: [    0.120012] ACPI: ACPI Dock Station Driver: 1 docks/bays found
Jun  5 20:37:45 hermes kernel: [    0.124442] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun  5 20:37:45 hermes kernel: [    0.124448] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jun  5 20:37:45 hermes kernel: [    0.124453] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
Jun  5 20:37:45 hermes kernel: [    0.124519] acpi PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Jun  5 20:37:45 hermes kernel: [    0.124522] acpi PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
Jun  5 20:37:45 hermes kernel: [    0.124525] acpi PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Jun  5 20:37:45 hermes kernel: [    0.124527] acpi PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
Jun  5 20:37:45 hermes kernel: [    0.124529] acpi PNP0A08:00: host bridge window [mem 0xaff00000-0xfebfffff] (ignored)
Jun  5 20:37:45 hermes kernel: [    0.124531] PCI: root bus 00: using default resources
Jun  5 20:37:45 hermes kernel: [    0.124723] PCI host bridge to bus 0000:00
Jun  5 20:37:45 hermes kernel: [    0.124726] pci_bus 0000:00: root bus resource [bus 00-ff]
Jun  5 20:37:45 hermes kernel: [    0.124728] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
Jun  5 20:37:45 hermes kernel: [    0.124731] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
Jun  5 20:37:45 hermes kernel: [    0.124740] pci 0000:00:00.0: [8086:29a0] type 00 class 0x060000
Jun  5 20:37:45 hermes kernel: [    0.124841] pci 0000:00:01.0: [8086:29a1] type 01 class 0x060400
Jun  5 20:37:45 hermes kernel: [    0.124880] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.124977] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
Jun  5 20:37:45 hermes kernel: [    0.125015] pci 0000:00:1a.0: reg 0x20: [io  0xff00-0xff1f]
Jun  5 20:37:45 hermes kernel: [    0.125081] pci 0000:00:1a.0: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.125113] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
Jun  5 20:37:45 hermes kernel: [    0.125151] pci 0000:00:1a.1: reg 0x20: [io  0xfe00-0xfe1f]
Jun  5 20:37:45 hermes kernel: [    0.125217] pci 0000:00:1a.1: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.125261] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
Jun  5 20:37:45 hermes kernel: [    0.125277] pci 0000:00:1a.7: reg 0x10: [mem 0xfdfff000-0xfdfff3ff]
Jun  5 20:37:45 hermes kernel: [    0.125346] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.125396] pci 0000:00:1a.7: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.125434] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
Jun  5 20:37:45 hermes kernel: [    0.125449] pci 0000:00:1b.0: reg 0x10: [mem 0xfdff8000-0xfdffbfff 64bit]
Jun  5 20:37:45 hermes kernel: [    0.125512] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.125566] pci 0000:00:1b.0: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.125600] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
Jun  5 20:37:45 hermes kernel: [    0.125665] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.125719] pci 0000:00:1c.0: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.125756] pci 0000:00:1c.2: [8086:2843] type 01 class 0x060400
Jun  5 20:37:45 hermes kernel: [    0.125820] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.125874] pci 0000:00:1c.2: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.125910] pci 0000:00:1c.4: [8086:2847] type 01 class 0x060400
Jun  5 20:37:45 hermes kernel: [    0.125974] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.126031] pci 0000:00:1c.4: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.126068] pci 0000:00:1c.5: [8086:2849] type 01 class 0x060400
Jun  5 20:37:45 hermes kernel: [    0.126132] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.126187] pci 0000:00:1c.5: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.126219] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
Jun  5 20:37:45 hermes kernel: [    0.126257] pci 0000:00:1d.0: reg 0x20: [io  0xfd00-0xfd1f]
Jun  5 20:37:45 hermes kernel: [    0.126322] pci 0000:00:1d.0: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.126353] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
Jun  5 20:37:45 hermes kernel: [    0.126390] pci 0000:00:1d.1: reg 0x20: [io  0xfc00-0xfc1f]
Jun  5 20:37:45 hermes kernel: [    0.126456] pci 0000:00:1d.1: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.126487] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
Jun  5 20:37:45 hermes kernel: [    0.126524] pci 0000:00:1d.2: reg 0x20: [io  0xfb00-0xfb1f]
Jun  5 20:37:45 hermes kernel: [    0.126589] pci 0000:00:1d.2: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.126630] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
Jun  5 20:37:45 hermes kernel: [    0.126646] pci 0000:00:1d.7: reg 0x10: [mem 0xfdffe000-0xfdffe3ff]
Jun  5 20:37:45 hermes kernel: [    0.126714] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.126766] pci 0000:00:1d.7: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.126799] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
Jun  5 20:37:45 hermes kernel: [    0.126891] pci 0000:00:1e.0: System wakeup disabled by ACPI
Jun  5 20:37:45 hermes kernel: [    0.126928] pci 0000:00:1f.0: [8086:2810] type 00 class 0x060100
Jun  5 20:37:45 hermes kernel: [    0.127001] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH6 ACPI/GPIO/TCO
Jun  5 20:37:45 hermes kernel: [    0.127006] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
Jun  5 20:37:45 hermes kernel: [    0.127011] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 00e0 (mask 000f)
Jun  5 20:37:45 hermes kernel: [    0.127112] pci 0000:00:1f.2: [8086:2820] type 00 class 0x01018f
Jun  5 20:37:45 hermes kernel: [    0.127126] pci 0000:00:1f.2: reg 0x10: [io  0xfa00-0xfa07]
Jun  5 20:37:45 hermes kernel: [    0.127133] pci 0000:00:1f.2: reg 0x14: [io  0xf900-0xf903]
Jun  5 20:37:45 hermes kernel: [    0.127141] pci 0000:00:1f.2: reg 0x18: [io  0xf800-0xf807]
Jun  5 20:37:45 hermes kernel: [    0.127149] pci 0000:00:1f.2: reg 0x1c: [io  0xf700-0xf703]
Jun  5 20:37:45 hermes kernel: [    0.127157] pci 0000:00:1f.2: reg 0x20: [io  0xf600-0xf60f]
Jun  5 20:37:45 hermes kernel: [    0.127164] pci 0000:00:1f.2: reg 0x24: [io  0xf500-0xf50f]
Jun  5 20:37:45 hermes kernel: [    0.127192] pci 0000:00:1f.2: PME# supported from D3hot
Jun  5 20:37:45 hermes kernel: [    0.127266] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
Jun  5 20:37:45 hermes kernel: [    0.127278] pci 0000:00:1f.3: reg 0x10: [mem 0xfdffd000-0xfdffd0ff]
Jun  5 20:37:45 hermes kernel: [    0.127303] pci 0000:00:1f.3: reg 0x20: [io  0x0500-0x051f]
Jun  5 20:37:45 hermes kernel: [    0.127393] pci 0000:00:1f.5: [8086:2825] type 00 class 0x010185
Jun  5 20:37:45 hermes kernel: [    0.127406] pci 0000:00:1f.5: reg 0x10: [io  0xf300-0xf307]
Jun  5 20:37:45 hermes kernel: [    0.127414] pci 0000:00:1f.5: reg 0x14: [io  0xf200-0xf203]
Jun  5 20:37:45 hermes kernel: [    0.127422] pci 0000:00:1f.5: reg 0x18: [io  0xf100-0xf107]
Jun  5 20:37:45 hermes kernel: [    0.127429] pci 0000:00:1f.5: reg 0x1c: [io  0xf000-0xf003]
Jun  5 20:37:45 hermes kernel: [    0.127437] pci 0000:00:1f.5: reg 0x20: [io  0xef00-0xef0f]
Jun  5 20:37:45 hermes kernel: [    0.127445] pci 0000:00:1f.5: reg 0x24: [io  0xee00-0xee0f]
Jun  5 20:37:45 hermes kernel: [    0.127472] pci 0000:00:1f.5: PME# supported from D3hot
Jun  5 20:37:45 hermes kernel: [    0.127588] pci 0000:01:00.0: [10de:0fc0] type 00 class 0x030000
Jun  5 20:37:45 hermes kernel: [    0.127599] pci 0000:01:00.0: reg 0x10: [mem 0xfb000000-0xfbffffff]
Jun  5 20:37:45 hermes kernel: [    0.127611] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.127622] pci 0000:01:00.0: reg 0x1c: [mem 0xce000000-0xcfffffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.127631] pci 0000:01:00.0: reg 0x24: [io  0xcf00-0xcf7f]
Jun  5 20:37:45 hermes kernel: [    0.127639] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0007ffff pref]
Jun  5 20:37:45 hermes kernel: [    0.127719] pci 0000:01:00.1: [10de:0e1b] type 00 class 0x040300
Jun  5 20:37:45 hermes kernel: [    0.127730] pci 0000:01:00.1: reg 0x10: [mem 0xfcffc000-0xfcffffff]
Jun  5 20:37:45 hermes kernel: [    0.127851] pci 0000:00:01.0: PCI bridge to [bus 01]
Jun  5 20:37:45 hermes kernel: [    0.127854] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Jun  5 20:37:45 hermes kernel: [    0.127857] pci 0000:00:01.0:   bridge window [mem 0xfb000000-0xfcffffff]
Jun  5 20:37:45 hermes kernel: [    0.127861] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xcfffffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.127909] pci 0000:00:1c.0: PCI bridge to [bus 02]
Jun  5 20:37:45 hermes kernel: [    0.127913] pci 0000:00:1c.0:   bridge window [io  0xb000-0xbfff]
Jun  5 20:37:45 hermes kernel: [    0.127917] pci 0000:00:1c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
Jun  5 20:37:45 hermes kernel: [    0.127922] pci 0000:00:1c.0:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.127994] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
Jun  5 20:37:45 hermes kernel: [    0.128018] pci 0000:03:00.0: reg 0x10: [io  0xae00-0xaeff]
Jun  5 20:37:45 hermes kernel: [    0.128048] pci 0000:03:00.0: reg 0x18: [mem 0xfd5ff000-0xfd5fffff 64bit]
Jun  5 20:37:45 hermes kernel: [    0.128083] pci 0000:03:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
Jun  5 20:37:45 hermes kernel: [    0.128161] pci 0000:03:00.0: supports D1 D2
Jun  5 20:37:45 hermes kernel: [    0.128163] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.128210] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jun  5 20:37:45 hermes kernel: [    0.128219] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jun  5 20:37:45 hermes kernel: [    0.128223] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
Jun  5 20:37:45 hermes kernel: [    0.128227] pci 0000:00:1c.2:   bridge window [mem 0xfd500000-0xfd5fffff]
Jun  5 20:37:45 hermes kernel: [    0.128232] pci 0000:00:1c.2:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.128305] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
Jun  5 20:37:45 hermes kernel: [    0.128323] pci 0000:04:00.0: reg 0x10: [io  0x8e00-0x8eff]
Jun  5 20:37:45 hermes kernel: [    0.128353] pci 0000:04:00.0: reg 0x18: [mem 0xfddff000-0xfddfffff 64bit]
Jun  5 20:37:45 hermes kernel: [    0.128389] pci 0000:04:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
Jun  5 20:37:45 hermes kernel: [    0.128467] pci 0000:04:00.0: supports D1 D2
Jun  5 20:37:45 hermes kernel: [    0.128469] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
Jun  5 20:37:45 hermes kernel: [    0.128516] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jun  5 20:37:45 hermes kernel: [    0.128525] pci 0000:00:1c.4: PCI bridge to [bus 04]
Jun  5 20:37:45 hermes kernel: [    0.128529] pci 0000:00:1c.4:   bridge window [io  0x8000-0x8fff]
Jun  5 20:37:45 hermes kernel: [    0.128533] pci 0000:00:1c.4:   bridge window [mem 0xfdd00000-0xfddfffff]
Jun  5 20:37:45 hermes kernel: [    0.128538] pci 0000:00:1c.4:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.128616] pci 0000:05:00.0: [197b:2363] type 00 class 0x010601
Jun  5 20:37:45 hermes kernel: [    0.128701] pci 0000:05:00.0: reg 0x24: [mem 0xfdbfe000-0xfdbfffff]
Jun  5 20:37:45 hermes kernel: [    0.128715] pci 0000:05:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
Jun  5 20:37:45 hermes kernel: [    0.128765] pci 0000:05:00.0: PME# supported from D3hot
Jun  5 20:37:45 hermes kernel: [    0.128825] pci 0000:05:00.1: [197b:2363] type 00 class 0x010185
Jun  5 20:37:45 hermes kernel: [    0.128849] pci 0000:05:00.1: reg 0x10: [io  0xdf00-0xdf07]
Jun  5 20:37:45 hermes kernel: [    0.128863] pci 0000:05:00.1: reg 0x14: [io  0xde00-0xde03]
Jun  5 20:37:45 hermes kernel: [    0.128876] pci 0000:05:00.1: reg 0x18: [io  0xdd00-0xdd07]
Jun  5 20:37:45 hermes kernel: [    0.128890] pci 0000:05:00.1: reg 0x1c: [io  0xdc00-0xdc03]
Jun  5 20:37:45 hermes kernel: [    0.128903] pci 0000:05:00.1: reg 0x20: [io  0xdb00-0xdb0f]
Jun  5 20:37:45 hermes kernel: [    0.129009] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jun  5 20:37:45 hermes kernel: [    0.129019] pci 0000:00:1c.5: PCI bridge to [bus 05]
Jun  5 20:37:45 hermes kernel: [    0.129023] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
Jun  5 20:37:45 hermes kernel: [    0.129027] pci 0000:00:1c.5:   bridge window [mem 0xfdb00000-0xfdbfffff]
Jun  5 20:37:45 hermes kernel: [    0.129033] pci 0000:00:1c.5:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.129078] pci 0000:06:02.0: [104c:8023] type 00 class 0x0c0010
Jun  5 20:37:45 hermes kernel: [    0.129095] pci 0000:06:02.0: reg 0x10: [mem 0xfd8ff000-0xfd8ff7ff]
Jun  5 20:37:45 hermes kernel: [    0.129106] pci 0000:06:02.0: reg 0x14: [mem 0xfd8f8000-0xfd8fbfff]
Jun  5 20:37:45 hermes kernel: [    0.129172] pci 0000:06:02.0: supports D1 D2
Jun  5 20:37:45 hermes kernel: [    0.129174] pci 0000:06:02.0: PME# supported from D0 D1 D2 D3hot
Jun  5 20:37:45 hermes kernel: [    0.129220] pci 0000:06:05.0: [1131:7146] type 00 class 0x048000
Jun  5 20:37:45 hermes kernel: [    0.129233] pci 0000:06:05.0: reg 0x10: [mem 0xfd8fe000-0xfd8fe1ff]
Jun  5 20:37:45 hermes kernel: [    0.129322] pci 0000:06:06.0: [168c:002d] type 00 class 0x028000
Jun  5 20:37:45 hermes kernel: [    0.129341] pci 0000:06:06.0: reg 0x10: [mem 0xfd8e0000-0xfd8effff]
Jun  5 20:37:45 hermes kernel: [    0.129483] pci 0000:00:1e.0: PCI bridge to [bus 06] (subtractive decode)
Jun  5 20:37:45 hermes kernel: [    0.129487] pci 0000:00:1e.0:   bridge window [io  0x9000-0x9fff]
Jun  5 20:37:45 hermes kernel: [    0.129491] pci 0000:00:1e.0:   bridge window [mem 0xfd800000-0xfd8fffff]
Jun  5 20:37:45 hermes kernel: [    0.129497] pci 0000:00:1e.0:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.129499] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Jun  5 20:37:45 hermes kernel: [    0.129501] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
Jun  5 20:37:45 hermes kernel: [    0.130119] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 *7 10 11 14 15)
Jun  5 20:37:45 hermes kernel: [    0.130179] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 *5 7 10 11 14 15)
Jun  5 20:37:45 hermes kernel: [    0.130235] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 *10 11 14 15)
Jun  5 20:37:45 hermes kernel: [    0.130292] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 10 *11 14 15)
Jun  5 20:37:45 hermes kernel: [    0.130349] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0, disabled.
Jun  5 20:37:45 hermes dbus[774]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jun  5 20:37:45 hermes kernel: [    0.130406] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 *10 11 14 15)
Jun  5 20:37:45 hermes kernel: [    0.130463] ACPI: PCI Interrupt Link [LNK0] (IRQs 4 5 7 10 *11 14 15)
Jun  5 20:37:45 hermes kernel: [    0.130522] ACPI: PCI Interrupt Link [LNK1] (IRQs *4 5 7 10 11 14 15)
Jun  5 20:37:45 hermes kernel: [    0.130687] ACPI: \_SB_.PCI0: notify handler is installed
Jun  5 20:37:45 hermes kernel: [    0.130727] Found 1 acpi root devices
Jun  5 20:37:45 hermes kernel: [    0.132021] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun  5 20:37:45 hermes kernel: [    0.132025] vgaarb: loaded
Jun  5 20:37:45 hermes kernel: [    0.132027] vgaarb: bridge control possible 0000:01:00.0
Jun  5 20:37:45 hermes kernel: [    0.132218] SCSI subsystem initialized
Jun  5 20:37:45 hermes kernel: [    0.132235] libata version 3.00 loaded.
Jun  5 20:37:45 hermes kernel: [    0.132235] ACPI: bus type USB registered
Jun  5 20:37:45 hermes kernel: [    0.132235] usbcore: registered new interface driver usbfs
Jun  5 20:37:45 hermes kernel: [    0.132235] usbcore: registered new interface driver hub
Jun  5 20:37:45 hermes kernel: [    0.132235] usbcore: registered new device driver usb
Jun  5 20:37:45 hermes kernel: [    0.132235] PCI: Using ACPI for IRQ routing
Jun  5 20:37:45 hermes kernel: [    0.138536] PCI: pci_cache_line_size set to 64 bytes
Jun  5 20:37:45 hermes kernel: [    0.138606] e820: reserve RAM buffer [mem 0x0009f400-0x0009ffff]
Jun  5 20:37:45 hermes kernel: [    0.138608] e820: reserve RAM buffer [mem 0xafee0000-0xafffffff]
Jun  5 20:37:45 hermes kernel: [    0.138702] NetLabel: Initializing
Jun  5 20:37:45 hermes kernel: [    0.138704] NetLabel:  domain hash size = 128
Jun  5 20:37:45 hermes kernel: [    0.138705] NetLabel:  protocols = UNLABELED CIPSOv4
Jun  5 20:37:45 hermes kernel: [    0.138720] NetLabel:  unlabeled traffic allowed by default
Jun  5 20:37:45 hermes kernel: [    0.138733] Switched to clocksource refined-jiffies
Jun  5 20:37:45 hermes kernel: [    0.145988] AppArmor: AppArmor Filesystem Enabled
Jun  5 20:37:45 hermes kernel: [    0.146028] pnp: PnP ACPI init
Jun  5 20:37:45 hermes kernel: [    0.146044] ACPI: bus type PNP registered
Jun  5 20:37:45 hermes kernel: [    0.146236] system 00:00: [io  0x04d0-0x04d1] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.146239] system 00:00: [io  0x0880-0x088f] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.146244] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun  5 20:37:45 hermes kernel: [    0.146258] pnp 00:01: [dma 4]
Jun  5 20:37:45 hermes kernel: [    0.146279] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Jun  5 20:37:45 hermes kernel: [    0.146319] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun  5 20:37:45 hermes kernel: [    0.146346] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
Jun  5 20:37:45 hermes kernel: [    0.146378] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun  5 20:37:45 hermes kernel: [    0.146733] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Jun  5 20:37:45 hermes kernel: [    0.146798] system 00:06: [io  0x0400-0x04bf] could not be reserved
Jun  5 20:37:45 hermes kernel: [    0.146802] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun  5 20:37:45 hermes kernel: [    0.146838] pnp 00:07: Plug and Play ACPI device, IDs INT0800 (active)
Jun  5 20:37:45 hermes kernel: [    0.147027] pnp 00:08: Plug and Play ACPI device, IDs ABT2005 (active)
Jun  5 20:37:45 hermes kernel: [    0.147080] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.147084] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun  5 20:37:45 hermes kernel: [    0.147192] system 00:0a: [mem 0x000f0000-0x000fffff] could not be reserved
Jun  5 20:37:45 hermes kernel: [    0.147195] system 00:0a: [mem 0xaff00000-0xafffffff] could not be reserved
Jun  5 20:37:45 hermes kernel: [    0.147198] system 00:0a: [mem 0xafee0000-0xafefffff] could not be reserved
Jun  5 20:37:45 hermes kernel: [    0.147200] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
Jun  5 20:37:45 hermes kernel: [    0.147203] system 00:0a: [mem 0x00100000-0xafedffff] could not be reserved
Jun  5 20:37:45 hermes kernel: [    0.147206] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun  5 20:37:45 hermes kernel: [    0.147209] system 00:0a: [mem 0xfed14000-0xfed1dfff] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.147211] system 00:0a: [mem 0xfed20000-0xfed9ffff] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.147214] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.147216] system 00:0a: [mem 0xffb00000-0xffb7ffff] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.147219] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.147221] system 00:0a: [mem 0x000e0000-0x000effff] has been reserved
Jun  5 20:37:45 hermes kernel: [    0.147225] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun  5 20:37:45 hermes kernel: [    0.147232] pnp: PnP ACPI: found 11 devices
Jun  5 20:37:45 hermes kernel: [    0.147233] ACPI: bus type PNP unregistered
Jun  5 20:37:45 hermes kernel: [    0.153611] Switched to clocksource acpi_pm
Jun  5 20:37:45 hermes kernel: [    0.153655] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0000000-0xc007ffff pref]
Jun  5 20:37:45 hermes kernel: [    0.153658] pci 0000:00:01.0: PCI bridge to [bus 01]
Jun  5 20:37:45 hermes kernel: [    0.153661] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
Jun  5 20:37:45 hermes kernel: [    0.153665] pci 0000:00:01.0:   bridge window [mem 0xfb000000-0xfcffffff]
Jun  5 20:37:45 hermes kernel: [    0.153668] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xcfffffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153672] pci 0000:00:1c.0: PCI bridge to [bus 02]
Jun  5 20:37:45 hermes kernel: [    0.153675] pci 0000:00:1c.0:   bridge window [io  0xb000-0xbfff]
Jun  5 20:37:45 hermes kernel: [    0.153680] pci 0000:00:1c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
Jun  5 20:37:45 hermes kernel: [    0.153684] pci 0000:00:1c.0:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153690] pci 0000:03:00.0: BAR 6: assigned [mem 0xfde00000-0xfde0ffff pref]
Jun  5 20:37:45 hermes kernel: [    0.153693] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jun  5 20:37:45 hermes kernel: [    0.153695] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
Jun  5 20:37:45 hermes kernel: [    0.153700] pci 0000:00:1c.2:   bridge window [mem 0xfd500000-0xfd5fffff]
Jun  5 20:37:45 hermes kernel: [    0.153704] pci 0000:00:1c.2:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153710] pci 0000:04:00.0: BAR 6: assigned [mem 0xfdc00000-0xfdc0ffff pref]
Jun  5 20:37:45 hermes kernel: [    0.153712] pci 0000:00:1c.4: PCI bridge to [bus 04]
Jun  5 20:37:45 hermes kernel: [    0.153715] pci 0000:00:1c.4:   bridge window [io  0x8000-0x8fff]
Jun  5 20:37:45 hermes kernel: [    0.153720] pci 0000:00:1c.4:   bridge window [mem 0xfdd00000-0xfddfffff]
Jun  5 20:37:45 hermes kernel: [    0.153724] pci 0000:00:1c.4:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153730] pci 0000:05:00.0: BAR 6: assigned [mem 0xfda00000-0xfda0ffff pref]
Jun  5 20:37:45 hermes kernel: [    0.153732] pci 0000:00:1c.5: PCI bridge to [bus 05]
Jun  5 20:37:45 hermes kernel: [    0.153735] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
Jun  5 20:37:45 hermes kernel: [    0.153740] pci 0000:00:1c.5:   bridge window [mem 0xfdb00000-0xfdbfffff]
Jun  5 20:37:45 hermes kernel: [    0.153744] pci 0000:00:1c.5:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153750] pci 0000:00:1e.0: PCI bridge to [bus 06]
Jun  5 20:37:45 hermes kernel: [    0.153752] pci 0000:00:1e.0:   bridge window [io  0x9000-0x9fff]
Jun  5 20:37:45 hermes kernel: [    0.153757] pci 0000:00:1e.0:   bridge window [mem 0xfd800000-0xfd8fffff]
Jun  5 20:37:45 hermes kernel: [    0.153761] pci 0000:00:1e.0:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153767] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
Jun  5 20:37:45 hermes kernel: [    0.153769] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
Jun  5 20:37:45 hermes kernel: [    0.153772] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Jun  5 20:37:45 hermes kernel: [    0.153774] pci_bus 0000:01: resource 1 [mem 0xfb000000-0xfcffffff]
Jun  5 20:37:45 hermes kernel: [    0.153776] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xcfffffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153779] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
Jun  5 20:37:45 hermes kernel: [    0.153781] pci_bus 0000:02: resource 1 [mem 0xfd900000-0xfd9fffff]
Jun  5 20:37:45 hermes kernel: [    0.153783] pci_bus 0000:02: resource 2 [mem 0xfd600000-0xfd6fffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153786] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
Jun  5 20:37:45 hermes kernel: [    0.153788] pci_bus 0000:03: resource 1 [mem 0xfd500000-0xfd5fffff]
Jun  5 20:37:45 hermes kernel: [    0.153790] pci_bus 0000:03: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153792] pci_bus 0000:04: resource 0 [io  0x8000-0x8fff]
Jun  5 20:37:45 hermes kernel: [    0.153795] pci_bus 0000:04: resource 1 [mem 0xfdd00000-0xfddfffff]
Jun  5 20:37:45 hermes kernel: [    0.153797] pci_bus 0000:04: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153799] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
Jun  5 20:37:45 hermes kernel: [    0.153801] pci_bus 0000:05: resource 1 [mem 0xfdb00000-0xfdbfffff]
Jun  5 20:37:45 hermes kernel: [    0.153804] pci_bus 0000:05: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153806] pci_bus 0000:06: resource 0 [io  0x9000-0x9fff]
Jun  5 20:37:45 hermes kernel: [    0.153808] pci_bus 0000:06: resource 1 [mem 0xfd800000-0xfd8fffff]
Jun  5 20:37:45 hermes kernel: [    0.153811] pci_bus 0000:06: resource 2 [mem 0xfd700000-0xfd7fffff 64bit pref]
Jun  5 20:37:45 hermes kernel: [    0.153813] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
Jun  5 20:37:45 hermes kernel: [    0.153815] pci_bus 0000:06: resource 5 [mem 0x00000000-0xfffffffff]
Jun  5 20:37:45 hermes kernel: [    0.153849] NET: Registered protocol family 2
Jun  5 20:37:45 hermes kernel: [    0.154056] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Jun  5 20:37:45 hermes kernel: [    0.154317] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun  5 20:37:45 hermes kernel: [    0.154629] TCP: Hash tables configured (established 65536 bind 65536)
Jun  5 20:37:45 hermes kernel: [    0.154666] TCP: reno registered
Jun  5 20:37:45 hermes kernel: [    0.154680] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jun  5 20:37:45 hermes kernel: [    0.154734] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jun  5 20:37:45 hermes kernel: [    0.154847] NET: Registered protocol family 1
Jun  5 20:37:45 hermes kernel: [    0.155775] pci 0000:01:00.0: Boot video device
Jun  5 20:37:45 hermes kernel: [    0.155804] PCI: CLS 64 bytes, default 64
Jun  5 20:37:45 hermes kernel: [    0.155891] Trying to unpack rootfs image as initramfs...
Jun  5 20:37:45 hermes kernel: [    0.486267] Freeing initrd memory: 18644K (ffff880035b86000 - ffff880036dbb000)
Jun  5 20:37:45 hermes kernel: [    0.486275] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jun  5 20:37:45 hermes kernel: [    0.486278] software IO TLB [mem 0xabee0000-0xafee0000] (64MB) mapped at [ffff8800abee0000-ffff8800afedffff]
Jun  5 20:37:45 hermes kernel: [    0.486529] microcode: CPU0 sig=0x6f6, pf=0x1, revision=0xc6
Jun  5 20:37:45 hermes kernel: [    0.486539] microcode: CPU1 sig=0x6f6, pf=0x1, revision=0xc6
Jun  5 20:37:45 hermes kernel: [    0.486613] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jun  5 20:37:45 hermes kernel: [    0.486615] Scanning for low memory corruption every 60 seconds
Jun  5 20:37:45 hermes kernel: [    0.486887] Initialise system trusted keyring
Jun  5 20:37:45 hermes kernel: [    0.486942] audit: initializing netlink socket (disabled)
Jun  5 20:37:45 hermes kernel: [    0.486955] type=2000 audit(1401997060.483:1): initialized
Jun  5 20:37:45 hermes kernel: [    0.515168] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun  5 20:37:45 hermes kernel: [    0.516944] VFS: Disk quotas dquot_6.5.2
Jun  5 20:37:45 hermes kernel: [    0.516991] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun  5 20:37:45 hermes kernel: [    0.517506] fuse init (API version 7.22)
Jun  5 20:37:45 hermes kernel: [    0.517594] msgmni has been set to 15962
Jun  5 20:37:45 hermes kernel: [    0.517647] Key type big_key registered
Jun  5 20:37:45 hermes kernel: [    0.518127] Key type asymmetric registered
Jun  5 20:37:45 hermes kernel: [    0.518129] Asymmetric key parser 'x509' registered
Jun  5 20:37:45 hermes kernel: [    0.518165] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jun  5 20:37:45 hermes kernel: [    0.518203] io scheduler noop registered
Jun  5 20:37:45 hermes kernel: [    0.518206] io scheduler deadline registered (default)
Jun  5 20:37:45 hermes kernel: [    0.518232] io scheduler cfq registered
Jun  5 20:37:45 hermes kernel: [    0.518440] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jun  5 20:37:45 hermes kernel: [    0.518556] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Jun  5 20:37:45 hermes kernel: [    0.518675] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Jun  5 20:37:45 hermes kernel: [    0.518795] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
Jun  5 20:37:45 hermes kernel: [    0.518916] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
Jun  5 20:37:45 hermes kernel: [    0.518989] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  5 20:37:45 hermes kernel: [    0.519005] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun  5 20:37:45 hermes kernel: [    0.519060] intel_idle: does not run on family 6 model 15
Jun  5 20:37:45 hermes kernel: [    0.519066] ipmi message handler version 39.2
Jun  5 20:37:45 hermes kernel: [    0.519122] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun  5 20:37:45 hermes kernel: [    0.519126] ACPI: Power Button [PWRB]
Jun  5 20:37:45 hermes kernel: [    0.519184] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun  5 20:37:45 hermes kernel: [    0.519187] ACPI: Power Button [PWRF]
Jun  5 20:37:45 hermes kernel: [    0.522277] thermal LNXTHERM:00: registered as thermal_zone0
Jun  5 20:37:45 hermes kernel: [    0.522280] ACPI: Thermal Zone [THRM] (20 C)
Jun  5 20:37:45 hermes kernel: [    0.522305] GHES: HEST is not enabled!
Jun  5 20:37:45 hermes kernel: [    0.522404] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun  5 20:37:45 hermes kernel: [    0.523956] Linux agpgart interface v0.103
Jun  5 20:37:45 hermes kernel: [    0.525576] brd: module loaded
Jun  5 20:37:45 hermes kernel: [    0.526354] loop: module loaded
Jun  5 20:37:45 hermes kernel: [    0.526469] ata_piix 0000:00:1f.2: version 2.13
Jun  5 20:37:45 hermes kernel: [    0.526544] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Jun  5 20:37:45 hermes kernel: [    0.527168] scsi0 : ata_piix
Jun  5 20:37:45 hermes kernel: [    0.527248] scsi1 : ata_piix
Jun  5 20:37:45 hermes kernel: [    0.527287] ata1: SATA max UDMA/133 cmd 0xfa00 ctl 0xf900 bmdma 0xf600 irq 19
Jun  5 20:37:45 hermes kernel: [    0.527291] ata2: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf608 irq 19
Jun  5 20:37:45 hermes kernel: [    0.527365] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Jun  5 20:37:45 hermes kernel: [    0.527736] scsi2 : ata_piix
Jun  5 20:37:45 hermes kernel: [    0.527805] scsi3 : ata_piix
Jun  5 20:37:45 hermes kernel: [    0.527843] ata3: SATA max UDMA/133 cmd 0xf300 ctl 0xf200 bmdma 0xef00 irq 19
Jun  5 20:37:45 hermes kernel: [    0.527846] ata4: SATA max UDMA/133 cmd 0xf100 ctl 0xf000 bmdma 0xef08 irq 19
Jun  5 20:37:45 hermes kernel: [    0.528223] libphy: Fixed MDIO Bus: probed
Jun  5 20:37:45 hermes kernel: [    0.528319] tun: Universal TUN/TAP device driver, 1.6
Jun  5 20:37:45 hermes kernel: [    0.528320] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun  5 20:37:45 hermes kernel: [    0.528368] PPP generic driver version 2.4.2
Jun  5 20:37:45 hermes kernel: [    0.528417] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun  5 20:37:45 hermes kernel: [    0.528422] ehci-pci: EHCI PCI platform driver
Jun  5 20:37:45 hermes kernel: [    0.528529] ehci-pci 0000:00:1a.7: EHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.528536] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jun  5 20:37:45 hermes kernel: [    0.532444] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
Jun  5 20:37:45 hermes kernel: [    0.532472] ehci-pci 0000:00:1a.7: irq 18, io mem 0xfdfff000
Jun  5 20:37:45 hermes kernel: [    0.544044] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jun  5 20:37:45 hermes kernel: [    0.544117] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jun  5 20:37:45 hermes kernel: [    0.544121] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun  5 20:37:45 hermes kernel: [    0.544124] usb usb1: Product: EHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.544128] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
Jun  5 20:37:45 hermes kernel: [    0.544131] usb usb1: SerialNumber: 0000:00:1a.7
Jun  5 20:37:45 hermes kernel: [    0.544284] hub 1-0:1.0: USB hub found
Jun  5 20:37:45 hermes kernel: [    0.544294] hub 1-0:1.0: 4 ports detected
Jun  5 20:37:45 hermes kernel: [    0.544487] ehci-pci 0000:00:1d.7: EHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.544493] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jun  5 20:37:45 hermes kernel: [    0.548407] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
Jun  5 20:37:45 hermes kernel: [    0.548430] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfdffe000
Jun  5 20:37:45 hermes kernel: [    0.560035] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jun  5 20:37:45 hermes kernel: [    0.560099] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jun  5 20:37:45 hermes kernel: [    0.560103] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun  5 20:37:45 hermes kernel: [    0.560107] usb usb2: Product: EHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.560110] usb usb2: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
Jun  5 20:37:45 hermes kernel: [    0.560113] usb usb2: SerialNumber: 0000:00:1d.7
Jun  5 20:37:45 hermes kernel: [    0.560263] hub 2-0:1.0: USB hub found
Jun  5 20:37:45 hermes kernel: [    0.560272] hub 2-0:1.0: 6 ports detected
Jun  5 20:37:45 hermes kernel: [    0.560415] ehci-platform: EHCI generic platform driver
Jun  5 20:37:45 hermes kernel: [    0.560427] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun  5 20:37:45 hermes kernel: [    0.560428] ohci-pci: OHCI PCI platform driver
Jun  5 20:37:45 hermes kernel: [    0.560440] ohci-platform: OHCI generic platform driver
Jun  5 20:37:45 hermes kernel: [    0.560447] uhci_hcd: USB Universal Host Controller Interface driver
Jun  5 20:37:45 hermes kernel: [    0.560522] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.560528] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jun  5 20:37:45 hermes kernel: [    0.560559] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
Jun  5 20:37:45 hermes kernel: [    0.560613] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jun  5 20:37:45 hermes kernel: [    0.560616] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun  5 20:37:45 hermes kernel: [    0.560618] usb usb3: Product: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.560620] usb usb3: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
Jun  5 20:37:45 hermes kernel: [    0.560622] usb usb3: SerialNumber: 0000:00:1a.0
Jun  5 20:37:45 hermes kernel: [    0.560715] hub 3-0:1.0: USB hub found
Jun  5 20:37:45 hermes kernel: [    0.560725] hub 3-0:1.0: 2 ports detected
Jun  5 20:37:45 hermes kernel: [    0.560885] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.560891] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jun  5 20:37:45 hermes kernel: [    0.560922] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
Jun  5 20:37:45 hermes kernel: [    0.560973] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jun  5 20:37:45 hermes kernel: [    0.560976] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun  5 20:37:45 hermes kernel: [    0.560978] usb usb4: Product: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.560980] usb usb4: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
Jun  5 20:37:45 hermes kernel: [    0.560982] usb usb4: SerialNumber: 0000:00:1a.1
Jun  5 20:37:45 hermes kernel: [    0.561076] hub 4-0:1.0: USB hub found
Jun  5 20:37:45 hermes kernel: [    0.561084] hub 4-0:1.0: 2 ports detected
Jun  5 20:37:45 hermes kernel: [    0.561230] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.561236] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Jun  5 20:37:45 hermes kernel: [    0.561257] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fd00
Jun  5 20:37:45 hermes kernel: [    0.561310] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jun  5 20:37:45 hermes kernel: [    0.561312] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun  5 20:37:45 hermes kernel: [    0.561315] usb usb5: Product: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.561317] usb usb5: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
Jun  5 20:37:45 hermes kernel: [    0.561319] usb usb5: SerialNumber: 0000:00:1d.0
Jun  5 20:37:45 hermes kernel: [    0.561409] hub 5-0:1.0: USB hub found
Jun  5 20:37:45 hermes kernel: [    0.561418] hub 5-0:1.0: 2 ports detected
Jun  5 20:37:45 hermes kernel: [    0.561567] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.561573] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Jun  5 20:37:45 hermes kernel: [    0.561594] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fc00
Jun  5 20:37:45 hermes kernel: [    0.561645] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Jun  5 20:37:45 hermes kernel: [    0.561647] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun  5 20:37:45 hermes kernel: [    0.561649] usb usb6: Product: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.561652] usb usb6: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
Jun  5 20:37:45 hermes kernel: [    0.561654] usb usb6: SerialNumber: 0000:00:1d.1
Jun  5 20:37:45 hermes kernel: [    0.561744] hub 6-0:1.0: USB hub found
Jun  5 20:37:45 hermes kernel: [    0.561753] hub 6-0:1.0: 2 ports detected
Jun  5 20:37:45 hermes kernel: [    0.561899] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.561905] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Jun  5 20:37:45 hermes kernel: [    0.561926] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fb00
Jun  5 20:37:45 hermes kernel: [    0.561976] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Jun  5 20:37:45 hermes kernel: [    0.561979] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jun  5 20:37:45 hermes kernel: [    0.561981] usb usb7: Product: UHCI Host Controller
Jun  5 20:37:45 hermes kernel: [    0.561983] usb usb7: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
Jun  5 20:37:45 hermes kernel: [    0.561985] usb usb7: SerialNumber: 0000:00:1d.2
Jun  5 20:37:45 hermes kernel: [    0.562075] hub 7-0:1.0: USB hub found
Jun  5 20:37:45 hermes kernel: [    0.562084] hub 7-0:1.0: 2 ports detected
Jun  5 20:37:45 hermes kernel: [    0.562227] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jun  5 20:37:45 hermes kernel: [    0.562229] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jun  5 20:37:45 hermes kernel: [    0.562826] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  5 20:37:45 hermes kernel: [    0.562930] mousedev: PS/2 mouse device common for all mice
Jun  5 20:37:45 hermes kernel: [    0.563074] rtc_cmos 00:02: RTC can wake from S4
Jun  5 20:37:45 hermes kernel: [    0.583051] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jun  5 20:37:45 hermes kernel: [    0.583073] rtc_cmos 00:02: alarms up to one month, 242 bytes nvram
Jun  5 20:37:45 hermes kernel: [    0.583138] device-mapper: uevent: version 1.0.3
Jun  5 20:37:45 hermes kernel: [    0.583203] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Jun  5 20:37:45 hermes kernel: [    0.583210] ledtrig-cpu: registered to indicate activity on CPUs
Jun  5 20:37:45 hermes kernel: [    0.583310] TCP: cubic registered
Jun  5 20:37:45 hermes kernel: [    0.583414] NET: Registered protocol family 10
Jun  5 20:37:45 hermes kernel: [    0.583594] NET: Registered protocol family 17
Jun  5 20:37:45 hermes kernel: [    0.583604] Key type dns_resolver registered
Jun  5 20:37:45 hermes kernel: [    0.583826] Loading compiled-in X.509 certificates
Jun  5 20:37:45 hermes kernel: [    0.584934] Loaded X.509 cert 'Magrathea: Glacier signing key: 69b0d0a79b85d90621706e8d06604d730b359fc0'
Jun  5 20:37:45 hermes kernel: [    0.584947] registered taskstats version 1
Jun  5 20:37:45 hermes kernel: [    0.588098] Key type trusted registered
Jun  5 20:37:45 hermes kernel: [    0.590520] Key type encrypted registered
Jun  5 20:37:45 hermes kernel: [    0.592917] AppArmor: AppArmor sha1 policy hashing enabled
Jun  5 20:37:45 hermes kernel: [    0.592920] IMA: No TPM chip found, activating TPM-bypass!
Jun  5 20:37:45 hermes kernel: [    0.593268] regulator-dummy: disabling
Jun  5 20:37:45 hermes kernel: [    0.593317]   Magic number: 2:970:646
Jun  5 20:37:45 hermes kernel: [    0.593333] scsi_host host0: hash matches
Jun  5 20:37:45 hermes kernel: [    0.593335] scsi host0: hash matches
Jun  5 20:37:45 hermes kernel: [    0.593431] rtc_cmos 00:02: setting system clock to 2014-06-05 19:37:41 UTC (1401997061)
Jun  5 20:37:45 hermes kernel: [    0.593693] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  5 20:37:45 hermes kernel: [    0.593695] EDD information not available.
Jun  5 20:37:45 hermes kernel: [    0.593724] PM: Hibernation image not present or could not be loaded.
Jun  5 20:37:45 hermes kernel: [    0.601456] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Jun  5 20:37:45 hermes kernel: [    1.000106] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun  5 20:37:45 hermes kernel: [    1.049446] ata3.00: ATA-7: ST3250820AS, 3.AAC, max UDMA/133
Jun  5 20:37:45 hermes kernel: [    1.049451] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun  5 20:37:45 hermes kernel: [    1.116098] ata3.00: configured for UDMA/133
Jun  5 20:37:45 hermes kernel: [    1.320090] ata1.00: SATA link down (SStatus 0 SControl 300)
Jun  5 20:37:45 hermes kernel: [    1.320102] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun  5 20:37:45 hermes kernel: [    1.330806] ata2.00: SATA link down (SStatus 0 SControl 300)
Jun  5 20:37:45 hermes kernel: [    1.330817] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  5 20:37:45 hermes kernel: [    1.342483] ata1.01: ATA-7: Maxtor 6L200M0, BANC1E00, max UDMA/133
Jun  5 20:37:45 hermes kernel: [    1.342486] ata1.01: 398297088 sectors, multi 0: LBA48 NCQ (not used)
Jun  5 20:37:45 hermes kernel: [    1.357144] ata1.01: configured for UDMA/133
Jun  5 20:37:45 hermes kernel: [    1.357308] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6L200M0   BANC PQ: 0 ANSI: 5
Jun  5 20:37:45 hermes kernel: [    1.357469] sd 0:0:1:0: [sda] 398297088 512-byte logical blocks: (203 GB/189 GiB)
Jun  5 20:37:45 hermes kernel: [    1.357470] sd 0:0:1:0: Attached scsi generic sg0 type 0
Jun  5 20:37:45 hermes kernel: [    1.357555] sd 0:0:1:0: [sda] Write Protect is off
Jun  5 20:37:45 hermes kernel: [    1.357558] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
Jun  5 20:37:45 hermes kernel: [    1.357602] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  5 20:37:45 hermes kernel: [    1.368875] ata2.01: ATA-8: WDC WD5000AAKS-22YGA0, 12.01C02, max UDMA/133
Jun  5 20:37:45 hermes kernel: [    1.368879] ata2.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun  5 20:37:45 hermes kernel: [    1.377775]  sda: sda1
Jun  5 20:37:45 hermes kernel: [    1.378101] sd 0:0:1:0: [sda] Attached SCSI disk
Jun  5 20:37:45 hermes kernel: [    1.384538] ata2.01: configured for UDMA/133
Jun  5 20:37:45 hermes kernel: [    1.384660] scsi 1:0:1:0: Direct-Access     ATA      WDC WD5000AAKS-2 12.0 PQ: 0 ANSI: 5
Jun  5 20:37:45 hermes kernel: [    1.384802] sd 1:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jun  5 20:37:45 hermes kernel: [    1.384820] sd 1:0:1:0: Attached scsi generic sg1 type 0
Jun  5 20:37:45 hermes kernel: [    1.384867] sd 1:0:1:0: [sdb] Write Protect is off
Jun  5 20:37:45 hermes kernel: [    1.384870] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jun  5 20:37:45 hermes kernel: [    1.384898] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  5 20:37:45 hermes kernel: [    1.384922] scsi 2:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
Jun  5 20:37:45 hermes kernel: [    1.385023] sd 2:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jun  5 20:37:45 hermes kernel: [    1.385046] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun  5 20:37:45 hermes kernel: [    1.385133] sd 2:0:0:0: [sdc] Write Protect is off
Jun  5 20:37:45 hermes kernel: [    1.385136] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jun  5 20:37:45 hermes kernel: [    1.385158] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  5 20:37:45 hermes kernel: [    1.390137]  sdb: sdb1
Jun  5 20:37:45 hermes kernel: [    1.390443] sd 1:0:1:0: [sdb] Attached SCSI disk
Jun  5 20:37:45 hermes kernel: [    1.405676]  sdc: sdc1
Jun  5 20:37:45 hermes kernel: [    1.405910] sd 2:0:0:0: [sdc] Attached SCSI disk
Jun  5 20:37:45 hermes kernel: [    1.484047] tsc: Refined TSC clocksource calibration: 2448.000 MHz
Jun  5 20:37:45 hermes kernel: [    1.560077] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun  5 20:37:45 hermes kernel: [    1.568336] ata4.00: ATA-7: Maxtor 6Y250M0, YAR51FW0, max UDMA/133
Jun  5 20:37:45 hermes kernel: [    1.568340] ata4.00: 490234752 sectors, multi 0: LBA48 
Jun  5 20:37:45 hermes kernel: [    1.584348] ata4.00: configured for UDMA/133
Jun  5 20:37:45 hermes kernel: [    1.584472] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6Y250M0   YAR5 PQ: 0 ANSI: 5
Jun  5 20:37:45 hermes kernel: [    1.584610] sd 3:0:0:0: [sdd] 490234752 512-byte logical blocks: (251 GB/233 GiB)
Jun  5 20:37:45 hermes kernel: [    1.584638] sd 3:0:0:0: Attached scsi generic sg3 type 0
Jun  5 20:37:45 hermes kernel: [    1.584680] sd 3:0:0:0: [sdd] Write Protect is off
Jun  5 20:37:45 hermes kernel: [    1.584684] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Jun  5 20:37:45 hermes kernel: [    1.584715] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  5 20:37:45 hermes kernel: [    1.591096]  sdd: sdd1
Jun  5 20:37:45 hermes kernel: [    1.591330] sd 3:0:0:0: [sdd] Attached SCSI disk
Jun  5 20:37:45 hermes kernel: [    1.592859] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
Jun  5 20:37:45 hermes kernel: [    1.592861] Write protecting the kernel read-only data: 12288k
Jun  5 20:37:45 hermes kernel: [    1.595425] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
Jun  5 20:37:45 hermes kernel: [    1.597501] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
Jun  5 20:37:45 hermes kernel: [    1.640259] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun  5 20:37:45 hermes kernel: [    1.640272] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
Jun  5 20:37:45 hermes kernel: [    1.640487] r8169 0000:03:00.0: irq 45 for MSI/MSI-X
Jun  5 20:37:45 hermes kernel: [    1.640651] r8169 0000:03:00.0 eth0: RTL8168b/8111b at 0xffffc90010e24000, 00:50:8d:93:27:fa, XID 10000000 IRQ 45
Jun  5 20:37:45 hermes kernel: [    1.640654] r8169 0000:03:00.0 eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
Jun  5 20:37:45 hermes kernel: [    1.640894] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun  5 20:37:45 hermes kernel: [    1.640903] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
Jun  5 20:37:45 hermes kernel: [    1.641090] r8169 0000:04:00.0: irq 46 for MSI/MSI-X
Jun  5 20:37:45 hermes kernel: [    1.641222] r8169 0000:04:00.0 eth1: RTL8168b/8111b at 0xffffc90010e26000, 00:50:8d:93:27:fb, XID 10000000 IRQ 46
Jun  5 20:37:45 hermes kernel: [    1.641225] r8169 0000:04:00.0 eth1: jumbo features [frames: 4080 bytes, tx checksumming: ko]
Jun  5 20:37:45 hermes kernel: [    1.651165] scsi4 : pata_jmicron
Jun  5 20:37:45 hermes kernel: [    1.652619] scsi5 : pata_jmicron
Jun  5 20:37:45 hermes kernel: [    1.652666] ata5: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 18
Jun  5 20:37:45 hermes kernel: [    1.652668] ata6: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 18
Jun  5 20:37:45 hermes kernel: [    1.652709] ahci 0000:05:00.0: version 3.0
Jun  5 20:37:45 hermes kernel: [    1.668436] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Jun  5 20:37:45 hermes kernel: [    1.668441] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Jun  5 20:37:45 hermes kernel: [    1.669611] scsi6 : ahci
Jun  5 20:37:45 hermes kernel: [    1.669764] scsi7 : ahci
Jun  5 20:37:45 hermes kernel: [    1.669810] ata7: SATA max UDMA/133 abar m8192@0xfdbfe000 port 0xfdbfe100 irq 17
Jun  5 20:37:45 hermes kernel: [    1.669814] ata8: SATA max UDMA/133 abar m8192@0xfdbfe000 port 0xfdbfe180 irq 17
Jun  5 20:37:45 hermes kernel: [    1.720128] firewire_ohci 0000:06:02.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
Jun  5 20:37:45 hermes kernel: [    1.988062] ata7: SATA link down (SStatus 0 SControl 300)
Jun  5 20:37:45 hermes kernel: [    2.160063] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  5 20:37:45 hermes kernel: [    2.160281] ata8.00: ATA-8: PLEXTOR PX-128M5S, 1.05, max UDMA/133
Jun  5 20:37:45 hermes kernel: [    2.160284] ata8.00: 250069680 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Jun  5 20:37:45 hermes kernel: [    2.160666] ata8.00: configured for UDMA/133
Jun  5 20:37:45 hermes kernel: [    2.160824] scsi 7:0:0:0: Direct-Access     ATA      PLEXTOR PX-128M5 1.05 PQ: 0 ANSI: 5
Jun  5 20:37:45 hermes kernel: [    2.160962] sd 7:0:0:0: [sde] 250069680 512-byte logical blocks: (128 GB/119 GiB)
Jun  5 20:37:45 hermes kernel: [    2.160986] sd 7:0:0:0: Attached scsi generic sg4 type 0
Jun  5 20:37:45 hermes kernel: [    2.161060] sd 7:0:0:0: [sde] Write Protect is off
Jun  5 20:37:45 hermes kernel: [    2.161063] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
Jun  5 20:37:45 hermes kernel: [    2.161095] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  5 20:37:45 hermes kernel: [    2.161492] random: nonblocking pool is initialized
Jun  5 20:37:45 hermes kernel: [    2.161670]  sde: sde1 sde2 < sde5 >
Jun  5 20:37:45 hermes kernel: [    2.162116] sd 7:0:0:0: [sde] Attached SCSI disk
Jun  5 20:37:45 hermes kernel: [    2.201244] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
Jun  5 20:37:45 hermes kernel: [    2.220212] firewire_core 0000:06:02.0: created device fw0: GUID 00508d000090af3d, S400
Jun  5 20:37:45 hermes kernel: [    2.491010] Switched to clocksource tsc
Jun  5 20:37:45 hermes kernel: [    2.509901] Adding 5240828k swap on /dev/sde5.  Priority:-1 extents:1 across:5240828k SSFS
Jun  5 20:37:45 hermes kernel: [    2.572572] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  5 20:37:45 hermes kernel: [    2.572580] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  5 20:37:45 hermes kernel: [    2.701623] EXT4-fs (sde1): re-mounted. Opts: errors=remount-ro
Jun  5 20:37:45 hermes kernel: [    2.810169] lp: driver loaded but no devices found
Jun  5 20:37:45 hermes kernel: [    2.843415] ppdev: user-space parallel port driver
Jun  5 20:37:45 hermes kernel: [    2.918881] [drm] Initialized drm 1.1.0 20060810
Jun  5 20:37:45 hermes kernel: [    3.019456] type=1400 audit(1401997063.921:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=404 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.019464] type=1400 audit(1401997063.921:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=404 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.019470] type=1400 audit(1401997063.921:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=404 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.020050] type=1400 audit(1401997063.925:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=398 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.020057] type=1400 audit(1401997063.925:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=398 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.020062] type=1400 audit(1401997063.925:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=398 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.020516] type=1400 audit(1401997063.925:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=398 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.020521] type=1400 audit(1401997063.925:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=398 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.020739] type=1400 audit(1401997063.925:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=398 comm="apparmor_parser"
Jun  5 20:37:45 hermes kernel: [    3.109482] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PM2S 1 (20131115/utaddress-251)
Jun  5 20:37:45 hermes kernel: [    3.109489] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun  5 20:37:45 hermes kernel: [    3.109493] ACPI Warning: 0x00000000000004b0-0x00000000000004bf SystemIO conflicts with Region \GPO2 1 (20131115/utaddress-251)
Jun  5 20:37:45 hermes kernel: [    3.109497] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun  5 20:37:45 hermes kernel: [    3.109499] ACPI Warning: 0x0000000000000480-0x00000000000004af SystemIO conflicts with Region \GPO_ 1 (20131115/utaddress-251)
Jun  5 20:37:45 hermes kernel: [    3.109502] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun  5 20:37:45 hermes kernel: [    3.109504] lpc_ich: Resource conflict(s) found affecting gpio_ich
Jun  5 20:37:45 hermes kernel: [    3.164872] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
Jun  5 20:37:45 hermes kernel: [    3.165100] cfg80211: Calling CRDA to update world regulatory domain
Jun  5 20:37:45 hermes kernel: [    3.175045] nvidia: module license 'NVIDIA' taints kernel.
Jun  5 20:37:45 hermes kernel: [    3.175049] Disabling lock debugging due to kernel taint
Jun  5 20:37:45 hermes kernel: [    3.194590] SKU: Nid=0x1d sku_cfg=0x4014a601
Jun  5 20:37:45 hermes kernel: [    3.194593] SKU: port_connectivity=0x1
Jun  5 20:37:45 hermes kernel: [    3.194594] SKU: enable_pcbeep=0x1
Jun  5 20:37:45 hermes kernel: [    3.194596] SKU: check_sum=0x00000004
Jun  5 20:37:45 hermes kernel: [    3.194597] SKU: customization=0x000000a6
Jun  5 20:37:45 hermes kernel: [    3.194598] SKU: external_amp=0x0
Jun  5 20:37:45 hermes kernel: [    3.194599] SKU: platform_type=0x0
Jun  5 20:37:45 hermes kernel: [    3.194601] SKU: swap=0x0
Jun  5 20:37:45 hermes kernel: [    3.194602] SKU: override=0x1
Jun  5 20:37:45 hermes kernel: [    3.195069] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
Jun  5 20:37:45 hermes kernel: [    3.195072]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jun  5 20:37:45 hermes kernel: [    3.195074]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Jun  5 20:37:45 hermes kernel: [    3.195075]    mono: mono_out=0x0
Jun  5 20:37:45 hermes kernel: [    3.195077]    dig-out=0x1e/0x0
Jun  5 20:37:45 hermes kernel: [    3.195078]    inputs:
Jun  5 20:37:45 hermes kernel: [    3.195080]      Front Mic=0x19
Jun  5 20:37:45 hermes kernel: [    3.195081]      Rear Mic=0x18
Jun  5 20:37:45 hermes kernel: [    3.195083]      Line=0x1a
Jun  5 20:37:45 hermes kernel: [    3.195084]    dig-in=0x1f
Jun  5 20:37:45 hermes kernel: [    3.195086] realtek: No valid SSID, checking pincfg 0x4014a601 for NID 0x1d
Jun  5 20:37:45 hermes kernel: [    3.195088] realtek: Enabling init ASM_ID=0xa601 CODEC_ID=10ec0882
Jun  5 20:37:45 hermes kernel: [    3.220736] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
Jun  5 20:37:45 hermes kernel: [    3.222963] saa7146: register extension 'budget_ci dvb'
Jun  5 20:37:45 hermes kernel: [    3.223152] saa7146: found saa7146 @ mem ffffc90010e4e000 (revision 1, irq 21) (0x13c2,0x100f)
Jun  5 20:37:45 hermes kernel: [    3.223156] saa7146 (0): dma buffer size 192512
Jun  5 20:37:45 hermes kernel: [    3.223158] DVB: registering new adapter (TT-Budget/WinTV-NOVA-CI PCI)
Jun  5 20:37:45 hermes kernel: [    3.229394] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Jun  5 20:37:45 hermes kernel: [    3.231302] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
Jun  5 20:37:45 hermes kernel: [    3.231319] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.38  Wed Jan  8 19:32:30 PST 2014
Jun  5 20:37:45 hermes kernel: [    3.244706] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jun  5 20:37:45 hermes kernel: [    3.244786] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jun  5 20:37:45 hermes kernel: [    3.244851] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Jun  5 20:37:45 hermes kernel: [    3.244918] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Jun  5 20:37:45 hermes kernel: [    3.244981] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
Jun  5 20:37:45 hermes kernel: [    3.245046] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Jun  5 20:37:45 hermes kernel: [    3.245117] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
Jun  5 20:37:45 hermes kernel: [    3.245180] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
Jun  5 20:37:45 hermes kernel: [    3.245955] hda_intel: Disabling MSI
Jun  5 20:37:45 hermes kernel: [    3.245967] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
Jun  5 20:37:45 hermes kernel: [    3.246360] hda-intel 0000:01:00.1: Disabling 64bit DMA
Jun  5 20:37:45 hermes kernel: [    3.249983] hda-intel 0000:01:00.1: Enable delay in RIRB handling
Jun  5 20:37:45 hermes kernel: [    3.258731] adapter has MAC addr = 00:d0:5c:22:35:03
Jun  5 20:37:45 hermes kernel: [    3.285508] coretemp coretemp.0: Using relative temperature scale!
Jun  5 20:37:45 hermes kernel: [    3.285519] coretemp coretemp.0: Using relative temperature scale!
Jun  5 20:37:45 hermes kernel: [    3.296575] Registered IR keymap rc-hauppauge
Jun  5 20:37:45 hermes kernel: [    3.297153] input: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:1e.0/0000:06:05.0/rc/rc0/input11
Jun  5 20:37:45 hermes kernel: [    3.297205] rc0: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:1e.0/0000:06:05.0/rc/rc0
Jun  5 20:37:45 hermes kernel: [    3.514878] budget_ci dvb 0000:06:05.0: DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
Jun  5 20:37:45 hermes kernel: [    3.772233] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
Jun  5 20:37:45 hermes kernel: [    3.772356] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
Jun  5 20:37:45 hermes kernel: [    3.820572] ath: EEPROM regdomain: 0x809c
Jun  5 20:37:45 hermes kernel: [    3.820573] ath: EEPROM indicates we should expect a country code
Jun  5 20:37:45 hermes kernel: [    3.820574] ath: doing EEPROM country->regdmn map search
Jun  5 20:37:45 hermes kernel: [    3.820575] ath: country maps to regdmn code: 0x52
Jun  5 20:37:45 hermes kernel: [    3.820576] ath: Country alpha2 being used: CN
Jun  5 20:37:45 hermes kernel: [    3.820576] ath: Regpair used: 0x52
Jun  5 20:37:45 hermes kernel: [    3.885070] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jun  5 20:37:45 hermes kernel: [    3.885586] ieee80211 phy0: Atheros AR9287 Rev:2 mem=0xffffc90010fe0000, irq=23
Jun  5 20:37:45 hermes kernel: [    3.887253] cfg80211: World regulatory domain updated:
Jun  5 20:37:45 hermes kernel: [    3.887257] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  5 20:37:45 hermes kernel: [    3.887259] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  5 20:37:45 hermes kernel: [    3.887261] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  5 20:37:45 hermes kernel: [    3.887263] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  5 20:37:45 hermes kernel: [    3.887265] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  5 20:37:45 hermes kernel: [    3.887267] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  5 20:37:45 hermes kernel: [    3.887279] cfg80211: Calling CRDA for country: CN
Jun  5 20:37:45 hermes kernel: [    3.949250] cfg80211: Regulatory domain changed to country: CN
Jun  5 20:37:45 hermes kernel: [    3.949253] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  5 20:37:45 hermes kernel: [    3.949256] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jun  5 20:37:45 hermes kernel: [    3.949258] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
Jun  5 20:37:45 hermes kernel: [    3.949260] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
Jun  5 20:37:45 hermes kernel: [    3.949261] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm)
Jun  5 20:37:45 hermes kernel: [    3.949263] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
Jun  5 20:37:45 hermes kernel: [    4.774664] Bluetooth: Core ver 2.17
Jun  5 20:37:45 hermes kernel: [    4.774687] NET: Registered protocol family 31
Jun  5 20:37:45 hermes kernel: [    4.774689] Bluetooth: HCI device and connection manager initialized
Jun  5 20:37:45 hermes kernel: [    4.775180] Bluetooth: HCI socket layer initialized
Jun  5 20:37:45 hermes kernel: [    4.775184] Bluetooth: L2CAP socket layer initialized
Jun  5 20:37:45 hermes kernel: [    4.775190] Bluetooth: SCO socket layer initialized
Jun  5 20:37:45 hermes kernel: [    4.783328] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun  5 20:37:45 hermes kernel: [    4.783331] Bluetooth: BNEP filters: protocol multicast
Jun  5 20:37:45 hermes kernel: [    4.783341] Bluetooth: BNEP socket layer initialized
Jun  5 20:37:45 hermes kernel: [    4.830513] Bluetooth: RFCOMM TTY layer initialized
Jun  5 20:37:45 hermes kernel: [    4.830526] Bluetooth: RFCOMM socket layer initialized
Jun  5 20:37:45 hermes kernel: [    4.830533] Bluetooth: RFCOMM ver 1.11
Jun  5 20:37:45 hermes avahi-daemon[905]: Found user 'avahi' (UID 110) and group 'avahi' (GID 116).
Jun  5 20:37:45 hermes avahi-daemon[905]: Successfully dropped root privileges.
Jun  5 20:37:45 hermes avahi-daemon[905]: avahi-daemon 0.6.31 starting up.
Jun  5 20:37:45 hermes avahi-daemon[905]: Successfully called chroot().
Jun  5 20:37:45 hermes avahi-daemon[905]: Successfully dropped remaining capabilities.
Jun  5 20:37:45 hermes avahi-daemon[905]: Loading service file /services/udisks.service.
Jun  5 20:37:45 hermes avahi-daemon[905]: Network interface enumeration completed.
Jun  5 20:37:45 hermes avahi-daemon[905]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun  5 20:37:45 hermes avahi-daemon[905]: Server startup complete. Host name is hermes.local. Local service cookie is 3120195430.
Jun  5 20:37:45 hermes avahi-daemon[905]: Service "hermes" (/services/udisks.service) successfully established.
Jun  5 20:37:45 hermes polkitd[892]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jun  5 20:37:45 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: init!
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: update_system_hostname
Jun  5 20:37:45 hermes NetworkManager[878]:       interface-parser: parsing file /etc/network/interfaces
Jun  5 20:37:45 hermes NetworkManager[878]:       interface-parser: finished parsing file /etc/network/interfaces
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPluginIfupdown: management mode: unmanaged
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth0, iface: eth0)
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth1, iface: eth1)
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:06.0/net/wlan0, iface: wlan0)
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:06.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: end _init.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ofono: init!
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ofono: end _init.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> Loaded plugin (null): (null)
Jun  5 20:37:45 hermes NetworkManager[878]:    Ifupdown: get unmanaged devices count: 0
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: (26870544) ... get_connections.
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ifupdown: (26870544) ... get_connections (managed=false): return empty list.
Jun  5 20:37:45 hermes NetworkManager[878]:    keyfile: parsing Wired connection 1 ... 
Jun  5 20:37:45 hermes NetworkManager[878]:    keyfile:     read connection 'Wired connection 1'
Jun  5 20:37:45 hermes NetworkManager[878]:    keyfile: parsing BackdoorTrojanInstaller32 ... 
Jun  5 20:37:45 hermes NetworkManager[878]:    keyfile:     read connection 'BackdoorTrojanInstaller32'
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ofono: (26670528) ... get_connections.
Jun  5 20:37:45 hermes NetworkManager[878]:    SCPlugin-Ofono: (26670528) connections count: 0
Jun  5 20:37:45 hermes NetworkManager[878]:    Ifupdown: get unmanaged devices count: 0
Jun  5 20:37:45 hermes NetworkManager[878]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:06:06.0/ieee80211/phy0/rfkill0) (driver ath9k)
Jun  5 20:37:45 hermes NetworkManager[878]: <info> WiFi disabled by radio killswitch; disabled by state file
Jun  5 20:37:45 hermes NetworkManager[878]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  5 20:37:45 hermes NetworkManager[878]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  5 20:37:45 hermes NetworkManager[878]: <info> Networking is enabled by state file
Jun  5 20:37:45 hermes NetworkManager[878]: <warn> failed to allocate link cache: (-12) Object not found
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth0): carrier is OFF
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth0): bringing up device.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth0): preparing device.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun  5 20:37:45 hermes NetworkManager[878]: <warn> failed to allocate link cache: (-12) Object not found
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth1): carrier is OFF
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 3)
Jun  5 20:37:45 hermes kernel: [    5.037315] r8169 0000:03:00.0 eth0: link down
Jun  5 20:37:45 hermes kernel: [    5.037386] r8169 0000:03:00.0 eth0: link down
Jun  5 20:37:45 hermes kernel: [    5.037388] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  5 20:37:45 hermes kernel: [    5.037897] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth1): bringing up device.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth1): preparing device.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (eth1): deactivating device (reason 'managed') [2]
Jun  5 20:37:45 hermes NetworkManager[878]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/eth1
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (wlan0): using nl80211 for WiFi device control
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (wlan0): driver supports Access Point (AP) mode
Jun  5 20:37:45 hermes kernel: [    5.049321] r8169 0000:04:00.0 eth1: link down
Jun  5 20:37:45 hermes kernel: [    5.049495] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  5 20:37:45 hermes kernel: [    5.050171] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 4)
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (wlan0): bringing up device.
Jun  5 20:37:45 hermes NetworkManager[878]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  5 20:37:45 hermes NetworkManager[878]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun  5 20:37:45 hermes NetworkManager[878]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun  5 20:37:45 hermes NetworkManager[878]: <info> urfkill disappeared from the bus
Jun  5 20:37:45 hermes kernel: [    5.053058] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  5 20:37:45 hermes NetworkManager[878]: <info> ModemManager available in the bus
Jun  5 20:37:46 hermes tvheadend[801]: charset: 138 entries loaded
Jun  5 20:37:46 hermes anacron[1097]: Anacron 2.3 started on 2014-06-05
Jun  5 20:37:46 hermes anacron[1097]: Normal exit (0 jobs run)
Jun  5 20:37:46 hermes acpid: starting up with netlink and the input layer
Jun  5 20:37:46 hermes cron[1020]: (CRON) INFO (pidfile fd = 3)
Jun  5 20:37:46 hermes acpid: 9 rules loaded
Jun  5 20:37:46 hermes acpid: waiting for events: event logging is off
Jun  5 20:37:46 hermes cron[1102]: (CRON) STARTUP (fork ok)
Jun  5 20:37:46 hermes cron[1102]: (CRON) INFO (Running @reboot jobs)
Jun  5 20:37:46 hermes whoopsie[1083]: whoopsie 0.2.24.5 starting up.
Jun  5 20:37:46 hermes whoopsie[1083]: Using lock path: /var/lock/whoopsie/lock
Jun  5 20:37:46 hermes whoopsie[1104]: offline
Jun  5 20:37:46 hermes dbus[774]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jun  5 20:37:46 hermes accounts-daemon[1145]: started daemon version 0.6.35
Jun  5 20:37:46 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jun  5 20:37:46 hermes kernel: [    5.776368] audit_printk_skb: 186 callbacks suppressed
Jun  5 20:37:46 hermes kernel: [    5.776372] type=1400 audit(1401997066.681:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1157 comm="apparmor_parser"
Jun  5 20:37:47 hermes kernel: [    6.186264] nvidia 0000:01:00.0: irq 48 for MSI/MSI-X
Jun  5 20:37:47 hermes tvheadend[801]: linuxdvb: adapter added /dev/dvb/adapter0
Jun  5 20:37:47 hermes kernel: [    6.373355] budget_ci dvb 0000:06:05.0: DVB: adapter 0 frontend 0 frequency 0 out of range (950000..2150000)
Jun  5 20:37:47 hermes tvheadend[801]: upnp: upnp_thread_multicast - cannot join 239.255.255.250 [No such device]
Jun  5 20:37:47 hermes tvheadend[801]: CSA: Using SSE2 128bit parallel descrambling
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module eit created
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module uk_freesat created
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module uk_freeview created
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module viasat_baltic created
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module opentv-ausat created
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module opentv-skyit created
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module opentv-skyuk created
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module pyepg created
Jun  5 20:37:47 hermes tvheadend[801]: epggrab: module xmltv created
Jun  5 20:37:47 hermes acpid: client connected from 1223[0:0]
Jun  5 20:37:47 hermes acpid: 1 client rule loaded
Jun  5 20:37:47 hermes ModemManager[844]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0': not supported by any plugin
Jun  5 20:37:47 hermes ModemManager[844]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0': not supported by any plugin
Jun  5 20:37:47 hermes ModemManager[844]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1e.0/0000:06:06.0': not supported by any plugin
Jun  5 20:37:48 hermes NetworkManager[878]: <info> (eth0): carrier now ON (device state 20)
Jun  5 20:37:48 hermes NetworkManager[878]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun  5 20:37:48 hermes kernel: [    7.894745] r8169 0000:03:00.0 eth0: link up
Jun  5 20:37:48 hermes kernel: [    7.894757] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Auto-activating connection 'Wired connection 1'.
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun  5 20:37:48 hermes NetworkManager[878]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  5 20:37:48 hermes NetworkManager[878]: <info> NetworkManager state is now CONNECTING
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  5 20:37:48 hermes NetworkManager[878]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  5 20:37:48 hermes NetworkManager[878]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  5 20:37:48 hermes NetworkManager[878]: <info> dhclient started with pid 1489
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun  5 20:37:48 hermes NetworkManager[878]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  5 20:37:48 hermes dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jun  5 20:37:48 hermes dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jun  5 20:37:48 hermes dhclient: All rights reserved.
Jun  5 20:37:48 hermes dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jun  5 20:37:48 hermes dhclient: 
Jun  5 20:37:48 hermes NetworkManager[878]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  5 20:37:48 hermes dhclient: Listening on LPF/eth0/00:50:8d:93:27:fa
Jun  5 20:37:48 hermes dhclient: Sending on   LPF/eth0/00:50:8d:93:27:fa
Jun  5 20:37:48 hermes dhclient: Sending on   Socket/fallback
Jun  5 20:37:48 hermes dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67 (xid=0x5792eaa5)
Jun  5 20:37:49 hermes dbus[774]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jun  5 20:37:49 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.UPower'
Jun  5 20:37:49 hermes dbus[774]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jun  5 20:37:49 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jun  5 20:37:49 hermes rtkit-daemon[1686]: Successfully called chroot.
Jun  5 20:37:49 hermes rtkit-daemon[1686]: Successfully dropped privileges.
Jun  5 20:37:49 hermes rtkit-daemon[1686]: Successfully limited resources.
Jun  5 20:37:49 hermes rtkit-daemon[1686]: Running.
Jun  5 20:37:49 hermes rtkit-daemon[1686]: Watchdog thread running.
Jun  5 20:37:49 hermes rtkit-daemon[1686]: Canary thread running.
Jun  5 20:37:49 hermes rtkit-daemon[1686]: Successfully made thread 1680 of process 1680 (n/a) owned by '1000' high priority at nice level -11.
Jun  5 20:37:49 hermes rtkit-daemon[1686]: Supervising 1 threads of 1 processes of 1 users.
Jun  5 20:37:49 hermes dbus[774]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jun  5 20:37:49 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jun  5 20:37:49 hermes avahi-daemon[905]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::250:8dff:fe93:27fa.
Jun  5 20:37:49 hermes avahi-daemon[905]: New relevant interface eth0.IPv6 for mDNS.
Jun  5 20:37:49 hermes avahi-daemon[905]: Registering new address record for fe80::250:8dff:fe93:27fa on eth0.*.
Jun  5 20:37:50 hermes anacron[1824]: Anacron 2.3 started on 2014-06-05
Jun  5 20:37:50 hermes anacron[1824]: Normal exit (0 jobs run)
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Successfully made thread 1850 of process 1680 (n/a) owned by '1000' RT at priority 5.
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Supervising 2 threads of 1 processes of 1 users.
Jun  5 20:37:50 hermes dbus[774]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jun  5 20:37:50 hermes colord: Using config file /etc/colord.conf
Jun  5 20:37:50 hermes colord: Using mapping database file /var/lib/colord/mapping.db
Jun  5 20:37:50 hermes colord: Using device database file /var/lib/colord/storage.db
Jun  5 20:37:50 hermes colord: loaded plugin libcd_plugin_scanner.so
Jun  5 20:37:50 hermes colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jun  5 20:37:50 hermes colord: loaded plugin libcd_plugin_camera.so
Jun  5 20:37:50 hermes colord: Daemon ready for requests
Jun  5 20:37:50 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jun  5 20:37:50 hermes colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Jun  5 20:37:50 hermes colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Jun  5 20:37:50 hermes colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Jun  5 20:37:50 hermes colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Jun  5 20:37:50 hermes colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Jun  5 20:37:50 hermes colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Jun  5 20:37:50 hermes colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Jun  5 20:37:50 hermes colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Successfully made thread 1921 of process 1680 (n/a) owned by '1000' RT at priority 5.
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Supervising 3 threads of 1 processes of 1 users.
Jun  5 20:37:50 hermes colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Successfully made thread 1923 of process 1680 (n/a) owned by '1000' RT at priority 5.
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Supervising 4 threads of 1 processes of 1 users.
Jun  5 20:37:50 hermes colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Jun  5 20:37:50 hermes colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Jun  5 20:37:50 hermes colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Jun  5 20:37:50 hermes colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Successfully made thread 1931 of process 1931 (n/a) owned by '1000' high priority at nice level -11.
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Supervising 5 threads of 2 processes of 1 users.
Jun  5 20:37:50 hermes pulseaudio[1931]: [pulseaudio] pid.c: Daemon already running.
Jun  5 20:37:50 hermes colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Successfully made thread 1937 of process 1937 (n/a) owned by '1000' high priority at nice level -11.
Jun  5 20:37:50 hermes rtkit-daemon[1686]: Supervising 5 threads of 2 processes of 1 users.
Jun  5 20:37:50 hermes pulseaudio[1937]: [pulseaudio] pid.c: Daemon already running.
Jun  5 20:37:50 hermes colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Jun  5 20:37:50 hermes colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Jun  5 20:37:50 hermes colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Jun  5 20:37:50 hermes colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Jun  5 20:37:50 hermes colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Jun  5 20:37:50 hermes dbus[774]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Jun  5 20:37:50 hermes colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Jun  5 20:37:50 hermes colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Jun  5 20:37:50 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.locale1'
Jun  5 20:37:50 hermes colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Jun  5 20:37:50 hermes colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Jun  5 20:37:50 hermes colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Jun  5 20:37:51 hermes colord: Device added: xrandr-Samsung Electric Company-SAMSUNG
Jun  5 20:37:51 hermes colord: Automatic metadata add icc-69beb923fd0899f6d191d345e1a57874 to xrandr-Samsung Electric Company-SAMSUNG
Jun  5 20:37:51 hermes colord: Profile added: icc-69beb923fd0899f6d191d345e1a57874
Jun  5 20:37:51 hermes colord: Automatic metadata add icc-73c36bfa242ba6cc9678aa2b64106f33 to xrandr-Samsung Electric Company-SAMSUNG
Jun  5 20:37:51 hermes colord: Profile added: icc-73c36bfa242ba6cc9678aa2b64106f33
Jun  5 20:37:51 hermes dbus[774]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jun  5 20:37:51 hermes udisksd[2081]: udisks daemon version 2.1.3 starting
Jun  5 20:37:51 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jun  5 20:37:51 hermes udisksd[2081]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jun  5 20:37:51 hermes dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67 (xid=0x5792eaa5)
Jun  5 20:37:52 hermes dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Jun  5 20:37:52 hermes dhclient: bound to 192.168.1.2 -- renewal in 284086 seconds.
Jun  5 20:37:52 hermes NetworkManager[878]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jun  5 20:37:52 hermes NetworkManager[878]: <info>   address 192.168.1.2
Jun  5 20:37:52 hermes NetworkManager[878]: <info>   prefix 24 (255.255.255.0)
Jun  5 20:37:52 hermes NetworkManager[878]: <info>   gateway 192.168.1.1
Jun  5 20:37:52 hermes NetworkManager[878]: <info>   nameserver '194.168.4.100'
Jun  5 20:37:52 hermes NetworkManager[878]: <info>   nameserver '194.168.8.100'
Jun  5 20:37:52 hermes NetworkManager[878]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  5 20:37:52 hermes NetworkManager[878]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun  5 20:37:52 hermes avahi-daemon[905]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Jun  5 20:37:52 hermes avahi-daemon[905]: New relevant interface eth0.IPv4 for mDNS.
Jun  5 20:37:52 hermes avahi-daemon[905]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Jun  5 20:37:53 hermes tvheadend[801]: AVAHI: Service 'Tvheadend' successfully established.
Jun  5 20:37:53 hermes NetworkManager[878]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun  5 20:37:53 hermes NetworkManager[878]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  5 20:37:53 hermes NetworkManager[878]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun  5 20:37:53 hermes NetworkManager[878]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun  5 20:37:53 hermes NetworkManager[878]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun  5 20:37:53 hermes NetworkManager[878]: <info> DNS: starting dnsmasq...
Jun  5 20:37:53 hermes NetworkManager[878]: <warn> dnsmasq not available on the bus, can't update servers.
Jun  5 20:37:53 hermes NetworkManager[878]: <error> [1401997073.663825] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun  5 20:37:53 hermes NetworkManager[878]: <warn> DNS: plugin dnsmasq update failed
Jun  5 20:37:53 hermes NetworkManager[878]: <info> Writing DNS information to /sbin/resolvconf
Jun  5 20:37:53 hermes dnsmasq[2163]: started, version 2.68 cache disabled
Jun  5 20:37:53 hermes dnsmasq[2163]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jun  5 20:37:53 hermes dnsmasq[2163]: DBus support enabled: connected to system bus
Jun  5 20:37:53 hermes dnsmasq[2163]: warning: no upstream servers configured
Jun  5 20:37:53 hermes NetworkManager[878]: <info> Activation (eth0) successful, device activated.
Jun  5 20:37:53 hermes dbus[774]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun  5 20:37:53 hermes NetworkManager[878]: <warn> dnsmasq appeared on DBus: :1.54
Jun  5 20:37:53 hermes dnsmasq[2163]: setting upstream servers from DBus
Jun  5 20:37:53 hermes dnsmasq[2163]: using nameserver 194.168.8.100#53
Jun  5 20:37:53 hermes dnsmasq[2163]: using nameserver 194.168.4.100#53
Jun  5 20:37:53 hermes NetworkManager[878]: <info> Writing DNS information to /sbin/resolvconf
Jun  5 20:37:53 hermes dbus[774]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  5 20:37:53 hermes whoopsie[1104]: message repeated 3 times: [ offline]
Jun  5 20:37:54 hermes whoopsie[1104]: online
Jun  5 20:37:55 hermes NetworkManager[878]: <info> WiFi hardware radio set disabled
Jun  5 20:37:56 hermes nvidia-persistenced: Started (2330)
Jun  5 20:37:59 hermes ntpdate[2250]: step time server 91.189.94.4 offset -0.635396 sec
Jun  5 20:38:08 hermes NetworkManager[878]: <info> (eth0): IP6 addrconf timed out or failed.
Jun  5 20:38:08 hermes NetworkManager[878]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  5 20:38:08 hermes NetworkManager[878]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  5 20:38:08 hermes NetworkManager[878]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  5 20:38:15 hermes kernel: [   35.030383] type=1400 audit(1401997095.296:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2428 comm="apparmor_parser"
Jun  5 20:38:15 hermes kernel: [   35.030393] type=1400 audit(1401997095.296:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2428 comm="apparmor_parser"
Jun  5 20:38:15 hermes kernel: [   35.030829] type=1400 audit(1401997095.296:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2428 comm="apparmor_parser"
Jun  5 20:39:01 hermes CRON[2571]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))

```

---

### Post by computer3 on 2014-06-05
> **ap0ll0uk2 said:**
> Evening All

I've switched on my Ubuntu 14.04 box this evening only to be greeted with a desktop wallpaper and not much else! There's no sidebar, no taskbar, only the wallpaper. 

I can right click on the desktop and am presented with the right click context menu and I can create a new folder. I can browse the folder but there is no window title, no minimise, maximise or close buttons.

I can SSH into the machine, and apps that run from the web server all run fine and are accesible.

Does anyone have any idea what might have caused this, or how I can troubleshoot it please?

I've included below the info from the Syslog:-

I'm having the same problem. I posted in the General Help section and so far the only response I've got was "Have you tried to remove the profile config folder? (rename ./config to ./config_bak or like this)" 

I'm not sure how to do that because I'm new to Linux. I was looking on Youtube for a solution and came across this - [http://www.youtube.com/watch?v=wMTkx8y1K88](http://www.youtube.com/watch?v=wMTkx8y1K88) - I haven't tried it since I'm a Linux noob and don't want to mess things up more by not doing it right.

---

### Post by ap0ll0uk2 on 2014-06-05
> **computer3 said:**
> I'm having the same problem. I posted in the General Help section and so far the only response I've got was "Have you tried to remove the profile config folder? (rename ./config to ./config_bak or like this)" 


I tried renaming the folder at the command line, rebooted and no change.

I then right clicked on the desktop, created a new folder, then browsed to /home/USERNAME/ and Cut the .config folder and pasted it on another drive, the launcher and taskbar came back but then disappeared again after a reboot.

I started watching the video you linked to and the guy starts by talking about nVidia drivers. I 'should' be running the newer official nVidia drivers. Are you?

I SSH'd into the box and ran 'dpkg -l | grep nvidia' which displayed the following:-

That then displayed the following:-

```

rc  nvidia-304                                            304.117-0ubuntu1                                    amd64        NVIDIA legacy binary driver - version 304.117
ii  nvidia-331-updates                                    331.38-0ubuntu7                                     amd64        NVIDIA binary driver - version 331.38
rc  nvidia-libopencl1-304                                 304.117-0ubuntu1                                    amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-libopencl1-331-updates                         331.38-0ubuntu7                                     amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-304                                 304.117-0ubuntu1                                    amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-331-updates                         331.38-0ubuntu7                                     amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver

```

Unfortunately I'm not sure what this should look like, and watch it did look like before I installed the 331 drivers. I haven't done this recently by the way, I installed the new drivers weeks ago and everything has been running fine. I'm not sure if the above suggests that I'm running a mixture of the 304 and 331 drives, hence the problem.

Hopefully someone else will be able to shine some more light on the issue. Failing that I'll have a bit more of a play at the weekend when I have more time.

---

### Post by grahammechanical on 2014-06-05
So, you can right click on the desktop and get a menu. Did you know that you can load system settings from that menu? Just select Change Desktop Background. That will load system settings and the Appearance utility but from there you can get to Software and Updates>Additional Drivers tab and change the video driver.

We can have more than one proprietary video driver downloaded onto the hard disk but only one can be activated at a time. As we activate/install one driver the Additional Drivers utility will de-activate the other one.

Another thing to keep in mind is that at the Grub boot menu we have Advanced Options for Ubuntu. That is a sub-menu. It has a recovery mode option. That will bring us to a recovery menu with an option to Resume. That will load to a desktop using an open source video driver and so bypassing any proprietary video driver that might be causing us trouble,

Regards.

---

### Post by ap0ll0uk2 on 2014-06-06
> **grahammechanical said:**
> So, you can right click on the desktop and get a menu. Did you know that you can load system settings from that menu? Just select Change Desktop Background. That will load system settings and the Appearance utility but from there you can get to Software and Updates>Additional Drivers tab and change the video driver.

We can have more than one proprietary video driver downloaded onto the hard disk but only one can be activated at a time. As we activate/install one driver the Additional Drivers utility will de-activate the other one.

Another thing to keep in mind is that at the Grub boot menu we have Advanced Options for Ubuntu. That is a sub-menu. It has a recovery mode option. That will bring us to a recovery menu with an option to Resume. That will load to a desktop using an open source video driver and so bypassing any proprietary video driver that might be causing us trouble,

Regards.

Many thanks for your suggestions, I wasn't aware that you could actually access 'All Settings' from there despite it starting me in the face :D

I've just tested this and I was using 'nVidia Binary Driver - Version 331.38 from nvidia-331-updates (proprietary)' and I've changed it to 'nVidia Legacy Driver - Version 304.38 from nvidia-331-updates (proprietary)' and also the legacy version > rebooted but still the same issue. 

I've then changed it to the Nouveau driver and the issue persists.

It's also strange that when my machine boots up, sometimes it displays the notification to say I am connected to the LAN via Ethernet which is fine, but then sometimes it says that my wireless is disconnected [which it should be as I disabled it] but then doesn't display the notification to say that the machine is connected to the LAN - it is not on the network at all at this point.

Do you have any other suggestions please?

---

