---
title: "undo ext4"
date: 2008-12-26
forum: General Help
---

### Post by ispy on 2008-12-26
Unthinkingly, I upgraded my whole partition to ext4. now, I read that grub has problems with it.

Now I think I want to wait, is there a way to fix this?

thanks,
Ispy

---

### Post by regala on 2008-12-26
> **ispy said:**
> Unthinkingly, I upgraded my whole partition to ext4. now, I read that grub has problems with it.

Now I think I want to wait, is there a way to fix this?

thanks,
Ispy

You upgraded your whole partition in which way ?
I wonder because if you have one and only one big partition it is quite complicated to do. You used a liveCD ?
Or did you just boot a recent enough kernel and see the ext4(dev) module taking care of your ext3 partition ?
so the question is: which version of Ubuntu do you run and which kernel do you boot ? :)

a hint would be the dmesg output. could you provide it here or on a pastebin service ?

cheers and happy xmas !

---

### Post by ispy on 2008-12-26
Looking at this site:

[http://kernelnewbies.org/Ext4]("http://kernelnewbies.org/Ext4")

I tried the code:

```
tune2fs -O extents,uninit_bg,dir_index /dev/yourfilesystem
```

and then:

```
fsck -pf /dev/yourfilesystem 
```

And now I read that Grub won't boot it. I haven't tried rebooting yet (I'm on a Xubuntu Live CD I had lying around).

It is on one big partition (I haven't set up my /home partition yet) with Ubuntu 8.10 (I'm not sure which kernel, but it ended with .9)

here's the dmesg output:

```
ubuntu@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d3400 (usable)
[    0.000000]  BIOS-e820: 000000003f6d3400 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3f6d3 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3ee9f000 - 3f6afcde
[    0.000000] Allocated new RAMDISK: 005c4000 - 00dd4cde
[    0.000000] Move RAMDISK from 000000003ee9f000 - 000000003f6afcdd to 005c4000 - 00dd4cdd
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 3F6D3A0F, 0040 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: FACP 3F6D4800, 0074 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: DSDT 3F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 3F6E3C00, 0040
[    0.000000] ACPI: HPET 3F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
[    0.000000] ACPI: APIC 3F6D5000, 0068 (r1 DELL    M07     27D70402 ASL        47)
[    0.000000] ACPI: MCFG 3F6D4FC0, 003E (r16 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: SLIC 3F6D509C, 0176 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: BOOT 3F6D4BC0, 0028 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: SSDT 3F6D3A4F, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00005c4000 - 0000dd4cde]      NEW RAMDISK ==> [00005c4000 - 0000dd4cde]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003f6d3
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f6d3
[    0.000000] On node 0 totalpages: 259698
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 30151 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
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
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257414
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1662.483 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1015220k/1039180k available (2572k kernel code, 23212k reserved, 1160k data, 424k init, 121676k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.96 BogoMIPS (lpj=6649932)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018635] ACPI: Core revision 20080609
[    0.020462] ACPI: Checking initramfs for custom DSDT
[    0.446481] ENABLING IO-APIC IRQs
[    0.446684] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.486899] CPU0: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[    0.488030] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3324.98 BogoMIPS (lpj=6649965)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.572568] CPU1: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[    0.572593] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.576031] Measured 3845529620 cycles TSC warp between CPUs, turning off TSC clock.
[    0.576031] Marking TSC unstable due to check_tsc_sync_source failed
[    0.576055] Brought up 2 CPUs
[    0.576059] Total of 2 processors activated (6649.94 BogoMIPS).
[    0.576086] CPU0 attaching sched-domain:
[    0.576090]  domain 0: span 0-1 level MC
[    0.576093]   groups: 0 1
[    0.576101] CPU1 attaching sched-domain:
[    0.576104]  domain 0: span 0-1 level MC
[    0.576106]   groups: 1 0
[    0.576235] net_namespace: 840 bytes
[    0.576235] Booting paravirtualized kernel on bare hardware
[    0.576357] Time: 19:55:59  Date: 12/26/08
[    0.576391] NET: Registered protocol family 16
[    0.576417] EISA bus registered
[    0.576417] ACPI: bus type pci registered
[    0.576417] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.576417] PCI: MCFG area at f0000000 reserved in E820
[    0.576417] PCI: Using MMCONFIG for extended config space
[    0.576417] PCI: Using configuration type 1 for base access
[    0.580311] ACPI: EC: Look up EC in DSDT
[    0.599093] ACPI: Interpreter enabled
[    0.599097] ACPI: (supports S0 S3 S4 S5)
[    0.600035] ACPI: Using IOAPIC for interrupt routing
[    0.636056] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.636103] PCI: 0000:00:02.0 reg 10 32bit mmio: [eff00000, eff7ffff]
[    0.636109] PCI: 0000:00:02.0 reg 14 io port: [eff8, efff]
[    0.636115] PCI: 0000:00:02.0 reg 18 32bit mmio: [d0000000, dfffffff]
[    0.636121] PCI: 0000:00:02.0 reg 1c 32bit mmio: [efec0000, efefffff]
[    0.636158] PCI: 0000:00:02.1 reg 10 32bit mmio: [eff80000, efffffff]
[    0.636278] PCI: 0000:00:1b.0 reg 10 64bit mmio: [efebc000, efebffff]
[    0.636335] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.636341] pci 0000:00:1b.0: PME# disabled
[    0.636415] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.636420] pci 0000:00:1c.0: PME# disabled
[    0.636497] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.636503] pci 0000:00:1c.3: PME# disabled
[    0.636556] PCI: 0000:00:1d.0 reg 20 io port: [bf80, bf9f]
[    0.636622] PCI: 0000:00:1d.1 reg 20 io port: [bf60, bf7f]
[    0.636688] PCI: 0000:00:1d.2 reg 20 io port: [bf40, bf5f]
[    0.636753] PCI: 0000:00:1d.3 reg 20 io port: [bf20, bf3f]
[    0.636823] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffa80000, ffa803ff]
[    0.636883] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.636890] pci 0000:00:1d.7: PME# disabled
[    0.637053] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.637059] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.637108] PCI: 0000:00:1f.2 reg 10 io port: [1f0, 1f7]
[    0.637116] PCI: 0000:00:1f.2 reg 14 io port: [3f4, 3f7]
[    0.637125] PCI: 0000:00:1f.2 reg 18 io port: [170, 177]
[    0.637134] PCI: 0000:00:1f.2 reg 1c io port: [374, 377]
[    0.637143] PCI: 0000:00:1f.2 reg 20 io port: [bfa0, bfaf]
[    0.637176] pci 0000:00:1f.2: PME# supported from D3hot
[    0.637182] pci 0000:00:1f.2: PME# disabled
[    0.637241] PCI: 0000:00:1f.3 reg 20 io port: [10c0, 10df]
[    0.637457] PCI: 0000:0b:00.0 reg 10 32bit mmio: [efdff000, efdfffff]
[    0.637668] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
[    0.637682] pci 0000:0b:00.0: PME# disabled
[    0.637739] PCI: bridge 0000:00:1c.0 32bit mmio: [efd00000, efdfffff]
[    0.637807] PCI: bridge 0000:00:1c.3 io port: [d000, dfff]
[    0.637813] PCI: bridge 0000:00:1c.3 32bit mmio: [efa00000, efcfffff]
[    0.637823] PCI: bridge 0000:00:1c.3 64bit mmio pref: [e0000000, e01fffff]
[    0.637868] PCI: 0000:03:00.0 reg 10 32bit mmio: [ef9fe000, ef9fffff]
[    0.637924] pci 0000:03:00.0: supports D1
[    0.637926] pci 0000:03:00.0: supports D2
[    0.637929] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.637935] pci 0000:03:00.0: PME# disabled
[    0.637973] PCI: 0000:03:01.0 reg 10 32bit mmio: [ef9fd800, ef9fdfff]
[    0.638031] pci 0000:03:01.0: supports D1
[    0.638033] pci 0000:03:01.0: supports D2
[    0.638036] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.638042] pci 0000:03:01.0: PME# disabled
[    0.638080] PCI: 0000:03:01.1 reg 10 32bit mmio: [ef9fd400, ef9fd4ff]
[    0.638139] pci 0000:03:01.1: supports D1
[    0.638141] pci 0000:03:01.1: supports D2
[    0.638144] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.638150] pci 0000:03:01.1: PME# disabled
[    0.638187] PCI: 0000:03:01.2 reg 10 32bit mmio: [ef9fd500, ef9fd5ff]
[    0.638246] pci 0000:03:01.2: supports D1
[    0.638248] pci 0000:03:01.2: supports D2
[    0.638251] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.638257] pci 0000:03:01.2: PME# disabled
[    0.638296] PCI: 0000:03:01.3 reg 10 32bit mmio: [ef9fd600, ef9fd6ff]
[    0.638355] pci 0000:03:01.3: supports D1
[    0.638357] pci 0000:03:01.3: supports D2
[    0.638360] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.638366] pci 0000:03:01.3: PME# disabled
[    0.638404] PCI: 0000:03:01.4 reg 10 32bit mmio: [ef9fd700, ef9fd7ff]
[    0.638462] pci 0000:03:01.4: supports D1
[    0.638464] pci 0000:03:01.4: supports D2
[    0.638467] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.638473] pci 0000:03:01.4: PME# disabled
[    0.638538] pci 0000:00:1e.0: transparent bridge
[    0.638547] PCI: bridge 0000:00:1e.0 32bit mmio: [ef900000, ef9fffff]
[    0.638577] bus 00 -> node 0
[    0.638584] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.639212] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.639401] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.639582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.652180] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.652352] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    0.652519] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.652689] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.652859] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.653031] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.653203] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.653375] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.653478] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.653478] pnp: PnP ACPI init
[    0.653478] ACPI: bus type pnp registered
[    0.697033] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.697033] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.697033] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.697033] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.697033] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.697033] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.697033] pnp: PnP ACPI: found 12 devices
[    0.697033] ACPI: ACPI bus type pnp unregistered
[    0.697033] PnPBIOS: Disabled by ACPI PNP
[    0.697033] PCI: Using ACPI for IRQ routing
[    0.704043] NET: Registered protocol family 8
[    0.704046] NET: Registered protocol family 20
[    0.704066] NetLabel: Initializing
[    0.704066] NetLabel:  domain hash size = 128
[    0.704066] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.704080] NetLabel:  unlabeled traffic allowed by default
[    0.704090] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.704095] hpet0: 3 64-bit timers, 14318180 Hz
[    0.705744] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.705747]    actual entries 65620
[    0.705842] AppArmor: AppArmor Filesystem Enabled
[    0.705870] ACPI: RTC can wake from S4
[    0.708048] Switched to high resolution mode on CPU 0
[    0.708631] Switched to high resolution mode on CPU 1
[    0.712033] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.712037] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.712041] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.712045] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.712049] system 00:00: iomem range 0x100000-0x3f6d33ff could not be reserved
[    0.712053] system 00:00: iomem range 0x3f6d3400-0x3f6fffff could not be reserved
[    0.712057] system 00:00: iomem range 0x3f700000-0x3f7fffff could not be reserved
[    0.712061] system 00:00: iomem range 0x3f700000-0x3fefffff could not be reserved
[    0.712065] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[    0.712069] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.712073] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.712078] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[    0.712082] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    0.712086] system 00:00: iomem range 0xf4000000-0xf4003fff could not be reserved
[    0.712090] system 00:00: iomem range 0xf4004000-0xf4004fff could not be reserved
[    0.712094] system 00:00: iomem range 0xf4005000-0xf4005fff could not be reserved
[    0.712098] system 00:00: iomem range 0xf4006000-0xf4006fff could not be reserved
[    0.712102] system 00:00: iomem range 0xf4008000-0xf400bfff could not be reserved
[    0.712106] system 00:00: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.712116] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.712124] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.712128] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.712132] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.712135] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.712147] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.712150] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.712154] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.712157] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.712161] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.712171] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.747685] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.747688] pci 0000:00:1c.0:   IO window: disabled
[    0.747696] pci 0000:00:1c.0:   MEM window: 0xefd00000-0xefdfffff
[    0.747702] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.747711] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
[    0.747716] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.747723] pci 0000:00:1c.3:   MEM window: 0xefa00000-0xefcfffff
[    0.747729] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0000000-0x000000e01fffff
[    0.747739] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.747742] pci 0000:00:1e.0:   IO window: disabled
[    0.747749] pci 0000:00:1e.0:   MEM window: 0xef900000-0xef9fffff
[    0.747755] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.747775] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.747782] pci 0000:00:1c.0: setting latency timer to 64
[    0.747794] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.747800] pci 0000:00:1c.3: setting latency timer to 64
[    0.747809] pci 0000:00:1e.0: setting latency timer to 64
[    0.747814] bus: 00 index 0 io port: [0, ffff]
[    0.747817] bus: 00 index 1 mmio: [0, ffffffff]
[    0.747820] bus: 0b index 0 mmio: [0, 0]
[    0.747823] bus: 0b index 1 mmio: [efd00000, efdfffff]
[    0.747826] bus: 0b index 2 mmio: [0, 0]
[    0.747828] bus: 0b index 3 mmio: [0, 0]
[    0.747831] bus: 0c index 0 io port: [d000, dfff]
[    0.747834] bus: 0c index 1 mmio: [efa00000, efcfffff]
[    0.747837] bus: 0c index 2 mmio: [e0000000, e01fffff]
[    0.747840] bus: 0c index 3 mmio: [0, 0]
[    0.747842] bus: 03 index 0 mmio: [0, 0]
[    0.747845] bus: 03 index 1 mmio: [ef900000, ef9fffff]
[    0.747848] bus: 03 index 2 mmio: [0, 0]
[    0.747850] bus: 03 index 3 io port: [0, ffff]
[    0.747853] bus: 03 index 4 mmio: [0, ffffffff]
[    0.747864] NET: Registered protocol family 2
[    0.760076] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.760352] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.760880] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.761165] TCP: Hash tables configured (established 131072 bind 65536)
[    0.761169] TCP reno registered
[    0.768108] NET: Registered protocol family 1
[    0.768244] checking if image is initramfs... it is
[    1.501016] Clocksource tsc unstable (delta = 2313128662 ns)
[    1.638963] Freeing initrd memory: 8259k freed
[    1.639194] Simple Boot Flag at 0x79 set to 0x1
[    1.640572] audit: initializing netlink socket (disabled)
[    1.640600] type=2000 audit(1230321359.637:1): initialized
[    1.648162] highmem bounce pool size: 64 pages
[    1.648170] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.651450] VFS: Disk quotas dquot_6.5.1
[    1.651584] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.651731] msgmni has been set to 1762
[    1.651888] io scheduler noop registered
[    1.651892] io scheduler anticipatory registered
[    1.651895] io scheduler deadline registered
[    1.651910] io scheduler cfq registered (default)
[    1.651925] pci 0000:00:02.0: Boot video device
[    1.652204] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.652257] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.652312] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.652379] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.652483] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.652636] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.652687] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.652736] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.652800] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.652865] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.653384] isapnp: Scanning for PnP cards...
[    2.007432] isapnp: No Plug & Play device found
[    2.056282] hpet_resources: 0xfed00000 is busy
[    2.056410] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.059638] brd: module loaded
[    2.059737] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.059904] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.062836] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.062844] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.064181] mice: PS/2 mouse device common for all mice
[    2.064375] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.064409] rtc0: alarms up to one month, y3k, hpet irqs
[    2.064615] EISA: Probing bus 0 at eisa.0
[    2.064625] Cannot allocate resource for EISA slot 1
[    2.064659] EISA: Detected 0 cards.
[    2.064662] cpuidle: using governor ladder
[    2.064665] cpuidle: using governor menu
[    2.065313] TCP cubic registered
[    2.065346] Using IPI No-Shortcut mode
[    2.065607] registered taskstats version 1
[    2.065753]   Magic number: 4:897:951
[    2.065765] tty ttya6: hash matches
[    2.065832] tty tty8: hash matches
[    2.065894] rtc_cmos 00:06: setting system clock to 2008-12-26 19:56:00 UTC (1230321360)
[    2.065899] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.065901] EDD information not available.
[    2.066172] Freeing unused kernel memory: 424k freed
[    2.066230] Write protecting the kernel text: 2576k
[    2.066276] Write protecting the kernel read-only data: 936k
[    2.066785] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.248621] fuse init (API version 7.9)
[    2.289643] ACPI: SSDT 3F6D4176, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.290055] ACPI: SSDT 3F6D3F2B, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.309250] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.309332] processor ACPI0007:00: registered as cooling_device0
[    2.309339] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.309763] ACPI: SSDT 3F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.310144] ACPI: SSDT 3F6D40F1, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.310888] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.310961] processor ACPI0007:01: registered as cooling_device1
[    2.310967] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.317412] thermal LNXTHERM:01: registered as thermal_zone0
[    2.321088] ACPI: Thermal Zone [THM] (51 C)
[    2.746984] usbcore: registered new interface driver usbfs
[    2.747012] usbcore: registered new interface driver hub
[    2.747081] usbcore: registered new device driver usb
[    2.757102] USB Universal Host Controller Interface driver v3.0
[    2.757168] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.757180] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.757186] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.757235] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.757276] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    2.757466] usb usb1: configuration #1 chosen from 1 choice
[    2.757503] hub 1-0:1.0: USB hub found
[    2.757512] hub 1-0:1.0: 2 ports detected
[    2.861364] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.861378] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.861383] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.861414] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.861455] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    2.861573] usb usb2: configuration #1 chosen from 1 choice
[    2.861608] hub 2-0:1.0: USB hub found
[    2.861616] hub 2-0:1.0: 2 ports detected
[    2.870642] No dock devices found.
[    2.922745] SCSI subsystem initialized
[    2.956150] libata version 3.00 loaded.
[    2.965539] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.965551] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.965556] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.965589] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.965631] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    2.965745] usb usb3: configuration #1 chosen from 1 choice
[    2.965780] hub 3-0:1.0: USB hub found
[    2.965789] hub 3-0:1.0: 2 ports detected
[    3.072354] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.072367] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.072372] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.072403] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.072445] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    3.072569] usb usb4: configuration #1 chosen from 1 choice
[    3.072604] hub 4-0:1.0: USB hub found
[    3.072613] hub 4-0:1.0: 2 ports detected
[    3.176591] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.176611] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.176616] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.176648] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.180555] ehci_hcd 0000:00:1d.7: debug port 1
[    3.180563] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.180573] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    3.196027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.196215] usb usb5: configuration #1 chosen from 1 choice
[    3.196253] hub 5-0:1.0: USB hub found
[    3.196262] hub 5-0:1.0: 8 ports detected
[    3.300226] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.353412] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.357566] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.416106] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    3.419818] b44.c:v2.0
[    3.421178] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.421214] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.421231] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.436695] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:25:d8:9c
[    3.442117] ata_piix 0000:00:1f.2: version 2.12
[    3.442131] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.442137] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.442184] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.442268] scsi0 : ata_piix
[    3.442390] scsi1 : ata_piix
[    3.443582] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    3.443586] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    3.604967] ata1.00: failed to set max address (err_mask=0x1)
[    3.604972] ata1.00: device aborted resize (153356490 -> 156301488), skipping HPA handling
[    3.604979] ata1.00: ATA-7: Hitachi HTS541080G9SA00, MB4OC60R, max UDMA/100
[    3.604982] ata1.00: 153356490 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    3.620377] ata1.00: configured for UDMA/100
[    3.784539] ata2.00: ATAPI: SONY DVD+/-RW DW-Q58A, UDS2, max UDMA/33
[    3.800473] ata2.00: configured for UDMA/33
[    3.800606] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54108 MB4O PQ: 0 ANSI: 5
[    3.801404] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-Q58A  UDS2 PQ: 0 ANSI: 5
[    3.811623] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.811671] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    3.825255] Driver 'sd' needs updating - please use bus_type methods
[    3.825487] sd 0:0:0:0: [sda] 153356490 512-byte hardware sectors (78519 MB)
[    3.825515] sd 0:0:0:0: [sda] Write Protect is off
[    3.825518] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.825563] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.825656] sd 0:0:0:0: [sda] 153356490 512-byte hardware sectors (78519 MB)
[    3.825681] sd 0:0:0:0: [sda] Write Protect is off
[    3.825685] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.825730] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.825736]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.187375]  sda1 sda2 < sda5 >
[    4.215034] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.219038] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.219043] Uniform CD-ROM driver Revision: 3.20
[    4.219151] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.489819] EXT3-fs: sda1: couldn't mount because of unsupported optional features (40).
[    4.628784] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc0002ad52d41]
[    5.537353] EXT3-fs: sda1: couldn't mount because of unsupported optional features (40).
[    6.632017] ISO 9660 Extensions: Microsoft Joliet Level 3
[    6.662664] ISO 9660 Extensions: RRIP_1991A
[    6.908990] aufs 20080922
[    6.916845] loop: module loaded
[    7.185501] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   56.273631] udevd version 124 started
[   57.056917] Linux agpgart interface v0.103
[   57.090667] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   57.091274] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   57.107726] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   57.215435] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   57.317528] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   57.536750] iTCO_vendor_support: vendor-support=0
[   57.551394] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   57.551501] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   57.551643] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   58.005930] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   58.178685] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   58.479202] intel_rng: FWH not detected
[   58.737441] ACPI: AC Adapter [AC] (on-line)
[   59.137462] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   59.160387] ACPI: Lid Switch [LID]
[   59.161591] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   59.171030] ricoh-mmc: Ricoh MMC Controller disabling driver
[   59.171034] ricoh-mmc: Copyright(c) Philip Langdale
[   59.171072] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
[   59.171093] ricoh-mmc: Controller is now disabled.
[   59.220191] ACPI: Power Button (CM) [PBTN]
[   59.220280] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   59.284442] ACPI: Sleep Button (CM) [SBTN]
[   59.429823] ACPI: Battery Slot [BAT0] (battery present)
[   59.483897] ACPI: WMI: Mapper loaded
[   59.874698] sdhci: Secure Digital Host Controller Interface driver
[   59.874702] sdhci: Copyright(c) Pierre Ossman
[   60.018250] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   60.018275] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   60.021384] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   60.023770] acpi device:25: registered as cooling_device2
[   60.024500] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/device:22/input/input6
[   60.066191] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   60.082107] acpi device:2a: registered as cooling_device3
[   60.084276] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:27/input/input7
[   60.125237] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   60.125775] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2c/input/input8
[   60.165211] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   60.172250] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   60.206470] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   60.206475] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   60.206752] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   60.206768] iwl3945 0000:0b:00.0: setting latency timer to 64
[   60.206794] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   60.281471] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   60.292475] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   60.324809] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   60.593137] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   60.593166] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   60.821150] iwl3945 0000:0b:00.0: PCI INT A disabled
[   63.348740] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   64.073763] ip_tables: (C) 2000-2006 Netfilter Core Team
[   68.683092] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   68.777800] apm: BIOS not found.
[   69.108560] lp: driver loaded but no devices found
[   69.226310] ppdev: user-space parallel port driver
[   75.632593] Bluetooth: Core ver 2.13
[   75.634329] NET: Registered protocol family 31
[   75.634339] Bluetooth: HCI device and connection manager initialized
[   75.634346] Bluetooth: HCI socket layer initialized
[   75.688328] Bluetooth: L2CAP ver 2.11
[   75.688340] Bluetooth: L2CAP socket layer initialized
[   75.962122] Bluetooth: RFCOMM socket layer initialized
[   75.962601] Bluetooth: RFCOMM TTY layer initialized
[   75.962612] Bluetooth: RFCOMM ver 1.10
[   75.967955] Bluetooth: SCO (Voice Link) ver 0.6
[   75.967965] Bluetooth: SCO socket layer initialized
[   76.638148] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   76.638259] Bluetooth: BNEP filters: protocol multicast
[   77.038843] Bridge firewalling registered
[   77.039454] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   81.443377] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   81.443549] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   81.447769] firmware: requesting iwlwifi-3945-1.ucode
[   81.687417] Registered led device: iwl-phy0:radio
[   81.688753] Registered led device: iwl-phy0:assoc
[   81.689983] Registered led device: iwl-phy0:RX
[   81.691135] Registered led device: iwl-phy0:TX
[   82.319623] NET: Registered protocol family 17
[   87.417011] [drm] Initialized drm 1.1.0 20060810
[   87.464223] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   87.464241] pci 0000:00:02.0: setting latency timer to 64
[   87.470138] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  125.277802] NET: Registered protocol family 10
[  125.278933] lo: Disabled Privacy Extensions
[  125.281094] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  125.282461] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  125.494123] CPU0 attaching NULL sched-domain.
[  125.494139] CPU1 attaching NULL sched-domain.
[  125.498321] CPU0 attaching sched-domain:
[  125.498333]  domain 0: span 0-1 level MC
[  125.498339]   groups: 0 1
[  125.498350] CPU1 attaching sched-domain:
[  125.498355]  domain 0: span 0-1 level MC
[  125.498359]   groups: 1 0
[  135.488669] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  135.491436] wlan0: authenticated
[  135.491443] wlan0: associate with AP 00:14:6c:f8:e3:18
[  135.494221] wlan0: RX AssocResp from 00:14:6c:f8:e3:18 (capab=0x431 status=0 aid=1)
[  135.494229] wlan0: associated
[  135.494644] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  139.490599] wlan0: deauthenticated
[  140.488073] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  140.489813] wlan0: authenticated
[  140.489826] wlan0: associate with AP 00:14:6c:f8:e3:18
[  140.492513] wlan0: RX ReassocResp from 00:14:6c:f8:e3:18 (capab=0x431 status=0 aid=1)
[  140.492524] wlan0: associated
[  144.490679] wlan0: deauthenticated
[  145.488069] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  145.489867] wlan0: authenticated
[  145.489877] wlan0: associate with AP 00:14:6c:f8:e3:18
[  145.492541] wlan0: RX ReassocResp from 00:14:6c:f8:e3:18 (capab=0x431 status=0 aid=1)
[  145.492550] wlan0: associated
[  146.332069] wlan0: no IPv6 routers present
[  149.490723] wlan0: deauthenticated
[  150.488068] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  150.489820] wlan0: authenticated
[  150.489831] wlan0: associate with AP 00:14:6c:f8:e3:18
[  150.492823] wlan0: RX ReassocResp from 00:14:6c:f8:e3:18 (capab=0x431 status=0 aid=1)
[  150.492832] wlan0: associated
[  154.490792] wlan0: deauthenticated
[  155.488082] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  155.489881] wlan0: authenticated
[  155.489891] wlan0: associate with AP 00:14:6c:f8:e3:18
[  155.494337] wlan0: RX ReassocResp from 00:14:6c:f8:e3:18 (capab=0x431 status=0 aid=1)
[  155.494346] wlan0: associated
[  159.507536] wlan0: deauthenticated
[  160.504061] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  160.505815] wlan0: authenticated
[  160.505826] wlan0: associate with AP 00:14:6c:f8:e3:18
[  160.509679] wlan0: RX ReassocResp from 00:14:6c:f8:e3:18 (capab=0x431 status=0 aid=1)
[  160.509688] wlan0: associated
[  160.510698] wlan0: disassociating by local choice (reason=3)
[  173.695147] wlan0: deauthenticated
[  173.696078] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  173.699598] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  173.699619] wlan0: authenticated
[  173.699625] wlan0: associate with AP 00:14:6c:f8:e3:18
[  173.712365] wlan0: deauthenticated
[  174.712068] wlan0: authenticate with AP 00:14:6c:f8:e3:18
[  174.714230] wlan0: authenticated
[  174.714240] wlan0: associate with AP 00:14:6c:f8:e3:18
[  174.718084] wlan0: RX ReassocResp from 00:14:6c:f8:e3:18 (capab=0x431 status=0 aid=1)
[  174.718093] wlan0: associated
[  868.248080] CE: hpet increasing min_delta_ns to 15000 nsec
[  868.248087] CE: hpet increasing min_delta_ns to 22500 nsec
[  868.248087] CE: hpet increasing min_delta_ns to 33750 nsec
[ 1142.028081] CE: hpet increasing min_delta_ns to 50624 nsec
ubuntu@ubuntu:~$ 


```

---

### Post by caljohnsmith on 2008-12-26
What version of Grub are you using in your Ubuntu partition? How about doing:
```
sudo mount /dev/[COLOR="Blue"]sdaX [/COLOR]/mnt
sudo chroot /mnt
apt-cache policy grub
exit
```
Replace sdaX with your Ubuntu partition, and please post the output of the above commands.

---

### Post by ispy on 2008-12-26
My Live CD won't mount it.

I get this:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: unknown filesystem type 'ext4'
ubuntu@ubuntu:~$
```

---

### Post by caljohnsmith on 2008-12-26
See if by chance you can mount it as ext3:
```
sudo mount -t ext3 /dev/sda1 /mnt
```

---

### Post by ispy on 2008-12-26
> **caljohnsmith said:**
> See if by chance you can mount it as ext3:
```
sudo mount -t ext3 /dev/sda1 /mnt
```

```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 

```

---

### Post by ispy on 2008-12-26
I should make this clear.

I'd be fine with keeping the ext4 fs if Grub could handle it.

But since Grub won't be able to handle it until later, I either need a patch for grub or a way to go back to ext3.

---

### Post by albinootje on 2008-12-26
> **ispy said:**
> Unthinkingly, I upgraded my whole partition to ext4. now, I read that grub has problems with it.

Now I think I want to wait, is there a way to fix this?


1) Time to backup to usb-disk or DVD first I'd say.

2)

See also comment #28 here :
[http://ubuntuforums.org/showthread.php?p=6437206](http://ubuntuforums.org/showthread.php?p=6437206)

Here's Grub2, still in development, but available as deb package :
[http://packages.ubuntu.com/search?keywords=grub2](http://packages.ubuntu.com/search?keywords=grub2)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/294763](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/294763)
> 
Launchpad Janitor  wrote on 2008-11-17:  (permalink)

This bug was fixed in the package grub2 - 1.96+20080724-12ubuntu1
---cut---
 * New upstream snapshot includes ext4 extents support (LP: #294763)

3) Perhaps the Sidux Live cd already has support for ext4 ?
Ext4 and Grub2 are mentioned here (Feb. 2008) :
[http://www.sidux.com/PNphpBB2-viewtopic-t-8990.html](http://www.sidux.com/PNphpBB2-viewtopic-t-8990.html)

Using a Jaunty Live cd is also an option.
Perhaps you can even boot from that by editing the boot parameters at the install cd prompt.

---

### Post by Archmage on 2008-12-26
Now, Grub can't load ext4. Grub2 can, but isn't stable yet and therefore isn't in Ubuntu.

Therefore if you want to use ext4, you need a bootpartiton in ext3 or something like this. The rest can be ext4.

But keep in mind that the Kernel from 8.10 or older can't handle ext4 at all. This could only work if you use the daily-build of Jaunty Jackalope. Even the Alpha 2 is to old.

---

### Post by ispy on 2008-12-26
thanks albinootje.

1: How do I go about backing up if I can't mount the filesystem?

2: How do I install grub2 if I can't mount the filesystem?

I appreciate the help a lot guys, I almost forgot why I love the forums so much.

---

### Post by thomas228 on 2008-12-26
> **albinootje said:**
> 1) Time to backup to usb-disk or DVD first I'd say.

2)

See also comment #28 here :
[http://ubuntuforums.org/showthread.php?p=6437206](http://ubuntuforums.org/showthread.php?p=6437206)

Here's Grub2, still in development, but available as deb package :
[http://packages.ubuntu.com/search?keywords=grub2](http://packages.ubuntu.com/search?keywords=grub2)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/294763](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/294763)

3) Perhaps the Sidux Live cd already has support for ext4 ?
Ext4 and Grub2 are mentioned here (Feb. 2008) :
[http://www.sidux.com/PNphpBB2-viewtopic-t-8990.html](http://www.sidux.com/PNphpBB2-viewtopic-t-8990.html)

Using a Jaunty Live cd is also an option.
Perhaps you can even boot from that by editing the boot parameters at the install cd prompt.

> **Archmage said:**
> Now, Grub can't load ext4. Grub2 can, but isn't stable yet and therefore isn't in Ubuntu.

Therefore if you want to use ext4, you need a bootpartiton in ext3 or something like this. The rest can be ext4.

But keep in mind that the Kernel from 8.10 or older can't handle ext4 at all. This could only work if you use the daily-build of Jaunty Jackalope. Even the Alpha 2 is to old.

> **ispy said:**
> thanks albinootje.

1: How do I go about backing up if I can't mount the filesystem?

2: How do I install grub2 if I can't mount the filesystem?

I appreciate the help a lot guys, I almost forgot why I love the forums so much.

Hi ispy

It seems to me that a Jaunty Jackalope live cd of the right ver "Even the Alpha 2 is to old." might be the way to go

I don't what what resources you have and that may not be an option.

If you use the Jaunty Jackalope live cd it may have a gparted on it that might help solve your problem after you backup your system to at least a ext3 disk (could even be a large thumb -see [http://ubuntuforums.org/showthread.php?t=1017566&page=3](http://ubuntuforums.org/showthread.php?t=1017566&page=3) post#21)

I installed a working ubuntu OS on an 8GB using [http://ubuntuforums.org/showthread.php?t=1017566&page=2]("http://ubuntuforums.org/showthread.php?t=1017566&page=2") post#14 and resolved boot problems with thread [http://ubuntuforums.org/showthread.php?t=1021772]("http://ubuntuforums.org/showthread.php?t=1021772")

Don't know if that would be an option or not with Jaunty but  its worth a thought.

Good luck 

Tom

---

### Post by albinootje on 2008-12-26
> **ispy said:**
> 
1: How do I go about backing up if I can't mount the filesystem?

2: How do I install grub2 if I can't mount the filesystem?


Good points!
I was earlier on even thinking of suggesting to use gparted to resize your partition and have a ext3 /boot partition.
But then again, I don't know whether gparted supports ext4 already (ext4 was called stable in oct. this year i read on the ext4 wikipedia page), but even then, if something would go wrong with the resizing (power-failure), then you can lose everything.

Looks like Sidux has ext4 + grub2 support since a while, but.. I'll see whether I can find more information.
I think I removed a fairly recent Sidux iso from the local file-server a few days ago to make space, but downloading again and testing is of course possible.

---

### Post by albinootje on 2008-12-26
I'm about to test the latest released Sidux which came out the 23rd of december.
I'm using it in VirtualBox, and I'll see whether it's possible to find a pre-compiled 2.6.28 kernel, or a pre-compiled patched for ext4 kernel, to test it on an ext4 partition.

Erhm.. make that : find the ext4 patch for the running Sidux kernel on the Live cd and compile and use that kernel module.

That reminds me of many years ago, where it was possible to write a kernel directly to a floppy with the cat commands.
No bootloader needed! only this special command to change the boot and root device for that kernel.
But nowadays the kernels are too big for floppies :(

---

### Post by albinootje on 2008-12-26
Sidux is cool, but too much work to try to compile the ext4 kernel module for the Sidux 2.6.27 kernel.
The ext4 patches are git --diff based. :|

In the meantime I read that Fedora 10 has support for ext4 during the installation, so I assume that it also has kernel support for it to mount the partition and use it.
Will test that (with VirtualBox) on a ext4 formatted usb-disk soonish.

---

### Post by ispy on 2008-12-26
No, the Gparted that I have on my Xubuntu 8.10 CD won't recognize the Ext4 partition.

I'll try downloading the Sidux and Jaunty ISOs when I get back home. I have a fairly recent backup of my computer (A couple weeks old) but I really don't want to lose my configuration files and such.

I just can't believe that it took two simple commands to screw up my file system. Shouldn't there be two equally easy commands to put it back?

---

### Post by albinootje on 2008-12-26
> **ispy said:**
> 
I'll try downloading the Sidux and Jaunty ISOs when I get back home. I have a fairly recent backup of my computer (A couple weeks old) but I really don't want to lose my configuration files and such.

I just can't believe that it took two simple commands to screw up my file system. Shouldn't there be two equally easy commands to put it back?

Forget about Sidux, make that Jaunty and/or Fedora10.
And I've read that converting back from ext4 to ext3 is not possible.

I've just tested Fedora10 Live/Install cd, and it works!
A fresh ext4 partition is successfully mounted :)

---

### Post by ispy on 2008-12-26
Looks like I'll try the Fedora 10 when I get home then.

Thanks a lot guys, I really appreciate the help you've given me.

---

