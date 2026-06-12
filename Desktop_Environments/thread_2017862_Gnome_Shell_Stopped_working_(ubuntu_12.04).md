---
title: "Gnome Shell Stopped working (ubuntu 12.04)"
date: 2012-07-05
forum: Desktop Environments
---

### Post by feliperamirez on 2012-07-05
Hi.

All of a sudden my Gnome 3 stopped working :confused:.  Any help would be more than appreciated

It gives me the following error:

gnome-session[3068]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1

Here my syslog:

```


Jul  5 10:31:52 UBUNTU-Casa rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="680" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jul  5 10:31:54 UBUNTU-Casa kernel: [  619.567951] init: cron main process (998) killed by TERM signal
Jul  5 10:31:57 UBUNTU-Casa kernel: [  622.609441] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Jul  5 10:32:55 UBUNTU-Casa cron[4090]: (CRON) INFO (pidfile fd = 3)
Jul  5 10:32:55 UBUNTU-Casa cron[4091]: (CRON) STARTUP (fork ok)
Jul  5 10:32:55 UBUNTU-Casa cron[4091]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Jul  5 10:33:08 UBUNTU-Casa AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/b28554f40aa0405081c604a2b9530204
Jul  5 10:33:14 UBUNTU-Casa anacron[992]: Job `cron.daily' terminated
Jul  5 10:33:14 UBUNTU-Casa anacron[992]: Normal exit (1 job run)
Jul  5 10:36:25 UBUNTU-Casa AptDaemon: INFO: UpdateCache() was called
Jul  5 10:36:26 UBUNTU-Casa AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/68046e041d964c7a9e122ed6f8db1b49
Jul  5 10:36:26 UBUNTU-Casa AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/68046e041d964c7a9e122ed6f8db1b49
Jul  5 10:36:26 UBUNTU-Casa AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/68046e041d964c7a9e122ed6f8db1b49
Jul  5 10:36:27 UBUNTU-Casa AptDaemon.Worker: INFO: Updating cache
Jul  5 10:36:30 UBUNTU-Casa AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/68046e041d964c7a9e122ed6f8db1b49
Jul  5 10:41:40 UBUNTU-Casa AptDaemon: INFO: Quitting due to inactivity
Jul  5 10:41:40 UBUNTU-Casa AptDaemon: INFO: Quitting was requested
Jul  5 10:45:33 UBUNTU-Casa kernel: [ 1438.829495] EXT4-fs (sda1): Unaligned AIO/DIO on inode 5637238 by VirtualBox; performance will be poor.
Jul  5 11:14:50 UBUNTU-Casa gnome-session[1734]: WARNING: Client '/org/gnome/SessionManager/Client7' failed to reply before timeout
Jul  5 11:14:51 UBUNTU-Casa gnome-session[1734]: WARNING: Client '/org/gnome/SessionManager/Client6' failed to reply before timeout
Jul  5 11:14:51 UBUNTU-Casa gnome-session[1734]: WARNING: Client '/org/gnome/SessionManager/Client3' failed to reply before timeout
Jul  5 11:17:02 UBUNTU-Casa CRON[4584]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 12:17:01 UBUNTU-Casa CRON[5347]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 13:17:01 UBUNTU-Casa CRON[5393]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  5 13:23:23 UBUNTU-Casa kernel: Kernel logging (proc) stopped.
Jul  5 13:23:23 UBUNTU-Casa rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="680" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul  5 13:24:09 UBUNTU-Casa kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jul  5 13:24:09 UBUNTU-Casa rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="749" x-info="http://www.rsyslog.com"] start
Jul  5 13:24:09 UBUNTU-Casa rsyslogd: rsyslogd's groupid changed to 103
Jul  5 13:24:09 UBUNTU-Casa rsyslogd: rsyslogd's userid changed to 101
Jul  5 13:24:09 UBUNTU-Casa rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Linux version 3.2.0-26-generic-pae (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 (Ubuntu 3.2.0-26.41-generic-pae 3.2.19)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] KERNEL supported cpus:
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   Intel GenuineIntel
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   AMD AuthenticAMD
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   NSC Geode by NSC
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   Cyrix CyrixInstead
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   Centaur CentaurHauls
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   Transmeta GenuineTMx86
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   Transmeta TransmetaCPU
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   UMC UMC UMC UMC
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077000000 (usable)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 0000000077000000 - 000000007f000000 (reserved)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007f000000 - 000000007fd90000 (usable)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fee0000 (reserved)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] NX (Execute Disable) protection: active
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] DMI 2.5 present.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] DMI: HP-Pavilion KN280AA-ABM s3410la/Irvine, BIOS 5.08 02/20/2008
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] last_pfn = 0x7fd90 max_arch_pfn = 0x1000000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] MTRR default type: uncachable
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] MTRR fixed ranges enabled:
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   00000-9FFFF write-back
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   A0000-BFFFF uncachable
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   C0000-CCFFF write-protect
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   CD000-FFFFF uncachable
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] MTRR variable ranges enabled:
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   2 disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   3 disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   4 disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   5 disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   6 disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   7 disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] original variable MTRRs
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] total RAM covered: 2047M
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Found optimal setting for mtrr clean up
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 2      lose cover RAM: 0G
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] New variable MTRRs
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] found SMP MP-table at [c00f3f50] f3f50
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] initial memory mapped : 0 - 02000000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] RAMDISK: 364fa000 - 37275000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: RSDP 000f81e0 00014 (v00 HPQOEM)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: RSDT 7fee3000 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: FACP 7fee3080 00084 (v02 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: DSDT 7fee3140 04F86 (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: FACS 7fee1800 00040
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: SLIC 7fee8100 00176 (v01 HPQOEM SLIC-CPC 00000001 AWRD 00000001)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: HPET 7fee8340 00038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: MCFG 7fee8380 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: APIC 7fee8280 00098 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: SSDT 7fee8a20 00380 (v01 HPQOEM SLIC-CPC 00003000 INTL 20040311)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] 1153MB HIGHMEM available.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] 891MB LOWMEM available.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   low ram: 0 - 37bfe000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Zone PFN ranges:
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0007fd90
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Movable zone start PFN for each node
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]     0: 0x00000100 -> 0x00077000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]     0: 0x0007f000 -> 0x0007fd90
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] On node 0 totalpages: 490783
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] free_area_init_node: node 0, pgdat c18669c0, node_mem_map f54fa200
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   HighMem zone: 2308 pages used for memmap
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]   HighMem zone: 260238 pages, LIFO batch:31
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Using APIC driver default
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ14 used by override.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ15 used by override.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] nr_irqs_gsi: 40
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:70100000)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb9000 s34240 r0 d23104 u57344
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 486691
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=2e7fca3e-5c01-451a-a2a2-b09735cc55b0 ro quiet splash vt.handoff=7
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Initializing CPU#0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] allocated 8378368 bytes of page_cgroup
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007fd90)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Memory: 1913324k/2094656k available (5814k kernel code, 49808k reserved, 2841k data, 740k init, 1050184k highmem)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] virtual kernel memory layout:
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]       .init : 0xc1875000 - 0xc192e000   ( 740 kB)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]       .data : 0xc15ada24 - 0xc18741c0   (2841 kB)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]       .text : 0xc1000000 - 0xc15ada24   (5814 kB)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Hierarchical RCU implementation.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712 16
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] CPU 0 irqstacks, hard=f500a000 soft=f500c000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Console: colour dummy device 80x25
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] console [tty0] enabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] hpet clockevent registered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Fast TSC calibration using PIT
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.000000] Detected 1999.992 MHz processor.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.98 BogoMIPS (lpj=7999968)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.004033] Security Framework initialized
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.004052] AppArmor: AppArmor initialized
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.004054] Yama: becoming mindful.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.004117] Mount-cache hash table entries: 512
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.004269] Initializing cgroup subsys cpuacct
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.004276] Initializing cgroup subsys memory
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008011] Initializing cgroup subsys devices
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008014] Initializing cgroup subsys freezer
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008016] Initializing cgroup subsys blkio
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008024] Initializing cgroup subsys perf_event
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008052] CPU: Physical Processor ID: 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008054] CPU: Processor Core ID: 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008057] mce: CPU supports 6 MCE banks
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008066] CPU0: Thermal monitoring enabled (TM2)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008070] using mwait in idle threads.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.010329] ACPI: Core revision 20110623
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.016015] ftrace: allocating 26538 entries in 52 pages
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.020062] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.020530] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.063276] CPU0: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] PEBS disabled due to CPU errata.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] ... version:                2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] ... bit width:              40
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] ... generic registers:      2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] ... value mask:             000000ffffffffff
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] ... max period:             000000007fffffff
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] ... fixed-purpose events:   3
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] ... event mask:             0000000700000003
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] CPU 1 irqstacks, hard=f5112000 soft=f5114000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] Booting Node   0, Processors  #1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.064003] smpboot cpu 1: start_ip = 9b000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.008000] Initializing CPU#1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.152045] NMI watchdog enabled, takes one hw-pmu counter.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.152086] Brought up 2 CPUs
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.152089] Total of 2 processors activated (7999.95 BogoMIPS).
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.152999] devtmpfs: initialized
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.152999] EVM: security.selinux
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.152999] EVM: security.SMACK64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.152999] EVM: security.capability
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.152999] PM: Registering ACPI NVS region at 7fee0000 (12288 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153228] print_constraints: dummy: 
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153269] RTC time: 17:23:58, date: 07/05/12
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153316] NET: Registered protocol family 16
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153353] Trying to unpack rootfs image as initramfs...
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153475] EISA bus registered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153495] ACPI: bus type pci registered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153576] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xf0000000-0xf1ffffff] (base 0xf0000000)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153580] PCI: MMCONFIG at [mem 0xf0000000-0xf1ffffff] reserved in E820
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153582] PCI: Using MMCONFIG for extended config space
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.153585] PCI: Using configuration type 1 for base access
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.156365] bio: create slab <bio-0> at 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.156469] ACPI: Added _OSI(Module Device)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.156472] ACPI: Added _OSI(Processor Device)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.156475] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.156478] ACPI: Added _OSI(Processor Aggregator Device)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.158233] ACPI: EC: Look up EC in DSDT
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.162981] ACPI: SSDT 7fee8400 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.163388] ACPI: Dynamic OEM Table Load:
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.163392] ACPI: SSDT   (null) 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.163572] ACPI: SSDT 7fee88c0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.163966] ACPI: Dynamic OEM Table Load:
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.163969] ACPI: SSDT   (null) 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.164252] ACPI: Interpreter enabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.164262] ACPI: (supports S0 S3 S4 S5)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.164286] ACPI: Using IOAPIC for interrupt routing
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171377] ACPI: No dock devices found.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171382] HEST: Table not found.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171388] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171571] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171707] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171710] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171713] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171717] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171720] pci_root PNP0A08:00: host bridge window [mem 0x7ff00000-0xfebfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171742] pci 0000:00:00.0: [10de:07c1] type 0 class 0x000600
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.171850] pci 0000:00:00.1: [10de:07cb] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.172021] pci 0000:00:01.0: [10de:07cd] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.172173] pci 0000:00:01.1: [10de:07ce] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.172327] pci 0000:00:01.2: [10de:07cf] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.172479] pci 0000:00:01.3: [10de:07d0] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.172630] pci 0000:00:01.4: [10de:07d1] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.172783] pci 0000:00:01.5: [10de:07d2] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.172935] pci 0000:00:01.6: [10de:07d3] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173088] pci 0000:00:02.0: [10de:07d6] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173242] pci 0000:00:03.0: [10de:07d7] type 0 class 0x000601
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173312] pci 0000:00:03.1: [10de:07d8] type 0 class 0x000c05
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173329] pci 0000:00:03.1: reg 10: [io  0xff00-0xff3f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173356] pci 0000:00:03.1: reg 20: [io  0x1c00-0x1c3f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173364] pci 0000:00:03.1: reg 24: [io  0x1c80-0x1cbf]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173404] pci 0000:00:03.1: PME# supported from D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173411] pci 0000:00:03.1: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173426] pci 0000:00:03.2: [10de:07d9] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173500] pci 0000:00:03.4: [10de:07c8] type 0 class 0x000500
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173655] pci 0000:00:04.0: [10de:07fe] type 0 class 0x000c03
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173670] pci 0000:00:04.0: reg 10: [mem 0xeffff000-0xefffffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173732] pci 0000:00:04.0: supports D1 D2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173734] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173739] pci 0000:00:04.0: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173757] pci 0000:00:04.1: [10de:056a] type 0 class 0x000c03
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173773] pci 0000:00:04.1: reg 10: [mem 0xefffe000-0xefffe0ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173845] pci 0000:00:04.1: supports D1 D2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173848] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173852] pci 0000:00:04.1: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173881] pci 0000:00:08.0: [10de:056c] type 0 class 0x000101
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173918] pci 0000:00:08.0: reg 20: [io  0xfc00-0xfc0f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173968] pci 0000:00:09.0: [10de:07fc] type 0 class 0x000403
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.173984] pci 0000:00:09.0: reg 10: [mem 0xefff4000-0xefff7fff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174051] pci 0000:00:09.0: PME# supported from D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174056] pci 0000:00:09.0: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174072] pci 0000:00:0a.0: [10de:056d] type 1 class 0x000604
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174135] pci 0000:00:0b.0: [10de:056e] type 1 class 0x000604
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174192] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174196] pci 0000:00:0b.0: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174217] pci 0000:00:0c.0: [10de:056f] type 1 class 0x000604
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174271] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174275] pci 0000:00:0c.0: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174297] pci 0000:00:0d.0: [10de:056f] type 1 class 0x000604
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174350] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174354] pci 0000:00:0d.0: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174374] pci 0000:00:0e.0: [10de:07f0] type 0 class 0x000101
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174389] pci 0000:00:0e.0: reg 10: [io  0x09f0-0x09f7]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174397] pci 0000:00:0e.0: reg 14: [io  0x0bf0-0x0bf3]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174404] pci 0000:00:0e.0: reg 18: [io  0x0970-0x0977]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174412] pci 0000:00:0e.0: reg 1c: [io  0x0b70-0x0b73]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174419] pci 0000:00:0e.0: reg 20: [io  0xf700-0xf70f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174427] pci 0000:00:0e.0: reg 24: [mem 0xefff8000-0xefff9fff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174480] pci 0000:00:0f.0: [10de:07dc] type 0 class 0x000200
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174495] pci 0000:00:0f.0: reg 10: [mem 0xefffd000-0xefffdfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174503] pci 0000:00:0f.0: reg 14: [io  0xf600-0xf607]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174511] pci 0000:00:0f.0: reg 18: [mem 0xefffc000-0xefffc0ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174519] pci 0000:00:0f.0: reg 1c: [mem 0xefffb000-0xefffb00f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174571] pci 0000:00:0f.0: supports D1 D2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174574] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174579] pci 0000:00:0f.0: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174596] pci 0000:00:10.0: [10de:07e1] type 0 class 0x000300
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174610] pci 0000:00:10.0: reg 10: [mem 0xed000000-0xedffffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174620] pci 0000:00:10.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174631] pci 0000:00:10.0: reg 1c: [mem 0xee000000-0xeeffffff 64bit]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174643] pci 0000:00:10.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174734] pci 0000:01:07.0: [1106:3044] type 0 class 0x000c00
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174753] pci 0000:01:07.0: reg 10: [mem 0xefbff000-0xefbff7ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174764] pci 0000:01:07.0: reg 14: [io  0xcf00-0xcf7f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174838] pci 0000:01:07.0: supports D2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174840] pci 0000:01:07.0: PME# supported from D2 D3hot D3cold
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174846] pci 0000:01:07.0: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174885] pci 0000:00:0a.0: PCI bridge to [bus 01-01] (subtractive decode)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174889] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174894] pci 0000:00:0a.0:   bridge window [mem 0xefb00000-0xefbfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174898] pci 0000:00:0a.0:   bridge window [mem 0xefa00000-0xefafffff pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174902] pci 0000:00:0a.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174905] pci 0000:00:0a.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174908] pci 0000:00:0a.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174911] pci 0000:00:0a.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174914] pci 0000:00:0a.0:   bridge window [mem 0x7ff00000-0xfebfffff] (subtractive decode)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174951] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174957] pci 0000:00:0b.0:   bridge window [io  0xb000-0xbfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174961] pci 0000:00:0b.0:   bridge window [mem 0xef900000-0xef9fffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.174967] pci 0000:00:0b.0:   bridge window [mem 0xef800000-0xef8fffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175017] pci 0000:03:00.0: [14f1:2f82] type 0 class 0x000780
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175037] pci 0000:03:00.0: reg 10: [mem 0xef7f0000-0xef7fffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175169] pci 0000:03:00.0: supports D1 D2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175172] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175177] pci 0000:03:00.0: PME# disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175200] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175211] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175216] pci 0000:00:0c.0:   bridge window [io  0xe000-0xefff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175220] pci 0000:00:0c.0:   bridge window [mem 0xef700000-0xef7fffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175226] pci 0000:00:0c.0:   bridge window [mem 0xefe00000-0xefefffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175262] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175267] pci 0000:00:0d.0:   bridge window [io  0xd000-0xdfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175272] pci 0000:00:0d.0:   bridge window [mem 0xefd00000-0xefdfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175277] pci 0000:00:0d.0:   bridge window [mem 0xefc00000-0xefcfffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175293] pci_bus 0000:00: on NUMA node 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175727]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175918]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0c
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.175921] ACPI _OSC control for PCIe not granted, disabling ASPM
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209298] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209359] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209415] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209474] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209530] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209585] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209640] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209695] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209750] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209807] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209863] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 *7 9 10 11 14 15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209920] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.209974] ACPI: PCI Interrupt Link [LU1B] (IRQs 5 7 9 10 11 14 15) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210028] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 10 11 14 15) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210087] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210142] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210196] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210252] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210307] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210364] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210466] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210564] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210660] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210755] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210849] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.210945] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211039] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211134] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211228] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211325] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211421] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211516] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211614] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211711] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211806] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.211903] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212105] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212201] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212297] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212480] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=io+mem,locks=none
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212485] vgaarb: loaded
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212487] vgaarb: bridge control possible 0000:00:10.0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212628] i2c-core: driver [aat2870] using legacy suspend method
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212630] i2c-core: driver [aat2870] using legacy resume method
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.212733] SCSI subsystem initialized
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.216257] libata version 3.00 loaded.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.216257] usbcore: registered new interface driver usbfs
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.216257] usbcore: registered new interface driver hub
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.216257] usbcore: registered new device driver usb
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.216304] PCI: Using ACPI for IRQ routing
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217253] PCI: pci_cache_line_size set to 64 bytes
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217399] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217403] reserve RAM buffer: 0000000077000000 - 0000000077ffffff 
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217406] reserve RAM buffer: 000000007fd90000 - 000000007fffffff 
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217548] NetLabel: Initializing
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217550] NetLabel:  domain hash size = 128
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217552] NetLabel:  protocols = UNLABELED CIPSOv4
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217564] NetLabel:  unlabeled traffic allowed by default
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217634] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217641] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.217647] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.224112] Switching to clocksource hpet
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234371] AppArmor: AppArmor Filesystem Enabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234415] pnp: PnP ACPI init
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234438] ACPI: bus type pnp registered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234568] pnp 00:00: [bus 00-ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234571] pnp 00:00: [io  0x0cf8-0x0cff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234574] pnp 00:00: [io  0x0000-0x0cf7 window]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234577] pnp 00:00: [io  0x0d00-0xffff window]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234580] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234583] pnp 00:00: [mem 0x000c0000-0x000dffff window]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234586] pnp 00:00: [mem 0x7ff00000-0xfebfffff window]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234671] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234829] pnp 00:01: [io  0x1000-0x107f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234832] pnp 00:01: [io  0x1080-0x10ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234835] pnp 00:01: [io  0x1400-0x147f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234837] pnp 00:01: [io  0x1480-0x14ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234840] pnp 00:01: [io  0x1800-0x187f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234842] pnp 00:01: [io  0x1880-0x18ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234845] pnp 00:01: [mem 0xfec80000-0xfecbffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234848] pnp 00:01: [mem 0xfefe0000-0xfefe01ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234850] pnp 00:01: [mem 0xfefe1000-0xfefe10ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234853] pnp 00:01: [mem 0x77000000-0x7effffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234947] system 00:01: [io  0x1000-0x107f] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234950] system 00:01: [io  0x1080-0x10ff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234954] system 00:01: [io  0x1400-0x147f] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234957] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234960] system 00:01: [io  0x1800-0x187f] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234963] system 00:01: [io  0x1880-0x18ff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234967] system 00:01: [mem 0xfec80000-0xfecbffff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234971] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234974] system 00:01: [mem 0xfefe1000-0xfefe10ff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234980] system 00:01: [mem 0x77000000-0x7effffff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.234985] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235058] pnp 00:02: [io  0x0010-0x001f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235061] pnp 00:02: [io  0x0022-0x003f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235063] pnp 00:02: [io  0x0044-0x005f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235066] pnp 00:02: [io  0x0062-0x0063]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235068] pnp 00:02: [io  0x0065-0x006f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235073] pnp 00:02: [io  0x0074-0x007f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235075] pnp 00:02: [io  0x0091-0x0093]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235078] pnp 00:02: [io  0x00a2-0x00bf]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235080] pnp 00:02: [io  0x00e0-0x00ef]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235083] pnp 00:02: [io  0x04d0-0x04d1]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235085] pnp 00:02: [io  0x0220-0x0225]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235088] pnp 00:02: [io  0x0880-0x088f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235167] system 00:02: [io  0x04d0-0x04d1] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235171] system 00:02: [io  0x0220-0x0225] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235174] system 00:02: [io  0x0880-0x088f] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235178] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235193] pnp 00:03: [dma 4]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235196] pnp 00:03: [io  0x0000-0x000f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235198] pnp 00:03: [io  0x0080-0x0090]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235201] pnp 00:03: [io  0x0094-0x009f]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235203] pnp 00:03: [io  0x00c0-0x00df]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235247] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235306] pnp 00:04: [irq 0 disabled]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235319] pnp 00:04: [irq 8]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235322] pnp 00:04: [mem 0xfeff0000-0xfeff03ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235367] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235399] pnp 00:05: [io  0x0070-0x0073]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235446] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235457] pnp 00:06: [io  0x0061]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235499] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235510] pnp 00:07: [io  0x00f0-0x00ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235517] pnp 00:07: [irq 13]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235563] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235606] pnp 00:08: [io  0x0060]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235608] pnp 00:08: [io  0x0064]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235616] pnp 00:08: [irq 1]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.235677] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236382] pnp 00:09: [mem 0xf0000000-0xf1ffffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236485] system 00:09: [mem 0xf0000000-0xf1ffffff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236489] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236550] pnp 00:0a: [mem 0x000f0000-0x000fffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236553] pnp 00:0a: [mem 0xfeff0000-0xfeff00ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236556] pnp 00:0a: [mem 0x7fee0000-0x7fefffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236558] pnp 00:0a: [mem 0xffff0000-0xffffffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236561] pnp 00:0a: [mem 0x00000000-0x0009ffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236564] pnp 00:0a: [mem 0x00100000-0x7fedffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236566] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236569] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236571] pnp 00:0a: [mem 0xfeff0000-0xfeff03ff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236676] system 00:0a: [mem 0x000f0000-0x000fffff] could not be reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236680] system 00:0a: [mem 0xfeff0000-0xfeff00ff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236684] system 00:0a: [mem 0x7fee0000-0x7fefffff] could not be reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236687] system 00:0a: [mem 0xffff0000-0xffffffff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236690] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236694] system 00:0a: [mem 0x00100000-0x7fedffff] could not be reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236697] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236701] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236704] system 00:0a: [mem 0xfeff0000-0xfeff03ff] could not be reserved
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236708] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236720] pnp: PnP ACPI: found 11 devices
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236722] ACPI: ACPI bus type pnp unregistered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.236727] PnPBIOS: Disabled by ACPI PNP
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273520] PCI: max bus depth: 1 pci_try_num: 2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273564] pci 0000:00:10.0: BAR 6: assigned [mem 0x7ff00000-0x7ff1ffff pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273568] pci 0000:00:0a.0: PCI bridge to [bus 01-01]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273572] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273578] pci 0000:00:0a.0:   bridge window [mem 0xefb00000-0xefbfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273582] pci 0000:00:0a.0:   bridge window [mem 0xefa00000-0xefafffff pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273589] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273592] pci 0000:00:0b.0:   bridge window [io  0xb000-0xbfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273597] pci 0000:00:0b.0:   bridge window [mem 0xef900000-0xef9fffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273601] pci 0000:00:0b.0:   bridge window [mem 0xef800000-0xef8fffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273607] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273610] pci 0000:00:0c.0:   bridge window [io  0xe000-0xefff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273615] pci 0000:00:0c.0:   bridge window [mem 0xef700000-0xef7fffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273619] pci 0000:00:0c.0:   bridge window [mem 0xefe00000-0xefefffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273624] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273628] pci 0000:00:0d.0:   bridge window [io  0xd000-0xdfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273632] pci 0000:00:0d.0:   bridge window [mem 0xefd00000-0xefdfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273637] pci 0000:00:0d.0:   bridge window [mem 0xefc00000-0xefcfffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273652] pci 0000:00:0a.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273659] pci 0000:00:0b.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273666] pci 0000:00:0c.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273673] pci 0000:00:0d.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273677] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273680] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273683] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273686] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273689] pci_bus 0000:00: resource 8 [mem 0x7ff00000-0xfebfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273692] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273694] pci_bus 0000:01: resource 1 [mem 0xefb00000-0xefbfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273697] pci_bus 0000:01: resource 2 [mem 0xefa00000-0xefafffff pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273700] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273703] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273706] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273709] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273712] pci_bus 0000:01: resource 8 [mem 0x7ff00000-0xfebfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273715] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273717] pci_bus 0000:02: resource 1 [mem 0xef900000-0xef9fffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273720] pci_bus 0000:02: resource 2 [mem 0xef800000-0xef8fffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273723] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273726] pci_bus 0000:03: resource 1 [mem 0xef700000-0xef7fffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273729] pci_bus 0000:03: resource 2 [mem 0xefe00000-0xefefffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273732] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273735] pci_bus 0000:04: resource 1 [mem 0xefd00000-0xefdfffff]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273738] pci_bus 0000:04: resource 2 [mem 0xefc00000-0xefcfffff 64bit pref]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273816] NET: Registered protocol family 2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.273909] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.274244] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.274832] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.275209] TCP: Hash tables configured (established 131072 bind 65536)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.275212] TCP reno registered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.275216] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.275229] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.275361] NET: Registered protocol family 1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.275692] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.275713] pci 0000:00:04.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.344047] pci 0000:00:04.0: PCI INT A disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.344273] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.344293] pci 0000:00:04.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.344316] pci 0000:00:04.1: PCI INT B disabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.344386] pci 0000:00:10.0: Boot video device
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.344395] PCI: CLS 64 bytes, default 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.344804] audit: initializing netlink socket (disabled)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.344818] type=2000 audit(1341509037.340:1): initialized
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.374846] highmem bounce pool size: 64 pages
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.374853] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.385858] VFS: Disk quotas dquot_6.5.2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.385941] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.386638] fuse init (API version 7.17)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.386758] msgmni has been set to 1685
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387151] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387186] io scheduler noop registered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387188] io scheduler deadline registered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387199] io scheduler cfq registered (default)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387359] pcieport 0000:00:0b.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387401] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387462] pcieport 0000:00:0c.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387497] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387550] pcieport 0000:00:0d.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387584] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387669] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387699] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387806] intel_idle: MWAIT substates: 0x220
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387809] intel_idle: does not run on family 6 model 15
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387913] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387918] ACPI: Power Button [PWRB]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387993] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.387998] ACPI: Power Button [PWRF]
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.388091] ACPI: Fan [FAN] (on)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.390350] thermal LNXTHERM:00: registered as thermal_zone0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.390354] ACPI: Thermal Zone [THRM] (-127 C)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.390418] ERST: Table is not found!
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.390420] GHES: HEST is not enabled!
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.390590] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.390778] isapnp: Scanning for PnP cards...
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.508618] Freeing initrd memory: 13804k freed
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.743776] isapnp: No Plug & Play device found
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.796650] Linux agpgart interface v0.103
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.798648] brd: module loaded
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.799652] loop: module loaded
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.799833] ahci 0000:00:0e.0: version 3.0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.800039] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.800058] ahci 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.800081] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.800084] ahci 0000:00:0e.0: controller can't do PMP, turning off CAP_PMP
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.800152] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.800157] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pio 
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.800161] ahci 0000:00:0e.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801042] scsi0 : ahci
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801170] scsi1 : ahci
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801268] scsi2 : ahci
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801366] scsi3 : ahci
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801526] ata1: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8100 irq 21
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801530] ata2: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8180 irq 21
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801533] ata3: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8200 irq 21
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801536] ata4: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8280 irq 21
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.801742] pata_acpi 0000:00:08.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802170] Fixed MDIO Bus: probed
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802196] tun: Universal TUN/TAP device driver, 1.6
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802199] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802290] PPP generic driver version 2.4.2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802434] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802458] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802480] ehci_hcd 0000:00:04.1: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802484] ehci_hcd 0000:00:04.1: EHCI Host Controller
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802543] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802563] ehci_hcd 0000:00:04.1: debug port 1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802573] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.802594] ehci_hcd 0000:00:04.1: irq 22, io mem 0xefffe000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812031] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812250] hub 1-0:1.0: USB hub found
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812255] hub 1-0:1.0: 10 ports detected
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812360] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812379] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812392] ohci_hcd 0000:00:04.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812395] ohci_hcd 0000:00:04.0: OHCI Host Controller
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812452] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.812477] ohci_hcd 0000:00:04.0: irq 23, io mem 0xeffff000
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870163] hub 2-0:1.0: USB hub found
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870169] hub 2-0:1.0: 10 ports detected
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870265] uhci_hcd: USB Universal Host Controller Interface driver
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870334] usbcore: registered new interface driver libusual
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870389] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870391] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870577] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870710] mousedev: PS/2 mouse device common for all mice
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.870900] rtc_cmos 00:05: RTC can wake from S4
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871058] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871095] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871160] device-mapper: uevent: version 1.0.3
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871253] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871296] EISA: Probing bus 0 at eisa.0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871299] EISA: Cannot allocate resource for mainboard
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871302] Cannot allocate resource for EISA slot 1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871304] Cannot allocate resource for EISA slot 2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871306] Cannot allocate resource for EISA slot 3
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871309] Cannot allocate resource for EISA slot 4
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871311] Cannot allocate resource for EISA slot 5
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871313] Cannot allocate resource for EISA slot 6
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871315] Cannot allocate resource for EISA slot 7
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871317] Cannot allocate resource for EISA slot 8
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871320] EISA: Detected 0 cards.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871331] cpufreq-nforce2: No nForce2 chipset.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871334] cpuidle: using governor ladder
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871336] cpuidle: using governor menu
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871339] EFI Variables Facility v0.08 2004-May-17
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871656] TCP cubic registered
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.871801] NET: Registered protocol family 10
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.872499] NET: Registered protocol family 17
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.872504] Registering the dns_resolver key type
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.872531] Using IPI No-Shortcut mode
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.872673] PM: Hibernation image not present or could not be loaded.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.872688] registered taskstats version 1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.884841]   Magic number: 4:8:390
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.884949] rtc_cmos 00:05: setting system clock to 2012-07-05 17:23:59 UTC (1341509039)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.885290] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.885293] EDD information not available.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    0.890775] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.120041] ata3: SATA link down (SStatus 0 SControl 300)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.120062] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.120081] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.120096] ata4: SATA link down (SStatus 0 SControl 300)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.121193] ata2.00: ATAPI: Optiarc DVD RW AD-7201S5, 1H0B, max UDMA/100
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.122599] ata2.00: configured for UDMA/100
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.125371] ata1.00: ATA-7: SAMSUNG HD250HJ, FH100-05, max UDMA7
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.125377] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.130703] ata1.00: configured for UDMA/133
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.130897] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD250HJ  FH10 PQ: 0 ANSI: 5
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.131046] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.131086] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.131101] sd 0:0:0:0: [sda] Write Protect is off
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.131104] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.131128] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.132737] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7201S5 1H0B PQ: 0 ANSI: 5
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.135081] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.135086] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.135281] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.135360] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.169357]  sda: sda1 sda2 < sda5 >
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.169827] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.169920] Freeing unused kernel memory: 740k freed
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.170288] Write protecting the kernel text: 5816k
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.170310] Write protecting the kernel read-only data: 2376k
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.170312] NX-protecting the kernel data: 4424k
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.180052] usb 1-9: new high-speed USB device number 3 using ehci_hcd
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.311216] pata_amd 0000:00:08.0: version 0.4.1
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.311279] pata_amd 0000:00:08.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.317774] scsi4 : pata_amd
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.320833] scsi5 : pata_amd
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.321404] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.321409] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.321475] ata5: port disabled--ignoring
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.321511] ata6: port disabled--ignoring
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.326493] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.326719] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.326739] forcedeth 0000:00:0f.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.326747] forcedeth 0000:00:0f.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.333971] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.333993] firewire_ohci 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.334001] firewire_ohci 0000:01:07.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.338289] Initializing USB Mass Storage driver...
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.338951] scsi6 : usb-storage 1-9:1.0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.339059] usbcore: registered new interface driver usb-storage
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.339062] USB Mass Storage support registered.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.344034] Refined TSC clocksource calibration: 2000.000 MHz.
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.344044] Switching to clocksource tsc
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.400095] firewire_ohci: Added fw-ohci device 0000:01:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.513389] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.636032] usb 2-7: new low-speed USB device number 2 using ohci_hcd
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.849123] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 13, addr 00:1c:25:8e:09:f7
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.849127] forcedeth 0000:00:0f.0: highdma pwrctl mgmt lnktim msi desc-v3
Jul  5 13:24:09 UBUNTU-Casa kernel: [    1.900151] firewire_core: created device fw0: GUID 00016c20005344bd, S400
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.343037] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.349530] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.356153] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.362780] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.363571] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.363765] sd 6:0:0:1: Attached scsi generic sg3 type 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.363963] sd 6:0:0:2: Attached scsi generic sg4 type 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.364175] sd 6:0:0:3: Attached scsi generic sg5 type 0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.369768] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.370634] sd 6:0:0:1: [sdc] Attached SCSI removable disk
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.372254] sd 6:0:0:2: [sdd] Attached SCSI removable disk
Jul  5 13:24:09 UBUNTU-Casa kernel: [    2.373002] sd 6:0:0:3: [sde] Attached SCSI removable disk
Jul  5 13:24:09 UBUNTU-Casa kernel: [    4.809681] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  5 13:24:09 UBUNTU-Casa kernel: [    5.153858] Adding 1961980k swap on /dev/sda5.  Priority:-1 extents:1 across:1961980k 
Jul  5 13:24:09 UBUNTU-Casa kernel: [    6.057586] lp: driver loaded but no devices found
Jul  5 13:24:09 UBUNTU-Casa kernel: [    6.194793] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jul  5 13:24:09 UBUNTU-Casa kernel: [    6.682141] wmi: Mapper loaded
Jul  5 13:24:09 UBUNTU-Casa kernel: [    6.702156] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Jul  5 13:24:09 UBUNTU-Casa kernel: [    6.702194] i2c i2c-1: nForce2 SMBus adapter at 0x1c80
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.369205] type=1400 audit(1341509046.982:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=648 comm="apparmor_parser"
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.369218] type=1400 audit(1341509046.982:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.369721] type=1400 audit(1341509046.982:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=648 comm="apparmor_parser"
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.369731] type=1400 audit(1341509046.982:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.369994] type=1400 audit(1341509046.982:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=648 comm="apparmor_parser"
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.370004] type=1400 audit(1341509046.982:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.976691] snd_hda_intel 0000:00:09.0: power state changed by ACPI to D0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.976699] snd_hda_intel 0000:00:09.0: power state changed by ACPI to D0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.977127] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.977136] snd_hda_intel 0000:00:09.0: PCI INT A -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.977141] hda_intel: Disabling MSI
Jul  5 13:24:09 UBUNTU-Casa kernel: [    8.977182] snd_hda_intel 0000:00:09.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [    9.382622] input: Genius       Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.0/input/input3
Jul  5 13:24:09 UBUNTU-Casa kernel: [    9.382875] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.10 Mouse [Genius       Optical Mouse] on usb-0000:00:04.0-7/input0
Jul  5 13:24:09 UBUNTU-Casa kernel: [    9.382899] usbcore: registered new interface driver usbhid
Jul  5 13:24:09 UBUNTU-Casa kernel: [    9.382901] usbhid: USB HID core driver
Jul  5 13:24:09 UBUNTU-Casa kernel: [   10.072053] hda_codec: ALC1200: BIOS auto-probing.
Jul  5 13:24:09 UBUNTU-Casa kernel: [   10.072059] hda_codec: ALC1200: SKU not ready 0x411111f0
Jul  5 13:24:09 UBUNTU-Casa kernel: [   10.326732] nvidia: module license 'NVIDIA' taints kernel.
Jul  5 13:24:09 UBUNTU-Casa kernel: [   10.326738] Disabling lock debugging due to kernel taint
Jul  5 13:24:09 UBUNTU-Casa kernel: [   10.948475] init: failsafe main process (743) killed by TERM signal
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.056186] input: HDA NVidia Line as /devices/pci0000:00/0000:00:09.0/sound/card0/input4
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.056301] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:09.0/sound/card0/input5
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.056437] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:09.0/sound/card0/input6
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.056579] input: HDA NVidia Line-Out as /devices/pci0000:00/0000:00:09.0/sound/card0/input7
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.057451] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.057460] nvidia 0000:00:10.0: PCI INT A -> Link[AIGP] -> GSI 22 (level, low) -> IRQ 22
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.057470] nvidia 0000:00:10.0: setting latency timer to 64
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.057476] vgaarb: device changed decodes: PCI:0000:00:10.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul  5 13:24:09 UBUNTU-Casa kernel: [   11.058109] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.59  Wed Jun  6 21:24:41 PDT 2012
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.515776] ppdev: user-space parallel port driver
Jul  5 13:24:11 UBUNTU-Casa bluetoothd[882]: Bluetooth daemon 4.98
Jul  5 13:24:11 UBUNTU-Casa bluetoothd[882]: Starting SDP server
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Successfully dropped root privileges.
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: avahi-daemon 0.6.30 starting up.
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.950331] type=1400 audit(1341509051.562:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=894 comm="apparmor_parser"
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.950921] type=1400 audit(1341509051.562:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=894 comm="apparmor_parser"
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.964924] Bluetooth: Core ver 2.16
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.964955] NET: Registered protocol family 31
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.964958] Bluetooth: HCI device and connection manager initialized
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.964962] Bluetooth: HCI socket layer initialized
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.964965] Bluetooth: L2CAP socket layer initialized
Jul  5 13:24:11 UBUNTU-Casa kernel: [   12.964972] Bluetooth: SCO socket layer initialized
Jul  5 13:24:11 UBUNTU-Casa bluetoothd[882]: Failed to init alert plugin
Jul  5 13:24:11 UBUNTU-Casa bluetoothd[882]: Failed to init time plugin
Jul  5 13:24:11 UBUNTU-Casa bluetoothd[882]: Failed to init proximity plugin
Jul  5 13:24:11 UBUNTU-Casa kernel: [   13.134789] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul  5 13:24:11 UBUNTU-Casa kernel: [   13.134793] Bluetooth: BNEP filters: protocol multicast
Jul  5 13:24:11 UBUNTU-Casa kernel: [   13.153125] Bluetooth: RFCOMM TTY layer initialized
Jul  5 13:24:11 UBUNTU-Casa kernel: [   13.153132] Bluetooth: RFCOMM socket layer initialized
Jul  5 13:24:11 UBUNTU-Casa kernel: [   13.153134] Bluetooth: RFCOMM ver 1.11
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Successfully called chroot().
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Successfully dropped remaining capabilities.
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Loading service file /services/udisks.service.
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Network interface enumeration completed.
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Registering HINFO record with values 'I686'/'LINUX'.
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Server startup complete. Host name is UBUNTU-Casa.local. Local service cookie is 928229088.
Jul  5 13:24:11 UBUNTU-Casa avahi-daemon[913]: Service "UBUNTU-Casa" (/services/udisks.service) successfully established.
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  ModemManager (version 0.5.2.0) starting...
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin AnyData
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Linktop
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin ZTE
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Nokia
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin MotoC
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin X22X
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin SimTech
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Longcheer
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Wavecom
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Generic
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Option
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Samsung
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Ericsson MBM
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Novatel
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Option High-Speed
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Gobi
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Sierra
Jul  5 13:24:12 UBUNTU-Casa modem-manager[866]: <info>  Loaded plugin Huawei
Jul  5 13:24:12 UBUNTU-Casa bluetoothd[882]: Failed to init gatt_example plugin
Jul  5 13:24:12 UBUNTU-Casa kernel: [   13.885513] type=1400 audit(1341509052.498:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=934 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   13.886019] type=1400 audit(1341509052.498:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=934 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   13.886293] type=1400 audit(1341509052.498:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=934 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   13.908005] type=1400 audit(1341509052.518:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=933 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   13.949180] type=1400 audit(1341509052.562:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=937 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   13.949859] type=1400 audit(1341509052.562:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=937 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   13.954737] type=1400 audit(1341509052.566:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=938 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   13.955338] type=1400 audit(1341509052.566:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=938 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   14.052095] type=1400 audit(1341509052.666:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=935 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa kernel: [   14.058566] type=1400 audit(1341509052.670:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=935 comm="apparmor_parser"
Jul  5 13:24:12 UBUNTU-Casa NetworkManager[932]: <info> NetworkManager (version 0.9.4.0) is starting...
Jul  5 13:24:12 UBUNTU-Casa NetworkManager[932]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul  5 13:24:13 UBUNTU-Casa NetworkManager[932]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul  5 13:24:13 UBUNTU-Casa NetworkManager[932]: <info> DNS: loaded plugin dnsmasq
Jul  5 13:24:13 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul  5 13:24:13 UBUNTU-Casa kernel: [   14.764817] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jul  5 13:24:13 UBUNTU-Casa kernel: [   14.764821] vesafb: scrolling: redraw
Jul  5 13:24:13 UBUNTU-Casa kernel: [   14.764825] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jul  5 13:24:13 UBUNTU-Casa kernel: [   14.765564] vesafb: framebuffer at 0xd0000000, mapped to 0xf8800000, using 1216k, total 1216k
Jul  5 13:24:13 UBUNTU-Casa kernel: [   14.765738] Console: switching to colour frame buffer device 80x30
Jul  5 13:24:13 UBUNTU-Casa kernel: [   14.765755] fb0: VESA VGA frame buffer device
Jul  5 13:24:13 UBUNTU-Casa polkitd[970]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jul  5 13:24:13 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: init!
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: update_system_hostname
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPluginIfupdown: management mode: unmanaged
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0f.0/net/eth0, iface: eth0)
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0f.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: end _init.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    Ifupdown: get unmanaged devices count: 0
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: (149783888) ... get_connections.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    SCPlugin-Ifupdown: (149783888) ... get_connections (managed=false): return empty list.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]:    Ifupdown: get unmanaged devices count: 0
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> modem-manager is now available
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Networking is enabled by state file
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <warn> failed to allocate link cache: (-10) Operation not supported
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): carrier is OFF
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): now managed
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): bringing up device.
Jul  5 13:24:14 UBUNTU-Casa kernel: [   15.447679] forcedeth 0000:00:0f.0: irq 43 for MSI/MSI-X
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): carrier now ON (device state 20)
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): preparing device.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0f.0/net/eth0
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Auto-activating connection 'Wired connection 1'.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> dhclient started with pid 980
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Beginning IP6 addrconf.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul  5 13:24:14 UBUNTU-Casa dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jul  5 13:24:14 UBUNTU-Casa dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jul  5 13:24:14 UBUNTU-Casa dhclient: All rights reserved.
Jul  5 13:24:14 UBUNTU-Casa dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul  5 13:24:14 UBUNTU-Casa dhclient: 
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul  5 13:24:14 UBUNTU-Casa dhclient: Listening on LPF/eth0/00:1c:25:8e:09:f7
Jul  5 13:24:14 UBUNTU-Casa dhclient: Sending on   LPF/eth0/00:1c:25:8e:09:f7
Jul  5 13:24:14 UBUNTU-Casa dhclient: Sending on   Socket/fallback
Jul  5 13:24:14 UBUNTU-Casa dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul  5 13:24:14 UBUNTU-Casa dhclient: DHCPREQUEST of 192.168.1.160 on eth0 to 255.255.255.255 port 67
Jul  5 13:24:14 UBUNTU-Casa dhclient: DHCPOFFER of 192.168.1.160 from 192.168.1.254
Jul  5 13:24:14 UBUNTU-Casa dhclient: DHCPACK of 192.168.1.160 from 192.168.1.254
Jul  5 13:24:14 UBUNTU-Casa dhclient: bound to 192.168.1.160 -- renewal in 41233 seconds.
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info>   address 192.168.1.160
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info>   prefix 24 (255.255.255.0)
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info>   gateway 192.168.1.254
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info>   nameserver '192.168.1.254'
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info>   domain name 'iptv.microsoft.com'
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul  5 13:24:14 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jul  5 13:24:14 UBUNTU-Casa avahi-daemon[913]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.160.
Jul  5 13:24:14 UBUNTU-Casa avahi-daemon[913]: New relevant interface eth0.IPv4 for mDNS.
Jul  5 13:24:14 UBUNTU-Casa avahi-daemon[913]: Registering new address record for 192.168.1.160 on eth0.IPv4.
Jul  5 13:24:15 UBUNTU-Casa NetworkManager[932]: <info> DNS: starting dnsmasq...
Jul  5 13:24:15 UBUNTU-Casa NetworkManager[932]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jul  5 13:24:15 UBUNTU-Casa dnsmasq[1013]: started, version 2.59 cache disabled
Jul  5 13:24:15 UBUNTU-Casa dnsmasq[1013]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jul  5 13:24:15 UBUNTU-Casa dnsmasq[1013]: using nameserver 192.168.1.254#53
Jul  5 13:24:16 UBUNTU-Casa avahi-daemon[913]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21c:25ff:fe8e:9f7.
Jul  5 13:24:16 UBUNTU-Casa avahi-daemon[913]: New relevant interface eth0.IPv6 for mDNS.
Jul  5 13:24:16 UBUNTU-Casa avahi-daemon[913]: Registering new address record for fe80::21c:25ff:fe8e:9f7 on eth0.*.
Jul  5 13:24:16 UBUNTU-Casa NetworkManager[932]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul  5 13:24:16 UBUNTU-Casa NetworkManager[932]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul  5 13:24:16 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) successful, device activated.
Jul  5 13:24:16 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jul  5 13:24:16 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul  5 13:24:16 UBUNTU-Casa kernel: [   18.301734] init: xbmc main process (960) terminated with status 1
Jul  5 13:24:16 UBUNTU-Casa anacron[1060]: Anacron 2.3 started on 2012-07-05
Jul  5 13:24:16 UBUNTU-Casa acpid: starting up with proc fs
Jul  5 13:24:16 UBUNTU-Casa cron[1002]: (CRON) INFO (pidfile fd = 3)
Jul  5 13:24:16 UBUNTU-Casa cron[1064]: (CRON) STARTUP (fork ok)
Jul  5 13:24:17 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul  5 13:24:17 UBUNTU-Casa cron[1064]: (CRON) INFO (Running @reboot jobs)
Jul  5 13:24:17 UBUNTU-Casa kernel: [   18.600134] vboxdrv: Found 2 processor cores.
Jul  5 13:24:17 UBUNTU-Casa kernel: [   18.601413] vboxdrv: fAsync=0 offMin=0x1f4 offMax=0x8c0
Jul  5 13:24:17 UBUNTU-Casa kernel: [   18.601510] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul  5 13:24:17 UBUNTU-Casa kernel: [   18.601513] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jul  5 13:24:17 UBUNTU-Casa acpid: 35 rules loaded
Jul  5 13:24:17 UBUNTU-Casa acpid: waiting for events: event logging is off
Jul  5 13:24:17 UBUNTU-Casa anacron[1060]: Normal exit (0 jobs run)
Jul  5 13:24:17 UBUNTU-Casa kernel: [   18.960572] vboxpci: IOMMU not found (not registered)
Jul  5 13:24:18 UBUNTU-Casa acpid: client connected from 1130[0:0]
Jul  5 13:24:18 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:24:19 UBUNTU-Casa kernel: [   21.327208] NVRM: Your system is not currently configured to drive a VGA console
Jul  5 13:24:19 UBUNTU-Casa kernel: [   21.327213] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
Jul  5 13:24:19 UBUNTU-Casa kernel: [   21.327217] NVRM: requires the use of a text-mode VGA console. Use of other console
Jul  5 13:24:19 UBUNTU-Casa kernel: [   21.327220] NVRM: drivers including, but not limited to, vesafb, may result in
Jul  5 13:24:19 UBUNTU-Casa kernel: [   21.327222] NVRM: corruption and stability problems, and is not supported.
Jul  5 13:24:20 UBUNTU-Casa acpid: client connected from 1130[0:0]
Jul  5 13:24:20 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:24:20 UBUNTU-Casa anacron[1233]: Anacron 2.3 started on 2012-07-05
Jul  5 13:24:20 UBUNTU-Casa anacron[1233]: Normal exit (0 jobs run)
Jul  5 13:24:21 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul  5 13:24:21 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul  5 13:24:21 UBUNTU-Casa accounts-daemon[1337]: started daemon version 0.6.15
Jul  5 13:24:21 UBUNTU-Casa kernel: [   22.966163] init: plymouth-stop pre-start process (1350) terminated with status 1
Jul  5 13:24:21 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jul  5 13:24:22 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jul  5 13:24:25 UBUNTU-Casa kernel: [   26.452260] eth0: no IPv6 routers present
Jul  5 13:24:25 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul  5 13:24:25 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul  5 13:24:26 UBUNTU-Casa anacron[1542]: Anacron 2.3 started on 2012-07-05
Jul  5 13:24:26 UBUNTU-Casa anacron[1542]: Normal exit (0 jobs run)
Jul  5 13:24:27 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul  5 13:24:27 UBUNTU-Casa ntpdate[1164]: adjust time server 91.189.94.4 offset -0.231144 sec
Jul  5 13:24:27 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul  5 13:24:30 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul  5 13:24:30 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul  5 13:24:30 UBUNTU-Casa rtkit-daemon[1681]: Successfully called chroot.
Jul  5 13:24:30 UBUNTU-Casa rtkit-daemon[1681]: Successfully dropped privileges.
Jul  5 13:24:30 UBUNTU-Casa rtkit-daemon[1681]: Successfully limited resources.
Jul  5 13:24:30 UBUNTU-Casa rtkit-daemon[1681]: Running.
Jul  5 13:24:30 UBUNTU-Casa rtkit-daemon[1681]: Canary thread running.
Jul  5 13:24:30 UBUNTU-Casa rtkit-daemon[1681]: Watchdog thread running.
Jul  5 13:24:30 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 1678 of process 1678 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:24:30 UBUNTU-Casa rtkit-daemon[1681]: Supervising 1 threads of 1 processes of 1 users.
Jul  5 13:24:31 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 1684 of process 1678 (n/a) owned by '104' RT at priority 5.
Jul  5 13:24:31 UBUNTU-Casa rtkit-daemon[1681]: Supervising 2 threads of 1 processes of 1 users.
Jul  5 13:24:31 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 1685 of process 1678 (n/a) owned by '104' RT at priority 5.
Jul  5 13:24:31 UBUNTU-Casa rtkit-daemon[1681]: Supervising 3 threads of 1 processes of 1 users.
Jul  5 13:24:31 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 1689 of process 1689 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:24:31 UBUNTU-Casa rtkit-daemon[1681]: Supervising 4 threads of 2 processes of 1 users.
Jul  5 13:24:31 UBUNTU-Casa pulseaudio[1689]: [pulseaudio] pid.c: Daemon already running.
Jul  5 13:24:34 UBUNTU-Casa NetworkManager[932]: <info> (eth0): IP6 addrconf timed out or failed.
Jul  5 13:24:34 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul  5 13:24:34 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul  5 13:24:34 UBUNTU-Casa NetworkManager[932]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul  5 13:25:10 UBUNTU-Casa gnome-session[1743]: WARNING: Session 'gnome' runnable check failed: Exited with code 1
Jul  5 13:25:11 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 1827 of process 1827 (n/a) owned by '1000' high priority at nice level -11.
Jul  5 13:25:11 UBUNTU-Casa rtkit-daemon[1681]: Supervising 4 threads of 2 processes of 2 users.
Jul  5 13:25:12 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 1832 of process 1827 (n/a) owned by '1000' RT at priority 5.
Jul  5 13:25:12 UBUNTU-Casa rtkit-daemon[1681]: Supervising 5 threads of 2 processes of 2 users.
Jul  5 13:25:12 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 1833 of process 1827 (n/a) owned by '1000' RT at priority 5.
Jul  5 13:25:12 UBUNTU-Casa rtkit-daemon[1681]: Supervising 6 threads of 2 processes of 2 users.
Jul  5 13:25:13 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jul  5 13:25:13 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jul  5 13:25:30 UBUNTU-Casa goa[2082]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jul  5 13:25:57 UBUNTU-Casa acpid: client 1130[0:0] has disconnected
Jul  5 13:25:57 UBUNTU-Casa acpid: client 1130[0:0] has disconnected
Jul  5 13:25:57 UBUNTU-Casa acpid: client connected from 2175[0:0]
Jul  5 13:25:57 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:25:57 UBUNTU-Casa acpid: client connected from 2175[0:0]
Jul  5 13:25:57 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:25:58 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 2288 of process 2288 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:25:58 UBUNTU-Casa rtkit-daemon[1681]: Supervising 4 threads of 2 processes of 2 users.
Jul  5 13:25:59 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 2295 of process 2288 (n/a) owned by '104' RT at priority 5.
Jul  5 13:25:59 UBUNTU-Casa rtkit-daemon[1681]: Supervising 5 threads of 2 processes of 2 users.
Jul  5 13:25:59 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 2296 of process 2288 (n/a) owned by '104' RT at priority 5.
Jul  5 13:25:59 UBUNTU-Casa rtkit-daemon[1681]: Supervising 6 threads of 2 processes of 2 users.
Jul  5 13:25:59 UBUNTU-Casa rtkit-daemon[1681]: Successfully made thread 2299 of process 2299 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:25:59 UBUNTU-Casa rtkit-daemon[1681]: Supervising 7 threads of 3 processes of 2 users.
Jul  5 13:25:59 UBUNTU-Casa pulseaudio[2299]: [pulseaudio] pid.c: Daemon already running.
Jul  5 13:26:07 UBUNTU-Casa gnome-session[2346]: WARNING: Session 'gnome' runnable check failed: Exited with code 1
Jul  5 13:26:23 UBUNTU-Casa goa[2740]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jul  5 13:27:10 UBUNTU-Casa dbus[849]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jul  5 13:27:11 UBUNTU-Casa AptDaemon: INFO: Initializing daemon
Jul  5 13:27:11 UBUNTU-Casa AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jul  5 13:27:11 UBUNTU-Casa dbus[849]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jul  5 13:27:11 UBUNTU-Casa AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jul  5 13:27:11 UBUNTU-Casa AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/1e64fdfdef654a73903fe020206cb5cc
Jul  5 13:27:11 UBUNTU-Casa AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/1e64fdfdef654a73903fe020206cb5cc
Jul  5 13:27:14 UBUNTU-Casa AptDaemon.PackageKit: INFO: Get updates()
Jul  5 13:27:15 UBUNTU-Casa AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/1e64fdfdef654a73903fe020206cb5cc
Jul  5 13:27:59 UBUNTU-Casa kernel: Kernel logging (proc) stopped.
Jul  5 13:27:59 UBUNTU-Casa rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="749" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul  5 13:28:30 UBUNTU-Casa kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jul  5 13:28:30 UBUNTU-Casa rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="787" x-info="http://www.rsyslog.com"] start
Jul  5 13:28:30 UBUNTU-Casa rsyslogd: rsyslogd's groupid changed to 103
Jul  5 13:28:30 UBUNTU-Casa rsyslogd: rsyslogd's userid changed to 101
Jul  5 13:28:30 UBUNTU-Casa rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Linux version 3.2.0-26-generic-pae (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 (Ubuntu 3.2.0-26.41-generic-pae 3.2.19)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] KERNEL supported cpus:
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   Intel GenuineIntel
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   AMD AuthenticAMD
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   NSC Geode by NSC
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   Cyrix CyrixInstead
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   Centaur CentaurHauls
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   Transmeta GenuineTMx86
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   Transmeta TransmetaCPU
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   UMC UMC UMC UMC
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077000000 (usable)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 0000000077000000 - 000000007f000000 (reserved)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007f000000 - 000000007fd90000 (usable)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fee0000 (reserved)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] NX (Execute Disable) protection: active
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] DMI 2.5 present.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] DMI: HP-Pavilion KN280AA-ABM s3410la/Irvine, BIOS 5.08 02/20/2008
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] last_pfn = 0x7fd90 max_arch_pfn = 0x1000000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] MTRR default type: uncachable
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] MTRR fixed ranges enabled:
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   00000-9FFFF write-back
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   A0000-BFFFF uncachable
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   C0000-CCFFF write-protect
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   CD000-FFFFF uncachable
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] MTRR variable ranges enabled:
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   2 disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   3 disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   4 disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   5 disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   6 disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   7 disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] original variable MTRRs
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] total RAM covered: 2047M
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Found optimal setting for mtrr clean up
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 2      lose cover RAM: 0G
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] New variable MTRRs
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] found SMP MP-table at [c00f3f50] f3f50
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] initial memory mapped : 0 - 02000000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] RAMDISK: 364fa000 - 37275000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: RSDP 000f81e0 00014 (v00 HPQOEM)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: RSDT 7fee3000 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: FACP 7fee3080 00084 (v02 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: DSDT 7fee3140 04F86 (v01 HPQOEM SLIC-CPC 00001000 MSFT 03000000)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: FACS 7fee1800 00040
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: SLIC 7fee8100 00176 (v01 HPQOEM SLIC-CPC 00000001 AWRD 00000001)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: HPET 7fee8340 00038 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000098)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: MCFG 7fee8380 0003C (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: APIC 7fee8280 00098 (v01 HPQOEM SLIC-CPC 42302E31 AWRD 00000000)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: SSDT 7fee8a20 00380 (v01 HPQOEM SLIC-CPC 00003000 INTL 20040311)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] 1153MB HIGHMEM available.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] 891MB LOWMEM available.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   low ram: 0 - 37bfe000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Zone PFN ranges:
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0007fd90
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Movable zone start PFN for each node
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] early_node_map[3] active PFN ranges
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]     0: 0x00000100 -> 0x00077000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]     0: 0x0007f000 -> 0x0007fd90
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] On node 0 totalpages: 490783
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] free_area_init_node: node 0, pgdat c18669c0, node_mem_map f54fa200
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   HighMem zone: 2308 pages used for memmap
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]   HighMem zone: 260238 pages, LIFO batch:31
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Using APIC driver default
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ14 used by override.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: IRQ15 used by override.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] nr_irqs_gsi: 40
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:70100000)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb9000 s34240 r0 d23104 u57344
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 486691
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=2e7fca3e-5c01-451a-a2a2-b09735cc55b0 ro quiet splash vt.handoff=7
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Initializing CPU#0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] allocated 8378368 bytes of page_cgroup
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007fd90)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Memory: 1913324k/2094656k available (5814k kernel code, 49808k reserved, 2841k data, 740k init, 1050184k highmem)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] virtual kernel memory layout:
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]       .init : 0xc1875000 - 0xc192e000   ( 740 kB)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]       .data : 0xc15ada24 - 0xc18741c0   (2841 kB)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]       .text : 0xc1000000 - 0xc15ada24   (5814 kB)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Hierarchical RCU implementation.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712 16
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] CPU 0 irqstacks, hard=f500a000 soft=f500c000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Console: colour dummy device 80x25
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] console [tty0] enabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] hpet clockevent registered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Fast TSC calibration using PIT
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.000000] Detected 1999.861 MHz processor.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.72 BogoMIPS (lpj=7999444)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.004034] Security Framework initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.004053] AppArmor: AppArmor initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.004055] Yama: becoming mindful.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008057] Mount-cache hash table entries: 512
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008208] Initializing cgroup subsys cpuacct
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008215] Initializing cgroup subsys memory
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008224] Initializing cgroup subsys devices
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008227] Initializing cgroup subsys freezer
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008229] Initializing cgroup subsys blkio
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008236] Initializing cgroup subsys perf_event
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008265] CPU: Physical Processor ID: 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008267] CPU: Processor Core ID: 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008271] mce: CPU supports 6 MCE banks
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008279] CPU0: Thermal monitoring enabled (TM2)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008283] using mwait in idle threads.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.010548] ACPI: Core revision 20110623
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.016016] ftrace: allocating 26538 entries in 52 pages
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.020062] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.020530] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.062930] CPU0: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] PEBS disabled due to CPU errata.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] ... version:                2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] ... bit width:              40
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] ... generic registers:      2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] ... value mask:             000000ffffffffff
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] ... max period:             000000007fffffff
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] ... fixed-purpose events:   3
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] ... event mask:             0000000700000003
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] CPU 1 irqstacks, hard=f5112000 soft=f5114000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] Booting Node   0, Processors  #1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.064003] smpboot cpu 1: start_ip = 9b000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.008000] Initializing CPU#1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.152043] NMI watchdog enabled, takes one hw-pmu counter.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.152085] Brought up 2 CPUs
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.152089] Total of 2 processors activated (7999.69 BogoMIPS).
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153001] devtmpfs: initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153001] EVM: security.selinux
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153001] EVM: security.SMACK64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153001] EVM: security.capability
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153001] PM: Registering ACPI NVS region at 7fee0000 (12288 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153224] print_constraints: dummy: 
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153266] RTC time: 17:28:19, date: 07/05/12
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153313] NET: Registered protocol family 16
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153348] Trying to unpack rootfs image as initramfs...
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153478] EISA bus registered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153497] ACPI: bus type pci registered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153577] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xf0000000-0xf1ffffff] (base 0xf0000000)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153581] PCI: MMCONFIG at [mem 0xf0000000-0xf1ffffff] reserved in E820
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153584] PCI: Using MMCONFIG for extended config space
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.153586] PCI: Using configuration type 1 for base access
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.156491] bio: create slab <bio-0> at 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.156596] ACPI: Added _OSI(Module Device)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.156599] ACPI: Added _OSI(Processor Device)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.156601] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.156604] ACPI: Added _OSI(Processor Aggregator Device)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.158349] ACPI: EC: Look up EC in DSDT
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.163116] ACPI: SSDT 7fee8400 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.163522] ACPI: Dynamic OEM Table Load:
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.163527] ACPI: SSDT   (null) 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.163707] ACPI: SSDT 7fee88c0 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.164117] ACPI: Dynamic OEM Table Load:
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.164121] ACPI: SSDT   (null) 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.164403] ACPI: Interpreter enabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.164414] ACPI: (supports S0 S3 S4 S5)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.164438] ACPI: Using IOAPIC for interrupt routing
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171519] ACPI: No dock devices found.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171523] HEST: Table not found.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171529] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171711] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171851] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171855] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171858] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171861] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171864] pci_root PNP0A08:00: host bridge window [mem 0x7ff00000-0xfebfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171887] pci 0000:00:00.0: [10de:07c1] type 0 class 0x000600
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.171996] pci 0000:00:00.1: [10de:07cb] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.172179] pci 0000:00:01.0: [10de:07cd] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.172332] pci 0000:00:01.1: [10de:07ce] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.172486] pci 0000:00:01.2: [10de:07cf] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.172637] pci 0000:00:01.3: [10de:07d0] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.172791] pci 0000:00:01.4: [10de:07d1] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.172942] pci 0000:00:01.5: [10de:07d2] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173096] pci 0000:00:01.6: [10de:07d3] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173248] pci 0000:00:02.0: [10de:07d6] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173404] pci 0000:00:03.0: [10de:07d7] type 0 class 0x000601
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173470] pci 0000:00:03.1: [10de:07d8] type 0 class 0x000c05
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173486] pci 0000:00:03.1: reg 10: [io  0xff00-0xff3f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173513] pci 0000:00:03.1: reg 20: [io  0x1c00-0x1c3f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173521] pci 0000:00:03.1: reg 24: [io  0x1c80-0x1cbf]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173561] pci 0000:00:03.1: PME# supported from D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173568] pci 0000:00:03.1: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173582] pci 0000:00:03.2: [10de:07d9] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173657] pci 0000:00:03.4: [10de:07c8] type 0 class 0x000500
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173814] pci 0000:00:04.0: [10de:07fe] type 0 class 0x000c03
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173828] pci 0000:00:04.0: reg 10: [mem 0xeffff000-0xefffffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173889] pci 0000:00:04.0: supports D1 D2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173892] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173896] pci 0000:00:04.0: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173914] pci 0000:00:04.1: [10de:056a] type 0 class 0x000c03
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.173930] pci 0000:00:04.1: reg 10: [mem 0xefffe000-0xefffe0ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174000] pci 0000:00:04.1: supports D1 D2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174003] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174007] pci 0000:00:04.1: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174036] pci 0000:00:08.0: [10de:056c] type 0 class 0x000101
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174074] pci 0000:00:08.0: reg 20: [io  0xfc00-0xfc0f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174124] pci 0000:00:09.0: [10de:07fc] type 0 class 0x000403
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174140] pci 0000:00:09.0: reg 10: [mem 0xefff4000-0xefff7fff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174209] pci 0000:00:09.0: PME# supported from D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174214] pci 0000:00:09.0: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174230] pci 0000:00:0a.0: [10de:056d] type 1 class 0x000604
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174291] pci 0000:00:0b.0: [10de:056e] type 1 class 0x000604
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174345] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174349] pci 0000:00:0b.0: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174371] pci 0000:00:0c.0: [10de:056f] type 1 class 0x000604
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174424] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174428] pci 0000:00:0c.0: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174450] pci 0000:00:0d.0: [10de:056f] type 1 class 0x000604
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174503] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174507] pci 0000:00:0d.0: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174527] pci 0000:00:0e.0: [10de:07f0] type 0 class 0x000101
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174542] pci 0000:00:0e.0: reg 10: [io  0x09f0-0x09f7]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174550] pci 0000:00:0e.0: reg 14: [io  0x0bf0-0x0bf3]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174557] pci 0000:00:0e.0: reg 18: [io  0x0970-0x0977]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174565] pci 0000:00:0e.0: reg 1c: [io  0x0b70-0x0b73]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174573] pci 0000:00:0e.0: reg 20: [io  0xf700-0xf70f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174581] pci 0000:00:0e.0: reg 24: [mem 0xefff8000-0xefff9fff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174636] pci 0000:00:0f.0: [10de:07dc] type 0 class 0x000200
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174652] pci 0000:00:0f.0: reg 10: [mem 0xefffd000-0xefffdfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174659] pci 0000:00:0f.0: reg 14: [io  0xf600-0xf607]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174667] pci 0000:00:0f.0: reg 18: [mem 0xefffc000-0xefffc0ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174675] pci 0000:00:0f.0: reg 1c: [mem 0xefffb000-0xefffb00f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174723] pci 0000:00:0f.0: supports D1 D2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174726] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174731] pci 0000:00:0f.0: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174748] pci 0000:00:10.0: [10de:07e1] type 0 class 0x000300
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174762] pci 0000:00:10.0: reg 10: [mem 0xed000000-0xedffffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174772] pci 0000:00:10.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174783] pci 0000:00:10.0: reg 1c: [mem 0xee000000-0xeeffffff 64bit]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174795] pci 0000:00:10.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174889] pci 0000:01:07.0: [1106:3044] type 0 class 0x000c00
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174908] pci 0000:01:07.0: reg 10: [mem 0xefbff000-0xefbff7ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174919] pci 0000:01:07.0: reg 14: [io  0xcf00-0xcf7f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174991] pci 0000:01:07.0: supports D2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174994] pci 0000:01:07.0: PME# supported from D2 D3hot D3cold
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.174999] pci 0000:01:07.0: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175038] pci 0000:00:0a.0: PCI bridge to [bus 01-01] (subtractive decode)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175042] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175047] pci 0000:00:0a.0:   bridge window [mem 0xefb00000-0xefbfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175051] pci 0000:00:0a.0:   bridge window [mem 0xefa00000-0xefafffff pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175055] pci 0000:00:0a.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175058] pci 0000:00:0a.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175061] pci 0000:00:0a.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175064] pci 0000:00:0a.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175068] pci 0000:00:0a.0:   bridge window [mem 0x7ff00000-0xfebfffff] (subtractive decode)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175105] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175110] pci 0000:00:0b.0:   bridge window [io  0xb000-0xbfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175114] pci 0000:00:0b.0:   bridge window [mem 0xef900000-0xef9fffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175120] pci 0000:00:0b.0:   bridge window [mem 0xef800000-0xef8fffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175170] pci 0000:03:00.0: [14f1:2f82] type 0 class 0x000780
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175190] pci 0000:03:00.0: reg 10: [mem 0xef7f0000-0xef7fffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175322] pci 0000:03:00.0: supports D1 D2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175325] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175331] pci 0000:03:00.0: PME# disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175353] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175364] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175369] pci 0000:00:0c.0:   bridge window [io  0xe000-0xefff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175373] pci 0000:00:0c.0:   bridge window [mem 0xef700000-0xef7fffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175379] pci 0000:00:0c.0:   bridge window [mem 0xefe00000-0xefefffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175415] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175421] pci 0000:00:0d.0:   bridge window [io  0xd000-0xdfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175425] pci 0000:00:0d.0:   bridge window [mem 0xefd00000-0xefdfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175430] pci 0000:00:0d.0:   bridge window [mem 0xefc00000-0xefcfffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175446] pci_bus 0000:00: on NUMA node 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.175882]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.176108]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0c
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.176110] ACPI _OSC control for PCIe not granted, disabling ASPM
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.209558] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.209618] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.209674] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.209732] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.209798] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.209854] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.209910] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.209971] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210026] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210083] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210139] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 *7 9 10 11 14 15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210194] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210254] ACPI: PCI Interrupt Link [LU1B] (IRQs 5 7 9 10 11 14 15) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210309] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 10 11 14 15) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210366] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210421] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210480] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210536] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210591] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210648] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210755] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210850] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.210945] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211038] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211131] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211225] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211320] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211413] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211507] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211603] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211698] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211792] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211891] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.211987] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212102] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212198] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212293] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212389] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212485] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212580] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212765] vgaarb: device added: PCI:0000:00:10.0,decodes=io+mem,owns=io+mem,locks=none
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212769] vgaarb: loaded
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212772] vgaarb: bridge control possible 0000:00:10.0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212914] i2c-core: driver [aat2870] using legacy suspend method
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.212916] i2c-core: driver [aat2870] using legacy resume method
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.213013] SCSI subsystem initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.216166] libata version 3.00 loaded.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.216166] usbcore: registered new interface driver usbfs
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.216166] usbcore: registered new interface driver hub
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.216176] usbcore: registered new device driver usb
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.216306] PCI: Using ACPI for IRQ routing
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217257] PCI: pci_cache_line_size set to 64 bytes
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217404] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217408] reserve RAM buffer: 0000000077000000 - 0000000077ffffff 
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217411] reserve RAM buffer: 000000007fd90000 - 000000007fffffff 
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217548] NetLabel: Initializing
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217551] NetLabel:  domain hash size = 128
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217553] NetLabel:  protocols = UNLABELED CIPSOv4
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217565] NetLabel:  unlabeled traffic allowed by default
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217637] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217643] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.217650] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.220292] Switching to clocksource hpet
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230370] AppArmor: AppArmor Filesystem Enabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230412] pnp: PnP ACPI init
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230444] ACPI: bus type pnp registered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230580] pnp 00:00: [bus 00-ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230583] pnp 00:00: [io  0x0cf8-0x0cff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230587] pnp 00:00: [io  0x0000-0x0cf7 window]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230590] pnp 00:00: [io  0x0d00-0xffff window]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230593] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230596] pnp 00:00: [mem 0x000c0000-0x000dffff window]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230599] pnp 00:00: [mem 0x7ff00000-0xfebfffff window]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230681] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230841] pnp 00:01: [io  0x1000-0x107f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230844] pnp 00:01: [io  0x1080-0x10ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230847] pnp 00:01: [io  0x1400-0x147f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230849] pnp 00:01: [io  0x1480-0x14ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230852] pnp 00:01: [io  0x1800-0x187f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230854] pnp 00:01: [io  0x1880-0x18ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230857] pnp 00:01: [mem 0xfec80000-0xfecbffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230860] pnp 00:01: [mem 0xfefe0000-0xfefe01ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230862] pnp 00:01: [mem 0xfefe1000-0xfefe10ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230865] pnp 00:01: [mem 0x77000000-0x7effffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230950] system 00:01: [io  0x1000-0x107f] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230953] system 00:01: [io  0x1080-0x10ff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230957] system 00:01: [io  0x1400-0x147f] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230960] system 00:01: [io  0x1480-0x14ff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230963] system 00:01: [io  0x1800-0x187f] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230966] system 00:01: [io  0x1880-0x18ff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230970] system 00:01: [mem 0xfec80000-0xfecbffff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230973] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230977] system 00:01: [mem 0xfefe1000-0xfefe10ff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230980] system 00:01: [mem 0x77000000-0x7effffff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.230985] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231057] pnp 00:02: [io  0x0010-0x001f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231060] pnp 00:02: [io  0x0022-0x003f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231063] pnp 00:02: [io  0x0044-0x005f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231065] pnp 00:02: [io  0x0062-0x0063]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231067] pnp 00:02: [io  0x0065-0x006f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231070] pnp 00:02: [io  0x0074-0x007f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231072] pnp 00:02: [io  0x0091-0x0093]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231075] pnp 00:02: [io  0x00a2-0x00bf]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231077] pnp 00:02: [io  0x00e0-0x00ef]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231079] pnp 00:02: [io  0x04d0-0x04d1]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231082] pnp 00:02: [io  0x0220-0x0225]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231084] pnp 00:02: [io  0x0880-0x088f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231163] system 00:02: [io  0x04d0-0x04d1] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231167] system 00:02: [io  0x0220-0x0225] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231170] system 00:02: [io  0x0880-0x088f] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231174] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231189] pnp 00:03: [dma 4]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231191] pnp 00:03: [io  0x0000-0x000f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231194] pnp 00:03: [io  0x0080-0x0090]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231197] pnp 00:03: [io  0x0094-0x009f]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231199] pnp 00:03: [io  0x00c0-0x00df]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231242] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231303] pnp 00:04: [irq 0 disabled]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231318] pnp 00:04: [irq 8]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231320] pnp 00:04: [mem 0xfeff0000-0xfeff03ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231368] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231400] pnp 00:05: [io  0x0070-0x0073]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231445] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231456] pnp 00:06: [io  0x0061]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231499] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231509] pnp 00:07: [io  0x00f0-0x00ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231517] pnp 00:07: [irq 13]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231562] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231605] pnp 00:08: [io  0x0060]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231607] pnp 00:08: [io  0x0064]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231614] pnp 00:08: [irq 1]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.231667] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232370] pnp 00:09: [mem 0xf0000000-0xf1ffffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232481] system 00:09: [mem 0xf0000000-0xf1ffffff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232486] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232548] pnp 00:0a: [mem 0x000f0000-0x000fffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232552] pnp 00:0a: [mem 0xfeff0000-0xfeff00ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232554] pnp 00:0a: [mem 0x7fee0000-0x7fefffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232557] pnp 00:0a: [mem 0xffff0000-0xffffffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232560] pnp 00:0a: [mem 0x00000000-0x0009ffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232562] pnp 00:0a: [mem 0x00100000-0x7fedffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232565] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232567] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232570] pnp 00:0a: [mem 0xfeff0000-0xfeff03ff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232673] system 00:0a: [mem 0x000f0000-0x000fffff] could not be reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232677] system 00:0a: [mem 0xfeff0000-0xfeff00ff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232681] system 00:0a: [mem 0x7fee0000-0x7fefffff] could not be reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232684] system 00:0a: [mem 0xffff0000-0xffffffff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232688] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232691] system 00:0a: [mem 0x00100000-0x7fedffff] could not be reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232694] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232698] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232701] system 00:0a: [mem 0xfeff0000-0xfeff03ff] could not be reserved
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232705] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232717] pnp: PnP ACPI: found 11 devices
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232719] ACPI: ACPI bus type pnp unregistered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.232724] PnPBIOS: Disabled by ACPI PNP
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269579] PCI: max bus depth: 1 pci_try_num: 2
Jul  5 13:28:30 UBUNTU-Casa bluetoothd[813]: Failed to init alert plugin
Jul  5 13:28:30 UBUNTU-Casa bluetoothd[813]: Failed to init time plugin
Jul  5 13:28:30 UBUNTU-Casa bluetoothd[813]: Failed to init proximity plugin
Jul  5 13:28:30 UBUNTU-Casa bluetoothd[813]: Failed to init gatt_example plugin
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  ModemManager (version 0.5.2.0) starting...
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin AnyData
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Linktop
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin ZTE
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Nokia
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin MotoC
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin X22X
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin SimTech
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Longcheer
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Wavecom
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Generic
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Option
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Samsung
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Ericsson MBM
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Novatel
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Option High-Speed
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Gobi
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Sierra
Jul  5 13:28:30 UBUNTU-Casa modem-manager[878]: <info>  Loaded plugin Huawei
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269626] pci 0000:00:10.0: BAR 6: assigned [mem 0x7ff00000-0x7ff1ffff pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269631] pci 0000:00:0a.0: PCI bridge to [bus 01-01]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269634] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269640] pci 0000:00:0a.0:   bridge window [mem 0xefb00000-0xefbfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269644] pci 0000:00:0a.0:   bridge window [mem 0xefa00000-0xefafffff pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269651] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269654] pci 0000:00:0b.0:   bridge window [io  0xb000-0xbfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269659] pci 0000:00:0b.0:   bridge window [mem 0xef900000-0xef9fffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269663] pci 0000:00:0b.0:   bridge window [mem 0xef800000-0xef8fffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269669] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269672] pci 0000:00:0c.0:   bridge window [io  0xe000-0xefff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269677] pci 0000:00:0c.0:   bridge window [mem 0xef700000-0xef7fffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269681] pci 0000:00:0c.0:   bridge window [mem 0xefe00000-0xefefffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269687] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269690] pci 0000:00:0d.0:   bridge window [io  0xd000-0xdfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269695] pci 0000:00:0d.0:   bridge window [mem 0xefd00000-0xefdfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269699] pci 0000:00:0d.0:   bridge window [mem 0xefc00000-0xefcfffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269715] pci 0000:00:0a.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269722] pci 0000:00:0b.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269729] pci 0000:00:0c.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269735] pci 0000:00:0d.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269739] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269742] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269745] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269748] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269751] pci_bus 0000:00: resource 8 [mem 0x7ff00000-0xfebfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269754] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269757] pci_bus 0000:01: resource 1 [mem 0xefb00000-0xefbfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269760] pci_bus 0000:01: resource 2 [mem 0xefa00000-0xefafffff pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269763] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269765] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269768] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269771] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269774] pci_bus 0000:01: resource 8 [mem 0x7ff00000-0xfebfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269777] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269780] pci_bus 0000:02: resource 1 [mem 0xef900000-0xef9fffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269783] pci_bus 0000:02: resource 2 [mem 0xef800000-0xef8fffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269786] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269788] pci_bus 0000:03: resource 1 [mem 0xef700000-0xef7fffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269791] pci_bus 0000:03: resource 2 [mem 0xefe00000-0xefefffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269794] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269797] pci_bus 0000:04: resource 1 [mem 0xefd00000-0xefdfffff]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269800] pci_bus 0000:04: resource 2 [mem 0xefc00000-0xefcfffff 64bit pref]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269865] NET: Registered protocol family 2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.269960] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.270279] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.270878] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.271257] TCP: Hash tables configured (established 131072 bind 65536)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.271260] TCP reno registered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.271264] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.271278] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.271409] NET: Registered protocol family 1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.271741] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.271763] pci 0000:00:04.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.340051] pci 0000:00:04.0: PCI INT A disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.340285] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.340305] pci 0000:00:04.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.340329] pci 0000:00:04.1: PCI INT B disabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.340399] pci 0000:00:10.0: Boot video device
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.340408] PCI: CLS 64 bytes, default 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.340833] audit: initializing netlink socket (disabled)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.340847] type=2000 audit(1341509298.336:1): initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.370642] highmem bounce pool size: 64 pages
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.370648] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.381979] VFS: Disk quotas dquot_6.5.2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.382065] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.382757] fuse init (API version 7.17)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.382874] msgmni has been set to 1685
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383260] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383295] io scheduler noop registered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383297] io scheduler deadline registered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383307] io scheduler cfq registered (default)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383467] pcieport 0000:00:0b.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383513] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383571] pcieport 0000:00:0c.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383606] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383659] pcieport 0000:00:0d.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383693] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383781] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383811] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383917] intel_idle: MWAIT substates: 0x220
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.383919] intel_idle: does not run on family 6 model 15
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.384049] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.384055] ACPI: Power Button [PWRB]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.384128] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.384132] ACPI: Power Button [PWRF]
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.384200] ACPI: Fan [FAN] (on)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.386450] thermal LNXTHERM:00: registered as thermal_zone0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.386454] ACPI: Thermal Zone [THRM] (-127 C)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.386515] ERST: Table is not found!
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.386517] GHES: HEST is not enabled!
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.386642] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.386837] isapnp: Scanning for PnP cards...
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.506969] Freeing initrd memory: 13804k freed
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.739991] isapnp: No Plug & Play device found
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.792648] Linux agpgart interface v0.103
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.794638] brd: module loaded
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.795616] loop: module loaded
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.795795] ahci 0000:00:0e.0: version 3.0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.795979] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.795997] ahci 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.796038] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.796041] ahci 0000:00:0e.0: controller can't do PMP, turning off CAP_PMP
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.796110] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.796114] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pio 
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.796118] ahci 0000:00:0e.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797006] scsi0 : ahci
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797133] scsi1 : ahci
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797229] scsi2 : ahci
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797325] scsi3 : ahci
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797483] ata1: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8100 irq 21
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797487] ata2: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8180 irq 21
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797490] ata3: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8200 irq 21
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797493] ata4: SATA max UDMA/133 abar m8192@0xefff8000 port 0xefff8280 irq 21
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.797699] pata_acpi 0000:00:08.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798138] Fixed MDIO Bus: probed
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798163] tun: Universal TUN/TAP device driver, 1.6
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798166] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798264] PPP generic driver version 2.4.2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798404] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798429] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798451] ehci_hcd 0000:00:04.1: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798454] ehci_hcd 0000:00:04.1: EHCI Host Controller
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798510] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798531] ehci_hcd 0000:00:04.1: debug port 1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798540] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.798561] ehci_hcd 0000:00:04.1: irq 22, io mem 0xefffe000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808031] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808249] hub 1-0:1.0: USB hub found
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808254] hub 1-0:1.0: 10 ports detected
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808363] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808382] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808395] ohci_hcd 0000:00:04.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808399] ohci_hcd 0000:00:04.0: OHCI Host Controller
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808457] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.808482] ohci_hcd 0000:00:04.0: irq 23, io mem 0xeffff000
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866160] hub 2-0:1.0: USB hub found
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866166] hub 2-0:1.0: 10 ports detected
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866262] uhci_hcd: USB Universal Host Controller Interface driver
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866333] usbcore: registered new interface driver libusual
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866387] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866390] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866573] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866710] mousedev: PS/2 mouse device common for all mice
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.866902] rtc_cmos 00:05: RTC can wake from S4
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867055] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867092] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867161] device-mapper: uevent: version 1.0.3
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867258] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867300] EISA: Probing bus 0 at eisa.0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867303] EISA: Cannot allocate resource for mainboard
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867306] Cannot allocate resource for EISA slot 1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867308] Cannot allocate resource for EISA slot 2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867310] Cannot allocate resource for EISA slot 3
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867313] Cannot allocate resource for EISA slot 4
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867315] Cannot allocate resource for EISA slot 5
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867317] Cannot allocate resource for EISA slot 6
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867319] Cannot allocate resource for EISA slot 7
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867321] Cannot allocate resource for EISA slot 8
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867323] EISA: Detected 0 cards.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867335] cpufreq-nforce2: No nForce2 chipset.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867338] cpuidle: using governor ladder
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867340] cpuidle: using governor menu
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867342] EFI Variables Facility v0.08 2004-May-17
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867661] TCP cubic registered
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.867810] NET: Registered protocol family 10
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.868511] NET: Registered protocol family 17
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.868516] Registering the dns_resolver key type
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.868540] Using IPI No-Shortcut mode
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.868691] PM: Hibernation image not present or could not be loaded.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.868704] registered taskstats version 1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.880753]   Magic number: 4:111:491
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.880862] rtc_cmos 00:05: setting system clock to 2012-07-05 17:28:20 UTC (1341509300)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.881205] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.881208] EDD information not available.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    0.886891] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.116043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.116063] ata4: SATA link down (SStatus 0 SControl 300)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.116083] ata3: SATA link down (SStatus 0 SControl 300)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.116098] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.117226] ata2.00: ATAPI: Optiarc DVD RW AD-7201S5, 1H0B, max UDMA/100
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.118655] ata2.00: configured for UDMA/100
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.121329] ata1.00: ATA-7: SAMSUNG HD250HJ, FH100-05, max UDMA7
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.121335] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.126664] ata1.00: configured for UDMA/133
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.126860] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD250HJ  FH10 PQ: 0 ANSI: 5
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.127011] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.127051] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.127066] sd 0:0:0:0: [sda] Write Protect is off
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.127070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.127094] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.128721] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7201S5 1H0B PQ: 0 ANSI: 5
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.131029] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.131034] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.131229] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.131308] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.162079]  sda: sda1 sda2 < sda5 >
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.162551] sd 0:0:0:0: [sda] Attached SCSI disk
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.162645] Freeing unused kernel memory: 740k freed
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.163016] Write protecting the kernel text: 5816k
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.163038] Write protecting the kernel read-only data: 2376k
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.163040] NX-protecting the kernel data: 4424k
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.176040] usb 1-9: new high-speed USB device number 3 using ehci_hcd
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.305441] pata_amd 0000:00:08.0: version 0.4.1
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.305496] pata_amd 0000:00:08.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.309663] scsi4 : pata_amd
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.311799] scsi5 : pata_amd
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.313078] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.313082] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.313146] ata5: port disabled--ignoring
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.313184] ata6: port disabled--ignoring
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.320383] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.320406] firewire_ohci 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.320414] firewire_ohci 0000:01:07.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.325033] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.325265] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.325285] forcedeth 0000:00:0f.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.325292] forcedeth 0000:00:0f.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.334523] Initializing USB Mass Storage driver...
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.335231] scsi6 : usb-storage 1-9:1.0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.335328] usbcore: registered new interface driver usb-storage
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.335330] USB Mass Storage support registered.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.340072] Refined TSC clocksource calibration: 1999.999 MHz.
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.340079] Switching to clocksource tsc
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.384085] firewire_ohci: Added fw-ohci device 0000:01:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.472940] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.632030] usb 2-7: new low-speed USB device number 2 using ohci_hcd
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.849137] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 13, addr 00:1c:25:8e:09:f7
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.849142] forcedeth 0000:00:0f.0: highdma pwrctl mgmt lnktim msi desc-v3
Jul  5 13:28:30 UBUNTU-Casa kernel: [    1.884161] firewire_core: created device fw0: GUID 00016c20005344bd, S400
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.339003] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.345498] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.352121] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.358745] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.359426] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.359614] sd 6:0:0:1: Attached scsi generic sg3 type 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.359784] sd 6:0:0:2: Attached scsi generic sg4 type 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.359951] sd 6:0:0:3: Attached scsi generic sg5 type 0
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.365987] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.366853] sd 6:0:0:1: [sdc] Attached SCSI removable disk
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.368362] sd 6:0:0:2: [sdd] Attached SCSI removable disk
Jul  5 13:28:30 UBUNTU-Casa kernel: [    2.369231] sd 6:0:0:3: [sde] Attached SCSI removable disk
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.111872] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.199662] lp: driver loaded but no devices found
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.219363] Adding 1961980k swap on /dev/sda5.  Priority:-1 extents:1 across:1961980k 
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.297337] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.297412] i2c i2c-1: nForce2 SMBus adapter at 0x1c80
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.363499] wmi: Mapper loaded
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.381922] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.499376] type=1400 audit(1341509310.113:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=600 comm="apparmor_parser"
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.499887] type=1400 audit(1341509310.113:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=600 comm="apparmor_parser"
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.500212] type=1400 audit(1341509310.117:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=600 comm="apparmor_parser"
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.510957] nvidia: module license 'NVIDIA' taints kernel.
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.510964] Disabling lock debugging due to kernel taint
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.901692] input: Genius       Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.0/input/input3
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.902041] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.10 Mouse [Genius       Optical Mouse] on usb-0000:00:04.0-7/input0
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.902577] usbcore: registered new interface driver usbhid
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.902580] usbhid: USB HID core driver
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.913778] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 23
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.913789] nvidia 0000:00:10.0: PCI INT A -> Link[AIGP] -> GSI 23 (level, low) -> IRQ 23
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.913799] nvidia 0000:00:10.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.913805] vgaarb: device changed decodes: PCI:0000:00:10.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.914233] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.59  Wed Jun  6 21:24:41 PDT 2012
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.980041] snd_hda_intel 0000:00:09.0: power state changed by ACPI to D0
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.980048] snd_hda_intel 0000:00:09.0: power state changed by ACPI to D0
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.980225] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.980231] snd_hda_intel 0000:00:09.0: PCI INT A -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.980234] hda_intel: Disabling MSI
Jul  5 13:28:30 UBUNTU-Casa kernel: [   10.980263] snd_hda_intel 0000:00:09.0: setting latency timer to 64
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.279106] Bluetooth: Core ver 2.16
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.280900] NET: Registered protocol family 31
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.280904] Bluetooth: HCI device and connection manager initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.280908] Bluetooth: HCI socket layer initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.280911] Bluetooth: L2CAP socket layer initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.281373] Bluetooth: SCO socket layer initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.302087] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.302092] Bluetooth: BNEP filters: protocol multicast
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.308102] Bluetooth: RFCOMM TTY layer initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.308109] Bluetooth: RFCOMM socket layer initialized
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.308112] Bluetooth: RFCOMM ver 1.11
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.332390] ppdev: user-space parallel port driver
Jul  5 13:28:30 UBUNTU-Casa kernel: [   11.333301] init: failsafe main process (819) killed by TERM signal
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> NetworkManager (version 0.9.4.0) is starting...
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> DNS: loaded plugin dnsmasq
Jul  5 13:28:31 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.412201] type=1400 audit(1341509311.029:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=907 comm="apparmor_parser"
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.412845] type=1400 audit(1341509311.029:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=907 comm="apparmor_parser"
Jul  5 13:28:31 UBUNTU-Casa polkitd[897]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jul  5 13:28:31 UBUNTU-Casa dbus[792]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: init!
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: update_system_hostname
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPluginIfupdown: management mode: unmanaged
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0f.0/net/eth0, iface: eth0)
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0f.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: end _init.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    Ifupdown: get unmanaged devices count: 0
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: (162485160) ... get_connections.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    SCPlugin-Ifupdown: (162485160) ... get_connections (managed=false): return empty list.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]:    Ifupdown: get unmanaged devices count: 0
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> modem-manager is now available
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.450364] type=1400 audit(1341509311.065:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=931 comm="apparmor_parser"
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Networking is enabled by state file
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <warn> failed to allocate link cache: (-10) Operation not supported
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): carrier is OFF
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.461088] type=1400 audit(1341509311.077:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=931 comm="apparmor_parser"
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.461370] type=1400 audit(1341509311.077:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=931 comm="apparmor_parser"
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.461602] type=1400 audit(1341509311.077:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=930 comm="apparmor_parser"
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): now managed
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): bringing up device.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): carrier now ON (device state 20)
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.468526] forcedeth 0000:00:0f.0: irq 43 for MSI/MSI-X
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): preparing device.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0f.0/net/eth0
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.478547] type=1400 audit(1341509311.093:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=936 comm="apparmor_parser"
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Auto-activating connection 'Wired connection 1'.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> dhclient started with pid 941
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Beginning IP6 addrconf.
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul  5 13:28:31 UBUNTU-Casa dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jul  5 13:28:31 UBUNTU-Casa dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jul  5 13:28:31 UBUNTU-Casa dhclient: All rights reserved.
Jul  5 13:28:31 UBUNTU-Casa dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul  5 13:28:31 UBUNTU-Casa dhclient: 
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul  5 13:28:31 UBUNTU-Casa dhclient: Listening on LPF/eth0/00:1c:25:8e:09:f7
Jul  5 13:28:31 UBUNTU-Casa dhclient: Sending on   LPF/eth0/00:1c:25:8e:09:f7
Jul  5 13:28:31 UBUNTU-Casa dhclient: Sending on   Socket/fallback
Jul  5 13:28:31 UBUNTU-Casa dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul  5 13:28:31 UBUNTU-Casa dhclient: DHCPREQUEST of 192.168.1.160 on eth0 to 255.255.255.255 port 67
Jul  5 13:28:31 UBUNTU-Casa dhclient: DHCPOFFER of 192.168.1.160 from 192.168.1.254
Jul  5 13:28:31 UBUNTU-Casa dhclient: DHCPACK of 192.168.1.160 from 192.168.1.254
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info>   address 192.168.1.160
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info>   prefix 24 (255.255.255.0)
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info>   gateway 192.168.1.254
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info>   nameserver '192.168.1.254'
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info>   domain name 'iptv.microsoft.com'
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul  5 13:28:31 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jul  5 13:28:31 UBUNTU-Casa dhclient: bound to 192.168.1.160 -- renewal in 39740 seconds.
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.624807] init: alsa-restore main process (985) terminated with status 19
Jul  5 13:28:31 UBUNTU-Casa anacron[1003]: Anacron 2.3 started on 2012-07-05
Jul  5 13:28:31 UBUNTU-Casa cron[986]: (CRON) INFO (pidfile fd = 3)
Jul  5 13:28:31 UBUNTU-Casa acpid: starting up with proc fs
Jul  5 13:28:31 UBUNTU-Casa acpid: 35 rules loaded
Jul  5 13:28:31 UBUNTU-Casa acpid: waiting for events: event logging is off
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.660064] hda_codec: ALC1200: BIOS auto-probing.
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.660071] hda_codec: ALC1200: SKU not ready 0x411111f0
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.671412] vboxdrv: Found 2 processor cores.
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.672250] vboxdrv: fAsync=0 offMin=0x1f4 offMax=0x884
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.672345] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.672348] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jul  5 13:28:31 UBUNTU-Casa cron[1023]: (CRON) STARTUP (fork ok)
Jul  5 13:28:31 UBUNTU-Casa cron[1023]: (CRON) INFO (Running @reboot jobs)
Jul  5 13:28:31 UBUNTU-Casa kernel: [   11.692900] vboxpci: IOMMU not found (not registered)
Jul  5 13:28:31 UBUNTU-Casa anacron[1003]: Normal exit (0 jobs run)
Jul  5 13:28:31 UBUNTU-Casa anacron[1134]: Anacron 2.3 started on 2012-07-05
Jul  5 13:28:31 UBUNTU-Casa anacron[1134]: Normal exit (0 jobs run)
Jul  5 13:28:31 UBUNTU-Casa udev-configure-printer: add /module/lp
Jul  5 13:28:31 UBUNTU-Casa udev-configure-printer: Failed to get parent
Jul  5 13:28:32 UBUNTU-Casa NetworkManager[889]: <info> DNS: starting dnsmasq...
Jul  5 13:28:32 UBUNTU-Casa NetworkManager[889]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jul  5 13:28:32 UBUNTU-Casa dnsmasq[1179]: started, version 2.59 cache disabled
Jul  5 13:28:32 UBUNTU-Casa dnsmasq[1179]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jul  5 13:28:32 UBUNTU-Casa dnsmasq[1179]: using nameserver 192.168.1.254#53
Jul  5 13:28:32 UBUNTU-Casa NetworkManager[889]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul  5 13:28:32 UBUNTU-Casa NetworkManager[889]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jul  5 13:28:32 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) successful, device activated.
Jul  5 13:28:32 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jul  5 13:28:32 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul  5 13:28:32 UBUNTU-Casa kernel: [   12.652190] input: HDA NVidia Line as /devices/pci0000:00/0000:00:09.0/sound/card0/input4
Jul  5 13:28:32 UBUNTU-Casa kernel: [   12.652315] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:09.0/sound/card0/input5
Jul  5 13:28:32 UBUNTU-Casa kernel: [   12.652482] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:09.0/sound/card0/input6
Jul  5 13:28:32 UBUNTU-Casa kernel: [   12.652730] input: HDA NVidia Line-Out as /devices/pci0000:00/0000:00:09.0/sound/card0/input7
Jul  5 13:28:32 UBUNTU-Casa dbus[792]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul  5 13:28:32 UBUNTU-Casa kernel: [   13.103425] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jul  5 13:28:32 UBUNTU-Casa kernel: [   13.103430] vesafb: scrolling: redraw
Jul  5 13:28:32 UBUNTU-Casa kernel: [   13.103433] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jul  5 13:28:32 UBUNTU-Casa kernel: [   13.105138] vesafb: framebuffer at 0xd0000000, mapped to 0xf8900000, using 1216k, total 1216k
Jul  5 13:28:32 UBUNTU-Casa kernel: [   13.106009] Console: switching to colour frame buffer device 80x30
Jul  5 13:28:32 UBUNTU-Casa kernel: [   13.106027] fb0: VESA VGA frame buffer device
Jul  5 13:28:32 UBUNTU-Casa kernel: [   13.126402] init: plymouth-splash main process (1332) terminated with status 1
Jul  5 13:28:32 UBUNTU-Casa acpid: client connected from 1343[0:0]
Jul  5 13:28:32 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:28:33 UBUNTU-Casa kernel: [   13.870094] NVRM: Your system is not currently configured to drive a VGA console
Jul  5 13:28:33 UBUNTU-Casa kernel: [   13.870099] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
Jul  5 13:28:33 UBUNTU-Casa kernel: [   13.870102] NVRM: requires the use of a text-mode VGA console. Use of other console
Jul  5 13:28:33 UBUNTU-Casa kernel: [   13.870105] NVRM: drivers including, but not limited to, vesafb, may result in
Jul  5 13:28:33 UBUNTU-Casa kernel: [   13.870108] NVRM: corruption and stability problems, and is not supported.
Jul  5 13:28:33 UBUNTU-Casa acpid: client connected from 1343[0:0]
Jul  5 13:28:33 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:28:33 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul  5 13:28:33 UBUNTU-Casa dbus[792]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul  5 13:28:33 UBUNTU-Casa accounts-daemon[1354]: started daemon version 0.6.15
Jul  5 13:28:33 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jul  5 13:28:33 UBUNTU-Casa dbus[792]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jul  5 13:28:34 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul  5 13:28:34 UBUNTU-Casa dbus[792]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul  5 13:28:34 UBUNTU-Casa anacron[1555]: Anacron 2.3 started on 2012-07-05
Jul  5 13:28:34 UBUNTU-Casa anacron[1555]: Normal exit (0 jobs run)
Jul  5 13:28:34 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul  5 13:28:34 UBUNTU-Casa dbus[792]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul  5 13:28:35 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul  5 13:28:35 UBUNTU-Casa dbus[792]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Successfully called chroot.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Successfully dropped privileges.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Successfully limited resources.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Running.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Canary thread running.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 1680 of process 1680 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Supervising 1 threads of 1 processes of 1 users.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Watchdog thread running.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 1694 of process 1680 (n/a) owned by '104' RT at priority 5.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Supervising 2 threads of 1 processes of 1 users.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 1695 of process 1680 (n/a) owned by '104' RT at priority 5.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Supervising 3 threads of 1 processes of 1 users.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 1698 of process 1698 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:28:35 UBUNTU-Casa rtkit-daemon[1682]: Supervising 4 threads of 2 processes of 1 users.
Jul  5 13:28:35 UBUNTU-Casa pulseaudio[1698]: [pulseaudio] pid.c: Daemon already running.
Jul  5 13:28:41 UBUNTU-Casa ntpdate[1284]: adjust time server 91.189.94.4 offset -0.357050 sec
Jul  5 13:28:41 UBUNTU-Casa kernel: [   21.700014] eth0: no IPv6 routers present
Jul  5 13:28:45 UBUNTU-Casa gnome-session[1747]: WARNING: Session 'gnome' runnable check failed: Exited with code 1
Jul  5 13:28:46 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 1831 of process 1831 (n/a) owned by '1000' high priority at nice level -11.
Jul  5 13:28:46 UBUNTU-Casa rtkit-daemon[1682]: Supervising 4 threads of 2 processes of 2 users.
Jul  5 13:28:46 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 1836 of process 1831 (n/a) owned by '1000' RT at priority 5.
Jul  5 13:28:46 UBUNTU-Casa rtkit-daemon[1682]: Supervising 5 threads of 2 processes of 2 users.
Jul  5 13:28:46 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 1837 of process 1831 (n/a) owned by '1000' RT at priority 5.
Jul  5 13:28:46 UBUNTU-Casa rtkit-daemon[1682]: Supervising 6 threads of 2 processes of 2 users.
Jul  5 13:28:48 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jul  5 13:28:48 UBUNTU-Casa dbus[792]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jul  5 13:28:51 UBUNTU-Casa NetworkManager[889]: <info> (eth0): IP6 addrconf timed out or failed.
Jul  5 13:28:51 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul  5 13:28:51 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul  5 13:28:51 UBUNTU-Casa NetworkManager[889]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul  5 13:29:04 UBUNTU-Casa goa[2084]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jul  5 13:29:15 UBUNTU-Casa acpid: client 1343[0:0] has disconnected
Jul  5 13:29:15 UBUNTU-Casa acpid: client 1343[0:0] has disconnected
Jul  5 13:29:15 UBUNTU-Casa acpid: client connected from 2129[0:0]
Jul  5 13:29:15 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:29:16 UBUNTU-Casa acpid: client connected from 2129[0:0]
Jul  5 13:29:16 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:29:17 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 2240 of process 2240 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:29:17 UBUNTU-Casa rtkit-daemon[1682]: Supervising 4 threads of 2 processes of 2 users.
Jul  5 13:29:17 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 2247 of process 2240 (n/a) owned by '104' RT at priority 5.
Jul  5 13:29:17 UBUNTU-Casa rtkit-daemon[1682]: Supervising 5 threads of 2 processes of 2 users.
Jul  5 13:29:17 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 2248 of process 2240 (n/a) owned by '104' RT at priority 5.
Jul  5 13:29:17 UBUNTU-Casa rtkit-daemon[1682]: Supervising 6 threads of 2 processes of 2 users.
Jul  5 13:29:17 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 2251 of process 2251 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:29:17 UBUNTU-Casa rtkit-daemon[1682]: Supervising 7 threads of 3 processes of 2 users.
Jul  5 13:29:17 UBUNTU-Casa pulseaudio[2251]: [pulseaudio] pid.c: Daemon already running.
Jul  5 13:29:31 UBUNTU-Casa gnome-session[2300]: WARNING: Session 'gnome' runnable check failed: Exited with code 1
Jul  5 13:29:46 UBUNTU-Casa acpid: client connected from 2624[0:0]
Jul  5 13:29:46 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:29:46 UBUNTU-Casa acpid: client 2129[0:0] has disconnected
Jul  5 13:29:46 UBUNTU-Casa acpid: client 2129[0:0] has disconnected
Jul  5 13:29:46 UBUNTU-Casa acpid: client connected from 2624[0:0]
Jul  5 13:29:46 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:29:46 UBUNTU-Casa goa[2638]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jul  5 13:29:48 UBUNTU-Casa gnome-session[2737]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
Jul  5 13:29:48 UBUNTU-Casa kernel: [   89.301660] audit_printk_skb: 36 callbacks suppressed
Jul  5 13:29:48 UBUNTU-Casa kernel: [   89.301664] type=1400 audit(1341509388.915:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2784/cmdline" pid=2779 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:29:48 UBUNTU-Casa kernel: [   89.304513] type=1400 audit(1341509388.919:25): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2785/cmdline" pid=2779 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:29:48 UBUNTU-Casa kernel: [   89.316339] type=1400 audit(1341509388.931:26): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2787/cmdline" pid=2779 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:29:48 UBUNTU-Casa kernel: [   89.328400] type=1400 audit(1341509388.943:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2789/cmdline" pid=2779 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:29:48 UBUNTU-Casa kernel: [   89.341857] type=1400 audit(1341509388.955:28): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2794/cmdline" pid=2779 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:29:49 UBUNTU-Casa kernel: [   89.461572] type=1400 audit(1341509389.075:29): apparmor="DENIED" operation="mount" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/tmp/guest-4laP9a/.gvfs/" pid=2809 comm="gvfs-fuse-daemo" fstype="fuse.gvfs-fuse-daemon" srcname="gvfs-fuse-daemon" flags="rw, nosuid, nodev"
Jul  5 13:29:49 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 2832 of process 2832 (n/a) owned by '116' high priority at nice level -11.
Jul  5 13:29:49 UBUNTU-Casa rtkit-daemon[1682]: Supervising 7 threads of 3 processes of 3 users.
Jul  5 13:29:50 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 2833 of process 2832 (n/a) owned by '116' RT at priority 5.
Jul  5 13:29:50 UBUNTU-Casa rtkit-daemon[1682]: Supervising 8 threads of 3 processes of 3 users.
Jul  5 13:29:50 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 2834 of process 2832 (n/a) owned by '116' RT at priority 5.
Jul  5 13:29:50 UBUNTU-Casa rtkit-daemon[1682]: Supervising 9 threads of 3 processes of 3 users.
Jul  5 13:29:53 UBUNTU-Casa kernel: [   93.419322] type=1400 audit(1341509393.033:30): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2701/stat" pid=2896 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:29:53 UBUNTU-Casa kernel: [   93.419375] type=1400 audit(1341509393.033:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1336/stat" pid=2896 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:29:56 UBUNTU-Casa kernel: [   96.646444] type=1400 audit(1341509396.260:32): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/2701/stat" pid=2896 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:29:56 UBUNTU-Casa kernel: [   96.646496] type=1400 audit(1341509396.260:33): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1336/stat" pid=2896 comm="bamfdaemon" requested_mask="r" denied_mask="r" fsuid=116 ouid=0
Jul  5 13:30:01 UBUNTU-Casa acpid: client 2624[0:0] has disconnected
Jul  5 13:30:01 UBUNTU-Casa acpid: client 2624[0:0] has disconnected
Jul  5 13:30:01 UBUNTU-Casa acpid: client connected from 3129[0:0]
Jul  5 13:30:01 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:30:01 UBUNTU-Casa acpid: client connected from 3129[0:0]
Jul  5 13:30:01 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:30:03 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 3245 of process 3245 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:30:03 UBUNTU-Casa rtkit-daemon[1682]: Supervising 4 threads of 2 processes of 3 users.
Jul  5 13:30:04 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 3251 of process 3245 (n/a) owned by '104' RT at priority 5.
Jul  5 13:30:04 UBUNTU-Casa rtkit-daemon[1682]: Supervising 5 threads of 2 processes of 3 users.
Jul  5 13:30:04 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 3252 of process 3245 (n/a) owned by '104' RT at priority 5.
Jul  5 13:30:04 UBUNTU-Casa rtkit-daemon[1682]: Supervising 6 threads of 2 processes of 3 users.
Jul  5 13:30:04 UBUNTU-Casa rtkit-daemon[1682]: Successfully made thread 3255 of process 3255 (n/a) owned by '104' high priority at nice level -11.
Jul  5 13:30:04 UBUNTU-Casa rtkit-daemon[1682]: Supervising 7 threads of 3 processes of 3 users.
Jul  5 13:30:04 UBUNTU-Casa pulseaudio[3255]: [pulseaudio] pid.c: Daemon already running.
Jul  5 13:30:09 UBUNTU-Casa acpid: client 3129[0:0] has disconnected
Jul  5 13:30:09 UBUNTU-Casa acpid: client 3129[0:0] has disconnected
Jul  5 13:30:09 UBUNTU-Casa acpid: client connected from 2129[0:0]
Jul  5 13:30:09 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:30:09 UBUNTU-Casa acpid: client connected from 2129[0:0]
Jul  5 13:30:09 UBUNTU-Casa acpid: 1 client rule loaded
Jul  5 13:30:34 UBUNTU-Casa dbus[792]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)


```
Here my  Xorg.0.log

```

[    19.776] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    19.776] X Protocol Version 11, Revision 0
[    19.776] Build Operating System: Linux 2.6.42-23-generic i686 Ubuntu
[    19.776] Current Operating System: Linux UBUNTU-Casa 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686
[    19.776] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic-pae root=UUID=2e7fca3e-5c01-451a-a2a2-b09735cc55b0 ro quiet splash vt.handoff=7
[    19.776] Build Date: 26 June 2012  06:59:23AM
[    19.776] xorg-server 2:1.11.4-0ubuntu10.3 (For technical support please see http://www.ubuntu.com/support) 
[    19.776] Current version of pixman: 0.24.4
[    19.776]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    19.776] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.776] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul  5 21:05:06 2012
[    19.841] (==) Using config file: "/etc/X11/xorg.conf"
[    19.841] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.037] (==) ServerLayout "Layout0"
[    20.038] (**) |-->Screen "Screen0" (0)
[    20.038] (**) |   |-->Monitor "Monitor0"
[    20.069] (**) |   |-->Device "Device0"
[    20.087] (**) |-->Input Device "Keyboard0"
[    20.087] (**) |-->Input Device "Mouse0"
[    20.087] (==) Automatically adding devices
[    20.087] (==) Automatically enabling devices
[    20.117] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.117]     Entry deleted from font path.
[    20.117] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.117]     Entry deleted from font path.
[    20.117] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.117]     Entry deleted from font path.
[    20.127] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.127]     Entry deleted from font path.
[    20.127] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.127]     Entry deleted from font path.
[    20.127] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.127]     Entry deleted from font path.
[    20.127] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.127] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.127] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    20.127] (WW) Disabling Keyboard0
[    20.127] (WW) Disabling Mouse0
[    20.140] (II) Loader magic: 0xb77105a0
[    20.140] (II) Module ABI versions:
[    20.140]     X.Org ANSI C Emulation: 0.4
[    20.140]     X.Org Video Driver: 11.0
[    20.140]     X.Org XInput driver : 16.0
[    20.140]     X.Org Server Extension : 6.0
[    20.142] (--) PCI:*(0:0:16:0) 10de:07e1:103c:2a65 rev 162, Mem @ 0xed000000/16777216, 0xd0000000/268435456, 0xee000000/16777216, BIOS @ 0x????????/131072
[    20.142] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.142] (II) LoadModule: "extmod"
[    20.275] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.360] (II) Module extmod: vendor="X.Org Foundation"
[    20.360]     compiled for 1.11.3, module version = 1.0.0
[    20.360]     Module class: X.Org Server Extension
[    20.360]     ABI class: X.Org Server Extension, version 6.0
[    20.360] (II) Loading extension MIT-SCREEN-SAVER
[    20.360] (II) Loading extension XFree86-VidModeExtension
[    20.360] (II) Loading extension XFree86-DGA
[    20.369] (II) Loading extension DPMS
[    20.369] (II) Loading extension XVideo
[    20.369] (II) Loading extension XVideo-MotionCompensation
[    20.369] (II) Loading extension X-Resource
[    20.370] (II) LoadModule: "dbe"
[    20.370] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.423] (II) Module dbe: vendor="X.Org Foundation"
[    20.423]     compiled for 1.11.3, module version = 1.0.0
[    20.423]     Module class: X.Org Server Extension
[    20.423]     ABI class: X.Org Server Extension, version 6.0
[    20.423] (II) Loading extension DOUBLE-BUFFER
[    20.423] (II) LoadModule: "glx"
[    20.423] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.601] (II) Module glx: vendor="X.Org Foundation"
[    20.601]     compiled for 1.11.3, module version = 1.0.0
[    20.601]     ABI class: X.Org Server Extension, version 6.0
[    20.601] (==) AIGLX enabled
[    20.601] (II) Loading extension GLX
[    20.601] (II) LoadModule: "record"
[    20.601] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.648] (II) Module record: vendor="X.Org Foundation"
[    20.648]     compiled for 1.11.3, module version = 1.13.0
[    20.648]     Module class: X.Org Server Extension
[    20.648]     ABI class: X.Org Server Extension, version 6.0
[    20.648] (II) Loading extension RECORD
[    20.648] (II) LoadModule: "dri"
[    20.648] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.676] (II) Module dri: vendor="X.Org Foundation"
[    20.676]     compiled for 1.11.3, module version = 1.0.0
[    20.676]     ABI class: X.Org Server Extension, version 6.0
[    20.676] (II) Loading extension XFree86-DRI
[    20.676] (II) LoadModule: "dri2"
[    20.677] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.709] (II) Module dri2: vendor="X.Org Foundation"
[    20.709]     compiled for 1.11.3, module version = 1.2.0
[    20.709]     ABI class: X.Org Server Extension, version 6.0
[    20.709] (II) Loading extension DRI2
[    20.709] (II) LoadModule: "nvidia"
[    20.719] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    20.780] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.780]     compiled for 4.0.2, module version = 1.0.0
[    20.780]     Module class: X.Org Video Driver
[    20.913] (II) NVIDIA dlloader X Driver  295.59  Wed Jun  6 21:26:24 PDT 2012
[    20.918] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.961] (++) using VT number 7

[    20.962] (II) Loading sub module "fb"
[    20.962] (II) LoadModule: "fb"
[    20.993] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.013] (II) Module fb: vendor="X.Org Foundation"
[    21.013]     compiled for 1.11.3, module version = 1.0.0
[    21.013]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.014] (II) Loading sub module "wfb"
[    21.014] (II) LoadModule: "wfb"
[    21.014] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.024] (II) Module wfb: vendor="X.Org Foundation"
[    21.024]     compiled for 1.11.3, module version = 1.0.0
[    21.024]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.024] (II) Loading sub module "ramdac"
[    21.024] (II) LoadModule: "ramdac"
[    21.024] (II) Module "ramdac" already built-in
[    21.042] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    21.042] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.042] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.055] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.055] (==) NVIDIA(0): RGB weight 888
[    21.055] (==) NVIDIA(0): Default visual is TrueColor
[    21.055] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.056] (**) NVIDIA(0): Enabling 2D acceleration
[    21.056] (EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
[    21.056] (EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
[    21.056] (EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
[    21.056] (EE) NVIDIA(0):     you continue to encounter problems, Please try
[    21.056] (EE) NVIDIA(0):     reinstalling the NVIDIA driver.
[    21.852] (II) NVIDIA(GPU-0): Display (Envision L19W765 (CRT-0)) does not support NVIDIA 3D
[    21.852] (II) NVIDIA(GPU-0):     Vision stereo.
[    21.915] (II) NVIDIA(0): NVIDIA GPU GeForce 7100 / nForce 630i (C73) at PCI:0:16:0
[    21.920] (II) NVIDIA(0):     (GPU-0)
[    21.920] (--) NVIDIA(0): Memory: 524288 kBytes
[    21.920] (--) NVIDIA(0): VideoBIOS: 05.73.32.09.17
[    21.920] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    21.921] (--) NVIDIA(0): Connected display device(s) on GeForce 7100 / nForce 630i at
[    21.921] (--) NVIDIA(0):     PCI:0:16:0
[    21.921] (--) NVIDIA(0):     Envision L19W765 (CRT-0)
[    21.921] (--) NVIDIA(0): Envision L19W765 (CRT-0): 350.0 MHz maximum pixel clock
[    21.921] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.921] (**) NVIDIA(0):     device Envision L19W765 (CRT-0) (Using EDID frequencies
[    21.921] (**) NVIDIA(0):     has been enabled on all display devices.)
[    21.921] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    21.921] (==) NVIDIA(0): 
[    21.921] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    21.921] (==) NVIDIA(0):     will be used as the requested mode.
[    21.921] (==) NVIDIA(0): 
[    21.921] (II) NVIDIA(0): Validated modes:
[    21.921] (II) NVIDIA(0):     "nvidia-auto-select"
[    21.921] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    21.922] (--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
[    21.922] (--) NVIDIA(0):     option
[    21.996] (--) Depth 24 pixmap format is 32 bpp
[    22.000] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    22.140] (II) Loading extension NV-GLX
[    22.216] (==) NVIDIA(0): Disabling shared memory pixmaps
[    22.216] (==) NVIDIA(0): Backing store disabled
[    22.217] (==) NVIDIA(0): Silken mouse enabled
[    22.217] (**) NVIDIA(0): DPMS enabled
[    22.217] (II) Loading extension NV-CONTROL
[    22.217] (II) Loading extension XINERAMA
[    22.217] (II) Loading sub module "dri2"
[    22.217] (II) LoadModule: "dri2"
[    22.217] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.218] (II) Module dri2: vendor="X.Org Foundation"
[    22.218]     compiled for 1.11.3, module version = 1.2.0
[    22.218]     ABI class: X.Org Server Extension, version 6.0
[    22.218] (II) NVIDIA(0): [DRI2] Setup complete
[    22.218] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    22.218] (==) RandR enabled
[    22.218] (II) Initializing built-in extension Generic Event Extension
[    22.218] (II) Initializing built-in extension SHAPE
[    22.218] (II) Initializing built-in extension MIT-SHM
[    22.218] (II) Initializing built-in extension XInputExtension
[    22.218] (II) Initializing built-in extension XTEST
[    22.218] (II) Initializing built-in extension BIG-REQUESTS
[    22.218] (II) Initializing built-in extension SYNC
[    22.218] (II) Initializing built-in extension XKEYBOARD
[    22.218] (II) Initializing built-in extension XC-MISC
[    22.218] (II) Initializing built-in extension SECURITY
[    22.218] (II) Initializing built-in extension XINERAMA
[    22.218] (II) Initializing built-in extension XFIXES
[    22.218] (II) Initializing built-in extension RENDER
[    22.218] (II) Initializing built-in extension RANDR
[    22.218] (II) Initializing built-in extension COMPOSITE
[    22.218] (II) Initializing built-in extension DAMAGE
[    22.350] (II) AIGLX: Screen 0 is not DRI2 capable
[    22.351] (II) AIGLX: Screen 0 is not DRI capable
[    23.072] (II) AIGLX: Loaded and initialized swrast
[    23.072] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    23.231] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.247] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.247] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.247] (II) LoadModule: "evdev"
[    23.247] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.292] (II) Module evdev: vendor="X.Org Foundation"
[    23.292]     compiled for 1.11.3, module version = 2.7.0
[    23.292]     Module class: X.Org XInput Driver
[    23.292]     ABI class: X.Org XInput driver, version 16.0
[    23.292] (II) Using input driver 'evdev' for 'Power Button'
[    23.292] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.292] (**) Power Button: always reports core events
[    23.292] (**) evdev: Power Button: Device: "/dev/input/event1"
[    23.292] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.292] (--) evdev: Power Button: Found keys
[    23.292] (II) evdev: Power Button: Configuring as keyboard
[    23.293] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.293] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.293] (**) Option "xkb_rules" "evdev"
[    23.293] (**) Option "xkb_model" "pc105"
[    23.293] (**) Option "xkb_layout" "latam"
[    23.297] (II) XKB: reuse xkmfile /var/lib/xkb/server-D39A7DF07EFAADA1B152E688CBEB9ED49E8BFDBB.xkm
[    23.338] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.338] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.338] (II) Using input driver 'evdev' for 'Power Button'
[    23.338] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.338] (**) Power Button: always reports core events
[    23.338] (**) evdev: Power Button: Device: "/dev/input/event0"
[    23.338] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.338] (--) evdev: Power Button: Found keys
[    23.338] (II) evdev: Power Button: Configuring as keyboard
[    23.338] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    23.338] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    23.338] (**) Option "xkb_rules" "evdev"
[    23.338] (**) Option "xkb_model" "pc105"
[    23.338] (**) Option "xkb_layout" "latam"
[    23.339] (II) config/udev: Adding input device Genius       Optical Mouse (/dev/input/event3)
[    23.339] (**) Genius       Optical Mouse: Applying InputClass "evdev pointer catchall"
[    23.339] (II) Using input driver 'evdev' for 'Genius       Optical Mouse'
[    23.339] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.339] (**) Genius       Optical Mouse: always reports core events
[    23.339] (**) evdev: Genius       Optical Mouse: Device: "/dev/input/event3"
[    23.339] (--) evdev: Genius       Optical Mouse: Vendor 0x458 Product 0x3a
[    23.339] (--) evdev: Genius       Optical Mouse: Found 3 mouse buttons
[    23.339] (--) evdev: Genius       Optical Mouse: Found scroll wheel(s)
[    23.339] (--) evdev: Genius       Optical Mouse: Found relative axes
[    23.339] (--) evdev: Genius       Optical Mouse: Found x and y relative axes
[    23.339] (II) evdev: Genius       Optical Mouse: Configuring as mouse
[    23.339] (II) evdev: Genius       Optical Mouse: Adding scrollwheel support
[    23.339] (**) evdev: Genius       Optical Mouse: YAxisMapping: buttons 4 and 5
[    23.339] (**) evdev: Genius       Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.339] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb2/2-7/2-7:1.0/input/input3/event3"
[    23.339] (II) XINPUT: Adding extended input device "Genius       Optical Mouse" (type: MOUSE, id 8)
[    23.339] (II) evdev: Genius       Optical Mouse: initialized for relative axes.
[    23.339] (**) Genius       Optical Mouse: (accel) keeping acceleration scheme 1
[    23.339] (**) Genius       Optical Mouse: (accel) acceleration profile 0
[    23.340] (**) Genius       Optical Mouse: (accel) acceleration factor: 2.000
[    23.340] (**) Genius       Optical Mouse: (accel) acceleration threshold: 4
[    23.340] (II) config/udev: Adding input device Genius       Optical Mouse (/dev/input/mouse0)
[    23.340] (II) No input driver specified, ignoring this device.
[    23.340] (II) This device may have been added with another device file.
[    23.340] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event4)
[    23.340] (II) No input driver specified, ignoring this device.
[    23.340] (II) This device may have been added with another device file.
[    23.341] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event5)
[    23.341] (II) No input driver specified, ignoring this device.
[    23.341] (II) This device may have been added with another device file.
[    23.341] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event6)
[    23.341] (II) No input driver specified, ignoring this device.
[    23.341] (II) This device may have been added with another device file.
[    23.342] (II) config/udev: Adding input device HDA NVidia Line-Out (/dev/input/event7)
[    23.342] (II) No input driver specified, ignoring this device.
[    23.342] (II) This device may have been added with another device file.
[    23.342] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    23.342] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.342] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.342] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.342] (**) AT Translated Set 2 keyboard: always reports core events
[    23.342] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    23.342] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.342] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.342] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.342] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    23.342] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    23.342] (**) Option "xkb_rules" "evdev"
[    23.342] (**) Option "xkb_model" "pc105"
[    23.342] (**) Option "xkb_layout" "latam"
[    51.838] (II) XKB: reuse xkmfile /var/lib/xkb/server-357EB629388741CA7D03B5AACF7DAB92F0C7B0A8.xkm



```

---

