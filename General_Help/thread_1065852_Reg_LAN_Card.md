---
title: "Reg LAN Card"
date: 2009-02-10
forum: General Help
---

### Post by naani on 2009-02-10
Of late, my lan card is showing the message "network cable unplugged". after searching 4 many hours and suggestions, i have come to know that by using live cd's of linux, we can determine whether LAN Card is damaged or not working properly. 

The description of my ThinkPad R51 2887-MQ5 : Based on 2887-PCA: Celeron M 350(1.3GHz), 512MB RAM, 40GB 5400rpm HD, 14.1in 1024x768 LCD, Intel Extreme, CDRW/DVD, Intel 802.11bg wireless, Modem, 10/100 Ethernet, UltraNav, Secure chip, 6c Li-Ion batt, DOS license.

I request members to let me know how can i verify the status of LAN card by using live cd 8.1. At present I am downloading Ubuntu 8.10 Alternate i386.iso.

Please Help Me !!!!! Meanwhile i will do more search in forums.

Thank U :)

---

### Post by digitalbenji on 2009-02-10
My first question is are you certain the NIC is plugged in on a good switchport, and that you are not using a crossover cable?  
I would also try using ```
lspci
``` and ```
dmesg
``` to troubleshoot hardware problems.  You can also use System->Administration->Hardware Testing to determine problems as well.  Good luck.

---

### Post by naani on 2009-02-10
> **digitalbenji said:**
> My first question is are you certain the NIC is plugged in on a good switchport, and that you are not using a crossover cable?  
I would also try using ```
lspci
``` and ```
dmesg
``` to troubleshoot hardware problems.  You can also use System->Administration->Hardware Testing to determine problems as well.  Good luck.

Just found this one "ethernet (wired LAN connection) tutorial"
Right now i am installing in vmware and i will let u know the results for more clarifications.

---

### Post by naani on 2009-02-11
herewith i am submitting the results of lspci and dmesg : 

g:~$ lspci 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01) 
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01) 
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08) 
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) 
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB 
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08) 
00:0f.0 VGA compatible controller: VMware Inc Abstract SVGA II Adapter 
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01) 
00:11.0 PCI bridge: VMware Inc PCI bridge (rev 01) 
02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10) 
02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02) 
02:02.0 USB Controller: VMware Inc Abstract USB2 EHCI Controller 


sadas:~$ dmesg 
[    0.000000] Initializing cgroup subsys cpuset 
[    0.000000] Initializing cgroup subsys cpu 
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable) 
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000009ef0000 (usable) 
[    0.000000]  BIOS-e820: 0000000009ef0000 - 0000000009eff000 (ACPI data) 
[    0.000000]  BIOS-e820: 0000000009eff000 - 0000000009f00000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 0000000009f00000 - 000000000a000000 (usable) 
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved) 
[    0.000000] last_pfn = 0xa000 max_arch_pfn = 0x100000 
[    0.000000] kernel direct mapping tables up to a000000 @ 7000-c000 
[    0.000000] RAMDISK: 09713000 - 09edf035 
[    0.000000] DMI present. 
[    0.000000] ACPI: RSDP 000F6C20, 0014 (r0 PTLTD ) 
[    0.000000] ACPI: RSDT 09EFAB68, 0030 (r1 PTLTD    RSDT    6040000  LTP        0) 
[    0.000000] ACPI: FACP 09EFEF14, 0074 (r1 INTEL  440BX     6040000 PTL     F4240) 
[    0.000000] ACPI: DSDT 09EFAB98, 437C (r1 PTLTD  Custom    6040000 MSFT  100000D) 
[    0.000000] ACPI: FACS 09EFFFC0, 0040 
[    0.000000] ACPI: APIC 09EFEF88, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0) 
[    0.000000] ACPI: BOOT 09EFEFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1) 
[    0.000000] 0MB HIGHMEM available. 
[    0.000000] 160MB LOWMEM available. 
[    0.000000]   mapped low ram: 0 - 0a000000 
[    0.000000]   low ram: 00000000 - 0a000000 
[    0.000000]   bootmap 00002000 - 00003400 
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000a000000] 
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000] 
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000] 
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000] 
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20] 
[    0.000000]   #4 [0009713000 - 0009edf035]          RAMDISK ==> [0009713000 - 0009edf035] 
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000] 
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000] 
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000] 
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000] 
[    0.000000] found SMP MP-table at [c00f6c90] 000f6c90 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA      0x00000000 -> 0x00001000 
[    0.000000]   Normal   0x00001000 -> 0x0000a000 
[    0.000000]   HighMem  0x0000a000 -> 0x0000a000 
[    0.000000] Movable zone start PFN for each node 
[    0.000000] early_node_map[3] active PFN ranges 
[    0.000000]     0: 0x00000000 -> 0x0000009f 
[    0.000000]     0: 0x00000100 -> 0x00009ef0 
[    0.000000]     0: 0x00009f00 -> 0x0000a000 
[    0.000000] On node 0 totalpages: 40847 
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000 
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0 
[    0.000000]   Normal zone: 36524 pages, LIFO batch:7 
[    0.000000] ACPI: PM-Timer IO Port: 0x1008 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1]) 
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge) 
[    0.000000] ACPI: IRQ0 used by override. 
[    0.000000] ACPI: IRQ2 used by override. 
[    0.000000] ACPI: IRQ9 used by override. 
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs 
[    0.000000] mapped APIC to ffffb000 (fee00000) 
[    0.000000] mapped IOAPIC to ffffa000 (fec00000) 
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000 
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ca000 
[    0.000000] PM: Registered nosave memory: 00000000000ca000 - 00000000000cc000 
[    0.000000] PM: Registered nosave memory: 00000000000cc000 - 00000000000dc000 
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000 
[    0.000000] PM: Registered nosave memory: 0000000009ef0000 - 0000000009eff000 
[    0.000000] PM: Registered nosave memory: 0000000009eff000 - 0000000009f00000 
[    0.000000] Allocating PCI resources starting at 10000000 (gap: a000000:f4c00000) 
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data 
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 40487 
[    0.000000] Kernel command line: root=UUID=d5ef10d2-716a-4cea-8658-f471905d90c3 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes) 
[    0.000000] TSC: Unable to calibrate against PIT 
[    0.000000] TSC: using PMTIMER reference calibration 
[    0.000000] Detected 1298.897 MHz processor. 
[    0.004000] Console: colour VGA+ 80x25 
[    0.004000] console [tty0] enabled 
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes) 
[    0.004000] Memory: 148648k/163840k available (2572k kernel code, 14592k reserved, 1160k data, 424k init, 0k highmem) 
[    0.004000] virtual kernel memory layout: 
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB) 
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB) 
[    0.004000]     vmalloc : 0xca800000 - 0xff3fe000   ( 843 MB) 
[    0.004000]     lowmem  : 0xc0000000 - 0xca000000   ( 160 MB) 
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB) 
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB) 
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB) 
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok. 
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated 
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1 
[    0.004187] Calibrating delay loop (skipped), value calculated using timer frequency.. 2597.79 BogoMIPS (lpj=5195588) 
[    0.004250] Security Framework initialized 
[    0.004312] SELinux:  Disabled at boot. 
[    0.004375] AppArmor: AppArmor initialized 
[    0.004437] Mount-cache hash table entries: 512 
[    0.008103] Initializing cgroup subsys ns 
[    0.008166] Initializing cgroup subsys cpuacct 
[    0.008223] Initializing cgroup subsys memory 
[    0.008285] CPU: L1 I cache: 32K, L1 D cache: 32K 
[    0.008337] CPU: L2 cache: 1024K 
[    0.008399] Checking 'hlt' instruction... OK. 
[    0.024074] SMP alternatives: switching to UP code 
[    0.036189] Freeing SMP alternatives: 11k freed 
[    0.036252] ACPI: Core revision 20080609 
[    0.040086] ACPI: Checking initramfs for custom DSDT 
[    0.424357] ENABLING IO-APIC IRQs 
[    0.424769] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
[    0.464662] CPU0: Intel(R) Celeron(R) M processor         1.30GHz stepping 08 
[    0.468029] Brought up 1 CPUs 
[    0.468029] Total of 1 processors activated (2597.79 BogoMIPS). 
[    0.468029] CPU0 attaching sched-domain: 
[    0.468029]  domain 0: span 0 level CPU 
[    0.468029]   groups: 0 
[    0.472745] net_namespace: 840 bytes 
[    0.472774] Booting paravirtualized kernel on bare hardware 
[    0.472833] Time:  7:56:24  Date: 02/11/09 
[    0.472862] NET: Registered protocol family 16 
[    0.477340] EISA bus registered 
[    0.477369] ACPI: bus type pci registered 
[    0.477711] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=2 
[    0.477740] PCI: Using configuration type 1 for base access 
[    0.488060] ACPI: EC: Look up EC in DSDT 
[    0.518884] ACPI: Interpreter enabled 
[    0.518946] ACPI: (supports S0 S1 S4 S5) 
[    0.519009] ACPI: Using IOAPIC for interrupt routing 
[    0.533756] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    0.536094] PCI: 0000:00:07.1 reg 20 io port: [1050, 105f] 
[    0.536157] PCI: 0000:00:07.2 reg 20 io port: [1060, 107f] 
[    0.536219] pci 0000:00:07.3: quirk: region 1000-103f claimed by PIIX4 ACPI 
[    0.536280] pci 0000:00:07.3: quirk: region 1040-104f claimed by PIIX4 SMB 
[    0.536342] PCI: 0000:00:0f.0 reg 10 io port: [1400, 140f] 
[    0.536405] PCI: 0000:00:0f.0 reg 14 32bit mmio: [f0000000, f7ffffff] 
[    0.536456] PCI: 0000:00:0f.0 reg 18 32bit mmio: [e8000000, e87fffff] 
[    0.536518] PCI: 0000:00:0f.0 reg 30 32bit mmio: [0, 7fff] 
[    0.536580] PCI: 0000:00:10.0 reg 10 io port: [1080, 10ff] 
[    0.536643] PCI: 0000:00:10.0 reg 14 32bit mmio: [e8800000, e8800fff] 
[    0.536705] PCI: 0000:00:10.0 reg 30 32bit mmio: [0, 3fff] 
[    0.536768] PCI: 0000:00:11.0 reg 10 64bit mmio: [e8801000, e8801fff] 
[    0.536830] PCI: 0000:02:00.0 reg 10 io port: [2000, 207f] 
[    0.536893] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, ffff] 
[    0.536955] PCI: 0000:02:01.0 reg 10 io port: [2080, 20bf] 
[    0.537018] PCI: 0000:02:02.0 reg 10 32bit mmio: [e8900000, e8900fff] 
[    0.537080] PCI: bridge 0000:00:11.0 io port: [2000, 2fff] 
[    0.537140] PCI: bridge 0000:00:11.0 32bit mmio: [e8900000, e89fffff] 
[    0.537202] bus 00 -> node 0 
[    0.537265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.544094] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15) 
[    0.544157] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15) 
[    0.544219] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15) 
[    0.544282] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 14 15) 
[    0.544682] Linux Plug and Play Support v0.97 (c) Adam Belay 
[    0.544924] pnp: PnP ACPI init 
[    0.544986] ACPI: bus type pnp registered 
[    0.565062] pnp: PnP ACPI: found 12 devices 
[    0.565125] ACPI: ACPI bus type pnp unregistered 
[    0.565187] PnPBIOS: Disabled by ACPI PNP 
[    0.567208] PCI: Using ACPI for IRQ routing 
[    0.568495] NET: Registered protocol family 8 
[    0.568495] NET: Registered protocol family 20 
[    0.568512] NetLabel: Initializing 
[    0.568537] NetLabel:  domain hash size = 128 
[    0.568555] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.568617] NetLabel:  unlabeled traffic allowed by default 
[    0.568679] tracer: 772 pages allocated for 65536 entries of 48 bytes 
[    0.568703]    actual entries 65620 
[    0.568765] AppArmor: AppArmor Filesystem Enabled 
[    0.568871] system 00:01: ioport range 0x1000-0x103f has been reserved 
[    0.568871] system 00:01: ioport range 0x1040-0x104f has been reserved 
[    0.608115] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01 
[    0.608178] pci 0000:00:01.0:   IO window: disabled 
[    0.608240] pci 0000:00:01.0:   MEM window: disabled 
[    0.608303] pci 0000:00:01.0:   PREFETCH window: disabled 
[    0.608365] pci 0000:00:11.0: PCI bridge, secondary bus 0000:02 
[    0.608428] pci 0000:00:11.0:   IO window: 0x2000-0x2fff 
[    0.608490] pci 0000:00:11.0:   MEM window: 0xe8900000-0xe89fffff 
[    0.608553] pci 0000:00:11.0:   PREFETCH window: 0x00000010000000-0x000000100fffff 
[    0.608615] pci 0000:00:01.0: setting latency timer to 64 
[    0.608678] pci 0000:00:11.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    0.608740] bus: 00 index 0 io port: [0, ffff] 
[    0.608775] bus: 00 index 1 mmio: [0, ffffffff] 
[    0.608806] bus: 01 index 0 mmio: [0, 0] 
[    0.608812] bus: 01 index 1 mmio: [0, 0] 
[    0.608818] bus: 01 index 2 mmio: [0, 0] 
[    0.608823] bus: 01 index 3 mmio: [0, 0] 
[    0.608845] bus: 02 index 0 io port: [2000, 2fff] 
[    0.608852] bus: 02 index 1 mmio: [e8900000, e89fffff] 
[    0.608858] bus: 02 index 2 mmio: [10000000, 100fffff] 
[    0.608864] bus: 02 index 3 mmio: [0, 0] 
[    0.608926] NET: Registered protocol family 2 
[    0.609422] IP route cache hash table entries: 2048 (order: 1, 8192 bytes) 
[    0.612059] TCP established hash table entries: 8192 (order: 4, 65536 bytes) 
[    0.612122] TCP bind hash table entries: 8192 (order: 4, 65536 bytes) 
[    0.612184] TCP: Hash tables configured (established 8192 bind 8192) 
[    0.612247] TCP reno registered 
[    0.612483] NET: Registered protocol family 1 
[    0.616070] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0 
[    1.152091]  it is 
[    1.908110] Freeing initrd memory: 7984k freed 
[    1.908942] Simple Boot Flag at 0x36 set to 0x1 
[    1.911026] audit: initializing netlink socket (disabled) 
[    1.911090] type=2000 audit(1234338984.908:1): initialized 
[    1.922715] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    1.931219] VFS: Disk quotas dquot_6.5.1 
[    1.931499] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    1.932320] msgmni has been set to 306 
[    1.932562] io scheduler noop registered 
[    1.932627] io scheduler anticipatory registered 
[    1.932664] io scheduler deadline registered 
[    1.932728] io scheduler cfq registered (default) 
[    1.932793] pci 0000:00:00.0: Limiting direct PCI/PCI transfers 
[    1.932928] pci 0000:00:0f.0: Boot video device 
[    1.934287] isapnp: Scanning for PnP cards... 
[    2.290710] isapnp: No Plug & Play device found 
[    2.382537] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    2.384080] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    2.384363] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[    2.385283] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    2.385689] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[    2.392943] brd: module loaded 
[    2.393165] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[    2.393522] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12 
[    2.900113] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    2.900275] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    2.901828] mice: PS/2 mouse device common for all mice 
[    2.904665] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0 
[    2.904755] rtc0: alarms up to one month, y3k 
[    2.906266] EISA: Probing bus 0 at eisa.0 
[    2.906356] Cannot allocate resource for EISA slot 1 
[    2.906388] Cannot allocate resource for EISA slot 2 
[    2.906479] EISA: Detected 0 cards. 
[    2.906569] cpuidle: using governor ladder 
[    2.906660] cpuidle: using governor menu 
[    2.906864] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[    2.908119] TCP cubic registered 
[    2.908210] Using IPI No-Shortcut mode 
[    2.908937] registered taskstats version 1 
[    2.909028]   Magic number: 13:431:925 
[    2.909118] tty ptyxa: hash matches 
[    2.929389] rtc_cmos 00:04: setting system clock to 2009-02-11 07:56:27 UTC (1234338987) 
[    2.929480] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    2.929520] EDD information not available. 
[    2.988131] Freeing unused kernel memory: 424k freed 
[    2.988221] Write protecting the kernel text: 2576k 
[    2.988312] Write protecting the kernel read-only data: 936k 
[    3.369456] fuse init (API version 7.9) 
[    3.540991] processor ACPI0007:00: registered as cooling_device0 
[    3.541065] ACPI: Processor [CPU0] (supports 8 throttling states) 
[    4.096573] No dock devices found. 
[    4.297188] SCSI subsystem initialized 
[    4.624113] Fusion MPT base driver 3.04.07 
[    4.624139] Copyright (c) 1999-2008 LSI Corporation 
[    4.665633] libata version 3.00 loaded. 
[    4.732500] usbcore: registered new interface driver usbfs 
[    4.732533] usbcore: registered new interface driver hub 
[    4.750838] usbcore: registered new device driver usb 
[    4.758011] Fusion MPT SPI Host driver 3.04.07 
[    4.758044] mptspi 0000:00:10.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    4.765083] mptbase: ioc0: Initiating bringup 
[    4.768384] USB Universal Host Controller Interface driver v3.0 
[    4.780362] pcnet32.c:v1.35 21.Apr.2008 [email]tsbogend@alpha.franken.de[/email] 
[    4.836138] ioc0: LSI53C1030 B0: Capabilities={Initiator} 
[    4.972266] scsi0 : ioc0: LSI53C1030 B0, FwRev=01032920h, Ports=1, MaxQ=128, IRQ=17 
[    5.086475] uhci_hcd 0000:00:07.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[    5.086692] uhci_hcd 0000:00:07.2: UHCI Host Controller 
[    5.088249] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1 
[    5.088688] uhci_hcd 0000:00:07.2: irq 19, io base 0x00001060 
[    5.092244] usb usb1: configuration #1 chosen from 1 choice 
[    5.092461] hub 1-0:1.0: USB hub found 
[    5.092677] hub 1-0:1.0: 2 ports detected 
[    5.105187] scsi 0:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2 
[    5.105404] scsi target0:0:0: Beginning Domain Validation 
[    5.108317] scsi target0:0:0: Domain Validation skipping write tests 
[    5.108407] scsi target0:0:0: Ending Domain Validation 
[    5.109151] scsi target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127) 
[    5.200740] ehci_hcd 0000:02:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    5.200957] ehci_hcd 0000:02:02.0: EHCI Host Controller 
[    5.201095] ehci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 2 
[    5.201312] ehci_hcd 0000:02:02.0: cache line size of 32 is not supported 
[    5.201406] ehci_hcd 0000:02:02.0: irq 16, io mem 0xe8900000 
[    5.212291] ehci_hcd 0000:02:02.0: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    5.212507] usb usb2: configuration #1 chosen from 1 choice 
[    5.212724] hub 2-0:1.0: USB hub found 
[    5.212941] hub 2-0:1.0: 6 ports detected 
[    5.320310] pcnet32 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    5.320527] pcnet32: PCnet/PCI II 79C970A at 0x2000, 00:0c:29:2d:69:20 assigned IRQ 18. 
[    5.332487] eth0: registered as PCnet/PCI II 79C970A 
[    5.332704] pcnet32: 1 cards_found. 
[    5.333504] ata_piix 0000:00:07.1: version 2.12 
[    5.334925] scsi1 : ata_piix 
[    5.335267] scsi2 : ata_piix 
[    5.335483] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1050 irq 14 
[    5.335548] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1058 irq 15 
[    5.336251] ata1: port disabled. ignoring. 
[    5.472521] scsi 0:0:0:0: Attached scsi generic sg0 type 0 
[    5.493523] ata2.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33 
[    5.494147] ata2.00: configured for UDMA/33 
[    5.504796] scsi 2:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.03 PQ: 0 ANSI: 5 
[    5.504873] scsi 2:0:0:0: Attached scsi generic sg1 type 5 
[    5.532982] Driver 'sd' needs updating - please use bus_type methods 
[    5.533059] sd 0:0:0:0: [sda] 6291456 512-byte hardware sectors (3221 MB) 
[    5.533136] sd 0:0:0:0: [sda] Write Protect is off 
[    5.533191] sd 0:0:0:0: [sda] Mode Sense: 5d 6e 00 00 
[    5.533268] sd 0:0:0:0: [sda] Cache data unavailable 
[    5.533315] sd 0:0:0:0: [sda] Assuming drive cache: write through 
[    5.533393] sd 0:0:0:0: [sda] 6291456 512-byte hardware sectors (3221 MB) 
[    5.533470] sd 0:0:0:0: [sda] Write Protect is off 
[    5.533485] sd 0:0:0:0: [sda] Mode Sense: 5d 6e 00 00 
[    5.533563] sd 0:0:0:0: [sda] Cache data unavailable 
[    5.533570] sd 0:0:0:0: [sda] Assuming drive cache: write through 
[    5.533647]  sda: sda1 sda2 < sda5 > 
[    5.574072] sd 0:0:0:0: [sda] Attached SCSI disk 
[    5.649465] Driver 'sr' needs updating - please use bus_type methods 
[    5.650670] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray 
[    5.650747] Uniform CD-ROM driver Revision: 3.20 
[    5.650824] sr 2:0:0:0: Attached scsi CD-ROM sr0 
[    5.796560] PM: Starting manual resume from disk 
[    5.796598] PM: Resume from partition 8:5 
[    5.796620] PM: Checking hibernation image. 
[    5.796774] PM: Resume from disk failed. 
[    5.851080] EXT3-fs: INFO: recovery required on readonly filesystem. 
[    5.851110] EXT3-fs: write access will be enabled during recovery. 
[    7.415515] kjournald starting.  Commit interval 5 seconds 
[    7.416435] EXT3-fs: sda1: orphan cleanup on readonly fs 
[    7.416808] ext3_orphan_cleanup: deleting unreferenced inode 26208 
[    7.421725] ext3_orphan_cleanup: deleting unreferenced inode 111003 
[    7.421811] EXT3-fs: sda1: 2 orphan inodes deleted 
[    7.421859] EXT3-fs: recovery complete. 
[    7.442759] EXT3-fs: mounted filesystem with ordered data mode. 
[   34.753824] udevd version 124 started 
[   36.804142] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   36.893099] Linux agpgart interface v0.103 
[   37.025041] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   37.207253] agpgart-intel 0000:00:00.0: Intel 440BX Chipset 
[   37.211623] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x0 
[   37.227662] input: PC Speaker as /devices/platform/pcspkr/input/input2 
[   37.305209] ACPI: I/O resource piix4_smbus [0x1040-0x1047] conflicts with ACPI region SMB_ [0x1040-0x104b] 
[   37.305234] ACPI: Device needs an ACPI driver 
[   37.305371] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled! 
[   38.371404] ACPI: AC Adapter [ACAD] (on-line) 
[   38.433864] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3 
[   38.450276] ACPI: Power Button (FF) [PWRF] 
[   38.827237] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4 
[   41.536899] parport_pc 00:08: reported by Plug and Play ACPI 
[   41.538133] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
[   42.213316] ENS1371 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[   47.332387] NET: Registered protocol family 10 
[   47.346946] lo: Disabled Privacy Extensions 
[   48.367698] loop: module loaded 
[   48.451843] lp0: using parport0 (interrupt-driven). 
[   49.556730] Adding 192740k swap on /dev/sda5.  Priority:-1 extents:1 across:192740k 
[   50.239768] EXT3 FS on sda1, internal journal 
[   52.622060] type=1505 audit(1234339035.189:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3825 
[   53.020395] type=1505 audit(1234339035.589:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3830 
[   53.021594] type=1505 audit(1234339035.589:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3830 
[   53.402530] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   55.313904] ACPI: WMI: Mapper loaded 
[   57.876615] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[   58.037462] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
[   58.037601] apm: overridden by ACPI. 
[   58.335248] ppdev: user-space parallel port driver 
[   61.207132] Bluetooth: Core ver 2.13 
[   61.215116] NET: Registered protocol family 31 
[   61.215166] Bluetooth: HCI device and connection manager initialized 
[   61.215491] Bluetooth: HCI socket layer initialized 
[   61.303840] Bluetooth: L2CAP ver 2.11 
[   61.303882] Bluetooth: L2CAP socket layer initialized 
[   61.375931] Bluetooth: RFCOMM socket layer initialized 
[   61.378268] Bluetooth: RFCOMM TTY layer initialized 
[   61.378312] Bluetooth: RFCOMM ver 1.10 
[   61.385758] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   61.385798] Bluetooth: BNEP filters: protocol multicast 
[   61.702169] Bridge firewalling registered 
[   61.710605] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature. 
[   61.753003] Bluetooth: SCO (Voice Link) ver 0.6 
[   61.753046] Bluetooth: SCO socket layer initialized 
[   65.863267] eth0: link up 
[   67.182773] NET: Registered protocol family 17 
[   76.827037] eth0: no IPv6 routers present 
[  219.037188] ppdev0: registered pardevice 
[  219.263017] ppdev0: unregistered pardevice 
[  223.615182] ppdev0: registered pardevice 
[  223.666861] ppdev0: unregistered pardevice 
[  225.003089] type=1503 audit(1234339231.986:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5318/net/" pid=5318 profile="/usr/sbin/cupsd" 
[  226.364804] type=1503 audit(1234339233.350:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5322/net/" pid=5322 profile="/usr/sbin/cupsd" 
[  226.374691] type=1503 audit(1234339233.358:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5322 profile="/usr/sbin/cupsd" 
[  226.382103] type=1503 audit(1234339233.366:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5322 profile="/usr/sbin/cupsd" 
[  226.382132] type=1503 audit(1234339233.366:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5322 profile="/usr/sbin/cupsd" 
[  226.382162] type=1503 audit(1234339233.366:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5322 profile="/usr/sbin/cupsd" 
[  226.382178] type=1503 audit(1234339233.366:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5322 profile="/usr/sbin/cupsd" 
[  226.382194] type=1503 audit(1234339233.366:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5322 profile="/usr/sbin/cupsd" 
[  226.382210] type=1503 audit(1234339233.366:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5322 profile="/usr/sbin/cupsd" 
[  226.382226] type=1503 audit(1234339233.366:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5322 profile="/usr/sbin/cupsd" 
[  226.458005] ppdev0: registered pardevice 
[  226.506961] ppdev0: unregistered pardevice

---

### Post by digitalbenji on 2009-02-11
Ok, so, this output of lspci: ```
02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10
``` shows that your Ethernet Card was identified.  Additionally, this: ```
[ 5.320310] pcnet32 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 5.320527] pcnet32: PCnet/PCI II 79C970A at 0x2000, 00:0c:29:2d:69:20 assigned IRQ 18.
[ 5.332487] eth0: registered as PCnet/PCI II 79C970A
[ 5.332704] pcnet32: 1 cards_found. 
``` gives you more information about the ethernet card that was identified.  If there are hardware errors, they usually show up as message in dmesg.

---

### Post by naani on 2009-02-12
digitalbenji | thanks for highlighting about AMD .

I did cross verified in Device manager of my system and the Modem is provided by CXT and my Network Adapter is Intel. I am learning a lot about my system. I queried the modem and the following is the result :

AT+GMM - +GMM: ThinkPad Integrated 56K Modem
AT+FCLASS=? - 0,1
AT#CLS=? - COMMAND NOT SUPPORTED
AT+GCI? - +GCI: 100
AT+GCI=? - +GCI: (00,04,07,09,0A,0F,14,16,1B,20,25,26,27,2D,2E,31,35,3C,3D,46,50,51,52,53,54,57,58,59,61,68,69,6C,73,7B,7E,82,85,88,89,8A,8B,9C,9F,A0,A5,A6,A9,AE,B4,B5,B7,B8,BB,BC,F9,FB,FC,FE)
ATI1 - 255
ATI2 - OK
ATI3 - SoftK56V_B2.1_V7.34.00
ATI4 - ThinkPad Integrated 56K Modem
ATI5 - 256
ATI6 - SoftK56 
       CModem Version 12
       Rksample Version 342
ATI7 - 255
ATQ0V1E0 - OK
AT+GMM - +GMM: ThinkPad Integrated 56K Modem
AT+FCLASS=? - 0,1
AT#CLS=? - COMMAND NOT SUPPORTED
AT+GCI? - +GCI: 100
AT+GCI=? - +GCI: (00,04,07,09,0A,0F,14,16,1B,20,25,26,27,2D,2E,31,35,3C,3D,46,50,51,52,53,54,57,58,59,61,68,69,6C,73,7B,7E,82,85,88,89,8A,8B,9C,9F,A0,A5,A6,A9,AE,B4,B5,B7,B8,BB,BC,F9,FB,FC,FE)
ATI1 - 255
ATI2 - OK
ATI3 - SoftK56V_B2.1_V7.34.00
ATI4 - ThinkPad Integrated 56K Modem
ATI5 - 256
ATI6 - SoftK56 
       CModem Version 12
       Rksample Version 342
ATI7 - 255
ATQ0V1E0 - OK
AT+GMM - +GMM: ThinkPad Integrated 56K Modem
AT+FCLASS=? - 0,1
AT#CLS=? - COMMAND NOT SUPPORTED
AT+GCI? - +GCI: 100
AT+GCI=? - +GCI: (00,04,07,09,0A,0F,14,16,1B,20,25,26,27,2D,2E,31,35,3C,3D,46,50,51,52,53,54,57,58,59,61,68,69,6C,73,7B,7E,82,85,88,89,8A,8B,9C,9F,A0,A5,A6,A9,AE,B4,B5,B7,B8,BB,BC,F9,FB,FC,FE)
ATI1 - 255
ATI2 - OK
ATI3 - SoftK56V_B2.1_V7.34.00
ATI4 - ThinkPad Integrated 56K Modem
ATI5 - 256
ATI6 - SoftK56 
       CModem Version 12
       Rksample Version 342
ATI7 - 255
ATQ0V1E0 - OK
AT+GMM - +GMM: ThinkPad Integrated 56K Modem
AT+FCLASS=? - 0,1
AT#CLS=? - COMMAND NOT SUPPORTED
AT+GCI? - +GCI: 100
AT+GCI=? - +GCI: (00,04,07,09,0A,0F,14,16,1B,20,25,26,27,2D,2E,31,35,3C,3D,46,50,51,52,53,54,57,58,59,61,68,69,6C,73,7B,7E,82,85,88,89,8A,8B,9C,9F,A0,A5,A6,A9,AE,B4,B5,B7,B8,BB,BC,F9,FB,FC,FE)
ATI1 - 255
ATI2 - OK
ATI3 - SoftK56V_B2.1_V7.34.00
ATI4 - ThinkPad Integrated 56K Modem
ATI5 - 256
ATI6 - SoftK56 
       CModem Version 12
       Rksample Version 342
ATI7 - 255

---

