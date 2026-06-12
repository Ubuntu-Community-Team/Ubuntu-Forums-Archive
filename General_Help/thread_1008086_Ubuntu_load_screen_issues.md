---
title: "Ubuntu load screen issues"
date: 2008-12-11
forum: General Help
---

### Post by sub50hz on 2008-12-11
Hey all, first post here.

I recently (2 days ago) installed Ubuntu Intrepid on my Vista laptop. I have already fixed my wireless and nVidia issues thanks to the helpful links on this forum. Anywho, I have a bit of an issue on startup. When the Ubuntu load screen shows, the moving statusbar (that should bounce back and forth until showing the bar that grows) stops about 1/3 of the way to the right. If I don't do anything, the OS will not load. However, I have discovered taht I can move the bar manually by holding the down arrow or ESC key to advance the loading of Ubuntu. The few people I have queried about this issue had absolutely no idea what it could be, so I'm turning to you guys/girls for a little assistance. Please, if someone has a solution, try and keep it semi-dumbed-down for me (new user). It should be noted that after manually advancing the load statusbar using the down arrow, Ubuntu loads normally and has no apparent issues.

Thanks in advance!

---

### Post by kerry_s on 2008-12-11
the first step is to remove the splash screen so you can see whats happening.
press> alt+f2
type> gksu gedit /boot/grub/menu.lst

scroll down to the bottom, on the kernel line it should have "splash" or something like that, you want to remove that, save and reboot.

i'm sorry i'm not using ubuntu so i can't be exact with the wording, but it should be obvious once your in the file.

---

### Post by sub50hz on 2008-12-11
Thank you, kerry. The system hangs and displays a message that (not word-for-word here) 'USB Device at 2-0 could not be enumerated'. It also hangs once more at 'Setting preliminary key(pad?). Sorry, I'll go back once more and check it.

---

### Post by eBoxNet on 2008-12-11
It seems that its a known bug,

> I solved using in boot mode the option noapic nousb

best regards

original post : [https://bugs.launchpad.net/ubuntu/+bug/256767](https://bugs.launchpad.net/ubuntu/+bug/256767)

---

### Post by sub50hz on 2008-12-11
Ok, when I restarted again, without hitting any keys, Ubuntu will not load. When I give it keystroke input, it gives a message that the USB hub is not accepting the address. This really isn't a huge deal, but it's preventing me from starting the laptop, walking away for a minute, and coming back to the login screen.

---

### Post by sub50hz on 2008-12-11
> **eBoxNet said:**
> It seems that its a known bug,



original post : [https://bugs.launchpad.net/ubuntu/+bug/256767](https://bugs.launchpad.net/ubuntu/+bug/256767)

eBoxNet, where do I add this text -- to the Kernel line in kerry's aforementioned post?

---

### Post by eBoxNet on 2008-12-11
check this : [http://ubuntuforums.org/archive/index.php/t-148761.html](http://ubuntuforums.org/archive/index.php/t-148761.html)

---

### Post by kerry_s on 2008-12-11
in that menu.lst file put:
**pci=routeirq**
where you deleted "splash". then reboot. i don't recommend disabling anything just yet, so hold off on the noapic,nousb for now.

also it might help if we can see your dmesg log:
press> **alt+f2**
**gksu gedit /var/log/dmesg**

copy and paste that here in the #(code) tags

---

### Post by sub50hz on 2008-12-12
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbf50000 (usable)
[    0.000000]  BIOS-e820: 00000000bbf50000 - 00000000bbf65000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bbf65000 - 00000000bbf66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbf66000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xbbf50 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781e000 - 37fef707
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BBF5C0CE, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP BBF649BA, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT BBF5C13A, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS BBF65FC0, 0040
[    0.000000] ACPI: TCPA BBF64AAE, 0032 (r1 Phoeni  x        6040000  TL         0)
[    0.000000] ACPI: SRAT BBF64AE0, 00A0 (r1 AMD    HAMMER    6040000 AMD         1)
[    0.000000] ACPI: SSDT BBF64B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG BBF64D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET BBF64DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC BBF64DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BBF64E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC BBF64E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] 2111MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003781e000 - 0037fef707]          RAMDISK ==> [003781e000 - 0037fef707]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f8220] 000f8220
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000bbf50
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bbf50
[    0.000000] On node 0 totalpages: 769774
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 535745 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 763007
[    0.000000] Kernel command line: root=UUID=f31d2d45-0689-40b1-a7ea-6a65e5a11215 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2000.131 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3037292k/3079488k available (2572k kernel code, 40932k reserved, 1160k data, 424k init, 2161984k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.26 BogoMIPS (lpj=8000524)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017558] ACPI: Core revision 20080609
[    0.020492] ACPI: Checking initramfs for custom DSDT
[    0.364312] ENABLING IO-APIC IRQs
[    0.364542] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.407724] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.408025] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4000.38 BogoMIPS (lpj=8000771)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.492179] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.492207] Brought up 2 CPUs
[    0.492210] Total of 2 processors activated (8000.64 BogoMIPS).
[    0.492055] System has AMD C1E enabled
[    0.492249] CPU0 attaching sched-domain:
[    0.492072] Switch to broadcast mode on CPU1
[    0.492257]  domain 0: span 0-1 level CPU
[    0.492260]   groups: 0 1
[    0.492266] CPU1 attaching sched-domain:
[    0.492268]  domain 0: span 0-1 level CPU
[    0.492271]   groups: 1 0
[    0.492342] Switch to broadcast mode on CPU0
[    0.492342] net_namespace: 840 bytes
[    0.492342] Booting paravirtualized kernel on bare hardware
[    0.492342] Time:  3:18:15  Date: 12/12/08
[    0.492342] NET: Registered protocol family 16
[    0.492342] EISA bus registered
[    0.492342] ACPI: bus type pci registered
[    0.492342] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.492342] PCI: MCFG area at e0000000 reserved in E820
[    0.492342] PCI: Using MMCONFIG for extended config space
[    0.492342] PCI: Using configuration type 1 for base access
[    0.492804] ACPI: EC: Look up EC in DSDT
[    0.498190] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.499077] ACPI: Interpreter enabled
[    0.499080] ACPI: (supports S0 S3 S4 S5)
[    0.499096] ACPI: Using IOAPIC for interrupt routing
[    0.499161] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.520192] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.520192] ACPI: EC: driver started in interrupt mode
[    0.520192] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.520199] PCI: 0000:00:01.1 reg 10 io port: [3080, 30bf]
[    0.520211] PCI: 0000:00:01.1 reg 20 io port: [3040, 307f]
[    0.520215] PCI: 0000:00:01.1 reg 24 io port: [3000, 303f]
[    0.520231] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.520237] pci 0000:00:01.1: PME# disabled
[    0.520285] PCI: 0000:00:01.3 reg 10 32bit mmio: [f6200000, f627ffff]
[    0.520359] PCI: 0000:00:02.0 reg 10 32bit mmio: [f6486000, f6486fff]
[    0.520380] pci 0000:00:02.0: supports D1
[    0.520382] pci 0000:00:02.0: supports D2
[    0.520384] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520388] pci 0000:00:02.0: PME# disabled
[    0.520407] PCI: 0000:00:02.1 reg 10 32bit mmio: [f6489000, f64890ff]
[    0.520431] pci 0000:00:02.1: supports D1
[    0.520433] pci 0000:00:02.1: supports D2
[    0.520435] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520439] pci 0000:00:02.1: PME# disabled
[    0.520460] PCI: 0000:00:04.0 reg 10 32bit mmio: [f6487000, f6487fff]
[    0.520481] pci 0000:00:04.0: supports D1
[    0.520483] pci 0000:00:04.0: supports D2
[    0.520485] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520488] pci 0000:00:04.0: PME# disabled
[    0.520508] PCI: 0000:00:04.1 reg 10 32bit mmio: [f6489400, f64894ff]
[    0.520532] pci 0000:00:04.1: supports D1
[    0.520534] pci 0000:00:04.1: supports D2
[    0.520536] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520540] pci 0000:00:04.1: PME# disabled
[    0.520572] PCI: 0000:00:06.0 reg 20 io port: [30c0, 30cf]
[    0.520606] PCI: 0000:00:07.0 reg 10 32bit mmio: [f6480000, f6483fff]
[    0.520631] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.520634] pci 0000:00:07.0: PME# disabled
[    0.520686] PCI: 0000:00:09.0 reg 10 io port: [30f0, 30f7]
[    0.520690] PCI: 0000:00:09.0 reg 14 io port: [30e4, 30e7]
[    0.520694] PCI: 0000:00:09.0 reg 18 io port: [30e8, 30ef]
[    0.520699] PCI: 0000:00:09.0 reg 1c io port: [30e0, 30e3]
[    0.520703] PCI: 0000:00:09.0 reg 20 io port: [30d0, 30df]
[    0.520707] PCI: 0000:00:09.0 reg 24 32bit mmio: [f6484000, f6485fff]
[    0.520747] PCI: 0000:00:0a.0 reg 10 32bit mmio: [f6488000, f6488fff]
[    0.520751] PCI: 0000:00:0a.0 reg 14 io port: [30f8, 30ff]
[    0.520755] PCI: 0000:00:0a.0 reg 18 32bit mmio: [f6489c00, f6489cff]
[    0.520760] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [f6489800, f648980f]
[    0.520777] pci 0000:00:0a.0: supports D1
[    0.520779] pci 0000:00:0a.0: supports D2
[    0.520781] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520786] pci 0000:00:0a.0: PME# disabled
[    0.520815] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520818] pci 0000:00:0c.0: PME# disabled
[    0.520844] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.520847] pci 0000:00:0d.0: PME# disabled
[    0.520865] PCI: 0000:00:12.0 reg 10 32bit mmio: [f5000000, f5ffffff]
[    0.520869] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.520876] PCI: 0000:00:12.0 reg 1c 64bit mmio: [f4000000, f4ffffff]
[    0.520882] PCI: 0000:00:12.0 reg 30 32bit mmio: [0, 1ffff]
[    0.520985] PCI: 0000:02:05.0 reg 10 32bit mmio: [0, 7ff]
[    0.521016] pci 0000:02:05.0: supports D1
[    0.521018] pci 0000:02:05.0: supports D2
[    0.521020] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521024] pci 0000:02:05.0: PME# disabled
[    0.521045] PCI: 0000:02:05.1 reg 10 32bit mmio: [f6100800, f61008ff]
[    0.521075] pci 0000:02:05.1: supports D1
[    0.521077] pci 0000:02:05.1: supports D2
[    0.521079] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521083] pci 0000:02:05.1: PME# disabled
[    0.521104] PCI: 0000:02:05.2 reg 10 32bit mmio: [f6100c00, f6100cff]
[    0.521134] pci 0000:02:05.2: supports D1
[    0.521136] pci 0000:02:05.2: supports D2
[    0.521138] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521142] pci 0000:02:05.2: PME# disabled
[    0.521163] PCI: 0000:02:05.3 reg 10 32bit mmio: [f6101000, f61010ff]
[    0.521194] pci 0000:02:05.3: supports D1
[    0.521195] pci 0000:02:05.3: supports D2
[    0.521198] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521202] pci 0000:02:05.3: PME# disabled
[    0.521224] PCI: 0000:02:05.4 reg 10 32bit mmio: [f6101400, f61014ff]
[    0.521254] pci 0000:02:05.4: supports D1
[    0.521256] pci 0000:02:05.4: supports D2
[    0.521258] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521262] pci 0000:02:05.4: PME# disabled
[    0.521292] pci 0000:00:08.0: transparent bridge
[    0.521296] PCI: bridge 0000:00:08.0 32bit mmio: [f6100000, f61fffff]
[    0.521335] PCI: bridge 0000:00:0c.0 io port: [4000, 4fff]
[    0.521338] PCI: bridge 0000:00:0c.0 32bit mmio: [f2000000, f3ffffff]
[    0.521343] PCI: bridge 0000:00:0c.0 64bit mmio pref: [f0000000, f1ffffff]
[    0.521378] PCI: 0000:03:00.0 reg 10 64bit mmio: [f6000000, f600ffff]
[    0.521448] PCI: bridge 0000:00:0d.0 32bit mmio: [f6000000, f60fffff]
[    0.521458] bus 00 -> node 0
[    0.521464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.521583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.521610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.521653] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.564287] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.564546] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.564802] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.565058] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.565314] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.565570] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.565825] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.566081] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.566336] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.566591] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.566847] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.567107] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.567364] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.567565] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.567565] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.567565] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.567565] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.567565] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.567565] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.568160] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.568183] pnp: PnP ACPI init
[    0.568183] ACPI: bus type pnp registered
[    0.573292] pnp: PnP ACPI: found 12 devices
[    0.573292] ACPI: ACPI bus type pnp unregistered
[    0.573292] PnPBIOS: Disabled by ACPI PNP
[    0.573292] PCI: Using ACPI for IRQ routing
[    0.576044] NET: Registered protocol family 8
[    0.576047] NET: Registered protocol family 20
[    0.580039] NetLabel: Initializing
[    0.580039] NetLabel:  domain hash size = 128
[    0.580040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.580055] NetLabel:  unlabeled traffic allowed by default
[    0.580063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.580069] hpet0: 3 32-bit timers, 25000000 Hz
[    0.581673] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.581676]    actual entries 65620
[    0.581826] AppArmor: AppArmor Filesystem Enabled
[    0.581854] ACPI: RTC can wake from S4
[    0.584052] Switched to high resolution mode on CPU 0
[    0.584064] Switched to high resolution mode on CPU 1
[    0.584096] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.584103] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.584106] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.584109] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.584112] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.584115] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.584118] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.584125] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.584128] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.584139] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.584142] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.584146] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.584149] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.584152] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.619475] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.619478] pci 0000:00:08.0:   IO window: disabled
[    0.619482] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.619485] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.619490] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.619493] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.619497] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.619500] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.619504] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.619507] pci 0000:00:0d.0:   IO window: disabled
[    0.619510] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.619513] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.619523] pci 0000:00:08.0: setting latency timer to 64
[    0.619529] pci 0000:00:0c.0: setting latency timer to 64
[    0.619534] pci 0000:00:0d.0: setting latency timer to 64
[    0.619538] bus: 00 index 0 io port: [0, ffff]
[    0.619540] bus: 00 index 1 mmio: [0, ffffffff]
[    0.619543] bus: 02 index 0 mmio: [0, 0]
[    0.619545] bus: 02 index 1 mmio: [f6100000, f61fffff]
[    0.619547] bus: 02 index 2 mmio: [0, 0]
[    0.619549] bus: 02 index 3 io port: [0, ffff]
[    0.619551] bus: 02 index 4 mmio: [0, ffffffff]
[    0.619554] bus: 04 index 0 io port: [4000, 4fff]
[    0.619556] bus: 04 index 1 mmio: [f2000000, f3ffffff]
[    0.619559] bus: 04 index 2 mmio: [f0000000, f1ffffff]
[    0.619561] bus: 04 index 3 mmio: [0, 0]
[    0.619563] bus: 03 index 0 mmio: [0, 0]
[    0.619565] bus: 03 index 1 mmio: [f6000000, f60fffff]
[    0.619568] bus: 03 index 2 mmio: [0, 0]
[    0.619570] bus: 03 index 3 mmio: [0, 0]
[    0.619582] NET: Registered protocol family 2
[    0.629076] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.629380] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.630176] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.630627] TCP: Hash tables configured (established 131072 bind 65536)
[    0.630631] TCP reno registered
[    0.633120] NET: Registered protocol family 1
[    0.633249] checking if image is initramfs... it is
[    1.332768] Freeing initrd memory: 8005k freed
[    1.332947] Simple Boot Flag at 0x36 set to 0x1
[    1.334266] audit: initializing netlink socket (disabled)
[    1.334280] type=2000 audit(1229051895.332:1): initialized
[    1.340360] highmem bounce pool size: 64 pages
[    1.340367] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.343354] VFS: Disk quotas dquot_6.5.1
[    1.343457] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.343579] msgmni has been set to 1726
[    1.343711] io scheduler noop registered
[    1.343714] io scheduler anticipatory registered
[    1.343716] io scheduler deadline registered
[    1.343729] io scheduler cfq registered (default)
[    1.343761] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.343920] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.343936] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.343952] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.343969] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.343985] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.344001] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.344027] pci 0000:00:12.0: Boot video device
[    1.344167] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.344194] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.344217] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.344275] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.344363] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.344389] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.344408] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.344464] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.344873] isapnp: Scanning for PnP cards...
[    1.697452] isapnp: No Plug & Play device found
[    1.742420] hpet_resources: 0xfed00000 is busy
[    1.742534] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.745149] brd: module loaded
[    1.745224] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.745354] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.771911] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.771919] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.772324] mice: PS/2 mouse device common for all mice
[    1.772484] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.772522] rtc0: alarms up to one year, y3k, hpet irqs
[    1.772659] EISA: Probing bus 0 at eisa.0
[    1.772665] Cannot allocate resource for EISA slot 1
[    1.772671] Cannot allocate resource for EISA slot 3
[    1.772673] Cannot allocate resource for EISA slot 4
[    1.772685] EISA: Detected 0 cards.
[    1.772689] cpuidle: using governor ladder
[    1.772692] cpuidle: using governor menu
[    1.773202] TCP cubic registered
[    1.773230] Using IPI No-Shortcut mode
[    1.773440] registered taskstats version 1
[    1.773580]   Magic number: 4:524:310
[    1.773617] tty ttyxd: hash matches
[    1.773709] tty tty39: hash matches
[    1.773794] rtc_cmos 00:07: setting system clock to 2008-12-12 03:18:17 UTC (1229051897)
[    1.773797] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.773799] EDD information not available.
[    1.774107] Freeing unused kernel memory: 424k freed
[    1.774172] Write protecting the kernel text: 2576k
[    1.774213] Write protecting the kernel read-only data: 936k
[    1.801532] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.963907] fuse init (API version 7.9)
[    2.036387] ACPI: processor limited to max C-state 1
[    2.036582] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.036657] processor ACPI0007:00: registered as cooling_device0
[    2.036662] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.036848] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.036908] processor ACPI0007:01: registered as cooling_device1
[    2.036913] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.039706] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080609]
[    2.481703] usbcore: registered new interface driver usbfs
[    2.481731] usbcore: registered new interface driver hub
[    2.486361] usbcore: registered new device driver usb
[    2.497400] No dock devices found.
[    2.514455] SCSI subsystem initialized
[    2.555150] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    2.555164] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    2.555176] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.555179] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.555242] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    2.555270] ehci_hcd 0000:00:02.1: debug port 1
[    2.555275] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.555295] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    2.555345] libata version 3.00 loaded.
[    2.555466] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.564441] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.564597] usb usb1: configuration #1 chosen from 1 choice
[    2.564628] hub 1-0:1.0: USB hub found
[    2.564638] hub 1-0:1.0: 7 ports detected
[    2.668922] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    2.668930] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    2.668945] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    2.668948] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    2.668974] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    2.669006] ehci_hcd 0000:00:04.1: debug port 1
[    2.669011] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    2.669019] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    2.680016] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.680135] usb usb2: configuration #1 chosen from 1 choice
[    2.680166] hub 2-0:1.0: USB hub found
[    2.680175] hub 2-0:1.0: 2 ports detected
[    2.888876] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    2.888890] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    2.888906] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.888910] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.888937] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    2.888962] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    2.946256] usb usb3: configuration #1 chosen from 1 choice
[    2.946286] hub 3-0:1.0: USB hub found
[    2.946297] hub 3-0:1.0: 7 ports detected
[    4.533496] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    4.534775] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    4.534781] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    4.534796] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.534799] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.534829] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.534845] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    4.775929] Clocksource tsc unstable (delta = 4398045578088 ns)
[    4.778723] usb usb4: configuration #1 chosen from 1 choice
[    4.778750] hub 4-0:1.0: USB hub found
[    4.778762] hub 4-0:1.0: 2 ports detected
[    4.901207] pata_acpi 0000:00:06.0: setting latency timer to 64
[    4.901731] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    4.901742] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    4.901760] pata_acpi 0000:00:09.0: setting latency timer to 64
[    4.901768] pata_acpi 0000:00:09.0: PCI INT A disabled
[    4.901815] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.902209] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.902217] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    4.902222] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.915311] usb 2-2: configuration #1 chosen from 1 choice
[    5.464645] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:b9:e5:af
[    5.464650] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    5.466149] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[    5.466807] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    5.466820] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    5.518550] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.539417] ahci 0000:00:09.0: version 3.0
[    5.539436] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    5.539540] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    5.539544] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[    5.539549] ahci 0000:00:09.0: setting latency timer to 64
[    5.539925] scsi0 : ahci
[    5.551208] scsi1 : ahci
[    5.551312] scsi2 : ahci
[    5.551378] scsi3 : ahci
[    5.551484] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
[    5.551488] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
[    5.551491] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
[    5.551495] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
[    6.088802] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.089484] ata1.00: ATA-8: ST9200827AS, 3.BHA, max UDMA/100
[    6.089489] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.089937] ata1.00: configured for UDMA/100
[    6.464444] ata2: SATA link down (SStatus 0 SControl 300)
[    6.839868] ata3: SATA link down (SStatus 0 SControl 300)
[    6.905718] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00c3d32501]
[    7.457092] ata4: SATA link down (SStatus 0 SControl 300)
[    7.457216] scsi 0:0:0:0: Direct-Access     ATA      ST9200827AS      3.BH PQ: 0 ANSI: 5
[    7.457457] pata_amd 0000:00:06.0: version 0.3.10
[    7.457506] pata_amd 0000:00:06.0: setting latency timer to 64
[    7.460170] scsi4 : pata_amd
[    7.460309] scsi5 : pata_amd
[    7.460734] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    7.460737] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    7.730816] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T40L, KC07, max MWDMA2
[    7.730831] ata5: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    7.793322] ata5.00: configured for MWDMA2
[    7.793707] ata6: port disabled. ignoring.
[    7.797022] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T40L  KC07 PQ: 0 ANSI: 5
[    7.804326] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.804368] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    7.822159] Driver 'sd' needs updating - please use bus_type methods
[    7.822284] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    7.822305] sd 0:0:0:0: [sda] Write Protect is off
[    7.822308] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.822342] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.822426] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    7.822444] sd 0:0:0:0: [sda] Write Protect is off
[    7.822447] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.822480] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.822484]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.955735]  sda1 sda2 sda3 < sda5 sda6 >
[    7.985129] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.000626] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.000632] Uniform CD-ROM driver Revision: 3.20
[    8.000733] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    8.355904] PM: Starting manual resume from disk
[    8.355908] PM: Resume from partition 8:6
[    8.355911] PM: Checking hibernation image.
[    8.356026] PM: Resume from disk failed.
[    8.402359] kjournald starting.  Commit interval 5 seconds
[    8.402372] EXT3-fs: mounted filesystem with ordered data mode.
[   14.833136] udevd version 124 started
[   15.363781] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.412640] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.601176] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   15.629035] ACPI: Power Button (FF) [PWRF]
[   15.629164] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   15.666024] ACPI: Sleep Button (CM) [SLPB]
[   15.672202] ACPI: AC Adapter [ACAD] (on-line)
[   15.672275] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   15.672697] ACPI: Lid Switch [LID]
[   15.672839] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   15.697065] ACPI: Power Button (CM) [PWRB]
[   15.825868] Linux agpgart interface v0.103
[   16.029567] ACPI: Battery Slot [BAT0] (battery present)
[   16.029859] ACPI: WMI: Mapper loaded
[   16.183487] nvidia: module license 'NVIDIA' taints kernel.
[   16.562612] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   16.562625] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   16.562632] nvidia 0000:00:12.0: setting latency timer to 64
[   16.562906] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   16.572763] ricoh-mmc: Ricoh MMC Controller disabling driver
[   16.572767] ricoh-mmc: Copyright(c) Philip Langdale
[   16.572802] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   16.572817] ricoh-mmc: Controller is now disabled.
[   16.683830] sdhci: Secure Digital Host Controller Interface driver
[   16.683834] sdhci: Copyright(c) Pierre Ossman
[   16.706172] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   16.706595] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   16.706608] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   16.709699] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   16.924875] acpi device:25: registered as cooling_device2
[   16.925091] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
[   16.949025] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   16.986257] AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425, RF2417)
[   17.059966] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   17.203308] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   17.203321] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   17.203330] ath_pci 0000:03:00.0: setting latency timer to 64
[   17.693452] MadWifi: ath_attach: Switching rfkill capability off.
[   17.786708] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[   17.814595] ath_pci: wifi0: Atheros 5424/2424: mem=0xf6000000, irq=19
[   17.961744] Linux video capture interface: v2.00
[   18.185101] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   18.187205] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input8
[   18.213250] usbcore: registered new interface driver uvcvideo
[   18.213270] USB Video Class driver (v0.1.0)
[   18.423328] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   18.423342] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   18.423372] HDA Intel 0000:00:07.0: setting latency timer to 64
[   18.610784] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   18.690281] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   18.933578] lp: driver loaded but no devices found
[   19.096417] Adding 2128572k swap on /dev/sda6.  Priority:-1 extents:1 across:2128572k
[   19.637533] EXT3 FS on sda5, internal journal
[   20.717989] type=1505 audit(1229073515.967:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4180
[   20.919866] type=1505 audit(1229073516.167:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4185
[   20.920133] type=1505 audit(1229073516.167:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4185
[   21.124330] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by kerry_s on 2008-12-12
try it with "pci=routeirq"

example:
.... root=UUID=f31d2d45-0689-40b1-a7ea-6a65e5a11215 ro **pci=routeirq**

---

