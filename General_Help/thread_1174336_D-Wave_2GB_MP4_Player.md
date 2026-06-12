---
title: "D-Wave 2GB MP4 Player"
date: 2009-05-30
forum: General Help
---

### Post by abclemons on 2009-05-30
Okay, I should of shelled out a few extra dollars for an Ipod, but I got this 8gb Ipod knock off for $10 and free shipping. What more can I ask for... besides that it works?

The device mounted twice. The first time I browsed through deleted the sample Britney Spears song and music video. I then added one of my own MP3 files to via Nautilus. I unmounted the drive played with the gadget for a second or two and plugged it back the usb drive so it would charge. I hit the menu button (the device is the Chinese Ipod knock-off) and the device magically unmounted before my eyes. It is still connected and charging, but it does not show up in the file menu for me to mount back.

Here's my lsusb output:
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 014: ID 10d6:1101 Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player
Bus 001 Device 004: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 003: ID 0bc2:3110 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Here's my fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/abc-root during installation
UUID=baffc5b0-6edb-4c0a-8ae0-28886622a7db /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=316304f9-be95-484d-8abd-d2c189fa4c0d /boot           ext2    relatime        0       2
# swap was on /dev/mapper/abc-swap_1 during installation
UUID=a5884b03-17fa-4dba-8046-c7a4f7646242 none            swap    sw              0       
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

I am running Ubuntu 9.04 64 bit. 

I can get around terminal a little bit and don't mind editing some system settings. However, I am not 100% confident and do not usually meander too far from default settings on this laptop; instead, I have dummy laptop I don't mind making into a brick :)

Help!?!?!?!?

---

### Post by dcstar on 2009-05-31
> **abclemons said:**
> Okay, I should of shelled out a few extra dollars for an Ipod, but I got this 8gb Ipod knock off for $10 and free shipping. What more can I ask for... besides that it works?

The device mounted twice. The first time I browsed through deleted the sample Britney Spears song and music video. I then added one of my own MP3 files to via Nautilus. I unmounted the drive played with the gadget for a second or two and plugged it back the usb drive so it would charge. I hit the menu button (the device is the Chinese Ipod knock-off) and the device magically unmounted before my eyes. It is still connected and charging, but it does not show up in the file menu for me to mount back.
.........

Post the output of **dmesg** when you plug it in.

---

### Post by abclemons on 2009-05-31
Okay. Get ready for one heck of a long code section. Here's my **dmesg** output:
```
[    0.000000] BIOS EBDA/lowmem at: 0009dc00/0009dc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=/dev/mapper/abc-root ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf00000 (usable)
[    0.000000]  BIOS-e820: 000000007bf00000 - 000000007bf15000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf15000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7bf00 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000090c00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007bf00000 (usable)
[    0.000000]  modified: 000000007bf00000 - 000000007bf15000 (ACPI data)
[    0.000000]  modified: 000000007bf15000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  modified: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007bf00000
[    0.000000]  0000000000 - 007be00000 page 2M
[    0.000000]  007be00000 - 007bf00000 page 4k
[    0.000000] kernel direct mapping tables up to 7bf00000 @ 10000-14000
[    0.000000] last_map_addr: 7bf00000 end: 7bf00000
[    0.000000] RAMDISK: 377e3000 - 37fef9f9
[    0.000000] ACPI: RSDP 000F88F0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 7BF0BBA9, 0040 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7BF14B9A, 0074 (r1 HP     MCP51M    6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 7BF0BBE9, 8FB1 (r1 HP       MCP51M  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 7BF15FC0, 0040
[    0.000000] ACPI: SSDT 7BF14C0E, 0182 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 7BF14D90, 003C (r1 HP       MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 7BF14DCC, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 7BF14E04, 005E (r1 HP     	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7BF14E62, 0028 (r1     HP $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 7BF14E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007bf00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [00377e3000 - 0037fef9f9]          RAMDISK ==> [00377e3000 - 0037fef9f9]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f8920] 000f8920
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000090
[    0.000000]     0: 0x00000100 -> 0x0007bf00
[    0.000000] On node 0 totalpages: 507523
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2542 pages reserved
[    0.000000]   DMA zone: 1373 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6885 pages used for memmap
[    0.000000]   DMA32 zone: 496667 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000090000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 498040
[    0.000000] Kernel command line: root=/dev/mapper/abc-root ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1607.245 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 20971520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ fbb2000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 1958864k/2030592k available (4760k kernel code, 500k absent, 70508k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3214.49 BogoMIPS (lpj=6428980)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] tseg: 007bf80000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] ACPI: Core revision 20080926
[    0.005249] ACPI: Checking initramfs for custom DSDT
[    0.384061] Setting APIC routing to flat
[    0.384685] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.427764] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.428001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3214.57 BogoMIPS (lpj=6429146)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.512152] CPU1: <6>System has AMD C1E enabled
[    0.512159] AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.512166] Switch to broadcast mode on CPU1
[    0.512173] Brought up 2 CPUs
[    0.512177] Total of 2 processors activated (6429.06 BogoMIPS).
[    0.512286] CPU0 attaching sched-domain:
[    0.512289]  domain 0: span 0-1 level CPU
[    0.512292]   groups: 0 1
[    0.512298] CPU1 attaching sched-domain:
[    0.512300]  domain 0: span 0-1 level CPU
[    0.512302]   groups: 1 0
[    0.512382] Switch to broadcast mode on CPU0
[    0.512382] net_namespace: 1400 bytes
[    0.512382] Booting paravirtualized kernel on bare hardware
[    0.512382] Time: 22:44:51  Date: 05/30/09
[    0.512382] regulator: core version 0.5
[    0.512382] NET: Registered protocol family 16
[    0.512382] node 0 link 0: io port [1000, fffff]
[    0.512382] TOM: 0000000080000000 aka 2048M
[    0.512382] node 0 link 0: mmio [e0000000, efffffff]
[    0.512382] node 0 link 0: mmio [a0000, bffff]
[    0.512382] node 0 link 0: mmio [80000000, fe0bffff]
[    0.512382] bus: [00,ff] on node 0 link 0
[    0.512382] bus: 00 index 0 io port: [0, ffff]
[    0.512382] bus: 00 index 1 mmio: [80000000, fcffffffff]
[    0.512382] bus: 00 index 2 mmio: [a0000, bffff]
[    0.512382] ACPI: bus type pci registered
[    0.512382] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
[    0.512382] PCI: MCFG area at e0000000 reserved in E820
[    0.512816] PCI: Using MMCONFIG at e0000000 - e06fffff
[    0.512819] PCI: Using configuration type 1 for base access
[    0.513542] ACPI: EC: Look up EC in DSDT
[    0.518624] ACPI: BIOS _OSI(Linux) query ignored
[    0.519178] ACPI: Interpreter enabled
[    0.519182] ACPI: (supports S0 S3 S4 S5)
[    0.519203] ACPI: Using IOAPIC for interrupt routing
[    0.516025] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.524350] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.524353] ACPI: EC: driver started in interrupt mode
[    0.524565] ACPI: No dock devices found.
[    0.524577] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.524836] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524839] pci 0000:00:02.0: PME# disabled
[    0.524865] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524868] pci 0000:00:03.0: PME# disabled
[    0.524889] pci 0000:00:05.0: reg 10 32bit mmio: [0xb2000000-0xb2ffffff]
[    0.524895] pci 0000:00:05.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.524900] pci 0000:00:05.0: reg 1c 64bit mmio: [0xb1000000-0xb1ffffff]
[    0.524907] pci 0000:00:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.525064] pci 0000:00:0a.0: reg 10 io port: [0x1d00-0x1d7f]
[    0.525125] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.525131] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.525145] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.525150] pci 0000:00:0a.1: PME# disabled
[    0.525184] pci 0000:00:0a.3: reg 10 32bit mmio: [0xb0040000-0xb007ffff]
[    0.525275] pci 0000:00:0b.0: reg 10 32bit mmio: [0xb0004000-0xb0004fff]
[    0.525303] pci 0000:00:0b.0: supports D1 D2
[    0.525305] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.525310] pci 0000:00:0b.0: PME# disabled
[    0.525340] pci 0000:00:0b.1: reg 10 32bit mmio: [0xb0005000-0xb00050ff]
[    0.525365] pci 0000:00:0b.1: supports D1 D2
[    0.525367] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.525371] pci 0000:00:0b.1: PME# disabled
[    0.525410] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.525450] pci 0000:00:0e.0: reg 10 io port: [0x30c0-0x30c7]
[    0.525455] pci 0000:00:0e.0: reg 14 io port: [0x30b4-0x30b7]
[    0.525461] pci 0000:00:0e.0: reg 18 io port: [0x30b8-0x30bf]
[    0.525466] pci 0000:00:0e.0: reg 1c io port: [0x30b0-0x30b3]
[    0.525471] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.525476] pci 0000:00:0e.0: reg 24 32bit mmio: [0xb0006000-0xb0006fff]
[    0.525552] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]
[    0.525576] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.525580] pci 0000:00:10.1: PME# disabled
[    0.525613] pci 0000:00:14.0: reg 10 32bit mmio: [0xb0008000-0xb0008fff]
[    0.525618] pci 0000:00:14.0: reg 14 io port: [0x30e0-0x30e7]
[    0.525637] pci 0000:00:14.0: supports D1 D2
[    0.525639] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.525643] pci 0000:00:14.0: PME# disabled
[    0.525757] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]
[    0.525760] pci 0000:00:02.0: bridge 32bit mmio: [0xb4000000-0xb5ffffff]
[    0.525764] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]
[    0.525797] pci 0000:03:00.0: reg 10 32bit mmio: [0xb6000000-0xb6003fff]
[    0.525828] pci 0000:03:00.0: supports D1 D2
[    0.525873] pci 0000:00:03.0: bridge 32bit mmio: [0xb6000000-0xb7ffffff]
[    0.525908] pci 0000:07:05.0: reg 10 32bit mmio: [0xb8000000-0xb80007ff]
[    0.525938] pci 0000:07:05.0: supports D1 D2
[    0.525941] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.525945] pci 0000:07:05.0: PME# disabled
[    0.525971] pci 0000:07:05.1: reg 10 32bit mmio: [0xb8000800-0xb80008ff]
[    0.526001] pci 0000:07:05.1: supports D1 D2
[    0.526004] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.526007] pci 0000:07:05.1: PME# disabled
[    0.526034] pci 0000:07:05.2: reg 10 32bit mmio: [0xb8000c00-0xb8000cff]
[    0.526064] pci 0000:07:05.2: supports D1 D2
[    0.526067] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.526070] pci 0000:07:05.2: PME# disabled
[    0.526097] pci 0000:07:05.3: reg 10 32bit mmio: [0xb8001000-0xb80010ff]
[    0.526128] pci 0000:07:05.3: supports D1 D2
[    0.526130] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.526134] pci 0000:07:05.3: PME# disabled
[    0.526161] pci 0000:07:05.4: reg 10 32bit mmio: [0xb8001400-0xb80014ff]
[    0.526191] pci 0000:07:05.4: supports D1 D2
[    0.526193] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.526197] pci 0000:07:05.4: PME# disabled
[    0.526231] pci 0000:00:10.0: transparent bridge
[    0.526236] pci 0000:00:10.0: bridge 32bit mmio: [0xb8000000-0xb80fffff]
[    0.526246] bus 00 -> node 0
[    0.526253] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.526388] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.526428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.526472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.568025] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.568297] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.568562] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.568827] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.569091] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.569354] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.569618] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *11
[    0.569881] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.570146] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.570409] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.570677] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.570949] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.571212] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.571477] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.571741] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.572017] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.572282] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.572557] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.572828] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.573064] ACPI: WMI: Mapper loaded
[    0.576129] SCSI subsystem initialized
[    0.576137] libata version 3.00 loaded.
[    0.576137] usbcore: registered new interface driver usbfs
[    0.576137] usbcore: registered new interface driver hub
[    0.576137] usbcore: registered new device driver usb
[    0.576137] PCI: Using ACPI for IRQ routing
[    0.588013] Bluetooth: Core ver 2.13
[    0.592014] NET: Registered protocol family 31
[    0.592016] Bluetooth: HCI device and connection manager initialized
[    0.592019] Bluetooth: HCI socket layer initialized
[    0.592021] NET: Registered protocol family 8
[    0.592023] NET: Registered protocol family 20
[    0.592036] NetLabel: Initializing
[    0.592038] NetLabel:  domain hash size = 128
[    0.592040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.592058] NetLabel:  unlabeled traffic allowed by default
[    0.592258] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.592263] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.596087] AppArmor: AppArmor Filesystem Enabled
[    0.604026] Switched to high resolution mode on CPU 0
[    0.604040] Switched to high resolution mode on CPU 1
[    0.609045] pnp: PnP ACPI init
[    0.609060] ACPI: bus type pnp registered
[    0.614232] pnp: PnP ACPI: found 13 devices
[    0.614236] ACPI: ACPI bus type pnp unregistered
[    0.614249] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.614257] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.614261] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.614264] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.614267] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.614275] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved
[    0.614282] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.614285] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.614288] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.614291] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.614294] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.614297] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.614299] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.614306] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.614309] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.614312] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.619078] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.619081] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.619086] pci 0000:00:02.0:   MEM window: 0xb4000000-0xb5ffffff
[    0.619089] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    0.619093] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.619096] pci 0000:00:03.0:   IO window: disabled
[    0.619099] pci 0000:00:03.0:   MEM window: 0xb6000000-0xb7ffffff
[    0.619102] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.619106] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.619108] pci 0000:00:10.0:   IO window: disabled
[    0.619112] pci 0000:00:10.0:   MEM window: 0xb8000000-0xb80fffff
[    0.619115] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.619126] pci 0000:00:02.0: setting latency timer to 64
[    0.619132] pci 0000:00:03.0: setting latency timer to 64
[    0.619137] pci 0000:00:10.0: setting latency timer to 64
[    0.619141] bus: 00 index 0 io port: [0x00-0xffff]
[    0.619143] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.619146] bus: 01 index 0 io port: [0x4000-0x4fff]
[    0.619148] bus: 01 index 1 mmio: [0xb4000000-0xb5ffffff]
[    0.619151] bus: 01 index 2 mmio: [0xd0000000-0xd01fffff]
[    0.619153] bus: 01 index 3 mmio: [0x0-0x0]
[    0.619155] bus: 03 index 0 mmio: [0x0-0x0]
[    0.619157] bus: 03 index 1 mmio: [0xb6000000-0xb7ffffff]
[    0.619159] bus: 03 index 2 mmio: [0x0-0x0]
[    0.619162] bus: 03 index 3 mmio: [0x0-0x0]
[    0.619164] bus: 07 index 0 mmio: [0x0-0x0]
[    0.619166] bus: 07 index 1 mmio: [0xb8000000-0xb80fffff]
[    0.619169] bus: 07 index 2 mmio: [0x0-0x0]
[    0.619171] bus: 07 index 3 io port: [0x00-0xffff]
[    0.619173] bus: 07 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.619188] NET: Registered protocol family 2
[    0.657103] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.657668] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.660697] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.661435] TCP: Hash tables configured (established 262144 bind 65536)
[    0.661438] TCP reno registered
[    0.673138] NET: Registered protocol family 1
[    0.673280] checking if image is initramfs... it is
[    1.441643] Freeing initrd memory: 8242k freed
[    1.447443] Simple Boot Flag at 0x36 set to 0x1
[    1.447823] audit: initializing netlink socket (disabled)
[    1.447838] type=2000 audit(1243723491.444:1): initialized
[    1.457878] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.459439] VFS: Disk quotas dquot_6.5.1
[    1.459506] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.460236] fuse init (API version 7.10)
[    1.460334] msgmni has been set to 3843
[    1.460572] alg: No test for stdrng (krng)
[    1.460589] io scheduler noop registered
[    1.460591] io scheduler anticipatory registered
[    1.460594] io scheduler deadline registered
[    1.460645] io scheduler cfq registered (default)
[    1.460661] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.460705] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.460716] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.460726] pci 0000:00:05.0: Boot video device
[    1.460748] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.676105] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.676117] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.676131] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.682514] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.682540] pcieport-driver 0000:00:02.0: found MSI capability
[    1.682558] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X
[    1.682566] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.682585] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.682626] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.682649] pcieport-driver 0000:00:03.0: found MSI capability
[    1.682663] pcieport-driver 0000:00:03.0: irq 2302 for MSI/MSI-X
[    1.682670] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.682685] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.682742] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.682753] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.683815] ACPI: AC Adapter [ACAD] (on-line)
[    1.956708] ACPI: Battery Slot [BAT0] (battery present)
[    1.956810] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.956813] ACPI: Power Button (FF) [PWRF]
[    1.956877] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.956880] ACPI: Power Button (CM) [PWRB]
[    1.956935] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.956938] ACPI: Sleep Button (CM) [SLPB]
[    1.956988] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.958115] ACPI: Lid Switch [LID]
[    1.958513] ACPI: processor limited to max C-state 1
[    1.958542] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.958576] processor ACPI_CPU:00: registered as cooling_device0
[    1.958617] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.958638] processor ACPI_CPU:01: registered as cooling_device1
[    2.218632] thermal LNXTHERM:01: registered as thermal_zone0
[    2.220728] ACPI: Thermal Zone [THRM] (36 C)
[    2.257355] Linux agpgart interface v0.103
[    2.257368] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.258438] brd: module loaded
[    2.258804] loop: module loaded
[    2.258904] Fixed MDIO Bus: probed
[    2.258910] PPP generic driver version 2.4.2
[    2.258977] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.259015] Driver 'sd' needs updating - please use bus_type methods
[    2.259024] Driver 'sr' needs updating - please use bus_type methods
[    2.259264] sata_nv 0000:00:0e.0: version 3.5
[    2.259275] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    2.259749] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    2.259762] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    2.259766] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.259831] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.259989] scsi0 : sata_nv
[    2.260146] scsi1 : sata_nv
[    2.260353] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    2.260356] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    3.136067] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.144236] ata1.00: ATA-7: HTS541010G9SA00, MBZOC60P, max UDMA/100
[    3.144239] ata1.00: 195371568 sectors, multi 16: LBA48 
[    3.160245] ata1.00: configured for UDMA/100
[    3.894609] ata2: SATA link down (SStatus 0 SControl 300)
[    3.894657] isa bounce pool size: 16 pages
[    3.894741] scsi 0:0:0:0: Direct-Access     ATA      HTS541010G9SA00  MBZO PQ: 0 ANSI: 5
[    3.894862] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    3.894881] sd 0:0:0:0: [sda] Write Protect is off
[    3.894884] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.894913] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.894996] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    3.895013] sd 0:0:0:0: [sda] Write Protect is off
[    3.895016] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.895044] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.895048]  sda: sda1 sda2 < sda5 >
[    4.295762] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.295822] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.295933] pata_amd 0000:00:0d.0: version 0.3.10
[    4.295978] pata_amd 0000:00:0d.0: setting latency timer to 64
[    4.296088] scsi2 : pata_amd
[    4.296168] scsi3 : pata_amd
[    4.296984] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    4.296987] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    4.460466] ata3.00: ATAPI: MATSHITADVD-RAM UJ-851S, 1.50, max MWDMA2
[    4.460490] ata3: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    4.476425] ata3.00: configured for MWDMA2
[    4.476813] ata4: port disabled. ignoring.
[    4.478646] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-851S  1.50 PQ: 0 ANSI: 5
[    4.482946] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.482950] Uniform CD-ROM driver Revision: 3.20
[    4.483071] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.483126] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    4.483669] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.484143] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    4.484156] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    4.484178] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    4.484181] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    4.484255] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    4.484292] ehci_hcd 0000:00:0b.1: debug port 1
[    4.484297] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    4.484323] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xb0005000
[    4.492046] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    4.492142] usb usb1: configuration #1 chosen from 1 choice
[    4.492174] hub 1-0:1.0: USB hub found
[    4.492183] hub 1-0:1.0: 8 ports detected
[    4.492329] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.492792] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    4.492796] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    4.492821] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    4.492824] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    4.492881] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    4.492901] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000
[    4.550102] usb usb2: configuration #1 chosen from 1 choice
[    4.550133] hub 2-0:1.0: USB hub found
[    4.550145] hub 2-0:1.0: 8 ports detected
[    4.550270] uhci_hcd: USB Universal Host Controller Interface driver
[    4.550344] usbcore: registered new interface driver libusual
[    4.550381] usbcore: registered new interface driver usbserial
[    4.550392] USB Serial support registered for generic
[    4.550409] usbcore: registered new interface driver usbserial_generic
[    4.550411] usbserial: USB Serial Driver core
[    4.550458] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.568708] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.568716] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.577068] mice: PS/2 mouse device common for all mice
[    4.637106] rtc_cmos 00:09: RTC can wake from S4
[    4.637147] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    4.637188] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.637269] device-mapper: uevent: version 1.0.3
[    4.637407] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.637612] device-mapper: multipath: version 1.0.5 loaded
[    4.637616] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.637891] cpuidle: using governor ladder
[    4.637967] cpuidle: using governor menu
[    4.638461] TCP cubic registered
[    4.638548] NET: Registered protocol family 10
[    4.638984] lo: Disabled Privacy Extensions
[    4.639333] NET: Registered protocol family 17
[    4.639363] Bluetooth: L2CAP ver 2.11
[    4.639365] Bluetooth: L2CAP socket layer initialized
[    4.639368] Bluetooth: SCO (Voice Link) ver 0.6
[    4.639370] Bluetooth: SCO socket layer initialized
[    4.639433] Bluetooth: RFCOMM socket layer initialized
[    4.639450] Bluetooth: RFCOMM TTY layer initialized
[    4.639452] Bluetooth: RFCOMM ver 1.10
[    4.639520] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[    4.639582] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    4.639586] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    4.639742] registered taskstats version 1
[    4.639933]   Magic number: 9:268:756
[    4.640056] rtc_cmos 00:09: setting system clock to 2009-05-30 22:44:55 UTC (1243723495)
[    4.640060] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.640062] EDD information not available.
[    4.640119] Freeing unused kernel memory: 536k freed
[    4.640443] Write protecting the kernel read-only data: 6708k
[    4.649252] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.817839] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    4.953568] usb 1-1: configuration #1 chosen from 1 choice
[    4.958471] Initializing USB Mass Storage driver...
[    4.958609] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.958715] usbcore: registered new interface driver usb-storage
[    4.958718] USB Mass Storage support registered.
[    4.958897] usb-storage: device found at 2
[    4.958899] usb-storage: waiting for device to settle before scanning
[    5.068023] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    5.225222] usb 1-2: configuration #1 chosen from 1 choice
[    5.241120] scsi5 : SCSI emulation for USB Mass Storage devices
[    5.241236] usb-storage: device found at 3
[    5.241239] usb-storage: waiting for device to settle before scanning
[    5.252213] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    5.252229] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    5.258114] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    5.258600] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    5.258614] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    5.258619] forcedeth 0000:00:14.0: setting latency timer to 64
[    5.258674] nv_probe: set workaround bit for reversed mac addr
[    5.304026] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.363460] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    5.526960] usb 1-4: configuration #1 chosen from 1 choice
[    5.777114] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:0b:e8:31
[    5.777119] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    5.814493] PM: Starting manual resume from disk
[    5.814498] PM: Resume from partition 252:1
[    5.814500] PM: Checking hibernation image.
[    5.814789] PM: Resume from disk failed.
[    5.878677] kjournald starting.  Commit interval 5 seconds
[    5.878697] EXT3-fs: mounted filesystem with ordered data mode.
[    6.584162] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00ed4a0700]
[    9.956184] usb-storage: device scan complete
[    9.957640] scsi 4:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[   10.019760] sd 4:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[   10.020380] sd 4:0:0:0: [sdb] Write Protect is off
[   10.020383] sd 4:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[   10.020386] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   10.021629] sd 4:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[   10.022126] sd 4:0:0:0: [sdb] Write Protect is off
[   10.022129] sd 4:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[   10.022131] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   10.022135]  sdb: unknown partition table
[   10.024811] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   10.024874] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   10.241442] usb-storage: device scan complete
[   10.244134] scsi 5:0:0:0: Direct-Access     Seagate  FreeAgent Pro    4109 PQ: 0 ANSI: 4
[   10.246870] sd 5:0:0:0: [sdc] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[   10.248368] sd 5:0:0:0: [sdc] Write Protect is off
[   10.248371] sd 5:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[   10.248373] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   10.250621] sd 5:0:0:0: [sdc] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[   10.252119] sd 5:0:0:0: [sdc] Write Protect is off
[   10.252121] sd 5:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[   10.252123] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   10.252127]  sdc: sdc1
[   10.252857] sd 5:0:0:0: [sdc] Attached SCSI disk
[   10.252919] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   12.102298] udev: starting version 141
[   12.408120] acpi device:24: registered as cooling_device2
[   12.408484] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/input/input6
[   12.441150] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   12.478940] ieee80211_crypt: registered algorithm 'NULL'
[   12.484557] wl: module license '' taints kernel.
[   12.487748] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   12.487765] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[   12.487772] wl 0000:03:00.0: setting latency timer to 64
[   13.542092] ieee80211_crypt: registered algorithm 'TKIP'
[   13.557081] eth1: Broadcom BCM4311 802.11 Wireless Controller 5.10.79.10
[   13.681587] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   13.681634] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   13.745688] nvidia 0000:00:05.0: power state changed by ACPI to D0
[   13.746126] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   13.746140] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[   13.746148] nvidia 0000:00:05.0: setting latency timer to 64
[   13.747799] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   13.992814] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   14.008993] sdhci: Secure Digital Host Controller Interface driver
[   14.008997] sdhci: Copyright(c) Pierre Ossman
[   14.014881] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   14.015376] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   14.015390] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   14.018594] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   14.020243] ricoh-mmc: Ricoh MMC Controller disabling driver
[   14.020247] ricoh-mmc: Copyright(c) Philip Langdale
[   14.020285] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   14.020301] ricoh-mmc: Controller is now disabled.
[   14.099877] Linux video capture interface: v2.00
[   14.147873] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   14.150982] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4:1.0/input/input8
[   14.165158] usbcore: registered new interface driver uvcvideo
[   14.165164] USB Video Class driver (v0.1.0)
[   14.236054] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.334710] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   14.334726] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   14.334837] HDA Intel 0000:00:10.1: setting latency timer to 64
[   14.958225] lp: driver loaded but no devices found
[   15.128553] Adding 3219448k swap on /dev/mapper/abc-swap_1.  Priority:-1 extents:1 across:3219448k
[   15.220828] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   15.284418] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   15.693416] EXT3 FS on dm-0, internal journal
[   17.035559] type=1505 audit(1243723507.891:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2245
[   17.097523] type=1505 audit(1243723507.955:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2249
[   17.097684] type=1505 audit(1243723507.955:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2249
[   17.097740] type=1505 audit(1243723507.955:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2249
[   17.097790] type=1505 audit(1243723507.955:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2249
[   17.264960] type=1505 audit(1243723508.123:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2254
[   17.265201] type=1505 audit(1243723508.123:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2254
[   17.304507] type=1505 audit(1243723508.163:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2258
[   23.683624] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.683627] Bluetooth: BNEP filters: protocol multicast
[   23.706607] Bridge firewalling registered
[   25.209412] ppdev: user-space parallel port driver
[   29.140732] eth0: no link during initialization.
[   29.141530] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.404012] eth1: no IPv6 routers present
[   46.119358] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   46.119363] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   46.121872] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   46.121877] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   46.121995] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   46.121998] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   47.083934] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   47.083939] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   47.114042] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   47.114048] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   47.150688] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   47.150694] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   90.000038] Clocksource tsc unstable (delta = -95752970 ns)
[   95.254553] usb 1-1: USB disconnect, address 2
[   98.692057] usb 1-1: new high speed USB device using ehci_hcd and address 5
[   98.825919] usb 1-1: configuration #1 chosen from 1 choice
[   98.826437] scsi6 : SCSI emulation for USB Mass Storage devices
[   98.826817] usb-storage: device found at 5
[   98.826822] usb-storage: waiting for device to settle before scanning
[  103.824429] usb-storage: device scan complete
[  103.826695] scsi 6:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[  103.830293] sd 6:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  103.831434] sd 6:0:0:0: [sdb] Write Protect is off
[  103.831443] sd 6:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  103.831448] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  103.837523] sd 6:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  103.838129] sd 6:0:0:0: [sdb] Write Protect is off
[  103.838136] sd 6:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  103.838141] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  103.838154]  sdb: sdb1
[  103.838921] sdb: p1 size 16156161 limited to end of disk
[  103.899945] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  103.900193] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  118.498919] usb 1-1: USB disconnect, address 5
[  121.708054] usb 1-1: new high speed USB device using ehci_hcd and address 6
[  121.857352] usb 1-1: configuration #1 chosen from 1 choice
[  121.865167] scsi7 : SCSI emulation for USB Mass Storage devices
[  121.865896] usb-storage: device found at 6
[  121.865901] usb-storage: waiting for device to settle before scanning
[  126.864434] usb-storage: device scan complete
[  126.866691] scsi 7:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[  126.870145] sd 7:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  126.870757] sd 7:0:0:0: [sdb] Write Protect is off
[  126.870764] sd 7:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  126.870769] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  126.872159] sd 7:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  126.872763] sd 7:0:0:0: [sdb] Write Protect is off
[  126.872771] sd 7:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  126.872776] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  126.872789]  sdb: sdb1
[  126.875992] sdb: p1 size 16156161 limited to end of disk
[  126.938209] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  126.938438] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  135.968047] usb 1-1: USB disconnect, address 6
[  138.676041] usb 1-1: new high speed USB device using ehci_hcd and address 7
[  138.809784] usb 1-1: configuration #1 chosen from 1 choice
[  138.810375] scsi8 : SCSI emulation for USB Mass Storage devices
[  138.810654] usb-storage: device found at 7
[  138.810661] usb-storage: waiting for device to settle before scanning
[  143.808439] usb-storage: device scan complete
[  143.810682] scsi 8:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[  143.812269] sd 8:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  143.814176] sd 8:0:0:0: [sdb] Write Protect is off
[  143.814187] sd 8:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  143.814194] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  143.815639] sd 8:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  143.816128] sd 8:0:0:0: [sdb] Write Protect is off
[  143.816136] sd 8:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  143.816143] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  143.816155]  sdb: sdb1
[  143.816950] sdb: p1 size 16156161 limited to end of disk
[  143.877911] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  143.878142] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  894.757928] usb 1-1: USB disconnect, address 7
[  919.732044] usb 1-1: new high speed USB device using ehci_hcd and address 8
[  919.866528] usb 1-1: configuration #1 chosen from 1 choice
[  919.868215] scsi9 : SCSI emulation for USB Mass Storage devices
[  919.868949] usb-storage: device found at 8
[  919.868954] usb-storage: waiting for device to settle before scanning
[  924.868423] usb-storage: device scan complete
[  924.870706] scsi 9:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[  924.872269] sd 9:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  924.872933] sd 9:0:0:0: [sdb] Write Protect is off
[  924.872944] sd 9:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  924.872951] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  924.875524] sd 9:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  924.876141] sd 9:0:0:0: [sdb] Write Protect is off
[  924.876150] sd 9:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  924.876158] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  924.876174]  sdb: sdb1
[  924.876919] sdb: p1 size 16156161 limited to end of disk
[  924.939235] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  924.939466] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  931.204933] usb 1-1: USB disconnect, address 8
[  957.981055] usb 1-1: new high speed USB device using ehci_hcd and address 9
[  958.113775] usb 1-1: configuration #1 chosen from 1 choice
[  958.114181] scsi10 : SCSI emulation for USB Mass Storage devices
[  958.114801] usb-storage: device found at 9
[  958.114806] usb-storage: waiting for device to settle before scanning
[  963.113417] usb-storage: device scan complete
[  963.115690] scsi 10:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[  963.121172] sd 10:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  963.121782] sd 10:0:0:0: [sdb] Write Protect is off
[  963.121793] sd 10:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  963.121799] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  963.140746] sd 10:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  963.141929] sd 10:0:0:0: [sdb] Write Protect is off
[  963.141940] sd 10:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  963.141946] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  963.141960]  sdb: sdb1
[  963.142717] sdb: p1 size 16156161 limited to end of disk
[  963.203444] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[  963.203663] sd 10:0:0:0: Attached scsi generic sg2 type 0
[  963.584622] usb 1-1: USB disconnect, address 9
[  988.688041] usb 1-1: new high speed USB device using ehci_hcd and address 10
[  988.822639] usb 1-1: configuration #1 chosen from 1 choice
[  988.823730] scsi11 : SCSI emulation for USB Mass Storage devices
[  988.863791] usb-storage: device found at 10
[  988.863798] usb-storage: waiting for device to settle before scanning
[  993.860491] usb-storage: device scan complete
[  993.862682] scsi 11:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[  993.864261] sd 11:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  993.866488] sd 11:0:0:0: [sdb] Write Protect is off
[  993.866500] sd 11:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  993.866507] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[  993.868011] sd 11:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  993.868500] sd 11:0:0:0: [sdb] Write Protect is off
[  993.868506] sd 11:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  993.868511] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[  993.893956]  sdb: sdb1
[  993.895809] sdb: p1 size 16156161 limited to end of disk
[  993.957748] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[  993.957981] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 1211.905806] usb 1-1: USB disconnect, address 10
[ 1220.828067] usb 1-1: new high speed USB device using ehci_hcd and address 11
[ 1220.964775] usb 1-1: configuration #1 chosen from 1 choice
[ 1220.969176] scsi12 : SCSI emulation for USB Mass Storage devices
[ 1220.972076] usb-storage: device found at 11
[ 1220.972083] usb-storage: waiting for device to settle before scanning
[ 1225.969528] usb-storage: device scan complete
[ 1225.971704] scsi 12:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[ 1225.978050] sd 12:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 1225.988644] sd 12:0:0:0: [sdb] Write Protect is off
[ 1225.988655] sd 12:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 1225.988661] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 1225.991519] sd 12:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 1225.992872] sd 12:0:0:0: [sdb] Write Protect is off
[ 1225.992878] sd 12:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 1225.992883] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 1225.992894]  sdb: sdb1
[ 1225.993585] sdb: p1 size 16156161 limited to end of disk
[ 1226.055779] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 1226.056002] sd 12:0:0:0: Attached scsi generic sg2 type 0
[ 2463.319255] FAT: invalid media value (0xdc)
[ 2463.319268] VFS: Can't find a valid FAT filesystem on dev sdb.
[ 2652.858802] FAT: Unrecognized mount option "force" or missing value
[ 2663.975760] VFS: Can't find ext4 filesystem on dev sdb.
[ 2734.463930] usb 1-1: USB disconnect, address 11
[ 2917.996055] usb 1-1: new high speed USB device using ehci_hcd and address 12
[ 2918.129810] usb 1-1: configuration #1 chosen from 1 choice
[ 2918.136151] scsi13 : SCSI emulation for USB Mass Storage devices
[ 2918.137414] usb-storage: device found at 12
[ 2918.137421] usb-storage: waiting for device to settle before scanning
[ 2923.140467] usb-storage: device scan complete
[ 2923.142700] scsi 13:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[ 2923.165572] sd 13:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 2923.166675] sd 13:0:0:0: [sdb] Write Protect is off
[ 2923.166685] sd 13:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 2923.166691] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 2923.170267] sd 13:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 2923.171058] sd 13:0:0:0: [sdb] Write Protect is off
[ 2923.171068] sd 13:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 2923.171073] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 2923.171091]  sdb: sdb1
[ 2923.171795] sdb: p1 size 16156161 limited to end of disk
[ 2923.234090] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 2923.234303] sd 13:0:0:0: Attached scsi generic sg2 type 0
[ 2943.987664] usb 1-1: USB disconnect, address 12
[ 2948.180041] usb 1-7: new high speed USB device using ehci_hcd and address 13
[ 2948.313905] usb 1-7: configuration #1 chosen from 1 choice
[ 2948.333098] scsi14 : SCSI emulation for USB Mass Storage devices
[ 2948.340556] usb-storage: device found at 13
[ 2948.340563] usb-storage: waiting for device to settle before scanning
[ 2953.340448] usb-storage: device scan complete
[ 2953.342684] scsi 14:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[ 2953.347668] sd 14:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 2953.348442] sd 14:0:0:0: [sdb] Write Protect is off
[ 2953.348452] sd 14:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 2953.348458] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[ 2953.372945] sd 14:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 2953.373752] sd 14:0:0:0: [sdb] Write Protect is off
[ 2953.373763] sd 14:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 2953.373769] sd 14:0:0:0: [sdb] Assuming drive cache: write through
[ 2953.373784]  sdb: sdb1
[ 2953.376278] sdb: p1 size 16156161 limited to end of disk
[ 2953.436803] sd 14:0:0:0: [sdb] Attached SCSI removable disk
[ 2953.437053] sd 14:0:0:0: Attached scsi generic sg2 type 0
[ 3332.138793] usb 1-7: USB disconnect, address 13
[ 3336.140043] usb 1-1: new high speed USB device using ehci_hcd and address 14
[ 3336.273777] usb 1-1: configuration #1 chosen from 1 choice
[ 3336.274182] scsi15 : SCSI emulation for USB Mass Storage devices
[ 3336.274619] usb-storage: device found at 14
[ 3336.274623] usb-storage: waiting for device to settle before scanning
[ 3341.273663] usb-storage: device scan complete
[ 3341.275678] scsi 15:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[ 3341.279165] sd 15:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 3341.279752] sd 15:0:0:0: [sdb] Write Protect is off
[ 3341.279758] sd 15:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 3341.279764] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 3341.300072] sd 15:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 3341.300625] sd 15:0:0:0: [sdb] Write Protect is off
[ 3341.300631] sd 15:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 3341.300636] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 3341.300651]  sdb: sdb1
[ 3341.307784] sdb: p1 size 16156161 limited to end of disk
[ 3341.369884] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[ 3341.370078] sd 15:0:0:0: Attached scsi generic sg2 type 0
[ 4066.245673] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 4066.245688] usb 1-1: USB disconnect, address 14
[ 4068.984059] usb 1-1: new high speed USB device using ehci_hcd and address 15
[ 4069.118781] usb 1-1: configuration #1 chosen from 1 choice
[ 4069.119307] scsi16 : SCSI emulation for USB Mass Storage devices
[ 4069.119703] usb-storage: device found at 15
[ 4069.119708] usb-storage: waiting for device to settle before scanning
[ 4074.117423] usb-storage: device scan complete
[ 4074.119691] scsi 16:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[ 4074.124818] sd 16:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 4074.125399] sd 16:0:0:0: [sdb] Write Protect is off
[ 4074.125408] sd 16:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 4074.125413] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[ 4074.146271] sd 16:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[ 4074.146878] sd 16:0:0:0: [sdb] Write Protect is off
[ 4074.146884] sd 16:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[ 4074.146890] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[ 4074.146903]  sdb: sdb1
[ 4074.147669] sdb: p1 size 16156161 limited to end of disk
[ 4074.209906] sd 16:0:0:0: [sdb] Attached SCSI removable disk
[ 4074.210119] sd 16:0:0:0: Attached scsi generic sg2 type 0
[53913.679555] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[53913.679569] usb 1-1: USB disconnect, address 15
[54279.320078] usb 1-1: new high speed USB device using ehci_hcd and address 16
[54279.454543] usb 1-1: configuration #1 chosen from 1 choice
[54279.455666] scsi17 : SCSI emulation for USB Mass Storage devices
[54279.480849] usb-storage: device found at 16
[54279.480857] usb-storage: waiting for device to settle before scanning
[54284.480483] usb-storage: device scan complete
[54284.482711] scsi 17:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[54284.499648] sd 17:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[54284.500251] sd 17:0:0:0: [sdb] Write Protect is off
[54284.500257] sd 17:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[54284.500263] sd 17:0:0:0: [sdb] Assuming drive cache: write through
[54284.504808] sd 17:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[54284.509470] sd 17:0:0:0: [sdb] Write Protect is off
[54284.509481] sd 17:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[54284.509487] sd 17:0:0:0: [sdb] Assuming drive cache: write through
[54284.509506]  sdb: sdb1
[54284.510815] sdb: p1 size 16156161 limited to end of disk
[54284.572730] sd 17:0:0:0: [sdb] Attached SCSI removable disk
[54284.572956] sd 17:0:0:0: Attached scsi generic sg2 type 0
[54298.659931] usb 1-1: USB disconnect, address 16
[54308.308040] usb 1-1: new high speed USB device using ehci_hcd and address 17
[54308.441793] usb 1-1: configuration #1 chosen from 1 choice
[54308.442368] scsi18 : SCSI emulation for USB Mass Storage devices
[54308.470239] usb-storage: device found at 17
[54308.470248] usb-storage: waiting for device to settle before scanning
[54313.468471] usb-storage: device scan complete
[54313.470670] scsi 18:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[54313.472261] sd 18:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[54313.472877] sd 18:0:0:0: [sdb] Write Protect is off
[54313.472884] sd 18:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[54313.472889] sd 18:0:0:0: [sdb] Assuming drive cache: write through
[54313.494568] sd 18:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[54313.498431] sd 18:0:0:0: [sdb] Write Protect is off
[54313.498442] sd 18:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[54313.498448] sd 18:0:0:0: [sdb] Assuming drive cache: write through
[54313.498463]  sdb: sdb1
[54313.499563] sdb: p1 size 16156161 limited to end of disk
[54313.561867] sd 18:0:0:0: [sdb] Attached SCSI removable disk
[54313.562097] sd 18:0:0:0: Attached scsi generic sg2 type 0
[54318.562425] usb 1-1: USB disconnect, address 17
[55179.196040] usb 1-1: new high speed USB device using ehci_hcd and address 18
[55179.330538] usb 1-1: configuration #1 chosen from 1 choice
[55179.331680] scsi19 : SCSI emulation for USB Mass Storage devices
[55179.338298] usb-storage: device found at 18
[55179.338307] usb-storage: waiting for device to settle before scanning
[55184.336476] usb-storage: device scan complete
[55184.338673] scsi 19:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[55184.344892] sd 19:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[55184.345910] sd 19:0:0:0: [sdb] Write Protect is off
[55184.345919] sd 19:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[55184.345925] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[55184.356146] sd 19:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[55184.356749] sd 19:0:0:0: [sdb] Write Protect is off
[55184.356756] sd 19:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[55184.356761] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[55184.356774]  sdb: sdb1
[55184.358739] sdb: p1 size 16156161 limited to end of disk
[55184.420927] sd 19:0:0:0: [sdb] Attached SCSI removable disk
[55184.421724] sd 19:0:0:0: Attached scsi generic sg2 type 0
[56014.084549] usb 1-1: USB disconnect, address 18
[56886.816046] usb 1-1: new high speed USB device using ehci_hcd and address 19
[56886.949798] usb 1-1: configuration #1 chosen from 1 choice
[56886.980172] scsi20 : SCSI emulation for USB Mass Storage devices
[56886.983476] usb-storage: device found at 19
[56886.983483] usb-storage: waiting for device to settle before scanning
[56891.980356] usb-storage: device scan complete
[56891.982685] scsi 20:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[56891.987526] sd 20:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[56891.988640] sd 20:0:0:0: [sdb] Write Protect is off
[56891.988648] sd 20:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[56891.988654] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[56891.990143] sd 20:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[56891.990753] sd 20:0:0:0: [sdb] Write Protect is off
[56891.990759] sd 20:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[56891.990764] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[56891.990775]  sdb: sdb1
[56891.991417] sdb: p1 size 16156161 limited to end of disk
[56892.085457] sd 20:0:0:0: [sdb] Attached SCSI removable disk
[56892.085687] sd 20:0:0:0: Attached scsi generic sg2 type 0
[57405.735785] FAT: Unrecognized mount option "force" or missing value

```

---

### Post by abclemons on 2009-05-31
Some more possibly useful information I got from the [B]/usr/sbin/lsusb -vv
[/B] command:
```
Bus 001 Device 019: ID 10d6:1101 Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x10d6 Actions Semiconductor Co., Ltd
  idProduct          0x1101 D-Wave 2GB MP4 Player
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      5 SFF-8070i
      bInterfaceProtocol     80 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

```

---

### Post by LintonHanes on 2010-01-31
[  103.826695] scsi 6:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[  103.830293] sd 6:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)
[  103.831434] sd 6:0:0:0: [sdb] Write Protect is off
[  103.831443] sd 6:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  103.831448] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  103.837523] sd 6:0:0:0: [sdb] 614401 512-byte hardware sectors: (314 MB/300 MiB)

so that needs formatting badly > 300mb won't be too useful

I guess you know by now to try plugging it in while it's off etc...

I've got one of these and am trying to sort it out

---

