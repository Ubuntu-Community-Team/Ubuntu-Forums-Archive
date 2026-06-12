---
title: "Having so much trouble"
date: 2009-05-21
forum: General Help
---

### Post by Gurboura on 2009-05-21
I recently formatted, got rid of Windows and installed Ubuntu 9.04, I've been wanting to play around with Linux for awhile, knowing how stable it is, but I'm starting to regret my decision.

It seems I've been having so much trouble since installing Ubuntu. Sound stops working, mic randomly stops working, programs randomly crashing, resolution changes sometimes and I have to reboot.

Anyone know what could be causing this? Possibly a bad install or something? Or is it just 9.04 being such a new release some bugs are still being fixed?

---

### Post by celticbhoy on 2009-05-21
You will need to post a hardware list for your PC.

---

### Post by Gurboura on 2009-05-21
> **celticbhoy said:**
> You will need to post a hardware list for your PC.
MSI K7N Delta 2
nForce2 Chipset
AMD Athlon 2800+
512MB of Memory
6600GT 128MB Videocard
100GB IDE WD HD (Ubuntu installed on)
160GB SATA WD HD

---

### Post by stefangr1 on 2009-05-21
The Ubuntu CD has an option to check the memory: memtest. You might want to try it out, as random crashes etc. are often caused by memory failure. Linux is a little more picky on hardware than windows. An install from a bad cd is another possibility, maybe you can also have the cd check itself.

---

### Post by rehilliard on 2009-05-21
for what it's worth...you might consider backing down a version.

i installed 9.04 and lost sound. had to switch to oss to get it to work both locally (mp3s) and to get flash to work (youtube). i'm no expert, but i didn't have this problem on 8.10.

also, i have a usb turntable that i try to use audacity with. the turntable is "detected" as a mic input. when i try and listen to output from the turntable it'll start playing and then stop after a few seconds. that kind of thing. (on the same machine, audacity works FINE in vista...i'm sorry to say). I think it all boils down to the audio drivers...IMO.

you could try plowing thru this lengthy posting on audio problems:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

as for the other goofy problems...somebody out here is bound to help guide you...

---

### Post by Therion on 2009-05-21
Wow... That's a pretty wonky sounding install.  If I had to bet I'd say your install media was probably less than stellar.  How fast did you burn your install media?  I always suggest 8x for burning an install CD and 2x if it's a DVD.  

I also suggest downloading the .iso file using a Torrent to help ensure the file you're going to burn, and subsequently rely on, is also rock solid.  I've cleared up waaay to many borked installs using a known-good install CD; but *getting* a really solid install CD can take some effort.  Has to be done though.

---

### Post by Gurboura on 2009-05-21
> **stefangr1 said:**
> The Ubuntu CD has an option to check the memory: memtest. You might want to try it out, as random crashes etc. are often caused by memory failure. Linux is a little more picky on hardware than windows. An install from a bad cd is another possibility, maybe you can also have the cd check itself.
I thought it could have been memory as well and did memtest86 and it came out fine. I even tried switching out the memory with another computer I had laying around just to double check and still had the same problems.

> **rehilliard said:**
> for what it's worth...you might consider backing down a version.

i installed 9.04 and lost sound. had to switch to oss to get it to work both locally (mp3s) and to get flash to work (youtube). i'm no expert, but i didn't have this problem on 8.10.

also, i have a usb turntable that i try to use audacity with. the turntable is "detected" as a mic input. when i try and listen to output from the turntable it'll start playing and then stop after a few seconds. that kind of thing. (on the same machine, audacity works FINE in vista...i'm sorry to say). I think it all boils down to the audio drivers...IMO.

you could try plowing thru this lengthy posting on audio problems:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

as for the other goofy problems...somebody out here is bound to help guide you...
Weird, I never had the problem of losing sound after a few seconds, I either have it, or don't, losing it after a few seconds would drive me completely crazy :lol:

I might download 8.10 if it comes down to it.

> **Therion said:**
> Wow... That's a pretty wonky sounding install.  If I had to bet I'd say your install media was probably less than stellar.  How fast did you burn your install media?  I always suggest 8x for burning an install CD and 2x if it's a DVD.  

I also suggest downloading the .iso file using a Torrent to help ensure the file you're going to burn, and subsequently rely on, is also rock solid.  I've cleared up waaay to many borked installs using a known-good install CD; but *getting* a really solid install CD can take some effort.  Has to be done though.
Checked the ISOs HASH after the Torrent was done and burned the CD at 4x like the guide said,
  The install did crash several times, alot of times just crashed at the menu to pick install, check CD, ect. 


I thought all these problems were unsual, 3-4 years ago I messed around with SuSE and didn't have these issues, so I was starting to figure if maybe it was a bad install or something.



I appreciate everyone's help and input.

---

### Post by albinootje on 2009-05-21
> **Gurboura said:**
>  Anyone know what could be causing this?

Please post the output of the following :
```

dmesg
lspci

```
It's possible that your installation needs some special boot parameters, the output of "dmesg" is important for that.

---

### Post by clhsharky on 2009-05-21
I have that board also, but with Athlon 2500, 1 gig ram, 5200 Nvida, I now use it for file server with 8.04 because of legacy video card. Good board thou, hope you find fix.

---

### Post by Gurboura on 2009-05-21
> **albinootje said:**
> Please post the output of the following :
```

dmesg
lspci

```It's possible that your installation needs some special boot parameters, the output of "dmesg" is important for that.
[QUOTE=dmesg][    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  modified: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  modified: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 10000-16000
[    0.000000] RAMDISK: 1f8ae000 - 1ffdf91e
[    0.000000] ACPI: RSDP 000F7580, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 4E50 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF7F40, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 00000000 - 1fff0000
[    0.000000]   bootmap 00012000 - 00016000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [001f8ae000 - 001ffdf91e]          RAMDISK ==> [001f8ae000 - 001ffdf91e]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] found SMP MP-table at [c00f5b50] 000f5b50
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130943
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125968 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129919
[    0.000000] Kernel command line: root=UUID=27b186b7-30df-4e56-b231-f5a5735ad14b ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2074.892 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2620800 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 501404k/524224k available (4126k kernel code, 22192k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe07f0000 - 0xff3fe000   ( 492 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 4149.78 BogoMIPS (lpj=8299568)
[    0.004040] Security Framework initialized
[    0.004049] SELinux:  Disabled at boot.
[    0.004079] AppArmor: AppArmor initialized
[    0.004091] Mount-cache hash table entries: 512
[    0.004272] Initializing cgroup subsys ns
[    0.004277] Initializing cgroup subsys cpuacct
[    0.004279] Initializing cgroup subsys memory
[    0.004285] Initializing cgroup subsys freezer
[    0.004301] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004304] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004322] Checking 'hlt' instruction... OK.
[    0.020485] SMP alternatives: switching to UP code
[    0.168476] Freeing SMP alternatives: 18k freed
[    0.168483] ACPI: Core revision 20080926
[    0.170268] ACPI: Checking initramfs for custom DSDT
[    0.453995] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.493686] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[    0.496001] Brought up 1 CPUs
[    0.496001] Total of 1 processors activated (4149.78 BogoMIPS).
[    0.496001] CPU0 attaching NULL sched-domain.
[    0.496001] net_namespace: 776 bytes
[    0.496001] Booting paravirtualized kernel on bare hardware
[    0.496001] Time: 18:31:08  Date: 05/21/09
[    0.496001] regulator: core version 0.5
[    0.496001] NET: Registered protocol family 16
[    0.496001] EISA bus registered
[    0.496001] ACPI: bus type pci registered
[    0.525570] PCI: PCI BIOS revision 2.10 entry at 0xfbe50, last bus=2
[    0.525573] PCI: Using configuration type 1 for base access
[    0.527453] ACPI: EC: Look up EC in DSDT
[    0.535194] ACPI: Interpreter enabled
[    0.535200] ACPI: (supports S0 S1 S4 S5)
[    0.535220] ACPI: Using IOAPIC for interrupt routing
[    0.544445] ACPI: No dock devices found.
[    0.544458] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.544509] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.544705] pci 0000:00:01.1: reg 10 io port: [0xe400-0xe41f]
[    0.544736] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.544741] pci 0000:00:01.1: PME# disabled
[    0.544771] pci 0000:00:02.0: reg 10 32bit mmio: [0xe7001000-0xe7001fff]
[    0.544799] pci 0000:00:02.0: supports D1 D2
[    0.544801] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544805] pci 0000:00:02.0: PME# disabled
[    0.544830] pci 0000:00:02.1: reg 10 32bit mmio: [0xe7002000-0xe7002fff]
[    0.544859] pci 0000:00:02.1: supports D1 D2
[    0.544861] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544865] pci 0000:00:02.1: PME# disabled
[    0.544896] pci 0000:00:02.2: reg 10 32bit mmio: [0xe7003000-0xe70030ff]
[    0.544927] pci 0000:00:02.2: supports D1 D2
[    0.544929] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.544933] pci 0000:00:02.2: PME# disabled
[    0.544965] pci 0000:00:04.0: reg 10 32bit mmio: [0xe7000000-0xe7000fff]
[    0.544971] pci 0000:00:04.0: reg 14 io port: [0xe000-0xe007]
[    0.544996] pci 0000:00:04.0: supports D1 D2
[    0.544998] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.545002] pci 0000:00:04.0: PME# disabled
[    0.545027] pci 0000:00:06.0: reg 10 io port: [0xd800-0xd8ff]
[    0.545033] pci 0000:00:06.0: reg 14 io port: [0xdc00-0xdc7f]
[    0.545039] pci 0000:00:06.0: reg 18 32bit mmio: [0xe7004000-0xe7004fff]
[    0.545061] pci 0000:00:06.0: supports D1 D2
[    0.545120] pci 0000:00:09.0: reg 20 io port: [0xf000-0xf00f]
[    0.545161] pci 0000:00:0b.0: reg 10 io port: [0x9f0-0x9f7]
[    0.545167] pci 0000:00:0b.0: reg 14 io port: [0xbf0-0xbf3]
[    0.545173] pci 0000:00:0b.0: reg 18 io port: [0x970-0x977]
[    0.545179] pci 0000:00:0b.0: reg 1c io port: [0xb70-0xb73]
[    0.545185] pci 0000:00:0b.0: reg 20 io port: [0xd000-0xd00f]
[    0.545190] pci 0000:00:0b.0: reg 24 io port: [0xd400-0xd47f]
[    0.545327] pci 0000:01:00.0: reg 10 32bit mmio: [0xe4000000-0xe4ffffff]
[    0.545335] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.545342] pci 0000:01:00.0: reg 18 32bit mmio: [0xe5000000-0xe5ffffff]
[    0.545363] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.545409] pci 0000:00:1e.0: bridge 32bit mmio: [0xe4000000-0xe6ffffff]
[    0.545414] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.545424] bus 00 -> node 0
[    0.545432] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.545660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.546023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.609287] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.609514] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.609734] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.609954] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.610173] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.610395] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.610619] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.610840] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.611059] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.611281] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.611502] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.611724] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.611947] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.612176] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.612403] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.612623] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.612855] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.613046] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
[    0.613217] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[    0.613388] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[    0.613558] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[    0.613729] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.613980] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21) *0
[    0.614225] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21) *0
[    0.614468] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21) *0
[    0.614710] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21) *0, disabled.
[    0.614953] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21) *0
[    0.615194] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21) *0, disabled.
[    0.615368] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[    0.615610] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21) *0
[    0.615852] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21) *0, disabled.
[    0.616105] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21) *0, disabled.
[    0.616355] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21) *0, disabled.
[    0.616610] ACPI: PCI Interrupt Link [APSI] (IRQs 22) *0
[    0.616747] ACPI: Power Resource [ISAV] (on)
[    0.616828] ACPI: WMI: Mapper loaded
[    0.617081] SCSI subsystem initialized
[    0.617148] libata version 3.00 loaded.
[    0.617220] usbcore: registered new interface driver usbfs
[    0.617241] usbcore: registered new interface driver hub
[    0.617277] usbcore: registered new device driver usb
[    0.617421] PCI: Using ACPI for IRQ routing
[    0.617522] Bluetooth: Core ver 2.13
[    0.617522] NET: Registered protocol family 31
[    0.617522] Bluetooth: HCI device and connection manager initialized
[    0.617522] Bluetooth: HCI socket layer initialized
[    0.617522] NET: Registered protocol family 8
[    0.617522] NET: Registered protocol family 20
[    0.617522] NetLabel: Initializing
[    0.617522] NetLabel:  domain hash size = 128
[    0.617522] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.617522] NetLabel:  unlabeled traffic allowed by default
[    0.617522] AppArmor: AppArmor Filesystem Enabled
[    0.617522] pnp: PnP ACPI init
[    0.617522] ACPI: bus type pnp registered
[    0.623342] pnp: PnP ACPI: found 13 devices
[    0.623345] ACPI: ACPI bus type pnp unregistered
[    0.623349] PnPBIOS: Disabled by ACPI PNP
[    0.623360] system 00:00: ioport range 0x4000-0x407f has been reserved
[    0.623363] system 00:00: ioport range 0x4080-0x40ff has been reserved
[    0.623366] system 00:00: ioport range 0x4400-0x447f has been reserved
[    0.623369] system 00:00: ioport range 0x4480-0x44ff has been reserved
[    0.623372] system 00:00: ioport range 0x4200-0x427f has been reserved
[    0.623374] system 00:00: ioport range 0x4280-0x42ff has been reserved
[    0.623380] system 00:01: ioport range 0x5000-0x503f has been reserved
[    0.623382] system 00:01: ioport range 0x5100-0x513f has been reserved
[    0.623388] system 00:02: iomem range 0xd5800-0xd7fff has been reserved
[    0.623391] system 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[    0.623394] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[    0.623397] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[    0.623400] system 00:02: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    0.623402] system 00:02: iomem range 0xffff0000-0xffffffff has been reserved
[    0.623405] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    0.623408] system 00:02: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.623411] system 00:02: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.623414] system 00:02: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.623419] system 00:04: ioport range 0xb78-0xb7b has been reserved
[    0.623422] system 00:04: ioport range 0xf78-0xf7b has been reserved
[    0.623425] system 00:04: ioport range 0xa78-0xa7b has been reserved
[    0.623427] system 00:04: ioport range 0xe78-0xe7b has been reserved
[    0.623430] system 00:04: ioport range 0xbbc-0xbbf has been reserved
[    0.623432] system 00:04: ioport range 0xfbc-0xfbf has been reserved
[    0.623435] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.623438] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.658158] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.658161] pci 0000:00:08.0:   IO window: disabled
[    0.658166] pci 0000:00:08.0:   MEM window: disabled
[    0.658170] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.658179] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.658181] pci 0000:00:1e.0:   IO window: disabled
[    0.658186] pci 0000:00:1e.0:   MEM window: 0xe4000000-0xe6ffffff
[    0.658190] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.658204] pci 0000:00:08.0: setting latency timer to 64
[    0.658211] bus: 00 index 0 io port: [0x00-0xffff]
[    0.658214] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.658216] bus: 02 index 0 mmio: [0x0-0x0]
[    0.658218] bus: 02 index 1 mmio: [0x0-0x0]
[    0.658219] bus: 02 index 2 mmio: [0x0-0x0]
[    0.658221] bus: 02 index 3 mmio: [0x0-0x0]
[    0.658223] bus: 01 index 0 mmio: [0x0-0x0]
[    0.658225] bus: 01 index 1 mmio: [0xe4000000-0xe6ffffff]
[    0.658227] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.658229] bus: 01 index 3 mmio: [0x0-0x0]
[    0.658241] NET: Registered protocol family 2
[    0.658360] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.658635] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.658834] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.659014] TCP: Hash tables configured (established 16384 bind 16384)
[    0.659017] TCP reno registered
[    0.659094] NET: Registered protocol family 1
[    0.659257] checking if image is initramfs... it is
[    1.160038] Switched to high resolution mode on CPU 0
[    1.272102] Freeing initrd memory: 7366k freed
[    1.272241] cpufreq: Detected nForce2 chipset revision C1
[    1.272243] cpufreq: FSB changing is maybe unstable and can lead to crashes and data loss.
[    1.272258] cpufreq: FSB currently at 166 MHz, FID 12.5
[    1.272282] Marking TSC unstable due to cpufreq changes
[    1.274238] audit: initializing netlink socket (disabled)
[    1.274263] type=2000 audit(1242930668.272:1): initialized
[    1.281797] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.283179] VFS: Disk quotas dquot_6.5.1
[    1.283238] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.283914] fuse init (API version 7.10)
[    1.284026] msgmni has been set to 994
[    1.284239] alg: No test for stdrng (krng)
[    1.284254] io scheduler noop registered
[    1.284256] io scheduler anticipatory registered
[    1.284258] io scheduler deadline registered
[    1.284274] io scheduler cfq registered (default)
[    1.316102] pci 0000:01:00.0: Boot video device
[    1.322931] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.322941] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.323125] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.323129] ACPI: Power Button (FF) [PWRF]
[    1.323185] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.323188] ACPI: Power Button (CM) [PWRB]
[    1.323768] processor ACPI_CPU:00: registered as cooling_device0
[    1.327891] isapnp: Scanning for PnP cards...
[    1.681897] isapnp: No Plug & Play device found
[    1.683139] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.683249] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.683589] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.684397] brd: module loaded
[    1.684748] loop: module loaded
[    1.684827] Fixed MDIO Bus: probed
[    1.684834] PPP generic driver version 2.4.2
[    1.684902] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.684929] Driver 'sd' needs updating - please use bus_type methods
[    1.684939] Driver 'sr' needs updating - please use bus_type methods
[    1.685110] sata_nv 0000:00:0b.0: version 3.5
[    1.685611] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[    1.685625] sata_nv 0000:00:0b.0: PCI INT A -> Link[APSI] -> GSI 22 (level, high) -> IRQ 22
[    1.685689] sata_nv 0000:00:0b.0: setting latency timer to 64
[    1.685828] scsi0 : sata_nv
[    1.685956] scsi1 : sata_nv
[    1.686687] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd000 irq 22
[    1.686691] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd008 irq 22
[    2.464033] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.472341] ata2.00: ATA-7: WDC WD1600JS-00NCB1, 10.02E02, max UDMA/133
[    2.472344] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.480333] ata2.00: configured for UDMA/133
[    2.480485] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600JS-00N 10.0 PQ: 0 ANSI: 5
[    2.480602] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.480625] sd 1:0:0:0: [sda] Write Protect is off
[    2.480628] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.480660] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.480744] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.480761] sd 1:0:0:0: [sda] Write Protect is off
[    2.480764] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.480794] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.480800]  sda: sda1
[    2.490344] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.490409] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.490502] pata_amd 0000:00:09.0: version 0.3.10
[    2.490571] pata_amd 0000:00:09.0: power state changed by ACPI to D0
[    2.490633] pata_amd 0000:00:09.0: setting latency timer to 64
[    2.490737] scsi2 : pata_amd
[    2.490809] scsi3 : pata_amd
[    2.491665] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.491668] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.652460] ata3.00: ATAPI: MATSHITADVD-RAM SW-9585, B102, max UDMA/66
[    2.652485] ata3: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc500c600) ACPI=0x1f01f (30:600:0x13)
[    2.668423] ata3.00: configured for UDMA/66
[    2.833205] ata4.00: ATA-5: WDC WD1000BB-00CAA0, 16.06V16, max UDMA/100
[    2.833208] ata4.00: 195371568 sectors, multi 16: LBA 
[    2.833229] ata4: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc500c600) ACPI=0x3f01f (20:600:0x13)
[    2.849167] ata4.00: configured for UDMA/100
[    2.850710] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM SW-9585  B102 PQ: 0 ANSI: 5
[    2.854758] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.854762] Uniform CD-ROM driver Revision: 3.20
[    2.854879] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.854923] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.854989] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1000BB-00C 16.0 PQ: 0 ANSI: 5
[    2.855102] sd 3:0:0:0: [sdb] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.855122] sd 3:0:0:0: [sdb] Write Protect is off
[    2.855125] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.855156] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.855218] sd 3:0:0:0: [sdb] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.855236] sd 3:0:0:0: [sdb] Write Protect is off
[    2.855238] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.855268] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.855272]  sdb: sdb1 sdb2 < sdb5 >
[    2.895469] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.895511] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.895971] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.896412] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    2.896424] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 21 (level, high) -> IRQ 21
[    2.896459] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    2.896462] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    2.896542] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    2.896583] ehci_hcd 0000:00:02.2: debug port 1
[    2.896588] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    2.896611] ehci_hcd 0000:00:02.2: irq 21, io mem 0xe7003000
[    2.908019] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    2.908105] usb usb1: configuration #1 chosen from 1 choice
[    2.908136] hub 1-0:1.0: USB hub found
[    2.908149] hub 1-0:1.0: 8 ports detected
[    2.908263] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.908611] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    2.908617] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, high) -> IRQ 20
[    2.908628] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.908632] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.908677] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.908701] ohci_hcd 0000:00:02.0: irq 20, io mem 0xe7001000
[    2.966055] usb usb2: configuration #1 chosen from 1 choice
[    2.966086] hub 2-0:1.0: USB hub found
[    2.966099] hub 2-0:1.0: 4 ports detected
[    2.966507] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[    2.966511] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 21 (level, high) -> IRQ 21
[    2.966523] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    2.966526] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    2.966570] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    2.966585] ohci_hcd 0000:00:02.1: irq 21, io mem 0xe7002000
[    3.022058] usb usb3: configuration #1 chosen from 1 choice
[    3.022084] hub 3-0:1.0: USB hub found
[    3.022096] hub 3-0:1.0: 4 ports detected
[    3.022175] uhci_hcd: USB Universal Host Controller Interface driver
[    3.022282] usbcore: registered new interface driver libusual
[    3.022319] usbcore: registered new interface driver usbserial
[    3.022330] USB Serial support registered for generic
[    3.022343] usbcore: registered new interface driver usbserial_generic
[    3.022346] usbserial: USB Serial Driver core
[    3.022392] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    3.022395] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    3.022737] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.022866] mice: PS/2 mouse device common for all mice
[    3.023027] rtc_cmos 00:06: RTC can wake from S4
[    3.023074] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.023101] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    3.023168] device-mapper: uevent: version 1.0.3
[    3.023312] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.023377] device-mapper: multipath: version 1.0.5 loaded
[    3.023380] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.023465] EISA: Probing bus 0 at eisa.0
[    3.023489] Cannot allocate resource for EISA slot 4
[    3.023492] Cannot allocate resource for EISA slot 5
[    3.023507] EISA: Detected 0 cards.
[    3.023558] cpuidle: using governor ladder
[    3.023560] cpuidle: using governor menu
[    3.024139] TCP cubic registered
[    3.024230] NET: Registered protocol family 10
[    3.024670] lo: Disabled Privacy Extensions
[    3.024999] NET: Registered protocol family 17
[    3.025017] Bluetooth: L2CAP ver 2.11
[    3.025019] Bluetooth: L2CAP socket layer initialized
[    3.025022] Bluetooth: SCO (Voice Link) ver 0.6
[    3.025024] Bluetooth: SCO socket layer initialized
[    3.025056] Bluetooth: RFCOMM socket layer initialized
[    3.025065] Bluetooth: RFCOMM TTY layer initialized
[    3.025067] Bluetooth: RFCOMM ver 1.10
[    3.025090] powernow-k8: Processor cpuid 6a0 not supported
[    3.025110] Using IPI No-Shortcut mode
[    3.025206] registered taskstats version 1
[    3.025327]   Magic number: 9:957:544
[    3.025346] scsi_generic sg0: hash matches
[    3.025462] rtc_cmos 00:06: setting system clock to 2009-05-21 18:31:10 UTC (1242930670)
[    3.025465] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.025467] EDD information not available.
[    3.026150] Freeing unused kernel memory: 532k freed
[    3.026271] Write protecting the kernel text: 4128k
[    3.026311] Write protecting the kernel read-only data: 1532k
[    3.068344] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.336048] usb 1-7: new high speed USB device using ehci_hcd and address 3
[    3.477344] usb 1-7: configuration #1 chosen from 1 choice
[    3.620276] Floppy drive(s): fd0 is 1.44M
[    3.639945] FDC 0 is a post-1991 82077
[    3.710605] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.711069] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    3.711076] forcedeth 0000:00:04.0: PCI INT A -> Link[APCH] -> GSI 20 (level, high) -> IRQ 20
[    3.711083] forcedeth 0000:00:04.0: setting latency timer to 64
[    3.711158] nv_probe: set workaround bit for reversed mac addr
[    3.820068] usb 3-3: new full speed USB device using ohci_hcd and address 2
[    4.110253] usb 3-3: configuration #1 chosen from 1 choice
[    4.229016] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:11:09:5d:fd:0b
[    4.229022] forcedeth 0000:00:04.0: csum timirq lnktim desc-v2
[    4.360040] hub 3-0:1.0: unable to enumerate USB device on port 4
[    4.374323] PM: Starting manual resume from disk
[    4.374328] PM: Resume from partition 8:21
[    4.374330] PM: Checking hibernation image.
[    4.374493] PM: Resume from disk failed.
[    4.404659] EXT4-fs: barriers enabled
[    4.421364] kjournald2 starting.  Commit interval 5 seconds
[    4.421378] EXT4-fs: delayed allocation enabled
[    4.421380] EXT4-fs: file extents enabled
[    4.436280] EXT4-fs: mballoc enabled
[    4.436286] EXT4-fs: mounted filesystem with ordered data mode.
[    5.852022] usb 3-4: new low speed USB device using ohci_hcd and address 4
[    6.064247] usb 3-4: configuration #1 chosen from 1 choice
[    9.556132] udev: starting version 141
[    9.703133] Linux agpgart interface v0.103
[    9.724972] agpgart: Detected NVIDIA nForce2 chipset
[    9.730309] agpgart-nvidia 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[    9.749946] parport_pc 00:0b: reported by Plug and Play ACPI
[    9.750009] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.790065] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    9.790117] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[    9.830016] usbcore: registered new interface driver hiddev
[    9.836816] input: Darfon USB Mouse as /devices/pci0000:00/0000:00:02.1/usb3/3-4/3-4:1.0/input/input4
[    9.868295] generic-usb 0003:0D62:A100.0001: input,hidraw0: USB HID v1.10 Mouse [Darfon USB Mouse] on usb-0000:00:02.1-4/input0
[    9.868331] usbcore: registered new interface driver usbhid
[    9.868361] usbhid: v2.6:USB HID core driver
[   10.133216] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.256276] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.737921] nvidia: module license 'NVIDIA' taints kernel.
[   11.007279] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   11.007296] nvidia 0000:01:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   11.009477] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   11.038439] ppdev: user-space parallel port driver
[   11.156449] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[   11.156458] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 21 (level, high) -> IRQ 21
[   11.156542] Intel ICH 0000:00:06.0: setting latency timer to 64
[   11.480021] intel8x0_measure_ac97_clock: measured 54650 usecs
[   11.480026] intel8x0: clocking to 48000
[   11.640531] lp0: using parport0 (interrupt-driven).
[   11.771722] Adding 1485972k swap on /dev/sdb5.  Priority:-1 extents:1 across:1485972k
[   12.321928] EXT4 FS on sdb1, internal journal on sdb1:8
[   13.507817] type=1505 audit(1242930680.978:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1976
[   13.569948] type=1505 audit(1242930681.042:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1980
[   13.570224] type=1505 audit(1242930681.042:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1980
[   13.570316] type=1505 audit(1242930681.042:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1980
[   13.570386] type=1505 audit(1242930681.042:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1980
[   13.755677] type=1505 audit(1242930681.226:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1985
[   13.756103] type=1505 audit(1242930681.230:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1985
[   13.794001] type=1505 audit(1242930681.266:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1989
[   17.323221] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.323226] Bluetooth: BNEP filters: protocol multicast
[   17.469768] Bridge firewalling registered
[   19.903809] agpgart-nvidia 0000:00:00.0: AGP 3.0 bridge
[   19.903827] agpgart-nvidia 0000:00:00.0: putting AGP V3 device into 8x mode
[   19.903882] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   22.079440] Linux video capture interface: v2.00
[   22.096752] vloopback: Video4linux loopback driver v1.1.5
[   22.096876] vloopback: Loopback 0 registered, input: video1, output: video0
[   32.612015] eth0: no IPv6 routers present
[   68.729944] usb 1-7: USB disconnect, address 3
[   81.843555] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[   87.552026] usb 1-7: new high speed USB device using ehci_hcd and address 6
[   87.709182] usb 1-7: configuration #1 chosen from 1 choice
[/QUOTE]

[QUOTE=lspci]00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation MCP2A ISA bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP2A SMBus (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP2A USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation MCP2A USB Controller (rev a2)
00:04.0 Bridge: nVidia Corporation MCP2A Ethernet Controller (rev a3)
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP2A PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation MCP2A IDE (rev a3)
00:0b.0 IDE interface: nVidia Corporation nForce2 Serial ATA Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
[/QUOTE]

There you go. Thank you for the help.

---

### Post by albinootje on 2009-05-21
Thanks.
There's no mentioning of BIOS-bugs, and there's one hint in there, which might not be interesting to try, but still :

> 
[ 0.000000] Nvidia board detected. Ignoring ACPI timer override.
[ 0.000000] If you got timer trouble try acpi_use_timer_override


Okay, can you please boot with the "noapic nolapic" boot options, and test that ?

For more information about that see here :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Gurboura on 2009-05-21
I'll give that a try, just one question, I do the temporary boot options, and just add "noapic nolapic" at the end of the line?

Nevermind, found out how to do it on the page. I'll do that, what should I be looking for after I do this?

---

### Post by albinootje on 2009-05-21
> **Gurboura said:**
> I'll do that, what should I be looking for after I do this?

Just test it, and see whether it improves things or not.

And can you, when your desktop is up and running, have this running in a terminal to see whether you get some errors popping up there :
```

tail -f /var/log/syslog

```

---

### Post by Gurboura on 2009-05-21
> **albinootje said:**
> Just test it, and see whether it improves things or not.

And can you, when your desktop is up and running, have this running in a terminal to see whether you get some errors popping up there :
```

tail -f /var/log/syslog

```
Definitely, I can do that. Let me do the boot options and I'll post when I get back booted.

---

### Post by albinootje on 2009-05-21
> **Therion said:**
>  I also suggest downloading the .iso file using a Torrent to help ensure the file you're going to burn, and subsequently rely on, is also rock solid.  I've cleared up waaay to many borked installs using a known-good install CD; but *getting* a really solid install CD can take some effort.  Has to be done though.

What are you trying to say ?! Downloading the iso from a http mirror or via torrent should be the same. :)

After downloading the iso checking the md5sum is also a good idea.

And, imho, people should use the official torrents, not from some obscure torrent site. 

For burning the iso, see here :
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

For the OP, you can also test drive with 8.04 and 8.10 cdroms using the live session ("Try without making changes"), and see how well that goes.

Another thing, for the OP, I wondered about, did you overclock your CPU ? Or are you using the default settings ?

---

### Post by Gurboura on 2009-05-21
> **albinootje said:**
>  For the OP, you can also test drive with 8.04 and 8.10 cdroms using the live session ("Try without making changes"), and see how well that goes.

Another thing, for the OP, I wondered about, did you overclock your CPU ? Or are you using the default settings ?
I'll try the 8.04 and 8.10, downloading both right now.

CPU is default settings.

---

### Post by ALIENDUDE5300 on 2009-05-21
> **Gurboura said:**
> MSI K7N Delta 2
nForce2 Chipset
AMD Athlon 2800+
512MB of Memory
6600GT 128MB Videocard
100GB IDE WD HD (Ubuntu installed on)
160GB SATA WD HD

Could you post a more comprehensive hardware list so we can try to figure out if it's a dependency/driver problem? Go to terminal and type ```
logsave hardware.txt sudo lshw
```, and then post the hardware.txt file here.

---

### Post by albinootje on 2009-05-21
> **ALIENDUDE5300 said:**
> ```
logsave hardware.txt sudo lshw
```, and then post the hardware.txt file here.

Okay, but let's make that the following :
```

logsave hardware.txt sudo lshw -sanitize

```
(See : lshw --help)

---

### Post by Gurboura on 2009-05-21
> **ALIENDUDE5300 said:**
> Could you post a more comprehensive hardware list so we can try to figure out if it's a dependency/driver problem? Go to terminal and type ```
logsave hardware.txt sudo lshw
```, and then post the hardware.txt file here.

> **albinootje said:**
> Okay, but let's make that the following :
```

logsave hardware.txt sudo lshw -sanitize

```(See : lshw --help)
Hardware.txt uploaded.

---

### Post by Gurboura on 2009-05-21
I think I'm going to format, SwiftFox just crashed on me 4 times in a row trying to open MySpace.

---

### Post by Gurboura on 2009-05-21
I'm going to try Opera, but if that doesn't fix it, 8.04 here I come.

---

### Post by Gurboura on 2009-05-21
Had to switch my devices in "Sound" to get sound again.

---

### Post by Gurboura on 2009-05-21
Just locked up on me again. Using Opera and Rhythmbox

---

### Post by Gurboura on 2009-05-22
New problem to add:
No other sound devices work, except OSS. Now I get NO sound from any programs at all, except when I do a "Play test sound". YouTube, Skype, none of those work.


I'm about to give up on Ubuntu. I'm having more problems than I did with Windows ](*,)

---

### Post by albinootje on 2009-05-22
> **Gurboura said:**
>  I'm about to give up on Ubuntu. I'm having more problems than I did with Windows ](*,)

Did you try 8.04 and/or 8.10 already ? If so, did you have the same problems ?

What problems did you have in MS-Windows ? Is it possible that your 
machine is causing the problems ?

Can you try "default settings" in the BIOS ?

---

### Post by Gurboura on 2009-05-22
> **albinootje said:**
> Did you try 8.04 and/or 8.10 already ? If so, did you have the same problems ?
Not yet. I downloaded both and burning them to CD now.


> **albinootje said:**
> What problems did you have in MS-Windows ?
Mouse stopped working. 

> **albinootje said:**
> Is it possible that your 
machine is causing the problems ?
Could be.

> **albinootje said:**
> Can you try "default settings" in the BIOS ?
I did.

---

