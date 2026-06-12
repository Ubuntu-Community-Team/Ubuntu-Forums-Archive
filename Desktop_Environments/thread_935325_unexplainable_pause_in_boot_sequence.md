---
title: "unexplainable pause in boot sequence"
date: 2008-10-01
forum: Desktop Environments
---

### Post by Cclips on 2008-10-01
So i've recently developed an inexplicable pause in my booting sequence. After the usplash has vanished and when the log in screen would normally pop up, I get a black screen with the loading mouse icon. It stays for at least 45 seconds or so, pushing my boot times over a minute into windows territory lol.

Anyways, did some investigating with bootchart,BUM, and the likes and didn't find anything out of the ordinary, and nothing that isn't normally different from my desktop (this is on my laptop).

Any ideas?

Here is my bootchart. I tried it both with the wifi on and wifi off with the boot times nearly identical 26 seconds off, 27 on, but the pause is apparently after the bootchart stops reading.

---

### Post by Cclips on 2008-10-02
No one has ANY ideas what so ever?

---

### Post by cariboo on 2008-10-02
Why not remove quiet from you grub menu choice and just watch the output as it is booting, to see what part of the boot is holding it up.

Jim

---

### Post by Cclips on 2008-10-02
Becuase it is after boot spalsh disapears. I have a curser that I can move around, but there isn't anything else showing. Hard drive isn't reading either.

---

### Post by benerivo on 2008-10-02
Have you checked /var/log/dmesg

---

### Post by Cclips on 2008-10-02
Nothing showing up in that folder.

---

### Post by benerivo on 2008-10-02
> **Cclips said:**
> Nothing showing up in that folder.

Do you mean you can't find the file, or that when opening it, it doesn't show anything useful?

---

### Post by Cclips on 2008-10-02
well the folder isn't there to begin with.

---

### Post by benerivo on 2008-10-02
Sorry. dmesg is a file with no filetype extension and so  looks like a folder when its full path location is read (/var/log/dmesg). It is really just a text file inside /var/log/

---

### Post by Cclips on 2008-10-02
Heres the output of said file.


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f66d800 (usable)
[    0.000000]  BIOS-e820: 000000007f66d800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 521837) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521837
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521837
[    0.000000] On node 0 totalpages: 521837
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290177 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBBF0 checksum 0
[    0.000000] ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7F66F200, 0054 (r1 DELL    M08     27D80415 ASL        61)
[    0.000000] ACPI: FACP 7F66F09C, 00F4 (r4 DELL    M08     27D80415 ASL        61)
[    0.000000] ACPI: DSDT 7F66F800, 5676 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7F67E000, 0040
[    0.000000] ACPI: HPET 7F66F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7F66F400, 0068 (r1 DELL    M08     27D80415 ASL        47)
[    0.000000] ACPI: MCFG 7F66F3C0, 003E (r16 DELL    M08     27D80415 ASL        61)
[    0.000000] ACPI: BOOT 7F66EFC0, 0028 (r1 DELL    M08     27D80415 ASL        61)
[    0.000000] ACPI: SSDT 7F66D9B8, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517761
[    0.000000] Kernel command line: root=UUID=6c9f5161-a880-4615-bc3f-664cb81768d7 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2193.984 MHz processor.
[    7.605419] Console: colour VGA+ 80x25
[    7.605422] console [tty0] enabled
[    7.605708] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    7.605971] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.674619] Memory: 2057520k/2087348k available (2177k kernel code, 28620k reserved, 1006k data, 368k init, 1169844k highmem)
[    7.674625] virtual kernel memory layout:
[    7.674626]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    7.674626]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.674627]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.674628]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.674629]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    7.674629]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[    7.674630]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[    7.674633] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.674668] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    7.674787] hpet clockevent registered
[    7.754664] Calibrating delay using timer specific routine.. 4392.53 BogoMIPS (lpj=8785066)
[    7.754682] Security Framework initialized
[    7.754686] SELinux:  Disabled at boot.
[    7.754697] AppArmor: AppArmor initialized
[    7.754700] Failure registering capabilities with primary security module.
[    7.754707] Mount-cache hash table entries: 512
[    7.754806] Initializing cgroup subsys ns
[    7.754811] Initializing cgroup subsys cpuacct
[    7.754819] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[    7.754825] monitor/mwait feature present.
[    7.754826] using mwait in idle threads.
[    7.754829] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.754831] CPU: L2 cache: 4096K
[    7.754833] CPU: Physical Processor ID: 0
[    7.754834] CPU: Processor Core ID: 0
[    7.754835] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[    7.754843] Compat vDSO mapped to ffffe000.
[    7.754853] Checking 'hlt' instruction... OK.
[    7.770954] SMP alternatives: switching to UP code
[    7.772260] Early unpacking initramfs... done
[    8.032482] ACPI: Core revision 20070126
[    8.032516] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.035712] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[    8.035725] SMP alternatives: switching to SMP code
[    8.036289] Booting processor 1/1 eip 3000
[    8.046670] Initializing CPU#1
[    8.126055] Calibrating delay using timer specific routine.. 4387.73 BogoMIPS (lpj=8775469)
[    8.126061] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000001
[    8.126064] monitor/mwait feature present.
[    8.126067] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.126068] CPU: L2 cache: 4096K
[    8.126070] CPU: Physical Processor ID: 0
[    8.126071] CPU: Processor Core ID: 1
[    8.126072] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[    8.126684] CPU1: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[    8.126703] Total of 2 processors activated (8780.26 BogoMIPS).
[    8.126898] ENABLING IO-APIC IRQs
[    8.127081] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.273906] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    8.293886] Brought up 2 CPUs
[    8.293905] CPU0 attaching sched-domain:
[    8.293907]  domain 0: span 03
[    8.293909]   groups: 01 02
[    8.293911] CPU1 attaching sched-domain:
[    8.293912]  domain 0: span 03
[    8.293913]   groups: 02 01
[    8.294078] net_namespace: 64 bytes
[    8.294087] Booting paravirtualized kernel on bare hardware
[    8.294450] Time: 20:07:49  Date: 10/01/08
[    8.294471] NET: Registered protocol family 16
[    8.294609] EISA bus registered
[    8.294612] ACPI: bus type pci registered
[    8.305235] PCI: PCI BIOS revision 2.10 entry at 0xfad46, last bus=14
[    8.305237] PCI: Using configuration type 1
[    8.305249] Setting up standard PCI resources
[    8.312057] ACPI: EC: Look up EC in DSDT
[    8.352327] ACPI: Interpreter enabled
[    8.352330] ACPI: (supports S0 S3 S4 S5)
[    8.352340] ACPI: Using IOAPIC for interrupt routing
[    8.370357] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.371330] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.371334] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    8.372856] PCI: Transparent bridge - 0000:00:1e.0
[    8.372904] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.373259] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    8.373384] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    8.373480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    8.373574] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    8.373667] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    8.383138] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    8.383230] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    8.383321] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    8.383411] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    8.383501] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    8.383593] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    8.383684] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    8.383768] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    8.383876] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.383897] pnp: PnP ACPI init
[    8.383902] ACPI: bus type pnp registered
[    8.417284] pnpacpi: exceeded the max number of mem resources: 12
[    8.417444] pnp: PnP ACPI: found 12 devices
[    8.417446] ACPI: ACPI bus type pnp unregistered
[    8.417448] PnPBIOS: Disabled by ACPI PNP
[    8.417607] PCI: Using ACPI for IRQ routing
[    8.417610] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.505449] NET: Registered protocol family 8
[    8.505450] NET: Registered protocol family 20
[    8.505475] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    8.505478] hpet0: 3 64-bit timers, 14318180 Hz
[    8.506503] AppArmor: AppArmor Filesystem Enabled
[    8.509438] Time: tsc clocksource has been installed.
[    8.509444] Switched to high resolution mode on CPU 0
[    8.509531] Switched to high resolution mode on CPU 1
[    8.525398] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    8.525404] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    8.525408] system 00:09: ioport range 0x900-0x97f has been reserved
[    8.525410] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    8.525412] system 00:09: ioport range 0x1000-0x1005 has been reserved
[    8.525414] system 00:09: ioport range 0x1008-0x100f has been reserved
[    8.525419] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    8.525421] system 00:0a: ioport range 0x1006-0x1007 has been reserved
[    8.525423] system 00:0a: ioport range 0x100a-0x1059 could not be reserved
[    8.525425] system 00:0a: ioport range 0x1060-0x107f has been reserved
[    8.525427] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    8.525429] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    8.525431] system 00:0a: ioport range 0x1010-0x102f has been reserved
[    8.525433] system 00:0a: ioport range 0x809-0x809 has been reserved
[    8.525437] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    8.525440] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    8.525442] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    8.525444] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    8.525446] system 00:0b: iomem range 0x100000-0x7f66d7ff could not be reserved
[    8.525448] system 00:0b: iomem range 0x7f66d800-0x7f6fffff could not be reserved
[    8.525450] system 00:0b: iomem range 0x7f700000-0x7f7fffff could not be reserved
[    8.525452] system 00:0b: iomem range 0x7f700000-0x7fefffff could not be reserved
[    8.525455] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[    8.525457] system 00:0b: iomem range 0xffa00000-0xffafffff has been reserved
[    8.525459] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    8.525461] system 00:0b: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    8.555727] PCI: Bridge: 0000:00:1c.0
[    8.555729]   IO window: disabled.
[    8.555734]   MEM window: disabled.
[    8.555738]   PREFETCH window: disabled.
[    8.555744] PCI: Bridge: 0000:00:1c.1
[    8.555744]   IO window: disabled.
[    8.555750]   MEM window: fe800000-fe8fffff
[    8.555754]   PREFETCH window: disabled.
[    8.555759] PCI: Bridge: 0000:00:1c.3
[    8.555762]   IO window: d000-dfff
[    8.555767]   MEM window: fe600000-fe7fffff
[    8.555771]   PREFETCH window: f0000000-f01fffff
[    8.555777] PCI: Bridge: 0000:00:1c.5
[    8.555778]   IO window: disabled.
[    8.555783]   MEM window: fe500000-fe5fffff
[    8.555787]   PREFETCH window: disabled.
[    8.555793] PCI: Bridge: 0000:00:1e.0
[    8.555794]   IO window: disabled.
[    8.555799]   MEM window: fe400000-fe4fffff
[    8.555803]   PREFETCH window: disabled.
[    8.555832] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.555838] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    8.555861] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    8.555866] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    8.555889] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[    8.555894] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    8.555917] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[    8.555922] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    8.555936] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.555944] NET: Registered protocol family 2
[    8.593307] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.593474] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.593791] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.593947] TCP: Hash tables configured (established 131072 bind 65536)
[    8.593949] TCP reno registered
[    8.605338] checking if image is initramfs... it is
[    9.116351] Freeing initrd memory: 7303k freed
[    9.116492] Simple Boot Flag at 0x79 set to 0x1
[    9.116958] audit: initializing netlink socket (disabled)
[    9.116970] audit(1222891669.317:1): initialized
[    9.117134] highmem bounce pool size: 64 pages
[    9.118562] VFS: Disk quotas dquot_6.5.1
[    9.118616] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.118721] io scheduler noop registered
[    9.118723] io scheduler anticipatory registered
[    9.118725] io scheduler deadline registered
[    9.118733] io scheduler cfq registered (default)
[    9.118742] Boot video device is 0000:00:02.0
[    9.118949] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.119008] assign_interrupt_mode Found MSI capability
[    9.119056] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.119080] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.119170] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.119228] assign_interrupt_mode Found MSI capability
[    9.119273] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.119295] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.119385] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    9.119443] assign_interrupt_mode Found MSI capability
[    9.119488] Allocate Port Service[0000:00:1c.3:pcie00]
[    9.119511] Allocate Port Service[0000:00:1c.3:pcie02]
[    9.119602] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    9.119660] assign_interrupt_mode Found MSI capability
[    9.119704] Allocate Port Service[0000:00:1c.5:pcie00]
[    9.119727] Allocate Port Service[0000:00:1c.5:pcie02]
[    9.119931] isapnp: Scanning for PnP cards...
[    9.473714] isapnp: No Plug & Play device found
[    9.491969] Real Time Clock Driver v1.12ac
[    9.492085] hpet_resources: 0xfed00000 is busy
[    9.492132] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.493210] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.493257] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    9.493326] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.496569] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.496572] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.515838] mice: PS/2 mouse device common for all mice
[    9.515915] EISA: Probing bus 0 at eisa.0
[    9.515970] EISA: Mainboard M__FFFF detected.
[    9.515995] Cannot allocate resource for EISA slot 1
[    9.516024] EISA: Detected 0 cards.
[    9.516026] cpuidle: using governor ladder
[    9.516028] cpuidle: using governor menu
[    9.516088] NET: Registered protocol family 1
[    9.516109] Using IPI No-Shortcut mode
[    9.516138] registered taskstats version 1
[    9.516238]   Magic number: 12:285:143
[    9.516281]   hash matches device device:14
[    9.516286] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.516287] EDD information not available.
[    9.516433] Freeing unused kernel memory: 368k freed
[    9.519125] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   10.695541] fuse init (API version 7.9)
[   10.710825] ACPI: SSDT 7F66E4EE, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   10.710987] ACPI: SSDT 7F66DE84, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   10.711455] Monitor-Mwait will be used to enter C-1 state
[   10.711457] Monitor-Mwait will be used to enter C-2 state
[   10.711459] Monitor-Mwait will be used to enter C-3 state
[   10.711557] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.711561] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.711730] ACPI: SSDT 7F66E774, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   10.711874] ACPI: SSDT 7F66E469, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   10.712479] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   10.712482] ACPI: Processor [CPU1] (supports 8 throttling states)
[   10.717961] ACPI: Thermal Zone [THM] (46 C)
[   10.980392] usbcore: registered new interface driver usbfs
[   10.980412] usbcore: registered new interface driver hub
[   10.985460] usbcore: registered new device driver usb
[   10.986578] USB Universal Host Controller Interface driver v3.0
[   10.986620] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
[   10.986630] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   10.986633] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   10.986825] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   10.986855] uhci_hcd 0000:00:1a.0: irq 19, io base 0x00006f20
[   10.986952] usb usb1: configuration #1 chosen from 1 choice
[   10.986969] hub 1-0:1.0: USB hub found
[   10.986973] hub 1-0:1.0: 2 ports detected
[   11.033229] SCSI subsystem initialized
[   11.062394] libata version 3.00 loaded.
[   11.090311] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[   11.090321] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   11.090325] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   11.090342] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   11.090371] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00006f00
[   11.090458] usb usb2: configuration #1 chosen from 1 choice
[   11.090475] hub 2-0:1.0: USB hub found
[   11.090478] hub 2-0:1.0: 2 ports detected
[   11.194190] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 21
[   11.194204] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   11.194207] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   11.194226] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[   11.198121] ehci_hcd 0000:00:1a.7: debug port 1
[   11.198127] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   11.198134] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xfed1c400
[   11.214056] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.214129] usb usb3: configuration #1 chosen from 1 choice
[   11.214147] hub 3-0:1.0: USB hub found
[   11.214151] hub 3-0:1.0: 4 ports detected
[   11.317944] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[   11.317958] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.317961] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.317980] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   11.321887] ehci_hcd 0000:00:1d.7: debug port 1
[   11.321893] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   11.321897] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfed1c000
[   11.337852] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.337924] usb usb4: configuration #1 chosen from 1 choice
[   11.337942] hub 4-0:1.0: USB hub found
[   11.337945] hub 4-0:1.0: 6 ports detected
[   11.441844] tg3.c:v3.86 (November 9, 2007)
[   11.441900] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   11.441915] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   11.777222] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1e:c9:09:bb:d6
[   11.777228] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[   11.777230] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   11.777263] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   11.777293] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.777304] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   11.777452] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[   11.781011] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[   11.781019] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.781023] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.781043] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   11.781069] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00006f80
[   11.781170] usb usb5: configuration #1 chosen from 1 choice
[   11.781189] hub 5-0:1.0: USB hub found
[   11.781193] hub 5-0:1.0: 2 ports detected
[   11.796083] Clocksource tsc unstable (delta = -2925796545 ns)
[   11.797081] Time: hpet clocksource has been installed.
[   11.830108] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fe4ff800-fe4fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   11.845589] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[   11.845601] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.845607] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.845635] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   11.845665] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00006f60
[   11.845761] usb usb6: configuration #1 chosen from 1 choice
[   11.845778] hub 6-0:1.0: USB hub found
[   11.845782] hub 6-0:1.0: 2 ports detected
[   11.855313] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[   11.855324] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.855329] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.855355] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   11.855384] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006f40
[   11.855481] usb usb7: configuration #1 chosen from 1 choice
[   11.855497] hub 7-0:1.0: USB hub found
[   11.855500] hub 7-0:1.0: 2 ports detected
[   11.867037] ahci 0000:00:1f.2: version 3.0
[   11.867058] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   11.867103] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   11.867105] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   11.991281] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   11.991287] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   11.991294] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   11.991544] scsi0 : ahci
[   11.991691] scsi1 : ahci
[   11.991809] scsi2 : ahci
[   11.992012] ata1: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 219
[   11.992016] ata2: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb980 irq 219
[   11.992019] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 219
[   11.993278] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[4a4fc0000b0b59c1]
[   12.036181] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   12.079283] ata1.00: ATA-8: WDC WD1600BEVT-75ZCT1, 11.01A11, max UDMA/133
[   12.079288] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   12.080273] ata1.00: configured for UDMA/133
[   12.124691] ata2: SATA link down (SStatus 0 SControl 0)
[   12.147505] ata3: SATA link down (SStatus 0 SControl 300)
[   12.147732] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-7 11.0 PQ: 0 ANSI: 5
[   12.147974] ata_piix 0000:00:1f.1: version 2.12
[   12.147988] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   12.148018] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.148078] scsi3 : ata_piix
[   12.148184] scsi4 : ata_piix
[   12.148691] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   12.148693] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   12.154232] Driver 'sd' needs updating - please use bus_type methods
[   12.157065] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   12.157111] sd 0:0:0:0: [sda] Write Protect is off
[   12.157115] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.157190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.157267] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   12.157297] sd 0:0:0:0: [sda] Write Protect is off
[   12.157299] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.157355] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.157357]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   12.224697] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.227983] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.476793] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D400, max UDMA/33
[   12.520315] ata4.00: configured for UDMA/33
[   12.520409] ata5: port disabled. ignoring.
[   12.522461] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D400 PQ: 0 ANSI: 5
[   12.522566] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   12.530730] Driver 'sr' needs updating - please use bus_type methods
[   12.537944] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.537948] Uniform CD-ROM driver Revision: 3.20
[   12.538003] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   12.585048] Attempting manual resume
[   12.585050] swsusp: Resume From Partition 8:5
[   12.585052] PM: Checking swsusp image.
[   12.585204] PM: Resume from disk failed.
[   12.644930] kjournald starting.  Commit interval 5 seconds
[   12.644968] EXT3-fs: mounted filesystem with ordered data mode.
[   19.644309] Linux agpgart interface v0.102
[   19.685542] agpgart: Detected an Intel 965GM Chipset.
[   19.687160] agpgart: Detected 7676K stolen memory.
[   19.699351] agpgart: AGP aperture is 256M @ 0xe0000000
[   19.729464] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.748975] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.932772] ACPI: AC Adapter [AC] (on-line)
[   19.969672] input: Lid Switch as /devices/virtual/input/input2
[   19.970131] ACPI: Lid Switch [LID]
[   19.970180] input: Power Button (CM) as /devices/virtual/input/input3
[   20.001472] ACPI: Power Button (CM) [PBTN]
[   20.001534] input: Sleep Button (CM) as /devices/virtual/input/input4
[   20.025427] ACPI: Sleep Button (CM) [SBTN]
[   20.084413] ACPI: Battery Slot [BAT0] (battery present)
[   20.087213] ACPI: WMI-Acer: Mapper loaded
[   20.186609] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input5
[   20.217119] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   20.226231] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   20.257040] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   20.257181] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input7
[   20.281007] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   20.795347] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   20.795365] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.820886] iTCO_vendor_support: vendor-support=0
[   20.821521] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   20.821601] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   20.821647] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.905653] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   20.905656] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   20.975113] patch_cxthsfmodem: symbol_request(cnxthwhda_probe) failed
[   21.038907] sdhci: Secure Digital Host Controller Interface driver
[   21.038909] sdhci: Copyright(c) Pierre Ossman
[   21.270592] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   21.270609] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   21.270627] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   21.340648] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   21.399626] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   21.550567] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[   21.550591] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   21.550613] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
[   21.552660] mmc0: SDHCI at 0xfe4ff500 irq 22 DMA
[   21.743348] input: PS/2 Mouse as /devices/virtual/input/input9
[   21.841443] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   21.901258] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   22.183721] udev: renamed network interface wlan0 to eth1
[   22.345809] lp: driver loaded but no devices found
[   22.440382] Adding 6056464k swap on /dev/sda5.  Priority:-1 extents:1 across:6056464k
[   22.886860] EXT3 FS on sda3, internal journal
[   23.474569] kjournald starting.  Commit interval 5 seconds
[   23.474883] EXT3 FS on sda2, internal journal
[   23.474888] EXT3-fs: mounted filesystem with ordered data mode.
[   23.860590] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by benerivo on 2008-10-02
I believe the numbers on the left are seconds. So this might not contain any useful info for you as this file records events from bootup onwards, and yours ends at 23.8. If you have to wait for 45, then it is not recorded here. You could try temporarily changing your login manager (gdm) to something else, and rebooting to check if there is still the same delay. If not, then I would guess it is a gdm problem.

EDIT - Also, can you remember if there were any system changes that were made before this started to happen?

---

### Post by Cclips on 2008-10-02
Can't think of any system changes that would have effecetd it, as it has been awhile since the issue debuted. Any logs that I could check for GDM?

---

### Post by Cclips on 2008-10-02
Here is the sys.log after the 23 seconds...I think

```
Oct  2 19:40:37 Nostromo kernel: [   24.227099] kjournald starting.  Commit interval 5 seconds
Oct  2 19:40:37 Nostromo kernel: [   24.227413] EXT3 FS on sda2, internal journal
Oct  2 19:40:37 Nostromo kernel: [   24.227418] EXT3-fs: mounted filesystem with ordered data mode.
Oct  2 19:40:37 Nostromo kernel: [   24.601981] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct  2 19:40:37 Nostromo kernel: [   25.087730] No dock devices found.
Oct  2 19:40:37 Nostromo NetworkManager: <info>  starting... 
Oct  2 19:40:37 Nostromo avahi-daemon[6466]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Oct  2 19:40:37 Nostromo avahi-daemon[6466]: Successfully dropped root privileges.
Oct  2 19:40:37 Nostromo avahi-daemon[6466]: avahi-daemon 0.6.22 starting up.
Oct  2 19:40:37 Nostromo avahi-daemon[6466]: Successfully called chroot().
Oct  2 19:40:37 Nostromo avahi-daemon[6466]: Successfully dropped remaining capabilities.
Oct  2 19:40:38 Nostromo avahi-daemon[6466]: No service file found in /etc/avahi/services.
Oct  2 19:40:38 Nostromo avahi-daemon[6466]: Network interface enumeration completed.
Oct  2 19:40:38 Nostromo avahi-daemon[6466]: Registering HINFO record with values 'I686'/'LINUX'.
Oct  2 19:40:38 Nostromo avahi-daemon[6466]: Server startup complete. Host name is Nostromo.local. Local service cookie is 685998806.
Oct  2 19:40:38 Nostromo dhcdbd: Started up.
Oct  2 19:40:39 Nostromo NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'. 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  Deactivating device eth0. 
Oct  2 19:40:39 Nostromo kernel: [   27.209213] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct  2 19:40:39 Nostromo kernel: [   27.209366] PM: Writing back config space on device 0000:0c:00.0 at offset 1 (was 100102, writing 100106)
Oct  2 19:40:39 Nostromo kernel: [   27.260948] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Oct  2 19:40:39 Nostromo kernel: [   27.263078] Registered led device: iwl-phy0:RX
Oct  2 19:40:39 Nostromo kernel: [   27.263116] Registered led device: iwl-phy0:TX
Oct  2 19:40:39 Nostromo NetworkManager: <info>  eth1: Device is fully-supported using driver 'iwl3945'. 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  Deactivating device eth1. 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct  2 19:40:39 Nostromo NetworkManager: <debug> [1222994439.906806] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_TS_L632H'). 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 
Oct  2 19:40:39 Nostromo NetworkManager: <info>  Wireless now enabled by radio killswitch 
Oct  2 19:40:42 Nostromo anacron[7063]: Anacron 2.3 started on 2008-10-02
Oct  2 19:40:42 Nostromo anacron[7063]: Normal exit (0 jobs run)
Oct  2 19:40:42 Nostromo /usr/sbin/cron[7094]: (CRON) INFO (pidfile fd = 3)
Oct  2 19:40:42 Nostromo /usr/sbin/cron[7096]: (CRON) STARTUP (fork ok)
Oct  2 19:40:42 Nostromo /usr/sbin/cron[7096]: (CRON) INFO (Running @reboot jobs)
Oct  2 19:40:43 Nostromo kernel: [   29.706570] [drm] Initialized drm 1.1.0 20060810
Oct  2 19:40:43 Nostromo kernel: [   29.709484] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct  2 19:40:43 Nostromo kernel: [   29.709495] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct  2 19:40:43 Nostromo kernel: [   29.710035] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct  2 19:40:43 Nostromo NetworkManager: <debug> [1222994443.878142] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a02_drm_i915_card0'). 
Oct  2 19:42:58 Nostromo kernel: [  152.811138] NET: Registered protocol family 10
Oct  2 19:42:58 Nostromo kernel: [  152.811629] lo: Disabled Privacy Extensions
Oct  2 19:42:58 Nostromo kernel: [  152.812440] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  2 19:42:58 Nostromo kernel: [  152.813364] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by bsh on 2008-10-03
> Oct  2 19:42:58 Nostromo kernel: [  152.812440] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  2 19:42:58 Nostromo kernel: [  152.813364] ADDRCONF(NETDEV_UP): eth1: link is not ready

eth0 & eth1 are not ready (no link or no cable) and maybe they are both configured for dhcp and trying to retrieve the ip address and other configuration and this holds things back?
try to disable one of these (if you aren't using one of them) either in the bios or in ifconfig/interfaces and if possible, try not to use dhcp, try static ip configuration.

---

### Post by Cclips on 2008-10-03
I tried playing around with the settings but only ended up screwing up my connections. I've gotten those back working, but the pause issue is still present. 

I don't think its a network issue because if I disable the networking via the switch it doesn't effect anything, and the eth0 and eth1 have been listed as being on the laptop since before this problem started.

---

### Post by SpetsnazC4 on 2008-10-04
Hi, I come to the forums to find out a strange pause in my boot and I found your post. I am using an IBM ThinkPad T41 Laptop.

I have disabled USplash and now boot in texty mode. I can see exactly where my pause occurs. The system hangs at a line that says: 9.793175] Clocksource tsc unstable (delta = -1234713778 ns)

You have the same line (Clocksource tsc unstable) on line 378 of your dmesg. I wonder if that too is where your system hangs.

I don't know what it means or how to fix it. I am going to keep looking and if I find something I'll post it here too. Hopefully a guru will post some advice here.

Here is my dmesg, "9.793175] Clocksource tsc unstable (delta = -1234713778 ns)" is on line 319. 


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ff60000 (usable)
[    0.000000]  BIOS-e820: 000000002ff60000 - 000000002ff77000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ff77000 - 000000002ff79000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff80000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 196448) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196448
[    0.000000]   HighMem    196448 ->   196448
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196448
[    0.000000] On node 0 totalpages: 196448
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1502 pages used for memmap
[    0.000000]   Normal zone: 190850 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6E00 checksum 0
[    0.000000] ACPI: RSDP 000F6E00, 0024 (r2 IBM   )
[    0.000000] ACPI: XSDT 2FF6AF83, 004C (r1 IBM    TP-1R        3051  LTP        0)
[    0.000000] ACPI: FACP 2FF6B000, 00F4 (r3 IBM    TP-1R        3051 IBM         1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
[    0.000000] ACPI: DSDT 2FF6B1E7, BC1F (r1 IBM    TP-1R        3051 MSFT  100000E)
[    0.000000] ACPI: FACS 2FF78000, 0040
[    0.000000] ACPI: SSDT 2FF6B1B4, 0033 (r1 IBM    TP-1R        3051 MSFT  100000E)
[    0.000000] ACPI: ECDT 2FF76E06, 0052 (r1 IBM    TP-1R        3051 IBM         1)
[    0.000000] ACPI: TCPA 2FF76E58, 0032 (r1 IBM    TP-1R        3051 PTL         1)
[    0.000000] ACPI: BOOT 2FF76FD8, 0028 (r1 IBM    TP-1R        3051  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cf800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 00000000000d4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194914
[    0.000000] Kernel command line: root=UUID=4e2417be-df5e-4743-a808-a375391da1ec ro vga=792
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0160e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1594.854 MHz processor.
[    4.665952] Console: colour dummy device 80x25
[    4.665957] console [tty0] enabled
[    4.666717] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    4.667379] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    4.689796] Memory: 766852k/785792k available (2177k kernel code, 18408k reserved, 1006k data, 368k init, 0k highmem)
[    4.689814] virtual kernel memory layout:
[    4.689815]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    4.689817]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    4.689818]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[    4.689819]     lowmem  : 0xc0000000 - 0xeff60000   ( 767 MB)
[    4.689821]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    4.689822]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[    4.689824]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[    4.689849] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    4.689894] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    4.769913] Calibrating delay using timer specific routine.. 3192.14 BogoMIPS (lpj=6384290)
[    4.769946] Security Framework initialized
[    4.769956] SELinux:  Disabled at boot.
[    4.769975] AppArmor: AppArmor initialized
[    4.769981] Failure registering capabilities with primary security module.
[    4.769994] Mount-cache hash table entries: 512
[    4.770130] Initializing cgroup subsys ns
[    4.770139] Initializing cgroup subsys cpuacct
[    4.770152] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    4.770164] CPU: L1 I cache: 32K, L1 D cache: 32K
[    4.770170] CPU: L2 cache: 1024K
[    4.770174] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000 00000000
[    4.770184] Compat vDSO mapped to ffffe000.
[    4.770199] Checking 'hlt' instruction... OK.
[    4.786339] SMP alternatives: switching to UP code
[    4.788333] Freeing SMP alternatives: 11k freed
[    4.788452] Early unpacking initramfs... done
[    5.180738] ACPI: Core revision 20070126
[    5.180859] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    5.185450] ACPI: setting ELCR to 0200 (from 0800)
[    5.195508] CPU0: Intel(R) Pentium(R) M processor 1600MHz stepping 05
[    5.195517] SMP motherboard not detected.
[    5.195522] Local APIC not detected. Using dummy APIC emulation.
[    5.195571] Brought up 1 CPUs
[    5.195594] CPU0 attaching sched-domain:
[    5.195597]  domain 0: span 01
[    5.195599]   groups: 01
[    5.195784] net_namespace: 64 bytes
[    5.195794] Booting paravirtualized kernel on bare hardware
[    5.196425] Time: 12:17:45  Date: 10/04/08
[    5.196455] NET: Registered protocol family 16
[    5.196663] EISA bus registered
[    5.196677] ACPI: bus type pci registered
[    5.196984] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
[    5.196990] PCI: Using configuration type 1
[    5.196999] Setting up standard PCI resources
[    5.201525] ACPI: EC: EC description table is found, configuring boot EC
[    5.207191] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    5.210183] ACPI: Interpreter enabled
[    5.210189] ACPI: (supports S0 S3 S4 S5)
[    5.210207] ACPI: Using PIC for interrupt routing
[    5.217025] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    5.217034] ACPI: EC: driver started in poll mode
[    5.217181] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    5.217576] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    5.217584] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    5.218113] PCI: Transparent bridge - 0000:00:1e.0
[    5.218221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    5.218280] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    5.218305] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    5.222110] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    5.222310] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    5.222508] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    5.222706] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    5.222887] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    5.223069] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    5.223251] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    5.223450] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    5.223607] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    5.223692] ACPI: Power Resource [PUBS] (on)
[    5.223742] Linux Plug and Play Support v0.97 (c) Adam Belay
[    5.223777] pnp: PnP ACPI init
[    5.223787] ACPI: bus type pnp registered
[    5.224884] pnpacpi: exceeded the max number of mem resources: 12
[    5.227151] pnp: PnP ACPI: found 13 devices
[    5.227156] ACPI: ACPI bus type pnp unregistered
[    5.227163] PnPBIOS: Disabled by ACPI PNP
[    5.227391] PCI: Using ACPI for IRQ routing
[    5.227397] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    5.253890] NET: Registered protocol family 8
[    5.253895] NET: Registered protocol family 20
[    5.253969] AppArmor: AppArmor Filesystem Enabled
[    5.257881] Time: tsc clocksource has been installed.
[    5.265919] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    5.265926] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    5.265933] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    5.265939] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    5.265945] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    5.265952] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    5.265958] system 00:00: iomem range 0x0-0x0 could not be reserved
[    5.265964] system 00:00: iomem range 0x0-0x0 could not be reserved
[    5.265970] system 00:00: iomem range 0xdc000-0xdffff has been reserved
[    5.265976] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    5.265982] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    5.265989] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    5.265998] system 00:02: ioport range 0x1000-0x107f has been reserved
[    5.266005] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    5.266011] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    5.266016] system 00:02: ioport range 0x1600-0x167f has been reserved
[    5.296449] PCI: Bridge: 0000:00:01.0
[    5.296455]   IO window: 3000-3fff
[    5.296460]   MEM window: c0100000-c01fffff
[    5.296466]   PREFETCH window: e0000000-e7ffffff
[    5.296476] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[    5.296481]   IO window: 00004000-000040ff
[    5.296487]   IO window: 00004400-000044ff
[    5.296493]   PREFETCH window: e8000000-ebffffff
[    5.296500]   MEM window: c4000000-c7ffffff
[    5.296506] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[    5.296511]   IO window: 00004800-000048ff
[    5.296517]   IO window: 00004c00-00004cff
[    5.296523]   PREFETCH window: ec000000-efffffff
[    5.296529]   MEM window: c8000000-cbffffff
[    5.296535] PCI: Bridge: 0000:00:1e.0
[    5.296540]   IO window: 4000-8fff
[    5.296547]   MEM window: c0200000-cfffffff
[    5.296553]   PREFETCH window: e8000000-efffffff
[    5.296572] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    5.296938] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    5.296944] PCI: setting IRQ 11 as level-triggered
[    5.296948] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    5.297294] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    5.297299] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    5.297321] NET: Registered protocol family 2
[    5.333960] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    5.334283] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    5.335655] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    5.336633] TCP: Hash tables configured (established 131072 bind 65536)
[    5.336642] TCP reno registered
[    5.346089] checking if image is initramfs... it is
[    5.797865] Switched to high resolution mode on CPU 0
[    6.112161] Freeing initrd memory: 7321k freed
[    6.112397] Simple Boot Flag at 0x35 set to 0x1
[    6.112768] audit: initializing netlink socket (disabled)
[    6.112790] audit(1223122665.416:1): initialized
[    6.115182] VFS: Disk quotas dquot_6.5.1
[    6.115282] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    6.115458] io scheduler noop registered
[    6.115464] io scheduler anticipatory registered
[    6.115468] io scheduler deadline registered
[    6.115487] io scheduler cfq registered (default)
[    6.115564] Boot video device is 0000:01:00.0
[    6.115879] isapnp: Scanning for PnP cards...
[    6.468962] isapnp: No Plug & Play device found
[    6.502423] Real Time Clock Driver v1.12ac
[    6.502545] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    6.503596] serial 00:0a: activated
[    6.503858] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    6.504044] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    6.504060] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    6.504713] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    6.504801] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    6.504915] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    6.510208] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.510217] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.521753] mice: PS/2 mouse device common for all mice
[    6.521874] EISA: Probing bus 0 at eisa.0
[    6.521883] Cannot allocate resource for EISA slot 1
[    6.521890] Cannot allocate resource for EISA slot 2
[    6.521894] Cannot allocate resource for EISA slot 3
[    6.521899] Cannot allocate resource for EISA slot 4
[    6.521904] Cannot allocate resource for EISA slot 5
[    6.521908] Cannot allocate resource for EISA slot 6
[    6.521913] Cannot allocate resource for EISA slot 7
[    6.521918] Cannot allocate resource for EISA slot 8
[    6.521922] EISA: Detected 0 cards.
[    6.521928] cpuidle: using governor ladder
[    6.521932] cpuidle: using governor menu
[    6.522037] NET: Registered protocol family 1
[    6.522075] Using IPI No-Shortcut mode
[    6.522111] registered taskstats version 1
[    6.522241]   Magic number: 12:315:278
[    6.522263]   hash matches device ttyy6
[    6.522358]   hash matches device tty15
[    6.522389] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.522395] EDD information not available.
[    6.522634] Freeing unused kernel memory: 368k freed
[    6.525666] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    6.617845] vesafb: framebuffer at 0xe0000000, mapped to 0xf0880000, using 4608k, total 32704k
[    6.617861] vesafb: mode is 1024x768x24, linelength=3072, pages=13
[    6.617867] vesafb: protected mode interface info at c000:570c
[    6.617872] vesafb: pmi: set display start = c00c57a0, set palette = c00c57ec
[    6.617877] vesafb: pmi: ports = 3010 3016 3054 3038 303c 305c 3000 3004 30b0 30b2 30b4 
[    6.617889] vesafb: scrolling: redraw
[    6.617894] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    6.618014] Console: switching to colour frame buffer device 128x48
[    6.663342] fb0: VESA VGA frame buffer device
[    6.808502] fuse init (API version 7.9)
[    6.830992] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    6.831535] ACPI: Processor [CPU] (supports 8 throttling states)
[    6.834694] ACPI: Thermal Zone [THM0] (32 C)
[    7.557838] usbcore: registered new interface driver usbfs
[    7.558341] usbcore: registered new interface driver hub
[    7.587170] usbcore: registered new device driver usb
[    7.643824] SCSI subsystem initialized
[    7.657547] USB Universal Host Controller Interface driver v3.0
[    7.658138] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    7.658911] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    7.658916] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    7.659769] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    7.660418] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    7.661061] usb usb1: configuration #1 chosen from 1 choice
[    7.677844] hub 1-0:1.0: USB hub found
[    7.694892] hub 1-0:1.0: 2 ports detected
[    7.781544] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    7.798758] Copyright (c) 1999-2006 Intel Corporation.
[    7.816552] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    7.834016] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    7.851967] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    7.851972] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    7.870035] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    7.888529] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    7.906958] usb usb2: configuration #1 chosen from 1 choice
[    7.925302] hub 2-0:1.0: USB hub found
[    7.943867] hub 2-0:1.0: 2 ports detected
[    7.989484] libata version 3.00 loaded.
[    8.081991] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    8.100007] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    8.118181] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    8.118185] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.136505] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    8.154390] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    8.172138] usb usb3: configuration #1 chosen from 1 choice
[    8.189755] hub 3-0:1.0: USB hub found
[    8.207131] hub 3-0:1.0: 2 ports detected
[    8.253515] Floppy drive(s): fd0 is 1.44M
[    8.292457] FDC 0 is a National Semiconductor PC87306
[    8.326123] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    8.343366] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    8.360917] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    8.360922] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    8.378317] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    8.399760] ehci_hcd 0000:00:1d.7: debug port 1
[    8.417121] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    8.417129] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    8.453395] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    8.471014] usb usb4: configuration #1 chosen from 1 choice
[    8.488706] hub 4-0:1.0: USB hub found
[    8.506028] hub 4-0:1.0: 6 ports detected
[    8.633647] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    8.904185] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0d:60:ce:a2:c6
[    8.958476] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    8.976864] ata_piix 0000:00:1f.1: version 2.12
[    8.976882] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    8.995383] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    9.014462] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    9.015232] scsi0 : ata_piix
[    9.034920] scsi1 : ata_piix
[    9.054553] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    9.073798] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    9.253781] ata1.00: ATA-7: Hitachi HTS541680J9AT00, SB2OA70H, max UDMA/100
[    9.272824] ata1.00: 156301488 sectors, multi 16: LBA48 
[    9.305696] ata1.00: configured for UDMA/100
[    9.657575] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R9012, 1121, max UDMA/33
[    9.793175] Clocksource tsc unstable (delta = -1234713778 ns)
[    9.813167] Time: acpi_pm clocksource has been installed.
[    9.838285] ata2.00: configured for UDMA/33
[    9.856970] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    9.880687] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R9012 1121 PQ: 0 ANSI: 5
[    9.921163] Driver 'sd' needs updating - please use bus_type methods
[    9.940566] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    9.962086] sd 0:0:0:0: [sda] Write Protect is off
[    9.981013] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.984598] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.008959] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   10.028555] Driver 'sr' needs updating - please use bus_type methods
[   10.048010] sd 0:0:0:0: [sda] Write Protect is off
[   10.067133] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.076573] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.104528]  sda: sda1 sda2 < sda5 > sda3
[   10.540788] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.567637] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   10.587111] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   10.616673] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   10.635841] Uniform CD-ROM driver Revision: 3.20
[   10.654932] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   11.130772] Attempting manual resume
[   11.150672] swsusp: Resume From Partition 8:5
[   11.150674] PM: Checking swsusp image.
[   11.150842] PM: Resume from disk failed.
[   11.240020] kjournald starting.  Commit interval 5 seconds
[   11.259714] EXT3-fs: mounted filesystem with ordered data mode.
[   19.592086] Linux agpgart interface v0.102
[   19.688170] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.760685] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.824655] agpgart: Detected an Intel 855PM Chipset.
[   19.992712] iTCO_vendor_support: vendor-support=0
[   20.040069] agpgart: AGP aperture is 256M @ 0xd0000000
[   20.131990] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   20.156076] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.232023] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.595892] intel_rng: FWH not detected
[   20.660521] input: Power Button (FF) as /devices/virtual/input/input2
[   20.699860] ACPI: Power Button (FF) [PWRF]
[   20.718064] input: Lid Switch as /devices/virtual/input/input3
[   20.739951] ACPI: Lid Switch [LID]
[   20.757829] input: Sleep Button (CM) as /devices/virtual/input/input4
[   20.815843] ACPI: Sleep Button (CM) [SLPB]
[   22.628099] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/LNXVIDEO:00/input/input5
[   22.675513] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   23.079550] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
[   23.098306] Yenta: Using INTVAL to route CSC interrupts to PCI
[   23.116936] Yenta: Routing CardBus interrupts to PCI
[   23.135238] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
[   23.276440] ath_hal: module license 'Proprietary' taints kernel.
[   23.431939] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   23.450967] Socket status: 30000086
[   23.469673] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   23.507388] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   23.531357] cs: IO port probe 0x4000-0x8fff: clean.
[   23.551905] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   23.687328] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   23.767013] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0552]
[   23.785715] Yenta: Using INTVAL to route CSC interrupts to PCI
[   23.804383] Yenta: Routing CardBus interrupts to PCI
[   23.823045] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21b22, devctl 0x64
[   23.889128] wlan: 0.9.4
[   23.944099] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   24.047416] ath_pci: 0.9.4
[   24.099834] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   24.119035] Socket status: 30000086
[   24.138109] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   24.195238] cs: IO port probe 0x4000-0x8fff: clean.
[   24.215980] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   24.309410] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   24.364023] ACPI: AC Adapter [AC] (on-line)
[   24.436247] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   24.919741] ACPI: Battery Slot [BAT0] (battery present)
[   25.446537] parport_pc 00:0b: reported by Plug and Play ACPI
[   25.467252] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   25.556560] irda_init()
[   25.556580] NET: Registered protocol family 23
[   25.615062] Non-volatile memory driver v1.2
[   25.707293] ath_rate_sample: 1.2 (0.9.4)
[   25.728460] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   25.749398] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   25.770062] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   25.791133] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   25.811968] wifi0: mac 5.6 phy 4.1 5 GHz radio 1.7 2 GHz radio 2.3
[   25.832731] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   25.853337] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   25.873551] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   25.893381] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   25.912855] wifi0: Use hw queue 8 for CAB traffic
[   25.932060] wifi0: Use hw queue 9 for beacons
[   25.989705] wifi0: Atheros 5212: mem=0xc0210000, irq=11
[   26.012391] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   26.031371] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   26.513785] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   26.532503] serio: Synaptics pass-through port at isa0060/serio1/input0
[   26.588868] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   26.634600] nsc-ircc 00:0c: activated
[   26.653564] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   26.653724] nsc-ircc, chip->init
[   26.672342] nsc-ircc, Found chip at base=0x02e
[   26.690809] nsc-ircc, driver loaded (Dag Brattli)
[   26.709191] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   26.727540] thinkpad_acpi: http://ibm-acpi.sf.net/
[   26.745728] thinkpad_acpi: ThinkPad BIOS 1RETC6WW (3.05a), EC 1RHT68WW-3.01a
[   26.763918] thinkpad_acpi: IBM ThinkPad T41 
[   26.785257] IrDA: Registered device irda0
[   26.802830] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   26.830018] thinkpad_acpi: another device driver is already handling bay events
[   26.848291] thinkpad_acpi: disabling subdriver bay
[   26.878737] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
[   26.954821] intel8x0_measure_ac97_clock: measured 55504 usecs
[   26.973193] intel8x0: clocking to 48000
[   28.015485] cs: IO port probe 0x100-0x3af: clean.
[   28.034608] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   28.053078] cs: IO port probe 0x820-0x8ff: clean.
[   28.071961] cs: IO port probe 0x100-0x3af: clean.
[   28.090519] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   28.108460] cs: IO port probe 0x820-0x8ff: clean.
[   28.125976] cs: IO port probe 0xc00-0xcf7: clean.
[   28.143129] cs: IO port probe 0xc00-0xcf7: clean.
[   28.160347] cs: IO port probe 0xa00-0xaff: clean.
[   28.177166] cs: IO port probe 0xa00-0xaff: clean.
[   28.625776] lp0: using parport0 (interrupt-driven).
[   28.737130] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
[   29.173316] EXT3 FS on sda1, internal journal
[   29.745713] kjournald starting.  Commit interval 5 seconds
[   29.745933] EXT3 FS on sda3, internal journal
[   29.745938] EXT3-fs: mounted filesystem with ordered data mode.
[   30.444922] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by Cclips on 2008-10-05
Here is the syslog of the first thing after a reboot, any anomalies? 


```
Oct  5 13:39:28 Nostromo syslogd 1.5.0#1ubuntu1: restart.
Oct  5 13:39:28 Nostromo anacron[7064]: Job `cron.daily' terminated
Oct  5 13:39:28 Nostromo anacron[7064]: Job `cron.monthly' started
Oct  5 13:39:28 Nostromo anacron[8110]: Updated timestamp for job `cron.monthly' to 2008-10-05
Oct  5 13:41:53 Nostromo kernel: [  312.064225] NET: Registered protocol family 10
Oct  5 13:41:53 Nostromo kernel: [  312.064735] lo: Disabled Privacy Extensions
Oct  5 13:41:53 Nostromo kernel: [  312.065543] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  5 13:41:53 Nostromo kernel: [  312.066444] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Updating allowed wireless network lists. 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct  5 13:42:02 Nostromo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Will activate connection. 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Device eth1 activation scheduled... 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1) started... 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1/wireless): access point  is encrypted, but NO valid key exists.  New key needed. 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1) New wireless user key requested for network. 
Oct  5 13:42:02 Nostromo NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct  5 13:42:03 Nostromo kernel: [  320.686625] CPU0 attaching NULL sched-domain.
Oct  5 13:42:03 Nostromo kernel: [  320.686632] CPU1 attaching NULL sched-domain.
Oct  5 13:42:03 Nostromo kernel: [  320.701764] CPU0 attaching sched-domain:
Oct  5 13:42:03 Nostromo kernel: [  320.701771]  domain 0: span 03
Oct  5 13:42:03 Nostromo kernel: [  320.701774]   groups: 01 02
Oct  5 13:42:03 Nostromo kernel: [  320.701779] CPU1 attaching sched-domain:
Oct  5 13:42:03 Nostromo kernel: [  320.701781]  domain 0: span 03
Oct  5 13:42:03 Nostromo kernel: [  320.701783]   groups: 02 01
Oct  5 13:44:55 Nostromo anacron[7064]: Job `cron.monthly' terminated
Oct  5 13:44:55 Nostromo anacron[7064]: Normal exit (2 jobs run)
```

---

### Post by Cclips on 2008-10-08
New revelation, it also pauses if I log out/log in again...thoughts?

---

### Post by lavinog on 2008-10-10
Do you have any network shares?
I had a similar problem a long time ago where nautilus was trying to connect to a network share that didn't exist any more.

---

### Post by Cclips on 2008-10-13
> **lavinog said:**
> Do you have any network shares?
I had a similar problem a long time ago where nautilus was trying to connect to a network share that didn't exist any more.

Possibly, is there a command to check them?

I think it has more to do with GDM than the actual linux boot up.

---

### Post by lavinog on 2008-10-13
> **Cclips said:**
> Possibly, is there a command to check them?

I think it has more to do with GDM than the actual linux boot up.

Here is my old thread about my issue:
[http://ubuntuforums.org/showthread.php?t=571208]("http://ubuntuforums.org/showthread.php?t=571208")

Basically I went to the terminal and killed nautilus. Then i restarted nautilus and observed the long delay.

---

### Post by Cclips on 2008-10-13
Did that solve your problem at all? If I log in and out I can observe the delay, but it doesn't give me a solution to the issue at all :(

---

### Post by Cclips on 2008-10-14
I uninstalled Samba thinking that it might be causing the issue. I had installed it a while back on the laptop but not the Desktop which would account for it being a laptop only issue, but alas the problem still remains. 

Any other thoughts?

---

### Post by lavinog on 2008-10-14
did you try killing nautilus and restarting it to see if it causes the delay again?
```
pkill nautilus
```
I think it will restart automatically on its own.

---

### Post by Cclips on 2008-10-14
No dice, restarted just fine with no pause what so ever.

---

### Post by Cclips on 2008-10-14
Think I found the culprit.

```
Oct 14 20:04:53 Nostromo kernel: [   29.787165] [drm] Initialized drm 1.1.0 20060810
Oct 14 20:04:53 Nostromo kernel: [   29.790074] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 14 20:04:53 Nostromo kernel: [   29.790085] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct 14 20:04:53 Nostromo kernel: [   29.790151] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 14 20:04:53 Nostromo NetworkManager: <debug> [1224032693.619183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a02_drm_i915_card0'). 
Oct 14 20:07:05 Nostromo kernel: [  153.009843] NET: Registered protocol family 10
Oct 14 20:07:05 Nostromo kernel: [  153.010330] lo: Disabled Privacy Extensions
Oct 14 20:07:05 Nostromo kernel: [  153.011131] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 14 20:07:05 Nostromo kernel: [  153.012026] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

Notice the huge jump in terms of the seconds.....thoughts?

---

### Post by Cclips on 2008-10-14
Tried disabling HAL and the HAL service, but no change.

---

### Post by Cclips on 2008-10-17
should I just wait until 8.10 and see if that fixes the issue?

---

### Post by Cclips on 2008-10-19
replaced network manager with WICD thinking it might be the wireless issue, but still no change.

---

