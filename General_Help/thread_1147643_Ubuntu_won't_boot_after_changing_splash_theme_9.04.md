---
title: "Ubuntu won't boot after changing splash theme 9.04"
date: 2009-05-03
forum: General Help
---

### Post by opivy522 on 2009-05-03
I tried to install a usplash theme in Ubuntu 9.04 following these directions 
[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)
and when i rebooted into ubuntu it does not go into the normal user name and password screen. The screen is just black and asks of my user name and password and when I type them in I get a bunch of -bash: /dev/null: Permission denied 
and then it goes to 
william@william-laptop:~$
and i can type stuff in Please help.
if i try to log in as root the password i type in is incorrect

---

### Post by Woody1987 on 2009-05-03
you should be able to get to tour desktop by typing in sudo /etc/init.d/gdm start

Although this wont fix ur problem, it will should allow u to at least get back to ur desktop and fix the problem.

---

### Post by opivy522 on 2009-05-03
when i type that in it gives me

* Starting GNOME Display Manager...
return: 24: Illegal number: Starting

then it goes back to the prompt

---

### Post by lykwydchykyn on 2009-05-05
Try purging usplash, for starters:
```

sudo aptitude purge usplash

```
You might want to get a liveCD and run memtest.

---

### Post by opivy522 on 2009-05-05
I type in sudo aptitude purge usplash and this is what happend 
[PHP]E: /home/william/.aptitude is readable but not writable; unable to write configuration file.
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
Reading package lists.. Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
The following packages will be REMOVED:
   usplash{p} uspalsh-theme-ubuntu{u}
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 774kb will be freed.
Do you want to continue? [Y/n/?] y
Segmentation fault
william@william-laptop:~$
[/PHP]

and how do i run memtest from cd

---

### Post by Pnuts on 2009-05-05
It is on the initial menu when booting the CD

Something like:

Try Ubuntu
Install Ubuntu
Check cd for defects
**run memtest**

---

### Post by opivy522 on 2009-05-07
I ran memtest and everything passed.

---

### Post by lykwydchykyn on 2009-05-07
Unfortunately I don't have enough information to give you a "step-by-step" how-to-fix-this-problem response.  

What I can surmise is that your disks are being mounted read-only.  This usually happens when something goes wrong during boot.  I see two possibilities:

 - There is a hardware issue with the drive, which has only surfaced since you attempted this install.
 - Some part of the procedure you were doing messed up and is causing boot to fail.

Try this:
```

dmesg|less

```

And look for a line indicating that the drives are being mounted read-only.  If you find it, see if there is an error that indicates why.  That'd be a good starting point.

If it's possible there is a hardware issue: 
 - boot to the liveCD desktop
 - open a terminal
 - run this:
```

sudo badblocks -v /dev/sda

```
See if it shows any bad blocks (a.k.a. bad sectors) on your drive.

Sorry I cannot give you any more specific advice than that.

---

### Post by opivy522 on 2009-05-11
I found one error after running dmesg|less:
```

[403.493374] aptitude[1672]: segfault at 0 ip b7931511 sp bfb443bc error 4 in lib-2.9.so[b78d1000+15c000]

```
I don't know if this is it but it could be.

---

### Post by opivy522 on 2009-05-12
also i ran 
sudo badblocks -v /dev/sda
and it found no badblocks.

---

### Post by lykwydchykyn on 2009-05-12
> **opivy522 said:**
> I found one error after running dmesg|less:
```

[403.493374] aptitude[1672]: segfault at 0 ip b7931511 sp bfb443bc error 4 in lib-2.9.so[b78d1000+15c000]

```
I don't know if this is it but it could be.

That's just showing where you ran aptitude and it failed.  Is there any way you can post the entire output of dmesg?

---

### Post by opivy522 on 2009-05-12
Yea I can but it will take me a while so I let you know when I do

---

### Post by lykwydchykyn on 2009-05-12
> **opivy522 said:**
> Yea I can but it will take me a while so I let you know when I do

That fine, but I do check my subscribed threads regularly so you don't need to PM me.

---

### Post by opivy522 on 2009-05-13
Ok here is my dmesg. Took forever, I didn't want to type it all out so I had to figure out how to copy it. I used the command "dmesg > filename" to copy it, but my disk was read only so I found a command "remount -o ...." (I don't remember the rest) to mkdir and copy. Anyways, here is the dmesg:

```

[    0.000000] BIOS EBDA/lowmem at: 0009e000/0009e000
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
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbbf50 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000091000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bbf50000 (usable)
[    0.000000]  modified: 00000000bbf50000 - 00000000bbf65000 (ACPI data)
[    0.000000]  modified: 00000000bbf65000 - 00000000bbf66000 (ACPI NVS)
[    0.000000]  modified: 00000000bbf66000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 3769c000 - 37fefd5c
[    0.000000] Allocated new RAMDISK: 00881000 - 011d4d5c
[    0.000000] Move RAMDISK from 000000003769c000 - 0000000037fefd5b to 00881000 - 011d4d5b
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
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2123MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 00011d4d5c]      NEW RAMDISK ==> [0000881000 - 00011d4d5c]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f8220] 000f8220
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bbf50
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000091
[    0.000000]     0: 0x00000100 -> 0x000bbf50
[    0.000000] On node 0 totalpages: 769748
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c11d5000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3940 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4247 pages used for memmap
[    0.000000]   HighMem zone: 539323 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
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
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 763733
[    0.000000] Kernel command line: root=UUID=f4203f87-ca4f-4ee0-89be-5f53174ec94b ro quiet splash vga=791
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2000.009 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15397440 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3020804k/3079488k available (4126k kernel code, 57320k reserved, 2208k data, 532k init, 2174280k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.01 BogoMIPS (lpj=8000036)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018007] ACPI: Core revision 20080926
[    0.020993] ACPI: Checking initramfs for custom DSDT
[    0.372590] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.414031] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.416001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4000.39 BogoMIPS (lpj=8000780)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.500229] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.500286] Brought up 2 CPUs
[    0.500288] Total of 2 processors activated (8000.40 BogoMIPS).
[    0.500285] System has AMD C1E enabled
[    0.500285] Switch to broadcast mode on CPU1
[    0.500382] CPU0 attaching sched-domain:
[    0.500385]  domain 0: span 0-1 level CPU
[    0.500388]   groups: 0 1
[    0.500394] CPU1 attaching sched-domain:
[    0.500395]  domain 0: span 0-1 level CPU
[    0.500398]   groups: 1 0
[    0.500464] Switch to broadcast mode on CPU0
[    0.500464] net_namespace: 776 bytes
[    0.500464] Booting paravirtualized kernel on bare hardware
[    0.500464] Time:  5:25:08  Date: 05/13/09
[    0.500464] regulator: core version 0.5
[    0.500464] NET: Registered protocol family 16
[    0.500464] EISA bus registered
[    0.500464] ACPI: bus type pci registered
[    0.500464] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.500464] PCI: MCFG area at e0000000 reserved in E820
[    0.500464] PCI: Using MMCONFIG for extended config space
[    0.500464] PCI: Using configuration type 1 for base access
[    0.501109] ACPI: EC: Look up EC in DSDT
[    0.505498] ACPI: BIOS _OSI(Linux) query ignored
[    0.506436] ACPI: Interpreter enabled
[    0.506440] ACPI: (supports S0 S3 S4 S5)
[    0.506458] ACPI: Using IOAPIC for interrupt routing
[    0.504026] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.512051] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.512054] ACPI: EC: driver started in interrupt mode
[    0.512292] ACPI: No dock devices found.
[    0.512304] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.512490] pci 0000:00:01.1: reg 10 io port: [0x3080-0x30bf]
[    0.512501] pci 0000:00:01.1: reg 20 io port: [0x3040-0x307f]
[    0.512506] pci 0000:00:01.1: reg 24 io port: [0x3000-0x303f]
[    0.512517] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.512522] pci 0000:00:01.1: PME# disabled
[    0.512574] pci 0000:00:01.3: reg 10 32bit mmio: [0xf6200000-0xf627ffff]
[    0.512648] pci 0000:00:02.0: reg 10 32bit mmio: [0xf6486000-0xf6486fff]
[    0.512666] pci 0000:00:02.0: supports D1 D2
[    0.512668] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.512672] pci 0000:00:02.0: PME# disabled
[    0.512693] pci 0000:00:02.1: reg 10 32bit mmio: [0xf6489000-0xf64890ff]
[    0.512713] pci 0000:00:02.1: supports D1 D2
[    0.512715] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.512719] pci 0000:00:02.1: PME# disabled
[    0.512743] pci 0000:00:04.0: reg 10 32bit mmio: [0xf6487000-0xf6487fff]
[    0.512762] pci 0000:00:04.0: supports D1 D2
[    0.512764] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.512767] pci 0000:00:04.0: PME# disabled
[    0.512791] pci 0000:00:04.1: reg 10 32bit mmio: [0xf6489400-0xf64894ff]
[    0.512811] pci 0000:00:04.1: supports D1 D2
[    0.512813] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.512816] pci 0000:00:04.1: PME# disabled
[    0.512849] pci 0000:00:06.0: reg 20 io port: [0x30c0-0x30cf]
[    0.512881] pci 0000:00:07.0: reg 10 32bit mmio: [0xf6480000-0xf6483fff]
[    0.512900] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.512903] pci 0000:00:07.0: PME# disabled
[    0.512956] pci 0000:00:09.0: reg 10 io port: [0x30f0-0x30f7]
[    0.512960] pci 0000:00:09.0: reg 14 io port: [0x30e4-0x30e7]
[    0.512963] pci 0000:00:09.0: reg 18 io port: [0x30e8-0x30ef]
[    0.512967] pci 0000:00:09.0: reg 1c io port: [0x30e0-0x30e3]
[    0.512971] pci 0000:00:09.0: reg 20 io port: [0x30d0-0x30df]
[    0.512975] pci 0000:00:09.0: reg 24 32bit mmio: [0xf6484000-0xf6485fff]
[    0.513012] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf6488000-0xf6488fff]
[    0.513016] pci 0000:00:0a.0: reg 14 io port: [0x30f8-0x30ff]
[    0.513020] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf6489c00-0xf6489cff]
[    0.513024] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf6489800-0xf648980f]
[    0.513036] pci 0000:00:0a.0: supports D1 D2
[    0.513038] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.513042] pci 0000:00:0a.0: PME# disabled
[    0.513069] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.513072] pci 0000:00:0c.0: PME# disabled
[    0.513096] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.513098] pci 0000:00:0d.0: PME# disabled
[    0.513119] pci 0000:00:12.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.513124] pci 0000:00:12.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.513129] pci 0000:00:12.0: reg 1c 64bit mmio: [0xf4000000-0xf4ffffff]
[    0.513134] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.513230] pci 0000:02:05.0: reg 10 32bit mmio: [0x000000-0x0007ff]
[    0.513256] pci 0000:02:05.0: supports D1 D2
[    0.513258] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.513261] pci 0000:02:05.0: PME# disabled
[    0.513285] pci 0000:02:05.1: reg 10 32bit mmio: [0xf6100800-0xf61008ff]
[    0.513311] pci 0000:02:05.1: supports D1 D2
[    0.513313] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.513317] pci 0000:02:05.1: PME# disabled
[    0.513341] pci 0000:02:05.2: reg 10 32bit mmio: [0xf6100c00-0xf6100cff]
[    0.513367] pci 0000:02:05.2: supports D1 D2
[    0.513369] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.513373] pci 0000:02:05.2: PME# disabled
[    0.513396] pci 0000:02:05.3: reg 10 32bit mmio: [0xf6101000-0xf61010ff]
[    0.513422] pci 0000:02:05.3: supports D1 D2
[    0.513424] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.513428] pci 0000:02:05.3: PME# disabled
[    0.513451] pci 0000:02:05.4: reg 10 32bit mmio: [0xf6101400-0xf61014ff]
[    0.513477] pci 0000:02:05.4: supports D1 D2
[    0.513479] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.513483] pci 0000:02:05.4: PME# disabled
[    0.513513] pci 0000:00:08.0: transparent bridge
[    0.513517] pci 0000:00:08.0: bridge 32bit mmio: [0xf6100000-0xf61fffff]
[    0.513553] pci 0000:00:0c.0: bridge io port: [0x4000-0x4fff]
[    0.513556] pci 0000:00:0c.0: bridge 32bit mmio: [0xf2000000-0xf3ffffff]
[    0.513560] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.513594] pci 0000:03:00.0: reg 10 64bit mmio: [0xf6000000-0xf600ffff]
[    0.513662] pci 0000:00:0d.0: bridge 32bit mmio: [0xf6000000-0xf60fffff]
[    0.513671] bus 00 -> node 0
[    0.513678] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.513784] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.513809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.513848] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.547704] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.547930] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.548168] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.548393] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.548616] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.548840] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.549065] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.549289] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.549513] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.549737] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.549960] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.550189] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.550417] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.550641] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.550865] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.551089] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.551313] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.551541] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.551769] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.552030] ACPI: WMI: Mapper loaded
[    0.556121] SCSI subsystem initialized
[    0.556128] libata version 3.00 loaded.
[    0.556128] usbcore: registered new interface driver usbfs
[    0.556128] usbcore: registered new interface driver hub
[    0.556128] usbcore: registered new device driver usb
[    0.556128] PCI: Using ACPI for IRQ routing
[    0.560014] Bluetooth: Core ver 2.13
[    0.564014] NET: Registered protocol family 31
[    0.564014] Bluetooth: HCI device and connection manager initialized
[    0.564016] Bluetooth: HCI socket layer initialized
[    0.564018] NET: Registered protocol family 8
[    0.564020] NET: Registered protocol family 20
[    0.564030] NetLabel: Initializing
[    0.564031] NetLabel:  domain hash size = 128
[    0.564033] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.564047] NetLabel:  unlabeled traffic allowed by default
[    0.564063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.564067] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.568087] AppArmor: AppArmor Filesystem Enabled
[    0.576021] Switched to high resolution mode on CPU 0
[    0.576035] Switched to high resolution mode on CPU 1
[    0.576054] pnp: PnP ACPI init
[    0.576064] ACPI: bus type pnp registered
[    0.580235] pnp: PnP ACPI: found 12 devices
[    0.580237] ACPI: ACPI bus type pnp unregistered
[    0.580240] PnPBIOS: Disabled by ACPI PNP
[    0.580250] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.580256] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.580259] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.580261] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.580264] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.580267] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.580269] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.580275] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.580278] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.580286] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.580289] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.580292] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.580295] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.580298] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.615021] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.615023] pci 0000:00:08.0:   IO window: disabled
[    0.615027] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.615030] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.615034] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.615036] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.615040] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.615043] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.615046] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.615048] pci 0000:00:0d.0:   IO window: disabled
[    0.615051] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.615054] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.615062] pci 0000:00:08.0: setting latency timer to 64
[    0.615068] pci 0000:00:0c.0: setting latency timer to 64
[    0.615072] pci 0000:00:0d.0: setting latency timer to 64
[    0.615075] bus: 00 index 0 io port: [0x00-0xffff]
[    0.615077] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.615079] bus: 02 index 0 mmio: [0x0-0x0]
[    0.615081] bus: 02 index 1 mmio: [0xf6100000-0xf61fffff]
[    0.615083] bus: 02 index 2 mmio: [0x0-0x0]
[    0.615085] bus: 02 index 3 io port: [0x00-0xffff]
[    0.615087] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.615089] bus: 04 index 0 io port: [0x4000-0x4fff]
[    0.615091] bus: 04 index 1 mmio: [0xf2000000-0xf3ffffff]
[    0.615093] bus: 04 index 2 mmio: [0xf0000000-0xf1ffffff]
[    0.615095] bus: 04 index 3 mmio: [0x0-0x0]
[    0.615098] bus: 03 index 0 mmio: [0x0-0x0]
[    0.615099] bus: 03 index 1 mmio: [0xf6000000-0xf60fffff]
[    0.615102] bus: 03 index 2 mmio: [0x0-0x0]
[    0.615103] bus: 03 index 3 mmio: [0x0-0x0]
[    0.615114] NET: Registered protocol family 2
[    0.625074] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.625371] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.626169] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.626614] TCP: Hash tables configured (established 131072 bind 65536)
[    0.626616] TCP reno registered
[    0.629111] NET: Registered protocol family 1
[    0.629247] checking if image is initramfs... it is
[    1.350914] Freeing initrd memory: 9551k freed
[    1.350951] Simple Boot Flag at 0x36 set to 0x1
[    1.351121] cpufreq: No nForce2 chipset.
[    1.351269] audit: initializing netlink socket (disabled)
[    1.351284] type=2000 audit(1242192308.348:1): initialized
[    1.359343] highmem bounce pool size: 64 pages
[    1.359349] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.360630] VFS: Disk quotas dquot_6.5.1
[    1.360685] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.361290] fuse init (API version 7.10)
[    1.361366] msgmni has been set to 1673
[    1.361567] alg: No test for stdrng (krng)
[    1.361579] io scheduler noop registered
[    1.361581] io scheduler anticipatory registered
[    1.361583] io scheduler deadline registered
[    1.361598] io scheduler cfq registered (default)
[    1.361630] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.361806] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.361821] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.361837] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.361854] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.361869] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.361885] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.361900] pci 0000:00:12.0: Boot video device
[    1.368287] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.368313] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.368330] pcieport-driver 0000:00:0c.0: irq 2303 for MSI/MSI-X
[    1.368337] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.368354] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.368390] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.368413] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.368425] pcieport-driver 0000:00:0d.0: irq 2302 for MSI/MSI-X
[    1.368432] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.368443] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.368492] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.368501] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.369798] ACPI: AC Adapter [ACAD] (on-line)
[    1.649463] ACPI: Battery Slot [BAT0] (battery present)
[    1.649546] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.649549] ACPI: Power Button (FF) [PWRF]
[    1.649599] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.649602] ACPI: Sleep Button (CM) [SLPB]
[    1.649647] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.650775] ACPI: Lid Switch [LID]
[    1.650833] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.650836] ACPI: Power Button (CM) [PWRB]
[    1.651140] ACPI: processor limited to max C-state 1
[    1.651166] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.651197] processor ACPI_CPU:00: registered as cooling_device0
[    1.651202] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.651285] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.651306] processor ACPI_CPU:01: registered as cooling_device1
[    1.651311] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.915447] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.915504] isapnp: Scanning for PnP cards...
[    2.268082] isapnp: No Plug & Play device found
[    2.281251] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.282170] brd: module loaded
[    2.282479] loop: module loaded
[    2.282547] Fixed MDIO Bus: probed
[    2.282553] PPP generic driver version 2.4.2
[    2.282614] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.282647] Driver 'sd' needs updating - please use bus_type methods
[    2.282655] Driver 'sr' needs updating - please use bus_type methods
[    2.282695] ahci 0000:00:09.0: version 3.0
[    2.283056] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    2.283069] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    2.283111] ahci 0000:00:09.0: irq 2301 for MSI/MSI-X
[    2.283180] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    2.283184] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[    2.283187] ahci 0000:00:09.0: setting latency timer to 64
[    2.283680] scsi0 : ahci
[    2.283819] scsi1 : ahci
[    2.283914] scsi2 : ahci
[    2.284011] scsi3 : ahci
[    2.284109] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 2301
[    2.284112] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 2301
[    2.284115] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 2301
[    2.284118] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 2301
[    2.768031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.768518] ata1.00: ATA-8: ST9200827AS, 3.BHA, max UDMA/100
[    2.768521] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.768971] ata1.00: configured for UDMA/100
[    3.088031] ata2: SATA link down (SStatus 0 SControl 300)
[    3.408027] ata3: SATA link down (SStatus 0 SControl 300)
[    3.728025] ata4: SATA link down (SStatus 0 SControl 300)
[    3.728153] scsi 0:0:0:0: Direct-Access     ATA      ST9200827AS      3.BH PQ: 0 ANSI: 5
[    3.728250] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    3.728267] sd 0:0:0:0: [sda] Write Protect is off
[    3.728270] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.728294] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.728372] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    3.728385] sd 0:0:0:0: [sda] Write Protect is off
[    3.728387] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.728410] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.728414]  sda: sda1 sda2 < sda5 sda6 > sda3
[    3.803526] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.803580] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.803833] pata_amd 0000:00:06.0: version 0.3.10
[    3.803875] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.803966] scsi4 : pata_amd
[    3.804066] scsi5 : pata_amd
[    3.804422] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    3.804425] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    3.984310] ata5.00: ATAPI: TSSTcorp CDDVDW TS-L632N, 0503, max MWDMA2
[    3.984334] ata5: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    4.016256] ata5.00: configured for MWDMA2
[    4.018010] ata6: port disabled. ignoring.
[    4.020554] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632N  0503 PQ: 0 ANSI: 5
[    4.032327] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.032330] Uniform CD-ROM driver Revision: 3.20
[    4.032441] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    4.032481] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    4.032981] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.033355] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    4.033366] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    4.033388] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    4.033391] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.033449] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    4.033476] ehci_hcd 0000:00:02.1: debug port 1
[    4.033481] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    4.033500] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    4.044028] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    4.044101] usb usb1: configuration #1 chosen from 1 choice
[    4.044131] hub 1-0:1.0: USB hub found
[    4.044140] hub 1-0:1.0: 7 ports detected
[    4.044567] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    4.044570] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    4.044581] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.044583] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.044631] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    4.044654] ehci_hcd 0000:00:04.1: debug port 1
[    4.044658] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    4.044663] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    4.056025] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.056082] usb usb2: configuration #1 chosen from 1 choice
[    4.056105] hub 2-0:1.0: USB hub found
[    4.056113] hub 2-0:1.0: 2 ports detected
[    4.056197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.056539] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    4.056547] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    4.056557] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.056560] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.056605] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    4.056630] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    4.114058] usb usb3: configuration #1 chosen from 1 choice
[    4.114084] hub 3-0:1.0: USB hub found
[    4.114092] hub 3-0:1.0: 7 ports detected
[    4.114499] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    4.114502] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    4.114512] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.114515] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.114559] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.114570] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    4.170057] usb usb4: configuration #1 chosen from 1 choice
[    4.170079] hub 4-0:1.0: USB hub found
[    4.170088] hub 4-0:1.0: 2 ports detected
[    4.170164] uhci_hcd: USB Universal Host Controller Interface driver
[    4.170237] usbcore: registered new interface driver libusual
[    4.170274] usbcore: registered new interface driver usbserial
[    4.170284] USB Serial support registered for generic
[    4.170298] usbcore: registered new interface driver usbserial_generic
[    4.170300] usbserial: USB Serial Driver core
[    4.170343] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.197384] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.197391] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.200057] mice: PS/2 mouse device common for all mice
[    4.221090] rtc_cmos 00:07: RTC can wake from S4
[    4.221123] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    4.221162] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.221224] device-mapper: uevent: version 1.0.3
[    4.221336] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.221511] device-mapper: multipath: version 1.0.5 loaded
[    4.221514] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.221622] EISA: Probing bus 0 at eisa.0
[    4.221628] Cannot allocate resource for EISA slot 1
[    4.221633] Cannot allocate resource for EISA slot 3
[    4.221635] Cannot allocate resource for EISA slot 4
[    4.221647] EISA: Detected 0 cards.
[    4.221800] cpuidle: using governor ladder
[    4.221863] cpuidle: using governor menu
[    4.222357] TCP cubic registered
[    4.222453] NET: Registered protocol family 10
[    4.222840] lo: Disabled Privacy Extensions
[    4.223134] NET: Registered protocol family 17
[    4.223153] Bluetooth: L2CAP ver 2.11
[    4.223155] Bluetooth: L2CAP socket layer initialized
[    4.223158] Bluetooth: SCO (Voice Link) ver 0.6
[    4.223159] Bluetooth: SCO socket layer initialized
[    4.223216] Bluetooth: RFCOMM socket layer initialized
[    4.223222] Bluetooth: RFCOMM TTY layer initialized
[    4.223224] Bluetooth: RFCOMM ver 1.10
[    4.223274] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[    4.223322] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x11
[    4.223325] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[    4.223327] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[    4.223329] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    4.223380] Using IPI No-Shortcut mode
[    4.223470] registered taskstats version 1
[    4.223620]   Magic number: 9:870:415
[    4.223743] rtc_cmos 00:07: setting system clock to 2009-05-13 05:25:12 UTC (1242192312)
[    4.223746] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.223748] EDD information not available.
[    4.224159] Freeing unused kernel memory: 532k freed
[    4.224309] Write protecting the kernel text: 4128k
[    4.224361] Write protecting the kernel read-only data: 1532k
[    4.255626] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.300354] vesafb: framebuffer at 0xd0000000, mapped to 0xf7d00000, using 3072k, total 65536k
[    4.300358] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[    4.300362] vesafb: protected mode interface info at c000:da10
[    4.300364] vesafb: pmi: set display start = c00cda46, set palette = c00cdab0
[    4.300366] vesafb: pmi: ports = b4c3 b503 ba03 c003 c103 c403 c503 c603 c703 c803 c903 cc03 ce03 cf03 d003 d103 d203 d303 d403 d503 da03 ff03 
[    4.300378] vesafb: scrolling: redraw
[    4.300381] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    4.300471] Console: switching to colour frame buffer device 128x48
[    4.308863] fb0: VESA VGA frame buffer device
[    4.444110] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    4.595516] usb 2-2: configuration #1 chosen from 1 choice
[    4.740889] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[    4.741277] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    4.741292] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    4.747937] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.748342] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.748354] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    4.748359] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.793089] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.901225] usb 3-6: new low speed USB device using ohci_hcd and address 2
[    5.117136] usb 3-6: configuration #1 chosen from 1 choice
[    5.125381] usbcore: registered new interface driver hiddev
[    5.132390] input: Kensington Kensington Ci85m QuickStart Wireless Notebook Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-6/3-6:1.0/input/input6
[    5.132641] generic-usb 0003:047D:1049.0001: input,hidraw0: USB HID v1.10 Mouse [Kensington Kensington Ci85m QuickStart Wireless Notebook Mouse] on usb-0000:00:02.0-6/input0
[    5.132663] usbcore: registered new interface driver usbhid
[    5.132666] usbhid: v2.6:USB HID core driver
[    5.265061] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:7c:27:6d
[    5.265066] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    5.358985] PM: Starting manual resume from disk
[    5.358989] PM: Resume from partition 8:6
[    5.358991] PM: Checking hibernation image.
[    5.359131] PM: Resume from disk failed.
[    5.361370] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.361374] EXT3-fs: write access will be enabled during recovery.
[    5.396188] kjournald starting.  Commit interval 5 seconds
[    5.396205] EXT3-fs: recovery complete.
[    5.396420] EXT3-fs: mounted filesystem with ordered data mode.
[    6.068253] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0018e00101]
[   73.000023] Clocksource tsc unstable (delta = -296739689 ns)
[  230.563757] EXT3 FS on sda5, internal journal

```

---

### Post by opivy522 on 2009-05-13
Also after i remounted and took the computer out of read only I ran
sudo aptitude purge usplash 
and it worked this time but it did not make my computer work it still does the same thing.

---

### Post by petrus4 on 2009-05-13
> **opivy522 said:**
> Also after i remounted and took the computer out of read only I ran
sudo aptitude purge usplash 
and it worked this time but it did not make my computer work it still does the same thing.

Your hardware is probably fine.  Ubuntu just has unspeakably bad design, is all.

I cut gdm from /etc/rc*.d because I wanted to be able to run bare X with WoW in order to avoid Gnome's memory overhead, and the entire system started falling apart.  ALSA promptly died (again) which it routinely does if I sneeze at it, and all sorts of other weird things happened.  For a while bash wasn't displaying the correct prompt in Eterm, among other fun things.

Ubuntu's design is completely [non-orthogonal]("http://www.catb.org/~esr/writings/taoup/html/ch04s02.html#orthogonality").  There is no way in Hell, under any other distribution I've ever used, that removing gdm from init should or would cause ALSA to cease functioning, or cause bash problems in a terminal.  Bash and ALSA should not rightfully have any dependency on gdm AT ALL.

---

### Post by lykwydchykyn on 2009-05-14
Does it boot up read-only every time, or is it booting with the disk writable now?  There was nothing in the dmesg output about it mounting read-only, yet clearly it was.  It indicated that the disk required recovery, but it seems to have taken care of that automatically.

so trying to restart gdm you get the same error 24?

---

### Post by opivy522 on 2009-05-14
yes i get the same error and it boots up in read only

---

### Post by petrus4 on 2009-05-14
> **opivy522 said:**
> yes i get the same error and it boots up in read only

Do you have anything on the partition that you need to keep?

If you don't, wipe the whole thing and start again.  Easiest fix.

---

### Post by opivy522 on 2009-05-17
Yeah, that's what I'm going to do.

---

### Post by OobNosferatu on 2009-07-05
NOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!

crap... I have the exact same problem. I don't want to go through the pain of re-installing everything! I have a working ubuntu 9.04 on the same system, isn't there a way to just copy over some key boot up files???

---

### Post by noname01 on 2009-07-09
> **OobNosferatu said:**
> NOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!
 
crap... I have the exact same problem. I don't want to go through the pain of re-installing everything! I have a working ubuntu 9.04 on the same system, isn't there a way to just copy over some key boot up files???
 
 
ME TOOOOO and i dont want to format and re-install everything, as it took me around 2 weeks and lots of research to make my perfect ubuntu....
 
 
Some one help please

---

### Post by noname01 on 2009-07-10
Bump bump ...

---

### Post by lykwydchykyn on 2009-07-10
You guys might want to start new threads.  It's not entirely clear what the OP's problem was, it might have been hardware related.

When you start your new thread, I would also recommend supplying the diagnostic information that was requested of the OP, to save people time from having to ask you for it again.

---

### Post by grenadier32 on 2009-08-11
Found a solution! Splashy is still on your system and screwing you over!

To make the system read-write again:

```
sudo mount -o remount,rw /
```

That will allow you to edit things again. Now, all you should need to do:

```
sudo aptitude purge splashy libsplashy1
```

And reboot, and your system will be working again!

---

