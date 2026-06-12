---
title: "NVIDIA driver installation help - Ubuntu newbie"
date: 2009-05-01
forum: General Help
---

### Post by 2Real on 2009-05-01
I need help installing the nvidia graphics drive in Ubuntu 9.04.
I have an 8600M GT and I downloaded the newest drives for linux from NVIDIA's website and followed some guides here but I get this error after i reboot my computer.


(EE)Failed to load module "type1" (module does not exist, 0)
(EE)Failed to load module "freetype" (module does not exist, 0)
(EE) NVIDIA(0): Failed to load the NVIDIA kernal module!
(EE) NVIDIA(0) ****Aborting****
(EE) Screen(s) found, but none have a usuable configuration.

I'm lost. Help please :confused: I don't know what's going on.

---

### Post by doas777 on 2009-05-01
ok, open a terminal and run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` this will reset your xorg.conf to default. reboot.

now, when you boot back up and login, go to System -> Adminstration -> Hardware Drivers. do you see any nvidia drivers listed?
if not, go back to your terminal, and run 
```
sudo apt-get update
```
and then go back to hardware drivers, and check again.

if you still don't have drivers listed in your hardware drivers list, open System -> Administration -> Synaptic Package Manager, and search for and install envyNG
then run it to install your drivers.

good luck

---

### Post by 2Real on 2009-05-01
I tried running envyNG and it wouldn't start up so then I tried the text version of it and when I tried to install NVIDIA drivers i got this error 


Traceback (most recent call last):
   File "interface.py", line 432, in <module>
     a.mainMenu()
   File "interface.py", line 295, in mainMenu
     a.driverMenu('nvidia')
   File "interface.py", line 322, in driverMenu
     self.driverPage(driver)
   File "interface.py", line 216, in driverPage
     candidateLen.append(len(details['candidate']))
 TypeError: object of type 'NoneType' has no len()

---

### Post by GeekGirl1 on 2009-05-01
2Real - Here's what worked for me (NVidia proprietary driver):

First, you need the ability to compile your kernel. Maybe this is what you are missing.

>sudo apt-get install build-essential

Then, run the NVidia install

>sudo sh ./NV (hit tab to complete the filename)

- During the install, answer Yes to build the kernel.
- You will get an error with one of the object files (.o), and a message saying it's probably OK. I forget whether you answer Yes or No, but select whichever one allows you to proceed.
- Run the X11 configuration utility to modify xorg.conf as it suggests (occurs during the install).

Everything should now work.

---

### Post by 2Real on 2009-05-01
> **GeekGirl1 said:**
> 2Real - Here's what worked for me (NVidia proprietary driver):

First, you need the ability to compile your kernel. Maybe this is what you are missing.

>sudo apt-get install build-essential

Then, run the NVidia install

>sudo sh ./NV (hit tab to complete the filename)

- During the install, answer Yes to build the kernel.
- You will get an error with one of the object files (.o), and a message saying it's probably OK. I forget whether you answer Yes or No, but select whichever one allows you to proceed.
- Run the X11 configuration utility to modify xorg.conf as it suggests (occurs during the install).

Everything should now work.

i still get the same error from my first post

---

### Post by 2Real on 2009-05-01
bump

---

### Post by Racecar56 on 2009-05-01
dmesg please

---

### Post by 2Real on 2009-05-01
> **Racecar56 said:**
> dmesg please
huh?

---

### Post by Racecar56 on 2009-05-01
go into a terminal, maximize it and then do this:

```
dmesg > ~/dmesg
```

then open up your home folder in places and attach the file called dmesg into your next post

---

### Post by doas777 on 2009-05-01
he/she would like to see the output of the dmesg command

---

### Post by 2Real on 2009-05-02
> **Racecar56 said:**
> go into a terminal, maximize it and then do this:

```
dmesg > ~/dmesg
```then open up your home folder in places and attach the file called dmesg into your next post
it's not letting me upload the file so i'll plaste in parts

[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  modified: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378cf000 - 37fef213
[    0.000000] Allocated new RAMDISK: 00881000 - 00fa1213
[    0.000000] Move RAMDISK from 00000000378cf000 - 0000000037fef212 to 00881000 - 00fa1212
[    0.000000] ACPI: RSDP 000FB2F0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFB0000, 003C (r1 _ASUS_ Notebook  7000713 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0200, 0084 (r2 A_M_I_ OEMFACP   7000713 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB05C0, 73CB (r1  A0704 A0704000        0 INTL 20060113)
[    0.000000] ACPI: FACS 7FFBE000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 006C (r1 A_M_I_ OEMAPIC   7000713 MSFT       97)
[    0.000000] ACPI: MCFG 7FFB0400, 003C (r1 A_M_I_ OEMMCFG   7000713 MSFT       97)
[    0.000000] ACPI: SLIC 7FFB0440, 0176 (r1 _ASUS_ Notebook  7000713 MSFT       97)
[    0.000000] ACPI: OEMB 7FFBE040, 0061 (r1 A_M_I_ AMI_OEM   7000713 MSFT       97)
[    0.000000] ACPI: HPET 7FFB7990, 0038 (r1 A_M_I_ OEMHPET   7000713 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1163MB HIGHMEM available.
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
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fa1213]      NEW RAMDISK ==> [0000881000 - 0000fa1213]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2328 pages used for memmap
[    0.000000]   HighMem zone: 295578 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)

---

### Post by 2Real on 2009-05-02
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: root=UUID=7782802c-53cb-4d58-bcdb-696bb60df82c ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2133.302 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10483840 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2052872k/2096832k available (4126k kernel code, 42644k reserved, 2208k data, 532k init, 1191624k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4266.60 BogoMIPS (lpj=8533208)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018294] ACPI: Core revision 20080926
[    0.020948] ACPI: Checking initramfs for custom DSDT
[    0.296441] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.339770] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
[    0.340001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4266.69 BogoMIPS (lpj=8533382)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.424427] CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
[    0.424442] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.428039] Brought up 2 CPUs
[    0.428042] Total of 2 processors activated (8533.29 BogoMIPS).
[    0.428093] CPU0 attaching sched-domain:
[    0.428096]  domain 0: span 0-1 level MC
[    0.428098]   groups: 0 1
[    0.428104] CPU1 attaching sched-domain:
[    0.428106]  domain 0: span 0-1 level MC
[    0.428108]   groups: 1 0
[    0.428177] net_namespace: 776 bytes
[    0.428177] Booting paravirtualized kernel on bare hardware
[    0.428312] Time: 20:05:26  Date: 05/01/09
[    0.428312] regulator: core version 0.5
[    0.428312] NET: Registered protocol family 16
[    0.428312] EISA bus registered
[    0.428312] ACPI: bus type pci registered
[    0.428312] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub with MMCONFIG support.
[    0.428312] PCI: Using MMCONFIG for extended config space
[    0.428312] PCI: Using configuration type 1 for base access
[    0.429054] ACPI: EC: Look up EC in DSDT
[    0.947130] ACPI: Interpreter enabled
[    0.947136] ACPI: (supports S0 S1 S3 S4 S5)
[    0.947156] ACPI: Using IOAPIC for interrupt routing
[    0.949359] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.957516] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.957518] ACPI: EC: driver started in interrupt mode
[    0.957660] ACPI: No dock devices found.
[    0.957726] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.957811] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.957814] pci 0000:00:01.0: PME# disabled
[    0.957889] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf3ffc000-0xf3ffffff]
[    0.957924] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.957928] pci 0000:00:1b.0: PME# disabled
[    0.957983] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.957987] pci 0000:00:1c.0: PME# disabled
[    0.958044] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.958049] pci 0000:00:1c.1: PME# disabled
[    0.958106] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.958110] pci 0000:00:1c.2: PME# disabled
[    0.958167] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.958171] pci 0000:00:1c.3: PME# disabled
[    0.958229] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.958233] pci 0000:00:1c.4: PME# disabled
[    0.958287] pci 0000:00:1d.0: reg 20 io port: [0xa480-0xa49f]
[    0.958342] pci 0000:00:1d.1: reg 20 io port: [0xa800-0xa81f]
[    0.958397] pci 0000:00:1d.2: reg 20 io port: [0xa880-0xa89f]
[    0.958452] pci 0000:00:1d.3: reg 20 io port: [0xac00-0xac1f]
[    0.958513] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf3ffbc00-0xf3ffbfff]
[    0.958557] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.958562] pci 0000:00:1d.7: PME# disabled
[    0.958693] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.958697] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.958739] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.958746] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.958752] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.958758] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.958765] pci 0000:00:1f.2: reg 20 io port: [0xffa0-0xffaf]
[    0.958785] pci 0000:00:1f.2: PME# supported from D3hot
[    0.958789] pci 0000:00:1f.2: PME# disabled
[    0.958842] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.958914] pci 0000:01:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
[    0.958929] pci 0000:01:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.958944] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf4000000-0xf5ffffff]
[    0.958951] pci 0000:01:00.0: reg 24 io port: [0xbc00-0xbc7f]
[    0.958960] pci 0000:01:00.0: reg 30 32bit mmio: [0xf7ce0000-0xf7cfffff]
[    0.959027] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.959030] pci 0000:00:01.0: bridge 32bit mmio: [0xf4000000-0xf7cfffff]
[    0.959034] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.959083] pci 0000:00:1c.0: bridge io port: [0xe000-0xefff]
[    0.959087] pci 0000:00:1c.0: bridge 32bit mmio: [0xf8000000-0xfbefffff]
[    0.959094] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xdc000000-0xdfffffff]
[    0.959269] pci 0000:05:00.0: reg 10 32bit mmio: [0xf7fff000-0xf7ffffff]
[    0.959424] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.959436] pci 0000:05:00.0: PME# disabled
[    0.959530] pci 0000:00:1c.1: bridge 32bit mmio: [0xf7f00000-0xf7ffffff]
[    0.959653] pci 0000:03:00.0: reg 10 io port: [0xdc00-0xdc07]
[    0.959663] pci 0000:03:00.0: reg 14 io port: [0xd880-0xd883]
[    0.959673] pci 0000:03:00.0: reg 18 io port: [0xd800-0xd807]
[    0.959683] pci 0000:03:00.0: reg 1c io port: [0xd480-0xd483]
[    0.959693] pci 0000:03:00.0: reg 20 io port: [0xd400-0xd40f]
[    0.959703] pci 0000:03:00.0: reg 24 32bit mmio: [0xf7efe000-0xf7efffff]
[    0.959726] pci 0000:03:00.0: PME# supported from D3hot
[    0.959731] pci 0000:03:00.0: PME# disabled
[    0.959787] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.959792] pci 0000:00:1c.3: bridge 32bit mmio: [0xf7e00000-0xf7efffff]
[    0.959864] pci 0000:02:00.0: reg 10 64bit mmio: [0xf7dfc000-0xf7dfffff]

---

### Post by 2Real on 2009-05-02
[    0.959874] pci 0000:02:00.0: reg 18 io port: [0xc800-0xc8ff]
[    0.959904] pci 0000:02:00.0: reg 30 32bit mmio: [0xf7dc0000-0xf7ddffff]
[    0.959917] pci 0000:02:00.0: supports D1 D2
[    0.959919] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.959924] pci 0000:02:00.0: PME# disabled
[    0.959977] pci 0000:00:1c.4: bridge io port: [0xc000-0xcfff]
[    0.959981] pci 0000:00:1c.4: bridge 32bit mmio: [0xf7d00000-0xf7dfffff]
[    0.960030] pci 0000:08:01.0: reg 10 32bit mmio: [0xfbffe800-0xfbffefff]
[    0.960074] pci 0000:08:01.0: supports D1 D2
[    0.960076] pci 0000:08:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.960081] pci 0000:08:01.0: PME# disabled
[    0.960120] pci 0000:08:01.1: reg 10 32bit mmio: [0xfbfff400-0xfbfff4ff]
[    0.960165] pci 0000:08:01.1: supports D1 D2
[    0.960167] pci 0000:08:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.960171] pci 0000:08:01.1: PME# disabled
[    0.960210] pci 0000:08:01.2: reg 10 32bit mmio: [0xfbfff800-0xfbfff8ff]
[    0.960254] pci 0000:08:01.2: supports D1 D2
[    0.960256] pci 0000:08:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.960261] pci 0000:08:01.2: PME# disabled
[    0.960299] pci 0000:08:01.3: reg 10 32bit mmio: [0xfbfffc00-0xfbfffcff]
[    0.960344] pci 0000:08:01.3: supports D1 D2
[    0.960346] pci 0000:08:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.960350] pci 0000:08:01.3: PME# disabled
[    0.960409] pci 0000:00:1e.0: transparent bridge
[    0.960416] pci 0000:00:1e.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.960455] bus 00 -> node 0
[    0.960461] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.960666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.960777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.960881] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.960988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.961095] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.961202] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.961310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    1.001055] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.001189] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.001321] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    1.001452] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.001583] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.001716] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.001850] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.001982] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    1.002179] ACPI: WMI: Mapper loaded
[    1.002212] SCSI subsystem initialized
[    1.002212] libata version 3.00 loaded.
[    1.002212] usbcore: registered new interface driver usbfs
[    1.002212] usbcore: registered new interface driver hub
[    1.002212] usbcore: registered new device driver usb
[    1.002212] PCI: Using ACPI for IRQ routing
[    1.008012] Bluetooth: Core ver 2.13
[    1.008031] NET: Registered protocol family 31
[    1.008031] Bluetooth: HCI device and connection manager initialized
[    1.008031] Bluetooth: HCI socket layer initialized
[    1.008031] NET: Registered protocol family 8
[    1.008031] NET: Registered protocol family 20
[    1.008041] NetLabel: Initializing
[    1.008043] NetLabel:  domain hash size = 128
[    1.008045] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.008060] NetLabel:  unlabeled traffic allowed by default
[    1.008076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.008082] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.012068] AppArmor: AppArmor Filesystem Enabled
[    1.016012] Switched to high resolution mode on CPU 0
[    1.016496] Switched to high resolution mode on CPU 1
[    1.020033] pnp: PnP ACPI init
[    1.020043] ACPI: bus type pnp registered
[    1.024775] pnp: PnP ACPI: found 14 devices
[    1.024777] ACPI: ACPI bus type pnp unregistered
[    1.024781] PnPBIOS: Disabled by ACPI PNP
[    1.024790] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    1.024799] system 00:09: ioport range 0x25c-0x25f has been reserved
[    1.024801] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    1.024804] system 00:09: ioport range 0x800-0x87f has been reserved
[    1.024806] system 00:09: ioport range 0x480-0x4bf has been reserved
[    1.024809] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.024811] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.024814] system 00:09: iomem range 0xfed50000-0xfed8ffff has been reserved
[    1.024816] system 00:09: iomem range 0xffb00000-0xffbfffff has been reserved
[    1.024819] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    1.024824] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.024827] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.024832] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    1.024837] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    1.024840] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    1.024842] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    1.024845] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[    1.059546] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.059549] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    1.059552] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf7cfffff
[    1.059555] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.059560] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06
[    1.059563] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
[    1.059568] pci 0000:00:1c.0:   MEM window: 0xf8000000-0xfbefffff
[    1.059573] pci 0000:00:1c.0:   PREFETCH window: 0x000000dc000000-0x000000dfffffff
[    1.059579] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:05
[    1.059581] pci 0000:00:1c.1:   IO window: disabled
[    1.059586] pci 0000:00:1c.1:   MEM window: 0xf7f00000-0xf7ffffff
[    1.059590] pci 0000:00:1c.1:   PREFETCH window: disabled
[    1.059597] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    1.059599] pci 0000:00:1c.2:   IO window: disabled
[    1.059604] pci 0000:00:1c.2:   MEM window: disabled
[    1.059608] pci 0000:00:1c.2:   PREFETCH window: disabled
[    1.059614] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    1.059617] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    1.059622] pci 0000:00:1c.3:   MEM window: 0xf7e00000-0xf7efffff
[    1.059626] pci 0000:00:1c.3:   PREFETCH window: disabled
[    1.059633] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:02
[    1.059636] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    1.059641] pci 0000:00:1c.4:   MEM window: 0xf7d00000-0xf7dfffff
[    1.059645] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.059652] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    1.059654] pci 0000:00:1e.0:   IO window: disabled
[    1.059659] pci 0000:00:1e.0:   MEM window: 0xfbf00000-0xfbffffff
[    1.059663] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.059676] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.059679] pci 0000:00:01.0: setting latency timer to 64
[    1.059686] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.059691] pci 0000:00:1c.0: setting latency timer to 64
[    1.059699] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.059703] pci 0000:00:1c.1: setting latency timer to 64
[    1.059711] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.059716] pci 0000:00:1c.2: setting latency timer to 64
[    1.059724] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.059728] pci 0000:00:1c.3: setting latency timer to 64
[    1.059736] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.059740] pci 0000:00:1c.4: setting latency timer to 64
[    1.059747] pci 0000:00:1e.0: setting latency timer to 64
[    1.059751] bus: 00 index 0 io port: [0x00-0xffff]
[    1.059753] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.059755] bus: 01 index 0 io port: [0xb000-0xbfff]
[    1.059756] bus: 01 index 1 mmio: [0xf4000000-0xf7cfffff]
[    1.059758] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    1.059760] bus: 01 index 3 mmio: [0x0-0x0]
[    1.059762] bus: 06 index 0 io port: [0xe000-0xefff]
[    1.059764] bus: 06 index 1 mmio: [0xf8000000-0xfbefffff]
[    1.059766] bus: 06 index 2 mmio: [0xdc000000-0xdfffffff]
[    1.059767] bus: 06 index 3 mmio: [0x0-0x0]
[    1.059769] bus: 05 index 0 mmio: [0x0-0x0]
[    1.059771] bus: 05 index 1 mmio: [0xf7f00000-0xf7ffffff]
[    1.059772] bus: 05 index 2 mmio: [0x0-0x0]
[    1.059774] bus: 05 index 3 mmio: [0x0-0x0]
[    1.059776] bus: 04 index 0 mmio: [0x0-0x0]
[    1.059777] bus: 04 index 1 mmio: [0x0-0x0]
[    1.059779] bus: 04 index 2 mmio: [0x0-0x0]
[    1.059780] bus: 04 index 3 mmio: [0x0-0x0]
[    1.059782] bus: 03 index 0 io port: [0xd000-0xdfff]
[    1.059784] bus: 03 index 1 mmio: [0xf7e00000-0xf7efffff]
[    1.059786] bus: 03 index 2 mmio: [0x0-0x0]
[    1.059787] bus: 03 index 3 mmio: [0x0-0x0]
[    1.059789] bus: 02 index 0 io port: [0xc000-0xcfff]
[    1.059791] bus: 02 index 1 mmio: [0xf7d00000-0xf7dfffff]
[    1.059793] bus: 02 index 2 mmio: [0x0-0x0]
[    1.059794] bus: 02 index 3 mmio: [0x0-0x0]
[    1.059796] bus: 08 index 0 mmio: [0x0-0x0]
[    1.059797] bus: 08 index 1 mmio: [0xfbf00000-0xfbffffff]
[    1.059799] bus: 08 index 2 mmio: [0x0-0x0]
[    1.059801] bus: 08 index 3 io port: [0x00-0xffff]
[    1.059803] bus: 08 index 4 mmio: [0x000000-0xffffffff]
[    1.059810] NET: Registered protocol family 2
[    1.076086] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.076345] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.076704] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.076899] TCP: Hash tables configured (established 131072 bind 65536)
[    1.076901] TCP reno registered
[    1.084133] NET: Registered protocol family 1
[    1.084265] checking if image is initramfs... it is
[    1.639944] Freeing initrd memory: 7296k freed
[    1.640178] cpufreq: No nForce2 chipset.
[    1.640317] audit: initializing netlink socket (disabled)
[    1.640343] type=2000 audit(1241208327.640:1): initialized
[    1.646961] highmem bounce pool size: 64 pages
[    1.646967] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.648197] VFS: Disk quotas dquot_6.5.1
[    1.648251] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

---

### Post by 2Real on 2009-05-02
[    1.648821] fuse init (API version 7.10)
[    1.648898] msgmni has been set to 1698
[    1.649073] alg: No test for stdrng (krng)
[    1.649085] io scheduler noop registered
[    1.649087] io scheduler anticipatory registered
[    1.649089] io scheduler deadline registered
[    1.649100] io scheduler cfq registered (default)
[    1.649221] pci 0000:01:00.0: Boot video device
[    1.654926] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.654959] pcieport-driver 0000:00:01.0: found MSI capability
[    1.654981] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.654990] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.655004] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.655049] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.655089] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.655117] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.655130] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.655141] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.655152] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.655214] pcieport-driver 0000:00:1c.1: setting latency timer to 64

---

### Post by 2Real on 2009-05-02
[    1.655254] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.655281] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.655296] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.655307] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.655318] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.655381] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.655421] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.655448] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.655462] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.655476] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.655487] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.655549] pcieport-driver 0000:00:1c.3: setting latency timer to 64

---

### Post by 2Real on 2009-05-02
[    1.655589] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.655616] pcieport-driver 0000:00:1c.3: irq 2299 for MSI/MSI-X
[    1.655629] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.655641] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.655652] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.655714] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.655754] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.655782] pcieport-driver 0000:00:1c.4: irq 2298 for MSI/MSI-X
[    1.655794] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.655806] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.655818] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.655893] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.656581] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

---

### Post by 2Real on 2009-05-02
[    1.656695] ACPI: AC Adapter [AC0] (on-line)
[    1.689687] ACPI: Battery Slot [BAT0] (battery present)
[    1.689773] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.689776] ACPI: Power Button (FF) [PWRF]
[    1.689843] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.691340] ACPI: Lid Switch [LID]
[    1.691394] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.691403] ACPI: Sleep Button (CM) [SLPB]
[    1.691456] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.691460] ACPI: Power Button (CM) [PWRB]
[    1.691978] ACPI: SSDT 7FFBE0B0, 01E7 (r1    AMI   CPU1PM        1 INTL 20060113)
[    1.692328] processor ACPI_CPU:00: registered as cooling_device0
[    1.692332] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.692583] ACPI: SSDT 7FFBE2A0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[    1.692916] processor ACPI_CPU:01: registered as cooling_device1
[    1.692920] ACPI: Processor [CPU2] (supports 8 throttling states)
[    1.700603] thermal LNXTHERM:01: registered as thermal_zone0
[    1.702095] ACPI: Thermal Zone [TZ00] (60 C)
[    1.702158] isapnp: Scanning for PnP cards...
[    2.055743] isapnp: No Plug & Play device found
[    2.068780] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.069828] brd: module loaded
[    2.070116] loop: module loaded
[    2.070175] Fixed MDIO Bus: probed
[    2.070180] PPP generic driver version 2.4.2
[    2.070231] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.070258] Driver 'sd' needs updating - please use bus_type methods
[    2.070266] Driver 'sr' needs updating - please use bus_type methods
[    2.070305] ahci 0000:03:00.0: version 3.0
[    2.070318] ahci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.084053] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    2.084057] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.084065] ahci 0000:03:00.0: setting latency timer to 64
[    2.084181] scsi0 : ahci
[    2.084255] ata1: SATA max UDMA/133 abar m8192@0xf7efe000 port 0xf7efe100 irq 19
[    2.404049] ata1: SATA link down (SStatus 0 SControl 300)
[    2.420081] ata_piix 0000:00:1f.2: version 2.12
[    2.420091] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.420095] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.576036] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.576111] scsi1 : ata_piix
[    2.576183] scsi2 : ata_piix
[    2.577557] ata2: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.577560] ata3: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.772844] ata2.00: ATA-7: WDC WD1000BEVS-00LAT0, 01.06M01, max UDMA/133
[    2.772848] ata2.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/1)
[    2.788500] ata2.00: configured for UDMA/133
[    2.952575] ata3.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.21, max UDMA/33
[    2.968517] ata3.00: configured for UDMA/33
[    2.970987] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1000BEVS-0 01.0 PQ: 0 ANSI: 5
[    2.971108] sd 1:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.971123] sd 1:0:0:0: [sda] Write Protect is off
[    2.971125] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.971148] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.971205] sd 1:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.971219] sd 1:0:0:0: [sda] Write Protect is off
[    2.971221] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.971243] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.971246]  sda: sda1 sda2 sda3
[    3.005130] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.005179] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    3.006988] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.21 PQ: 0 ANSI: 5
[    3.011206] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.011209] Uniform CD-ROM driver Revision: 3.20
[    3.011309] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.011352] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    3.012004] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.012031] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.012043] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.012047] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.012101] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.015998] ehci_hcd 0000:00:1d.7: debug port 1
[    3.016008] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.016020] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3ffbc00
[    3.028042] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.028127] usb usb1: configuration #1 chosen from 1 choice
[    3.028165] hub 1-0:1.0: USB hub found
[    3.028173] hub 1-0:1.0: 8 ports detected
[    3.028312] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.028327] uhci_hcd: USB Universal Host Controller Interface driver
[    3.028346] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.028352] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.028355] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.028391] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.028414] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a480
[    3.028481] usb usb2: configuration #1 chosen from 1 choice
[    3.028503] hub 2-0:1.0: USB hub found
[    3.028509] hub 2-0:1.0: 2 ports detected
[    3.028584] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.028590] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.028593] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.028632] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.028655] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a800
[    3.028722] usb usb3: configuration #1 chosen from 1 choice
[    3.028744] hub 3-0:1.0: USB hub found
[    3.028750] hub 3-0:1.0: 2 ports detected
[    3.028829] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.028834] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.028837] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.028875] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.028906] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a880
[    3.028967] usb usb4: configuration #1 chosen from 1 choice
[    3.028989] hub 4-0:1.0: USB hub found
[    3.028995] hub 4-0:1.0: 2 ports detected
[    3.029072] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.029078] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.029081] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.029117] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.029147] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ac00
[    3.029213] usb usb5: configuration #1 chosen from 1 choice
[    3.029240] hub 5-0:1.0: USB hub found
[    3.029246] hub 5-0:1.0: 2 ports detected
[    3.029351] usbcore: registered new interface driver libusual
[    3.029378] usbcore: registered new interface driver usbserial
[    3.029388] USB Serial support registered for generic
[    3.029401] usbcore: registered new interface driver usbserial_generic
[    3.029403] usbserial: USB Serial Driver core
[    3.029454] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.031869] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.032517] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.032522] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.032524] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.032527] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.032529] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.036057] mice: PS/2 mouse device common for all mice
[    3.056100] rtc_cmos 00:03: RTC can wake from S4
[    3.056136] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.056164] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    3.056236] device-mapper: uevent: version 1.0.3
[    3.056327] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.056397] device-mapper: multipath: version 1.0.5 loaded
[    3.056399] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.056467] EISA: Probing bus 0 at eisa.0
[    3.056497] EISA: Detected 0 cards.
[    3.056542] cpuidle: using governor ladder
[    3.056544] cpuidle: using governor menu
[    3.057003] TCP cubic registered
[    3.057089] NET: Registered protocol family 10
[    3.057484] lo: Disabled Privacy Extensions
[    3.057787] NET: Registered protocol family 17
[    3.057802] Bluetooth: L2CAP ver 2.11
[    3.057804] Bluetooth: L2CAP socket layer initialized
[    3.057806] Bluetooth: SCO (Voice Link) ver 0.6
[    3.057808] Bluetooth: SCO socket layer initialized
[    3.057829] Bluetooth: RFCOMM socket layer initialized
[    3.057835] Bluetooth: RFCOMM TTY layer initialized
[    3.057837] Bluetooth: RFCOMM ver 1.10
[    3.058314] Using IPI No-Shortcut mode
[    3.058376] registered taskstats version 1
[    3.058501]   Magic number: 9:701:92
[    3.058567] rtc_cmos 00:03: setting system clock to 2009-05-01 20:05:29 UTC (1241208329)
[    3.058570] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.058572] EDD information not available.
[    3.058780] Freeing unused kernel memory: 532k freed
[    3.058894] Write protecting the kernel text: 4128k
[    3.058935] Write protecting the kernel read-only data: 1532k
[    3.088428] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.334669] sky2 driver version 1.22
[    3.334717] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.334730] sky2 0000:02:00.0: setting latency timer to 64
[    3.334783] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 2
[    3.366744] sky2 0000:02:00.0: Marvell Yukon 88E8056 Gigabit Ethernet Controller
[    3.366747]  Part Number: Yukon 88E8056
[    3.366748]  Engineering Level: Rev. 1.2
[    3.366750]  Manufacturer: Marvell
[    3.366829] sky2 0000:02:00.0: irq 2297 for MSI/MSI-X
[    3.369242] sky2 eth0: addr 00:1b:fc:c2:d2:dc
[    3.424528] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    3.429116] ohci1394 0000:08:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.481838] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fbffe800-fbffefff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.715646] usb 1-6: configuration #1 chosen from 1 choice
[    4.161010] PM: Starting manual resume from disk
[    4.161013] PM: Resume from partition 8:3
[    4.161015] PM: Checking hibernation image.
[    4.161181] PM: Resume from disk failed.
[    4.197832] kjournald starting.  Commit interval 5 seconds
[    4.197840] EXT3-fs: mounted filesystem with ordered data mode.
[    4.240059] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    4.421794] usb 3-1: configuration #1 chosen from 1 choice
[    4.672110] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    4.764137] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000740000000001]
[    4.917277] usb 5-1: configuration #1 chosen from 1 choice
[    5.160037] usb 5-2: new full speed USB device using uhci_hcd and address 3
[    5.334291] usb 5-2: configuration #1 chosen from 1 choice
[   15.578329] udev: starting version 141
[   15.821145] acpi device:05: registered as cooling_device2
[   15.821307] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[   15.837193] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.171473] Linux agpgart interface v0.103
[   16.292181] asus-laptop: Asus Laptop Support version 0.42
[   16.294889] asus-laptop: Error calling BSTS
[   16.294961] asus-laptop:   C90S model detected
[   16.296510] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   16.299578] asus-laptop: Brightness ignored, must be controlled by ACPI video driver
[   16.299605] Registered led device: asus::mail
[   16.341162] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   16.393090] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   16.393186] usbcore: registered new interface driver btusb
[   16.666268] intel_rng: FWH not detected
[   16.734680] cfg80211: Calling CRDA to update world regulatory domain
[   17.163935] cfg80211: World regulatory domain updated:
[   17.163939]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.163941]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.163943]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.163945]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.163947]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.163950]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.211082] sdhci: Secure Digital Host Controller Interface driver
[   17.211084] sdhci: Copyright(c) Pierre Ossman
[   17.211431] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04713/0x200000
[   17.212570] sdhci-pci 0000:08:01.1: SDHCI controller found [1180:0822] (rev 22)
[   17.212584] sdhci-pci 0000:08:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.215683] mmc0: SDHCI controller on PCI [0000:08:01.1] using PIO
[   17.257080] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   17.319001] usbcore: registered new interface driver hiddev
[   17.334168] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input9
[   17.344172] generic-usb 0003:046D:C51B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[   17.358077] generic-usb 0003:046D:C51B.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[   17.358106] usbcore: registered new interface driver usbhid
[   17.358132] usbhid: v2.6:USB HID core driver
[   17.359044] iTCO_vendor_support: vendor-support=0
[   17.376171] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   17.376311] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   17.376325] iTCO_wdt: No card detected
[   17.513392] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   17.513396] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   17.513504] iwl3945 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.513517] iwl3945 0000:05:00.0: setting latency timer to 64
[   17.513564] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   17.513848] iwl3945 0000:05:00.0: irq 2296 for MSI/MSI-X
[   17.569368] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   17.570534] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.652908] udev: renamed network interface wlan0 to eth1
[   17.726325] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.726389] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.020145] lp: driver loaded but no devices found
[   18.086986] coretemp coretemp.0: Using relative temperature scale!
[   18.087031] coretemp coretemp.1: Using relative temperature scale!
[   18.174747] Adding 1044216k swap on /dev/sda3.  Priority:-1 extents:1 across:1044216k
[   18.708243] EXT3 FS on sda2, internal journal
[   20.248673] type=1505 audit(1241233546.689:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2160
[   20.290191] type=1505 audit(1241233546.729:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2164
[   20.290289] type=1505 audit(1241233546.729:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2164
[   20.290328] type=1505 audit(1241233546.729:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2164
[   20.290365] type=1505 audit(1241233546.729:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2164
[   20.420448] type=1505 audit(1241233546.861:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2169
[   20.420628] type=1505 audit(1241233546.861:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2169
[   20.445250] type=1505 audit(1241233546.885:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2173
[   23.784324] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.784326] Bluetooth: BNEP filters: protocol multicast
[   23.829399] Bridge firewalling registered
[   25.683750] ppdev: user-space parallel port driver
[   29.564491] sky2 eth0: enabling interface
[   29.564690] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.565318] iwl3945 0000:05:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   29.705970] Registered led device: iwl-phy0:radio
[   29.705993] Registered led device: iwl-phy0:assoc
[   29.706051] Registered led device: iwl-phy0:RX
[   29.706070] Registered led device: iwl-phy0:TX
[   29.718110] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.235910] eth1: authenticate with AP 00:1b:2f:e7:46:0e
[   31.238154] eth1: authenticated
[   31.238158] eth1: associate with AP 00:1b:2f:e7:46:0e
[   31.240365] eth1: RX AssocResp from 00:1b:2f:e7:46:0e (capab=0x421 status=0 aid=902)
[   31.240367] eth1: associated
[   31.241664] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   31.244198] eth1: disassociating by local choice (reason=3)
[   31.646279] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   31.646453] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   39.005697] mtrr: base(0xf5000000) is not aligned on a size(0xe00000) boundary
[   41.984050] eth0: no IPv6 routers present
[   42.140072] eth1: no IPv6 routers present
[   52.803581] eth1: deauthenticated
[  295.929442] mtrr: no MTRR for f5000000,e00000 found
[  345.971661] CPU0 attaching NULL sched-domain.
[  345.971667] CPU1 attaching NULL sched-domain.
[  345.972831] CPU0 attaching sched-domain:
[  345.972834]  domain 0: span 0-1 level MC
[  345.972837]   groups: 0 1
[  345.972844] CPU1 attaching sched-domain:
[  345.972847]  domain 0: span 0-1 level MC
[  345.972849]   groups: 1 0
[  346.330797] eth1: authenticate with AP 00:1b:5b:51:23:e9
[  346.332836] eth1: authenticated
[  346.332840] eth1: associate with AP 00:1b:5b:51:23:e9
[  346.338713] eth1: RX AssocResp from 00:1b:5b:51:23:e9 (capab=0x431 status=0 aid=1)
[  346.338717] eth1: associated
[  346.671345] padlock: VIA PadLock not detected.

---

### Post by Racecar56 on 2009-05-02
dosent look how i thought it would (module is version xxx.xx but the driver version is yyy.yy (e.g. module version is 180.44 however the driver is 180.51). if that actually IS the case, the best idea is to install the older one (the module's version) so the driver matches the module.
so, you still have error right?

---

### Post by 2Real on 2009-05-02
> **Racecar56 said:**
> dosent look how i thought it would (module is version xxx.xx but the driver version is yyy.yy (e.g. module version is 180.44 however the driver is 180.51). if that actually IS the case, the best idea is to install the older one (the module's version) so the driver matches the module.
so, you still have error right?
trying to find a link for the 180.44 drivers

---

### Post by 2Real on 2009-05-02
> **Racecar56 said:**
> dosent look how i thought it would (module is version xxx.xx but the driver version is yyy.yy (e.g. module version is 180.44 however the driver is 180.51). if that actually IS the case, the best idea is to install the older one (the module's version) so the driver matches the module.
so, you still have error right?
same error as my first post :( 
i installed 180.44

---

### Post by 2Real on 2009-05-02
bump still not working :(

---

### Post by 4Orbs on 2009-05-02
Not sure, but it looks like you still have the driver from the .run package installed and it's conflicting with the other attempted installs. Did you ever tell EnvyNg to uninstall their driver after it failed to work? If not, that would be my next step (if it were me).

Then I would try to uninstall the manually installed driver from nvidia's website (the .run package) by stopping the gdm:
```
sudo /etc/init.d/gdm stop
```
Then log in to the black screen (you might need to hit CTL + Alt F1 to bring up the login, blinking cursor). Then unistall the manually installed driver by entering:
```
sudo nvidia-uninstall
```
Then start the gdm:
```
sudo /etc/init.d/gdm start
```
Then log in to the desktop (maybe in low graphics mode, if necessary) and then reboot. Again, login (low graphics,maybe).

Then open up the Hardware Drivers Mgr. and click the button to activate the recommended driver. Then wait, even if the progress doesn't move for five minutes. If it installs correctly you will eventually be prompted to restart the computer.

If it succeeded, you will reboot into the login screen at a different resolution than previously.

Then if you want to change the resolution, open the nvidia settings manager as root:
```
gksudo nvidia-settings
```
Change the resolution as desired, then click the button to save your changes to the xorg.conf file.

And you should probably reboot again to see what might have happened to the login screen.

---

### Post by DJonsson2008 on 2009-05-02
Did you try a fresh re-install, this worked for me with my Nvidia 8400 where other methods failed.

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> Not sure, but it looks like you still have the driver from the .run package installed and it's conflicting with the other attempted installs. Did you ever tell EnvyNg to uninstall their driver after it failed to work? If not, that would be my next step (if it were me).

Then I would try to uninstall the manually installed driver from nvidia's website (the .run package) by stopping the gdm:
```
sudo /etc/init.d/gdm stop
```Then log in to the black screen (you might need to hit CTL + Alt F1 to bring up the login, blinking cursor). Then unistall the manually installed driver by entering:
```
sudo nvidia-uninstall
```Then start the gdm:
```
sudo /etc/init.d/gdm start
```Then log in to the desktop (maybe in low graphics mode, if necessary) and then reboot. Again, login (low graphics,maybe).

Then open up the Hardware Drivers Mgr. and click the button to activate the recommended driver. Then wait, even if the progress doesn't move for five minutes. If it installs correctly you will eventually be prompted to restart the computer.

If it succeeded, you will reboot into the login screen at a different resolution than previously.

Then if you want to change the resolution, open the nvidia settings manager as root:
```
gksudo nvidia-settings
```Change the resolution as desired, then click the button to save your changes to the xorg.conf file.

And you should probably reboot again to see what might have happened to the login screen.
i'm going to try this 

i never got envyNG to work

---

### Post by 2Real on 2009-05-02
i uninstalled and i don't get a driver showing up in hardware drivers

---

### Post by 2Real on 2009-05-02
*bashes head into wall*

---

### Post by 2Real on 2009-05-02
i just broke my resolution

---

### Post by 4Orbs on 2009-05-02
If the resolution is sufficient to work with for the next half hour, don't worry about it for now. That broke because everything was removed properly and completely (which is what you want).

Now open Synaptic Package Mgr and install nvidia common, nvidia modaliases for the 180 driver. Then refresh Synapticreboot and go back to the Hardware Drivers Mgr again and it should show the 180 driver (recommended) is available. Activate the driver and wait for it to finish installing. Remember the progress bar will probably not give you any indication of activity.

And don't mess with the resolution until after the driver is activated.

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> If the resolution is sufficient to work with for the next half hour, don't worry about it for now. That broke because everything was removed properly and completely (which is what you want).

Now open Synaptic Package Mgr and install nvidia common, nvidia modaliases for the 180 driver. Then refresh Synapticreboot and go back to the Hardware Drivers Mgr again and it should show the 180 driver (recommended) is available. Activate the driver and wait for it to finish installing. Remember the progress bar will probably not give you any indication of activity.

And don't mess with the resolution until after the driver is activated.
doesn't show up in hardware drivers

---

### Post by doas777 on 2009-05-02
do a ```
sudo apt-get update
``` and try again

---

### Post by 2Real on 2009-05-02
> **doas777 said:**
> do a ```
sudo apt-get update
``` and try again
still doesn't show up

---

### Post by Racecar56 on 2009-05-02
you did wrong, that was an example

**NOTICE:** this guide assumes you use GNOME (XFCE would work too)
if you use KDE instead of GNOME/XFCE then when you are supposed to do 'sudo /etc/init.d/gdm stop' (or start) [COLOR=Red]_replace gdm with kdm unless you know what you are doing_[/COLOR]

try this in terminal:
```
sudo nvidia-uninstall
```when it says '[sudo] password for user:' (where user would be your username) _type your password [COLOR=Red]even though it looks like it isn't typing[/COLOR]_
[COLOR=Red]**_IMPORTANT:_**[/COLOR]delete any old nvidia driver setups if you have some
then download and install the latest nvidia drivers (180.51 at the time of this writing) _to your home folder_
[nvidia link]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
then go into a tty (ctrl+alt+f1) and then log in with your username and password (again, even though it dosen't look like it's working)
then do this:
```
sudo /etc/init.d/gdm stop && sudo ./NVIDIA*
```then do the setup like this:

[LIST=1]
[*]agree to the license
[*]say no to search for a pre-compiled driver
[*]the setup copys stuff...
[*][COLOR=Red]_**IMPORTANT:**_[COLOR=Black] tell it to auto-configure xorg.conf (it will ask after setup is copying stuff)[/COLOR][/COLOR]
[*][COLOR=Red][COLOR=Black]the setup is done[/COLOR][/COLOR]
[/LIST]
[COLOR=Red][COLOR=Black]then do this after the setup returns you where you left off:
[/COLOR][/COLOR]```
sudo /etc/init.d/gdm start
```that is how i do my nvidia setups
hope this helps
thanks to 4Orbs, ive never known that command (nvidia-uninstall) existed :P

---

### Post by 2Real on 2009-05-02
> **Racecar56 said:**
> you did wrong, that was an example

**NOTICE:** this guide assumes you use GNOME (XFCE would work too)
if you use KDE instead of GNOME/XFCE then when you are supposed to do 'sudo /etc/init.d/gdm stop' (or start) [COLOR=Red]_replace gdm with kdm unless you know what you are doing_[/COLOR]

try this in terminal:
```
sudo nvidia-uninstall
```when it says '[sudo] password for user:' (where user would be your username) _type your password [COLOR=Red]even though it looks like it isn't typing[/COLOR]_
[COLOR=Red]**_IMPORTANT:_**[/COLOR]delete any old nvidia driver setups if you have some
then download and install the latest nvidia drivers (180.51 at the time of this writing) _to your home folder_
[nvidia link]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
then go into a tty (ctrl+alt+f1) and then log in with your username and password (again, even though it dosen't look like it's working)
then do this:
```
sudo /etc/init.d/gdm stop && sudo ./NVIDIA*
```then do the setup like this:

[LIST=1]
[*]agree to the license
[*]say no to search for a pre-compiled driver
[*]the setup copys stuff...
[*][COLOR=Red]_**IMPORTANT:**_[COLOR=Black] tell it to auto-configure xorg.conf (it will ask after setup is copying stuff)[/COLOR][/COLOR]
[*][COLOR=Red][COLOR=Black]the setup is done[/COLOR][/COLOR]
[/LIST]
[COLOR=Red][COLOR=Black]then do this after the setup returns you where you left off:
[/COLOR][/COLOR]```
sudo /etc/init.d/gdm start
```that is how i do my nvidia setups
hope this helps
thanks to 4Orbs, ive never known that command existed :P

sudo nvidia-uninstall - command not found

[FONT=monospace]
sudo /etc/init.d/gdm stop && sudo ./NVIDIA* - seemed to run fine

sudo /etc/init.d/gdm start - ERROR

Ubuntu is running in low-graphics mode

(EE) NVIDIA(0) Failed to load the NVIDIA kernel module
(EE) NVIDIA(0) ***ABORTING***
(EE) Screen(s) found, but none have a usable configuration

:confused:
[/FONT]

---

### Post by Racecar56 on 2009-05-02
shoot, im stumped
maybe you should reinstall

---

### Post by 2Real on 2009-05-02
> **Racecar56 said:**
> shoot, im stumped
maybe you should reinstall
nooo :P

---

### Post by 4Orbs on 2009-05-02
Even though your resolution is messed up, and you can only get the desktop in low-graphics mode, I believe you are in a good spot right now.
The nvidia .run file didn't run because you first need the headers and the tool to compile. But for the next step you should decide which method you prefer for installing the driver: 1. If you install it successfully with the Hardware Drivers Mgr, future updates in Ubuntu should go smoothly because the driver will be managed as part of the update. 2. If you install it successfully with envyNG, you will need to use envyNG to uninstall the driver each time before allowing Ubuntu to perform an update of new kernel (example: update to the new linux .29 kernel from .28), or the driver will break. 3. If you install the driver successfully using the latest .run package from nVidia's website, you'll need to uninstall it before allowing Ubuntu to perform a kernel update (as mentioned previously). But with a manually installed driver, you use the command sudo nvidia-uninstall to remove it.

So, first decide which method above you prefer. I personally prefer the Hardware Drivers Mgr, because the Ubuntu developers eventually smooth out the wrinkles, and you don't need to bother with the driver again once it's working correctly.

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> Even though your resolution is messed up, and you can only get the desktop in low-graphics mode, I believe you are in a good spot right now.
The nvidia .run file didn't run because you first need the headers and the tool to compile. But for the next step you should decide which method you prefer for installing the driver: 1. If you install it successfully with the Hardware Drivers Mgr, future updates in Ubuntu should go smoothly because the driver will be managed as part of the update. 2. If you install it successfully with envyNG, you will need to use envyNG to uninstall the driver each time before allowing Ubuntu to perform an update of new kernel (example: update to the new linux .29 kernel from .28), or the driver will break. 3. If you install the driver successfully using the latest .run package from nVidia's website, you'll need to uninstall it before allowing Ubuntu to perform a kernel update (as mentioned previously). But with a manually installed driver, you use the command sudo nvidia-uninstall to remove it.

So, first decide which method above you prefer. I personally prefer the Hardware Drivers Mgr, because the Ubuntu developers eventually smooth out the wrinkles, and you don't need to bother with the driver again once it's working correctly.

i guess i'd prefer the hardware manager

i couldn't get envyNG to run for some reason

---

### Post by 4Orbs on 2009-05-02
O.K., but when you go to the Hardware Drivers Mgr it shows that there is no driver available for you to activate? But when you first installed Ubuntu there was an available restricted driver for your machine?

If the above is correct, then you need to open Synaptic Package Mgr and mark for installation the nvidia common, nvidia modaliases for your driver number (180), and the 180 driver. Click the button at the top of Synaptic to complete the install of the pieces. Then log out and back in and the 180 driver should show up in the Hardware Drivers Mgr. Then you can activate it and reboot.

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> O.K., but when you go to the Hardware Drivers Mgr it shows that there is no driver available for you to activate? But when you first installed Ubuntu there was an available restricted driver for your machine?

If the above is correct, then you need to open Synaptic Package Mgr and mark for installation the nvidia common, nvidia modaliases for your driver number (180), and the 180 driver. Then log out and back in and the 180 driver should show up in the Hardware Drivers Mgr. Then you can activate it and reboot.
yea when i first installed ubuntu about a year ago i installed the driver for my 8600M GT

i'll go to the package manager and see what i can install

---

### Post by 2Real on 2009-05-02
doesn't show up

---

### Post by 4Orbs on 2009-05-02
Does Synaptic show that the pieces are installed?

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> Does Synaptic show that the pieces are installed?
yea but if i try to do something like enable extra graphics it says cannot find driver or if i try to open nvidia settings it says you appear do not appear to be using the NVIDIA X driver

---

### Post by 4Orbs on 2009-05-02
If synaptic shows the driver is installed, you still need to activate it before you can use desktop effects. And don't try to change the resolution until after the driver is activated. In the case of drivers, "activated" and "installed" don't have the same meaning.

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> If synaptic shows the driver is installed, you still need to activate it before you can use desktop effects. And don't try to change the resolution until after the driver is activated. In the case of drivers, "activated" and "installed" don't have the same meaning.
ok so how do i activate the driver

---

### Post by 4Orbs on 2009-05-02
That is the real problem. If Synaptic shows it is installed, and you have refreshed Synaptic, then the Hardware Drivers Mgr should show the driver is available and recommended. Unless this isn't the proper driver for your nvidia card. Do you have Ubuntu installed on real partitions, or is it on a virtual machine by way of wubi install?

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> That is the real problem. If Synaptic shows it is installed, and you have refreshed Synaptic, then the Hardware Drivers Mgr should show the driver is available and recommended. Unless this isn't the proper driver for your nvidia card. Do you have Ubuntu installed on real partitions, or is it on a virtual machine by way of wubi install?
i have Ubutntu installed on a real partition and my graphics card is an 8600M GT

---

### Post by doas777 on 2009-05-02
> **2Real said:**
> i have Ubutntu installed on a real partition and my graphics card is an 8600M GT
have you enabled all the restriced/multiverse repositories, in System->Administration->Software Sources ?

---

### Post by 2Real on 2009-05-02
> **doas777 said:**
> have you enabled all the restriced/multiverse repositories, in System->Administration->Software Sources ?
haha that was it

---

### Post by 2Real on 2009-05-02
crap i installed the driver and now i get that low graphics mode error again

---

### Post by 4Orbs on 2009-05-02
Happy wobbly windows. The low graphics mode is because you are still stuck with the xorg.conf file you have been using before. Try booting into recovery mode and select the xfix option (fix the graphics by rewriting xorg.conf).

Just for clarification, the driver installation and activation completed and prompted you to reboot?

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> Happy wobbly windows.
i think i'm just doomed

---

### Post by doas777 on 2009-05-02
nah, your prolly almost there.
try resetting your xorg again, and reboot:
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot

```then when your back in, go back to the restricted drivers manager and reapply your driver. The first time I tried 180 in intrepid, it didn't work for me, and i had to use the 177 driver instead. once I got jaunty going, 180 worked flawlessly for my hardware, but may not play nicely with yours just yet.

---

### Post by 2Real on 2009-05-02
> **doas777 said:**
> nah, your prolly almost there.
try resetting your xorg again, and reboot:
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot

```then when your back in, go back to the restricted drivers manager and reapply your driver. The first time I tried 180 in intrepid, it didn't work for me, and i had to use the 177 driver instead. once I got jaunty going, 180 worked flawlessly for my hardware, but may not play nicely with yours just yet.

after
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot

```

computer rebooted fine so i installed the 180 then i got the error again
 i'm going to try installing the 173 drivers from the manager

---

### Post by doas777 on 2009-05-02
> **2Real said:**
> after
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot

```computer rebooted fine so i installed the 180 then i got the error again
 i'm going to try installing the 173 drivers from the manager

there may also be conflicts with the downloaded driver. I'm not sure how to completely uninstall it, but i think it may be in a previous post.

also you can try envy again. if you get an error post it, and lets see if we can attack it from that direction.

---

### Post by 2Real on 2009-05-02
> **doas777 said:**
> there may also be conflicts with the downloaded driver. I'm not sure how to completely uninstall it, but i think it may be in a previous post.

also you can try envy again. if you get an error post it, and lets see if we can attack it from that direction.
arg same low-graphics mode error with 173

ok so how do i use envy? 

i downloaded it from the package manager before and the graphical interface never ran when i clicked on it and when i tried the text interface i got this error when trying to install the nvidia driver

Traceback (most recent call last):
   File "interface.py", line 432, in <module>
     a.mainMenu()
   File "interface.py", line 295, in mainMenu
     a.driverMenu('nvidia')
   File "interface.py", line 322, in driverMenu
     self.driverPage(driver)
   File "interface.py", line 216, in driverPage
     candidateLen.append(len(details['candidate']))
 TypeError: object of type 'NoneType' has no len()

---

### Post by doas777 on 2009-05-02
> **2Real said:**
> arg same low-graphics mode error with 173

ok so how do i use envy? 

i downloaded it from the package manager before and the graphical interface never ran when i clicked on it and when i tried the text interface i got this error when trying to install the nvidia driver

Traceback (most recent call last):
   File "interface.py", line 432, in <module>
     a.mainMenu()
   File "interface.py", line 295, in mainMenu
     a.driverMenu('nvidia')
   File "interface.py", line 322, in driverMenu
     self.driverPage(driver)
   File "interface.py", line 216, in driverPage
     candidateLen.append(len(details['candidate']))
 TypeError: object of type 'NoneType' has no len()
.

what do you get from
```
python --version
```

---

### Post by 2Real on 2009-05-02
> **doas777 said:**
> .

what do you get from
```
python --version
```

Python 2.6.2

---

### Post by BslBryan on 2009-05-02
Okay, I had the exact same problem you do, and I've had to do this multiple times.  First, just for good measure, uninstall the drivers you've downloaded (again.) :P by following the instructions that the community has given you.

Then, uninstall envy (just in case you still have it on your computer.)
```
sudo apt-get remove envy
sudo apt-get remove envyng
sudo rm -R /usr/share/envy
```

Then, 
```
sudo apt-get install envyng-qt
```

The GUI will be available in Applications --> System Tools
But if you want, you can get it by typing in terminal, or konsole, as someone mentioned you might have KDE,
```
sudo envyng -t
```

Then follow the instructions on the GUI.

The first time I did that, it worked flawlessly.

Then I tried to configure a second screen for my tv, and I completely messed up everything, and had to reinstall envy.  For some reason, it did not work correctly the first time running it, but worked after that.

Just use your knowledge and common sense, and you should be fine.  

If it still doesn't work, though, let us know? :)

Good luck.

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Okay, I had the exact same problem you do, and I've had to do this multiple times.  First, just for good measure, uninstall the drivers you've downloaded (again.) :P by following the instructions that the community has given you.

Then, uninstall envy (just in case you still have it on your computer.)
```
sudo apt-get remove envy
sudo apt-get remove envyng
sudo rm -R /usr/share/envy
```Then, 
```
sudo apt-get install envyng-qt
```The GUI will be available in Applications --> System Tools
But if you want, you can get it by typing in terminal, or konsole, as someone mentioned you might have KDE,
```
sudo envyng -t
```Then follow the instructions on the GUI.

The first time I did that, it worked flawlessly.

Then I tried to configure a second screen for my tv, and I completely messed up everything, and had to reinstall envy.  For some reason, it did not work correctly the first time running it, but worked after that.

Just use your knowledge and common sense, and you should be fine.  

If it still doesn't work, though, let us know? :)

Good luck.

i got Envy to work and it installed the 180.44 driver but then when i rebooted i got the ubuntu is running in low-graphics mode error again :confused:

---

### Post by BslBryan on 2009-05-02
Run envy again, obviously click on NVIDIA, and uninstall the driver with the GUI, and reboot.

Then, instead of manually selecting the driver, select Automatic Hardware Detection.

---

### Post by Racecar56 on 2009-05-02
> **2Real said:**
> i got Envy to work and it installed the 180.44 driver but then when i rebooted i got the ubuntu is running in low-graphics mode error again :confused:
hope you get this fixed

by the way thanks everyone for helping... im not too good when it comes to nvidia problems

first post of 7th page

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Run envy again, obviously click on NVIDIA, and uninstall the driver with the GUI, and reboot.

Then, instead of manually selecting the driver, select Automatic Hardware Detection.

it doesn't give me the choice for automatic only compatible and recommended

---

### Post by 4Orbs on 2009-05-02
When you first installed Ubuntu, did you change the screen resolution before you tried to activate the driver? If so, you might try logging into low graphics mode and reset the resolution to default or auto. I'm assuming that, if you did change it before, that you used the "Display" settings from the Admin menu. If changing the resolution now has any affect, try rebooting afterwards.

If that doesn't help, I'd like to see your /etc/X11/xorg.conf file, if you don't mind posting it.

---

### Post by BslBryan on 2009-05-02
Hmm...  You did download EnvyNG, right?  

Maybe you have a more updated version than I do?

Okay...  So, what did you select the first time (when it didn't work)?

Try the opposite.

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Hmm...  You did download EnvyNG, right?  

Maybe you have a more updated version than I do?

Okay...  So, what did you select the first time (when it didn't work)?

Try the opposite.
i selected 180.44 which was compatible and recommended and it didn't work

---

### Post by BslBryan on 2009-05-02
Can you post a screenshot of the Envy interface?

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> When you first installed Ubuntu, did you change the screen resolution before you tried to activate the driver? If so, you might try logging into low graphics mode and reset the resolution to default or auto. I'm assuming that, if you did change it before, that you used the "Display" settings from the Admin menu. If changing the resolution now has any affect, try rebooting afterwards.

If that doesn't help, I'd like to see your /etc/X11/xorg.conf file, if you don't mind posting it.
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "dri"
    Load    "GLcore"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nv"
EndSection

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Can you post a screenshot of the Envy interface?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=112213&stc=1&d=1241308765[/IMG]

---

### Post by BslBryan on 2009-05-02
Have you tried uninstalling the current driver with envy, and then installing 173.14.16?

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Have you tried uninstalling the current driver with envy, and then installing 173.14.16?
yes and that did not work
i'll try it again to verify

---

### Post by 4Orbs on 2009-05-02
When you say it didn't work, do you mean that the installation did not complete; or that it installed (according to envy) correctly, but you still boot into low graphics?

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> When you say it didn't work, do you mean that the installation did not complete; or that it installed (according to envy) correctly, but you still boot into low graphics?
installed according to envy and then boots up to the "ubuntu is running in low-graphics mode" error

---

### Post by BslBryan on 2009-05-02
When you get that message, what do you do?  Do you ignore and continue booting up, or do you configure anything?

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> When you get that message, what do you do?  Do you ignore and continue booting up, or do you configure anything?
i don't know what to do at that screen i'm assuming it didn't install properly since it says 

failed to load the NVIDIA kernel module

---

### Post by BslBryan on 2009-05-02
Okay, forget envy.  It's not working.  What I want you to do is go [here]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html") and download the nVIDIA Linux driver that's supposed to work with your card.

I think there are instructions there, but post here if you need help.  Then, after install, reboot.  Then, run 
```
cat /etc/X11/xorg.conf | grep Driver
```
See the last two lines that say "driver"?  You have to manually edit the xorg.conf file line where it says that with 
```
nvidia
```

Then, 
```
modprobe nvidia

```
to start it.

Now reboot.  Tell us what happens.  I'm almost out of ideas.

---

### Post by Racecar56 on 2009-05-02
> **BslBryan said:**
> Okay, forget envy.  It's not working.  What I want you to do is go [here]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html") and download the nVIDIA Linux driver that's supposed to work with your card.

I think there are instructions there, but post here if you need help.  Then, after install, reboot.  Then, run 
```
cat /etc/X11/xorg.conf | grep Driver
```See the last two lines that say "driver"?  You have to manually edit the xorg.conf file line where it says that with 
```
nvidia
```Then, 
```
modprobe nvidia

```to start it.

Now reboot.  Tell us what happens.  I'm almost out of ideas.
nice one
im pretty sure that will help

---

### Post by BslBryan on 2009-05-02
Thanks, buddy.  

I've got my fingers crossed for him. :popcorn:

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Okay, forget envy.  It's not working.  What I want you to do is go [here]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html") and download the nVIDIA Linux driver that's supposed to work with your card.

I think there are instructions there, but post here if you need help.  Then, after install, reboot.  Then, run 
```
cat /etc/X11/xorg.conf | grep Driver
```See the last two lines that say "driver"?  You have to manually edit the xorg.conf file line where it says that with 
```
nvidia
```Then, 
```
modprobe nvidia

```to start it.

Now reboot.  Tell us what happens.  I'm almost out of ideas.

no when i'm trying to install the drive manually i'm getting this error

unable to open /usr/lib/xorg/modules/extensions/libglx.so for reading (no such file or directory)

aaahhhhh

got through installation though now i'm trying the 2nd part

---

### Post by BslBryan on 2009-05-02
You did download 
NVIDIA-Linux-x86-100.14.19-pkg1.run

And then 
```
sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```
right?

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> You did download 
NVIDIA-Linux-x86-100.14.19-pkg1.run

And then 
```
sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```right?

oh i downloaded ...180.51 because that's what the nvidia site said i should get lol

---

### Post by doas777 on 2009-05-02
just to make sure, your running a 32 bit version of ubuntu right?

---

### Post by BslBryan on 2009-05-02
Haha, I do that occasionally. :)

Anyway, keep us updated.

---

### Post by 2Real on 2009-05-02
> **doas777 said:**
> just to make sure, your running a 32 bit version of ubuntu right?
yes

---

### Post by 2Real on 2009-05-02
this is the error i get when trying to install the 100 driver

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat May  2 18:00:15 2009

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> There appears to already be a driver installed on your system (version: 180.
   51).  As part of installing this driver (version: 100.14.19), the existing d
   river will be uninstalled.  Are you sure you want to continue? ('no' will ab
   ort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-11-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by 4Orbs on 2009-05-02
To install a driver manually, you need to fetch the headers and tool before running the .run package.
```
sudo apt-get install build-essential
```
then
```
sudo apt-get install linux-headers-generic linux-source-2.6.28
```
then stop gdm:
```
sudo /etc/init.d/gdm stop
```
then hit CTL+Alt F2 to bring up the black screen login, then login and move yourself to the directory where the .run package was saved:
```
cd Desktop
```
Then run the .run package:
```
sudo sh NVIDIA-insert-correct-filename-here.run
```
Answer yes and ok to all the questions presented. After the package builder finishes installing the driver, start gdm:
```
sudo /etc/init.d/gdm start
```
Log in, then reboot. You should see the login screen at a different resolution now (maybe). You will probably see the green nvidia logo for a moment. Login, but DON'T try to activate the driver from Hardware Drivers Mgr, because it was activated during the compile and install. If you made it this far, DON'T try to enable any effects yet.

---

### Post by doas777 on 2009-05-02
have you installed the kernel source (header files) and the build-essentials packages? you may have to enable the sources repository. you should be albe to find both in synaptic

---

### Post by BslBryan on 2009-05-02
> **4Orbs said:**
> To install a driver manually, you need to fetch the headers and tool before running the .run package.
```
sudo apt-get install build-essential
```
then
```
sudo apt-get install linux-headers-generic linux-source-2.6.28
```
then stop gdm:
```
sudo /etc/init.d/gdm stop
```
then hit CTL+Alt F2 to bring up the black screen login, then login and move yourself to the directory where the .run package was saved:
```
cd Desktop
```
Then run the .run package:
```
sudo sh NVIDIA-insert-correct-filename-here.run
```
Answer yes and ok to all the questions presented. After the package builder finishes installing the driver, start gdm:
```
sudo /etc/init.d/gdm start
```
Log in, then reboot. You should see the login screen at a different resolution now (maybe). You will probably see the green nvidia logo for a moment. Login, but DON'T try to activate the driver from Hardware Drivers Mgr, because it was activated during the compile and install. If you made it this far, DON'T try to enable any effects yet.

+1.  Also, write this down.  These instructions will make you go blind (no GUI at all, just a shell, kind of like Windows Safe Mode with Command Prompt.)

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> To install a driver manually, you need to fetch the headers and tool before running the .run package.
```
sudo apt-get install build-essential
```then
```
sudo apt-get install linux-headers-generic linux-source-2.6.28
```then stop gdm:
```
sudo /etc/init.d/gdm stop
```then hit CTL+Alt F2 to bring up the black screen login, then login and move yourself to the directory where the .run package was saved:
```
cd Desktop
```Then run the .run package:
```
sudo sh NVIDIA-insert-correct-filename-here.run
```Answer yes and ok to all the questions presented. After the package builder finishes installing the driver, start gdm:
```
sudo /etc/init.d/gdm start
```Log in, then reboot. You should see the login screen at a different resolution now (maybe). You will probably see the green nvidia logo for a moment. Login, but DON'T try to activate the driver from Hardware Drivers Mgr, because it was activated during the compile and install. If you made it this far, DON'T try to enable any effects yet.

i did this and i still get the error with the 100 drivers 
i don't think they're meant for my card

---

### Post by BslBryan on 2009-05-02
Did you combine both of our sets of instructions?  You will still have to edit xorg.conf, for example.

---

### Post by doas777 on 2009-05-02
this line is key:
sudo apt-get install linux-headers-generic linux-source-2.6.28

---

### Post by 4Orbs on 2009-05-02
When you did this, did the nvidia installer tell you there was another driver installed that it needed to remove?

---

### Post by ed-koala on 2009-05-02
Hopefully I *may* have an answer for you.

The culprit could be in your xorg.conf file.  It should read:

```
	Driver 		"nvidia"
```

in the Device section.  I believe nv is for lagacy drivers, and is going to mess up your resolution.

Just verify you have the 180.xx stuff installed, and edit the xorg.conf file and reboot.

If this doesn't work, I have another idea.

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Did you combine both of our sets of instructions?  You will still have to edit xorg.conf, for example.
yea but the 100 drivers wont even install

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> When you did this, did the nvidia installer tell you there was another driver installed that it needed to remove?
no

---

### Post by BslBryan on 2009-05-02
> **ed-koala said:**
> If this doesn't work, I have another idea.

I think we're all ears.  We're stumped here.

---

### Post by 2Real on 2009-05-02
> **ed-koala said:**
> Hopefully I *may* have an answer for you.

The culprit could be in your xorg.conf file.  It should read:

```
    Driver         "nvidia"
```in the Device section.  I believe nv is for lagacy drivers, and is going to mess up your resolution.

Just verify you have the 180.xx stuff installed, and edit the xorg.conf file and reboot.

If this doesn't work, I have another idea.

ok how do completely wipe a driver and make sure it's uninstalled
i think i need to start fresh here i've done so many things lol

---

### Post by 4Orbs on 2009-05-02
I'm thinking that at some point earlier in the day, you probably had one of the drivers correctly installed, but the xorg.conf was messing it up. You might take a look at the xorg.conf-backup to see if it is any different than the one you posted here. If it is different, rename the current xorg.conf to xorg.conf-goofy then rename the backup to replace the current one. Reboot. Clue us in.

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> I'm thinking that at some point earlier in the day, you probably had one of the drivers correctly installed, but the xorg.conf was messing it up. You might take a look at the xorg.conf-backup to see if it is any different than the one you posted here. If it is different, rename the current xorg.conf to xorg.conf-goofy then rename the backup to replace the current one. Reboot. Clue us in.
ok should i reinstall the 180.51 drivers?

---

### Post by ed-koala on 2009-05-02
Ok, here's hoping ...

I had a problem similar, but not the same, and I had to do some hoop jumping, and some of my solution might work for you.  This shouldn't hurt things . . .

First, open Synaptic and make sure the following packages are installed:

make
gcc
build-essential
dkms
linux-headers-2.6.28-11.42 (assumes you use the current kernel)
linux-headers-2.6.28-11.42-generic
linux-generic
linux-headers-generic
module-assistant

Next, make sure the following are NOT installed, and use the "Mark for complete removal" option if any need to be removed:

ALL nvidia pkgs (search for nvidia)
ANY old kernel pkgs, ie linux-headers-2.6.27-X and earlier, etc.
(This might not be necessary, but I did it anyway)

Go to System-Administration-Hardware Drivers and choose 180.44 and activate the driver - DO NOT REBOOT yet!!!

<If you have nothing to activate in hardware drivers, then go to Synaptic and install:>

nvidia-180-lidvdpau
nvidia-180-kernel source
nvidia-settings
nvidia-common


Open terminal and type:

```
sudo gedit /etc/X11/xorg.conf

```

Replace the graphics "Device" section with the following:

Section "Device"
     Identifier      "Configured Video Device"
     Driver          "nvidia"
EndSection

Reboot, and hopefully you'll enjoy your working nvidia graphics.

---

### Post by BslBryan on 2009-05-02
> **ed-koala said:**
> ...and hopefully you'll enjoy your working nvidia graphics.

I think this might be what helps you out.  If it doesn't work, try what 4Orbs said and attempt to reinstall the nVidia driver, and just use 

```
gksudo gedit /etc/X11/xorg.conf
```

to change the driver line to "nvidia".

---

### Post by 2Real on 2009-05-02
> **ed-koala said:**
> Ok, here's hoping ...

I had a problem similar, but not the same, and I had to do some hoop jumping, and some of my solution might work for you.  This shouldn't hurt things . . .

First, open Synaptic and make sure the following packages are installed:

make
gcc
build-essential
dkms
linux-headers-2.6.28-11.42 (assumes you use the current kernel)
linux-headers-2.6.28-11.42-generic
linux-generic
linux-headers-generic
module-assistant

Next, make sure the following are NOT installed, and use the "Mark for complete removal" option if any need to be removed:

ALL nvidia pkgs (search for nvidia)
ANY old kernel pkgs, ie linux-headers-2.6.27-X and earlier, etc.
(This might not be necessary, but I did it anyway)

Go to System-Administration-Hardware Drivers and choose 180.44 and activate the driver - DO NOT REBOOT yet!!!

<If you have nothing to activate in hardware drivers, then go to Synaptic and install:>

nvidia-180-lidvdpau
nvidia-180-kernel source
nvidia-settings
nvidia-common


Open terminal and type:

```
sudo gedit /etc/X11/xorg.conf

```Replace the graphics "Device" section with the following:

Section "Device"
     Identifier      "Configured Video Device"
     Driver          "nvidia"
EndSection

Reboot, and hopefully you'll enjoy your working nvidia graphics.

i don't see nvidia-180-lidvdpau i only see
nvidia-180-modaliasses

---

### Post by ed-koala on 2009-05-02
It should be there, had it wrote wrong - nvidia-180-libvdpau

---

### Post by BslBryan on 2009-05-02
```
sudo apt-get install nvidia-180-lidvdpau
```

This is a really good way to simultaneously check if it's installed, and if it's not, it installs automatically.

---

### Post by ed-koala on 2009-05-02
This was originally written when running Intrepid, so a few things have changed and I'm still sorting out what, but everything should always use the latest version.

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> ```
sudo apt-get install nvidia-180-lidvdpau
```This is a really good way to simultaneously check if it's installed, and if it's not, it installs automatically.
  got this error when trying to use that command 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by BslBryan on 2009-05-02
Close Synaptic package manager.  Also, if you are downloading something in synaptic you will also get that message.

If this doesn't work, I've got something simple you can try.  I know you're tired of trying new stuff, but don't give up yet. :-)

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Close Synaptic package manager.  Also, if you are downloading something in synaptic you will also get that message.

If this doesn't work, I've got something simple you can try.  I know you're tired of trying new stuff, but don't give up yet. :-)


sudo apt-get install nvidia-180-lidvdpau
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nvidia-180-lidvdpau


lol

---

### Post by ed-koala on 2009-05-02
I'm not sure, but I recommend using Synaptic for this only because I know it worked for me.  And, you can see if the package is actually in the repository.

---

### Post by BslBryan on 2009-05-02
apt-get is the same thing as synaptic, it's just not GUI.  It's also quicker and doesn't freeze as often.  Why don't you want him using apt-get?

Anyway, Ed-Koala is trying hard to make sure that stuff from his instructions are right for you.  Until then, I'm curious...  Have you tried going to
System --> Administration --> Hardware Drivers, and enabling the nVIDIA driver that's listed?  

If not, do, and restart.  

Then press alt-f2 and run ```
gksu nvidia-settings
``` and set the resolution there.

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> apt-get is the same thing as synaptic, it's just not GUI.  It's also quicker and doesn't freeze as often.  Why don't you want him using apt-get?

Anyway, Ed-Koala is trying hard to make sure that stuff from his instructions are right for you.  Until then, I'm curious...  Have you tried going to
System --> Administration --> Hardware Drivers, and enabling the nVIDIA driver that's listed?  

If not, do, and restart.  

Then press alt-f2 and run ```
gksu nvidia-settings
``` and set the resolution there.
 
arg the drivers don't show up in hardware drivers any more

---

### Post by ed-koala on 2009-05-02
[I]<If you have nothing to activate in hardware drivers, then go to Synaptic and install:>

nvidia-180-lidvdpau
nvidia-180-kernel source
nvidia-settings
nvidia-common[/I]

That will make the drivers show up in restricted drivers

and i spelled lidvdpau wrong, it should be **nvidia-180-libvdpau**

---

### Post by ed-koala on 2009-05-02
I just prefer the GUI, I know it takes care of all those nagging details on it's own. Wasn't sure about the command line, that's all.

---

### Post by 2Real on 2009-05-02
ok i'm installing the 180 driver from hardware drivers right now

---

### Post by 2Real on 2009-05-02
ok 180 drivers activated what's the next step

---

### Post by ed-koala on 2009-05-02
just scroll up and follow the guide step by step. you're getting there :)

---

### Post by 4Orbs on 2009-05-02
And you rebooted and didn't have to log in to low graphics mode?

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> And you rebooted and didn't have to log in to low graphics mode?
rebooting right now i'll post if i'm in low graphics mode

---

### Post by BslBryan on 2009-05-02
Reboot.

Then, press alt-f2 and run 
```
gksu nvidia-settings
```

And select the resolution from the list.

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Reboot.

Then, press alt-f2 and run 
```
gksu nvidia-settings
```And select the resolution from the list.

low-graphics mode error

should i do this anyway?

---

### Post by BslBryan on 2009-05-02
Yes.  Just see if it works.

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> Yes.  Just see if it works.

GTK-warning cannot open display

---

### Post by ed-koala on 2009-05-02
Yup, won't hurt.  If things are still not right, check these:

1.  Are the restricted drivers showing up in the hardware drivers list?

2.  Check your xorg.conf file. Does it have the changes you made?

3.  Double check, thru Synaptic so you can see it in black and white, if all the packages mentioned in my original post are installed.

Let me know the results please.

---

### Post by 2Real on 2009-05-02
> **ed-koala said:**
> Yup, won't hurt.  If things are still not right, check these:

1.  Are the restricted drivers showing up in the hardware drivers list?

2.  Check your xorg.conf file. Does it have the changes you made?

3.  Double check, thru Synaptic so you can see it in black and white, if all the packages mentioned in my original post are installed.

Let me know the results please.

Section "Device"
    Identifier     "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

and still doesn't work

---

### Post by BslBryan on 2009-05-02
That's good!  

```
noLogo = "true"
```
means that the driver has been installed, and is functioning!

Now, why it's not working correctly is puzzling even more.

---

### Post by ed-koala on 2009-05-02
Are the drivers showing in the driver list?  Is it activated?
Are all the packages installed?

---

### Post by 2Real on 2009-05-02
> **ed-koala said:**
> Are the drivers showing in the driver list?  Is it activated?
Are all the packages installed?
yea i installed all the nvidia packages through package manager

---

### Post by ed-koala on 2009-05-02
Hmmm, well, if the driver is activated, why it won't work is a bit of a mystery.  I'm out of ideas, I thought that would do the trick.

Wish I could help. If I think of something I'll be sure to let you know.

---

### Post by 4Orbs on 2009-05-02
For clarification:
You activated the 180 driver successfully, and the Hardware Drivers Mgr now says the driver is activated or not activated? You are now in Low graphics mode, or not?

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> For clarification:
You activated the 180 driver successfully, and the Hardware Drivers Mgr now says the driver is activated or not activated? You are now in Low graphics mode, or not?

what happens is it gives me the low graphics mode error and then i pick run this one session in low graphics mode

when i try to start up nvidia setting manager it says i'm not running the x server driver

---

### Post by ed-koala on 2009-05-02
2Real, please check the System - Administration - Hardware drivers and see if the driver is there AND ACTIVATED.  If so, this may now be just a matter of setting the resolution properly.

---

### Post by BslBryan on 2009-05-02
What are the other options when the low graphics mode message comes up?

---

### Post by 4Orbs on 2009-05-02
In you System Administration menu, is there an nVidia X Server Settings button available?

---

### Post by 2Real on 2009-05-02
> **ed-koala said:**
> 2Real, please check the System - Administration - Hardware drivers and see if the driver is there AND ACTIVATED.  If so, this may now be just a matter of setting the resolution properly.

"this driver is currently activated but not in use"

---

### Post by 2Real on 2009-05-02
> **BslBryan said:**
> What are the other options when the low graphics mode message comes up?
umm revert to working or set generic or boot into low graphics for one session

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> In you System Administration menu, is there an nVidia X Server Settings button available?
yes, but it says the nvidia driver is not in use

---

### Post by ed-koala on 2009-05-02
is there an option to enable it?

---

### Post by Racecar56 on 2009-05-02
did you install libvdpau?

---

### Post by 2Real on 2009-05-02
> **ed-koala said:**
> is there an option to enable it?
no only to remove it

---

### Post by 2Real on 2009-05-02
> **Racecar56 said:**
> did you install libvdpau?
it said i had the most up to date one

---

### Post by ed-koala on 2009-05-02
Strange.  All I can do is post the instructions (correctly edited and updated) so you can check it line by line against what is on your system. Just check, don't do anything.  If you find something not right, then go back to the beginning and follow the guide line by line ****exactly**** (yes, this includes using Synaptic) and check the results.

Something's definately off or the driver would be in use.  But just what is off, we'll have to see ... it might be another issue tho I doubt it.

---

### Post by ed-koala on 2009-05-02
Ooops, it helps to post this huh?  **The sections in red apply to dual graphic card systems. Thus they were not in my first post and should not be done unless you have 2 video cards.**

First, open Synaptic and make sure the following pkgs are installed:

make
gcc
build-essential
dkms
linux-headers-2.6.27-9 (assumes you use the current kernel)
linux-headers-2.6.27-9-generic
linux-generic
linux-headers-generic
module-assistant

Next, make sure the following are NOT installed, and use the "Mark for complete removal option" if any need to be removed:

ALL nvidia pkgs (search for nvidia)
Any old kernel pkgs, ie linux-headers-2.6.27-7 and earlier, etc
(This might not be necessary, but I did it anyway)


[COLOR="Red"]Now, perform the following command in a terminal:[/COLOR]

```
[COLOR="Red"]sudo lspci | grep VGA[/COLOR]
```

[COLOR="Red"]The output will look something like this:[/COLOR]

```
[COLOR="Red"]
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)[/COLOR]

```

[COLOR="Red"]Write down the number begining each line.[/COLOR]

Go to System-Administration-Hardware Drivers and choose 180.44 and activate the driver - DO NOT REBOOT yet!!!

*<If you have nothing to activate in hardware drivers, then go to Synaptic and install:>*

nvidia-180-libvdpau
nvidia-180-kernel source
nvidia-settings
nvidia-common

Open terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

Replace the graphics "Device" section with the following:

```

Section "Device"
Identifier "Configured Video Device"
[COLOR="Red"]BusID "PCI:**1**:0:0"[/COLOR]
Driver "nvidia"
EndSection

```

[COLOR="Red"]Edit the BusID line to reflect the number you wrote down earlier (for me, that would be "PCI:2:0:0". *****MAKE SURE***** you use all colons as shown, and add the PCI part as shown.

If you have sli, add the following:[/COLOR]

```
[COLOR="Red"]Option "sli" "auto"[/COLOR]
```

Save the file, reboot and you should have 3d graphics working.

[COLOR="Red"]**Note** - for dual graphics PCs, you may boot to a black screen but you'll hear the normal boot sounds. If that happens, you used the wrong number in BusID. Change it to the other number OR plug your monitor into the other card.[/COLOR]

---

### Post by 2Real on 2009-05-02
k i'll do this in a sec

---

### Post by 4Orbs on 2009-05-02
I feel that, since the Hardware Drivers Mgr shows it Activated but Not in Use, that rewriting the xorg.conf back to default might allow the driver to function (which is where the other posters were headed). Maybe a good idea to set the resolution back to whatever the installed default was before doing this.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It may work this time around.

---

### Post by BslBryan on 2009-05-02
Okay, well a couple more suggestions.

The first is this:
[Download]("http://www.nvidia.com/Download/index.aspx?lang=en-us") the latest driver from nVIDIA.

Then
```
sudo apt-get install build-essential
```

Then
```
sudo apt-get remove nvidia*
```

This should get rid of all unwanted nVIDIA drivers.  You might check /lib/linux-restricted-modules/2.6.24.xx-generic/video and make sure there's no nVIDIA directory in there.

Then (now, here's where you might want to write it down, because it will be blind again.)

```
ctrl+alt+backspace
```
Wait for the drop out of X11.

Then, login to the terminal as yourself.

```
cd /wherever/you/saved/the/driver
```

```
chmod a+x NVIDIA-Linux-x86-173.14.05-pkg1.run
```
The numbers might be different, because I just guessed at remembering the filename.  

Then, 
```
sudo sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
```

Follow the directions on the screen.

Then, 

```
sudo reboot now
```

If that doesn't work, I have one more idea. :)

---

### Post by ed-koala on 2009-05-02
Just one note about the direct install method ... if the kernel changes you'll have to reinstall the driver.

---

### Post by 2Real on 2009-05-02
> **4Orbs said:**
> I feel that, since the Hardware Drivers Mgr shows it Activated but Not in Use, that rewriting the xorg.conf back to default might allow the driver to function (which is where the other posters were headed). Maybe a good idea to set the resolution back to whatever the installed default was before doing this.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```It may work this time around.

this unactivated the driver

---

### Post by BslBryan on 2009-05-02
Since it is now inactive, please try my approach.

Good luck.  :-)

---

### Post by 4Orbs on 2009-05-03
And reactivating it puts you right back to low graphics mode? Geez.

---

### Post by BslBryan on 2009-05-03
> **4Orbs said:**
> And reactivating it puts you right back to low graphics mode? Geez.

Haha, this is a tricky one.  I feel compelled to get it working, too. :)

---

### Post by ed-koala on 2009-05-03
Perhaps adding resolution settings to xorg.conf might help?  What does everyone think?  Been awhile since I did that myself so I'd have to look up the code, but I'd like to know if you think it'll make a difference.

---

### Post by BslBryan on 2009-05-03
Tried it a couple of pages ago.  Didn't help. :P

---

### Post by 4Orbs on 2009-05-03
Now to recap; If I understand correctly, you were originally running Intrepid successfully with the 180 driver, then upgraded to Jaunty where  the 180 is still the recommended driver but it doesn't work in Jaunty. You can activate the driver, but it says Activated but Not in Use, and you are forced to log in to a low graphics mode desktop... where you are unable to access the nvidia settings mgr because the driver is activated but not in use. You are not running dual video cards.

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Since it is now inactive, please try my approach.

Good luck.  :-)
trying lol i think i'm just cursed

---

### Post by 2Real on 2009-05-03
with Bryan's method i get this error

ubuntu is running in low-graphics mode

failed to load module type 1 module does not exist 
failed to load module freetype 
failed to load the NVIDIA kernel module

---

### Post by ed-koala on 2009-05-03
I think I know what will work ... a blend of things.

Follow this part of my post, then follow the direct install method posted.  If that doesn't work, I'm beginning to think hardware glitch. (lol, hope I'm just being nuts)



First, open Synaptic and make sure the following pkgs are installed:

make
gcc
build-essential
dkms
linux-headers-2.6.27-9 (assumes you use the current kernel)
linux-headers-2.6.27-9-generic
linux-generic
linux-headers-generic
module-assistant

Next, make sure the following are NOT installed, and use the "Mark for complete removal option" if any need to be removed:

ALL nvidia pkgs (search for nvidia)
Any old kernel pkgs, ie linux-headers-2.6.27-7 and earlier, etc
(This might not be necessary, but I did it anyway)

---

### Post by 2Real on 2009-05-03
then it asks

run ubuntu in low-graphics mode for just one session
reconfigure graphics 
trouble shoot
exit to console login

---

### Post by BslBryan on 2009-05-03
Are you going to have him install envy after removing nVIDIA's drivers?  That occurred to me, as well.  (Assuming this is actually what you're going to say to do.) :P

2Real, try troubleshooting/reconfiguring graphics.  It can't hurt.

---

### Post by ed-koala on 2009-05-03
No, I'm thinking if he gets the packages set, then installing the driver directly from nvidia HAS to work, or it's not really the driver at fault.

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Are you going to have him install envy after removing nVIDIA's drivers?  That occurred to me, as well.  (Assuming this is actually what you're going to say to do.) :P

2Real, try troubleshooting/reconfiguring graphics.  It can't hurt.
trouble shoot just asks

review the xserver log file
review the start up errors
edit cofig file
archive config and logs

---

### Post by BslBryan on 2009-05-03
Try reconfiguring graphics, and if that doesn't do anything, listen to ed-koala.  If he doesn't solve it, I've got one more thing for you to try.  After that, I think I'm out of ideas. :(

We'll get it, though.  I'm sure. :)

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Try reconfiguring graphics, and if that doesn't do anything, listen to ed-koala.  If he doesn't solve it, I've got one more thing for you to try.  After that, I think I'm out of ideas. :(

We'll get it, though.  I'm sure. :)
lol :popcorn:

---

### Post by 4Orbs on 2009-05-03
When was the last time you had a working driver? The 180 driver on Intrepid?

---

### Post by BslBryan on 2009-05-03
Haha, for real.  Look how many posts you've gotten out of this one thread.  :lol:

---

### Post by ed-koala on 2009-05-03
Those package installs came from nvidia's web site on how to install their driver (or they used to be there). That's why I figure doing that, then installing like nvidia instucts on their web site, *HAS* to work. The only other answers then are compatibility issue, hardware issue (doubtful), or something else unknown.

---

### Post by BslBryan on 2009-05-03
Yeah, but screen resolution being incorrect is one of the first things I have to deal with when installing an OS, and it always puts a bit of a bad taste in my mouth.  I think that that alone will cause me to write a patch to make it work some time tonight. :)

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Try reconfiguring graphics, and if that doesn't do anything, listen to ed-koala.  If he doesn't solve it, I've got one more thing for you to try.  After that, I think I'm out of ideas. :(

We'll get it, though.  I'm sure. :)
trying ed's way now reconfigure didn't work

---

### Post by 4Orbs on 2009-05-03
Just remember that when you install a driver manually, don't try to activate it with the Hardware Drivers Mgr. That will mess it up because the Hardware Drivers Mgr doesn't work with manually installed drivers.

Man, if you could get to your nvidia settings mgr just once and change the resolution and save those settings to the xorg.conf, you'd be on easy street.

---

### Post by BslBryan on 2009-05-03
> **4orbs said:**
> just remember that when you install a driver manually, don't try to activate it with the hardware drivers mgr. That will mess it up because the hardware drivers mgr doesn't work with manually installed drivers.

Man, if you could get to your nvidia settings mgr just once and change the resolution and save those settings to the xorg.conf, you'd be on easy street.
+1

---

### Post by 2Real on 2009-05-03
ed's way didn't work :(

low graphics mode error

---

### Post by 4Orbs on 2009-05-03
> Yeah, but screen resolution being incorrect is one of the first things I have to deal with when installing an OS

I agree. And its important to not change the default resolution (even if painful) settings until AFTER you get the driver successfully installed. The successful driver install will default you to a different, more appropriate resolution after reboot. Then you can either use the nvidia settings mgr to change resolution or (in my case better) just add a display subsection in the screen section with a mode line of preferred resolutions in the xorg.conf file.

---

### Post by ed-koala on 2009-05-03
Start a thread in the multimedia forum.  Probably someone there who has some ideas, since it is a specialty forum.

---

### Post by BslBryan on 2009-05-03
You have tried that right, 2Real?  Downloading the driver and adding a display subsection in xorg.conf?

---

### Post by 2Real on 2009-05-03
i'm running an Asus C90S with an 8600M GT

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> You have tried that right, 2Real?  Downloading the driver and adding a display subsection in xorg.conf?

i thought there was already one when viewed the config

---

### Post by BslBryan on 2009-05-03
With your correct driver/resolution?

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> With your correct driver/resolution?
huh?

---

### Post by BslBryan on 2009-05-03
Can you display the contents of your xorg.conf file?

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Can you display the contents of your xorg.conf file?
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

i think this is my reverted version

---

### Post by 4Orbs on 2009-05-03
Well, if you wanna try something easy, that probably won't work. Log out, then at the login screen change your session to gnome session rather than last session. Then login.

---

### Post by 2Real on 2009-05-03
> **4Orbs said:**
> Well, if you wanna try something easy, that probably won't work. Log out, then at the login screen change your session to gnome session rather than last session. Then login.
then install the driver?

---

### Post by 4Orbs on 2009-05-03
That xorg.conf is the vanilla default one, and its good because it should work with your activated driver. If you activate the driver in Hardware Drivers Mgr, then before rebooting be sure this is the active xorg.conf. Then after rebooting, do what I said above about changing your session before logging in. The thing might actually work.

---

### Post by 2Real on 2009-05-03
> **4Orbs said:**
> That xorg.conf is the vanilla default one, and its good because it should work with your activated driver. If you activate the driver in Hardware Drivers Mgr, then before rebooting be sure this is the active xorg.conf. Then after rebooting, do what I said above about changing your session before logging in. The thing might actually work.
 k i'll try

---

### Post by BslBryan on 2009-05-03
Good call.

---

### Post by 2Real on 2009-05-03
config after activating

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by 2Real on 2009-05-03
low graphics mode error :(

---

### Post by BslBryan on 2009-05-03
remove the line 
```
option "NoLogo" "true"
```

And reboot.

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> remove the line 
```
option "NoLogo" "true"
```And reboot.
:confused:

---

### Post by BslBryan on 2009-05-03
I want to see if that line was left in the xorg.conf file from a previous driver install, or if there's an nVIDIA driver installed that's trying to work. 

If you 
```
gksudo gedit /etc/X11/xorg.conf
```
and just erase that line, and save it, when you reboot, it will tell us whether or not a driver is installed.

---

### Post by 4Orbs on 2009-05-03
That xorg.conf looks right and it indicates that the driver is indeed installed and activated. Maybe we can overcome the low graphics nastiness by adding the modes subsection. Change your Screen section to look like this. Edit the xorg.conf file as root. First enter:
```
gksudo gedit /etc/X11/xorg.conf
```
Then edit
```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```
Then, before saving and closing the file, change the resolutions to agree with what you know works on your monitor. The first entry will become the default resolution for the login screen and ALL user accounts. It should be the highest resolution. After saving and closing the file, you'll need to reboot again and change the session to gnome before logging in.

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> I want to see if that line was left in the xorg.conf file from a previous driver install, or if there's an nVIDIA driver installed that's trying to work. 

If you 
```
gksudo gedit /etc/X11/xorg.conf
```and just erase that line, and save it, when you reboot, it will tell us whether or not a driver is installed.
ok so i erased the line and rebooted and linux started up as normal

---

### Post by 2Real on 2009-05-03
config after erasing line and rebooting

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

---

### Post by BslBryan on 2009-05-03
> **4Orbs said:**
> That xorg.conf looks right and it indicates that the driver is indeed installed and activated. Maybe we can overcome the low graphics nastiness by adding the modes subsection. Change your Screen section to look like this. Edit the xorg.conf file as root. First enter:
```
gksudo gedit /etc/X11/xorg.conf
```
Then edit
```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```
Then, before saving and closing the file, change the resolutions to agree with what you know works on your monitor. The first entry will become the default resolution for the login screen and ALL user accounts. It should be the highest resolution. After saving and closing the file, you'll need to reboot again and change the session to gnome before logging in.

Do this.  You did see an nVIDIA splash screen upon loading, right?

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Do this.  You did see an nVIDIA splash screen upon loading, right?
should i put that line i erased back in?

---

### Post by BslBryan on 2009-05-03
It's up to you.  All that line was saying was that there was an option in effect to make sure that you didn't see an nVIDIA splash screen (a big screen that says nVIDIA), and by erasing it, you just said, all right, it's fine that there's a splash screen, it's no big deal.

Anyway, do a ```
gksudo gedit /etc/X11/xorg.conf
```

and highlight the "screen section."  Then delete it, and copy this:
```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```

and paste it where your old one was.

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> It's up to you.  All that line was saying was that there was an option in effect to make sure that you didn't see an nVIDIA splash screen (a big screen that says nVIDIA), and by erasing it, you just said, all right, it's fine that there's a splash screen, it's no big deal.

Anyway, do a ```
gksudo gedit /etc/X11/xorg.conf
```and highlight the "screen section."  Then delete it, and copy this:
```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```and paste it where your old one was.
low graphics mode error


failed to load the NVIDIA kernel module

---

### Post by BslBryan on 2009-05-03
You did change the screen resolutions to the resolutions that you know work, right?  

The first one listed is the default, so that is the actual size of your monitor.

---

### Post by 4Orbs on 2009-05-03
I think he must have passed out from exhaustion.

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> You did change the screen resolutions to the resolutions that you know work, right?  

The first one listed is the default, so that is the actual size of your monitor.
yea my monitor supports resolutions much higher than what you wrote

i don't think it's an issue of the resolution if it is saying 
failed to load the NVIDIA kernel module right?

---

### Post by 2Real on 2009-05-03
> **4Orbs said:**
> I think he must have passed out from exhaustion.
i'm starting to think i'm just screwed haha

---

### Post by BslBryan on 2009-05-03
Well, even if you were on my computer, which works flawlessly, if you were to edit xorg.conf and put a different resolution in, my screen might not even work.  

In  fact, you're kind of lucky that it still does work.  Anyway, change the resolution to the proper one, and reboot.


> **4Orbs said:**
> I think he must have passed out from exhaustion.

:lol:  I'm sure he will soon.  Or I will. :)

---

### Post by 4Orbs on 2009-05-03
You were able to log in properly before you added the subsection. Then just remove the subsection, and you should be able to reboot and log in correctly again. Was your resolution right when you logged in normally a while ago?

---

### Post by 2Real on 2009-05-03
> **4Orbs said:**
> You were able to log in properly before you added the subsection. Then just remove the subsection, and you should be able to reboot and log in correctly again. Was your resolution right when you logged in normally a while ago?
i dunno the exact resolution but the right one for my monitor :P this is starting to give me a headache :P

---

### Post by BslBryan on 2009-05-03
What?

---

### Post by 4Orbs on 2009-05-03
If you don't know the resolutions supported by your video card, then just remove the Display subsection, save and reboot. Then you should be able to use the nVidia settings mgr to change your resolutions. It will overwrite this tidy, small xorg.conf with a bunch of extra stuff. But it might actually work better that way. If removing the subsection works in a good way, then save a backup of that xorg.conf before using the nvidia settings mgr (as root).

---

### Post by 2Real on 2009-05-03
> **4Orbs said:**
> If you don't know the resolutions supported by your video card, then just remove the Display subsection, save and reboot. Then you should be able to use the nVidia settings mgr to change your resolutions. It will overwrite this tidy, small xorg.conf with a bunch of extra stuff. But it might actually work better that way. If removing the subsection works in a good way, then save a backup of that xorg.conf before using the nvidia settings mgr (as root).
but i can't use the nvidia settings because it says i'm not using the xserver driver

---

### Post by BslBryan on 2009-05-03
Here, set the xorg.conf file back to what it used to be, or delete the subsection.

In a shell:
```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
```

Then, System --> Administration --> Synaptic Package Manager --> Settings --> Repositories --> Third Party Software 

Click +Add

APT Line:
```
deb http://www.avenard.org/files/ubuntu-repos jaunty release
```

After that, 
```
sudo apt-get update
```

Then, in Synaptic, search for nVIDIA.  
Download 

nvidia-180-libvdpau
nvidia-settings
nvidia-180-kernel-source
nvidia-common
nvidia-180-modealiases
nvidia-glx-180
jockey-common
jockey-gtk

```
sudo reboot now
```

Good luck. :)

---

### Post by 4Orbs on 2009-05-03
A while ago, when you removed the logo line, you were able to log in normally. You weren't in low graphics mode that one time. You have done nothing since to remove the driver, it still should be activated. So all you gotta do is edit the xorg.conf back to the way it was at the successful login, reboot, change the session to gnome rather than last session and login. You should be back at the good resolution and not at low graphics mode. If you are at the good resolution desktop, then you should be able to open the nvidia settings mgr as root.

---

### Post by 2Real on 2009-05-03
trying that in a sec lol

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Here, set the xorg.conf file back to what it used to be, or delete the subsection.

In a shell:
```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
```Then, System --> Administration --> Synaptic Package Manager --> Settings --> Repositories --> Third Party Software 

Click +Add

APT Line:
```
deb http://www.avenard.org/files/ubuntu-repos jaunty release
```After that, 
```
sudo apt-get update
```Then, in Synaptic, search for nVIDIA.  
Download 

nvidia-180-libvdpau
nvidia-settings
nvidia-180-kernel-source
nvidia-common
nvidia-180-modealiases
nvidia-glx-180
jockey-common
jockey-gtk

```
sudo reboot now
```Good luck. :)

same low graphics error about failing to load the nvidia kernel module from before :(

---

### Post by 4Orbs on 2009-05-03
it hurts more than brain-freeze from eating a sno-cone too quickly.

---

### Post by BslBryan on 2009-05-03
Well, after all night, I think that that's all I've got.  I'd suggest downgrading to Intrepid or Hardy, but that's really all I can think of.  4Orbs?

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Well, after all night, I think that that's all I've got.  I'd suggest downgrading to Intrepid or Hardy, but that's really all I can think of.  4Orbs?
ahhhh i thought upgrading to 9.04 would be beneficial

---

### Post by 4Orbs on 2009-05-03
You wanna trade computers with me for a week or two, I've got this new sledge hammer....

EDiT: anyway, if you had it working right one time, you can get it there again. Jaunty really is good. I think there is probably a simple solution. Maybe tomorrow things will work themselves out.

---

### Post by 2Real on 2009-05-03
> **4Orbs said:**
> You wanna trade computers with me for a week or two, I've got this new sledge hammer....
hahaha:lolflag: i think that would be fun

---

### Post by BslBryan on 2009-05-03
> **4Orbs said:**
> You wanna trade computers with me for a week or two, I've got this new sledge hammer....

:lol:

---

### Post by BslBryan on 2009-05-03
> **2Real said:**
> ahhhh i thought upgrading to 9.04 would be beneficial

Well, you managed to get a lot of posts here on the forums, and that's beneficial...  I guess. :)

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> Well, you managed to get a lot of posts here on the forums, and that's beneficial...  I guess. :)
i got another thread going but it isn't as active lol

[http://ubuntuforums.org/showthread.php?p=7201634#post7201634](http://ubuntuforums.org/showthread.php?p=7201634#post7201634)

---

### Post by BslBryan on 2009-05-03
...  I think I'm good for now.  :)

---

### Post by 2Real on 2009-05-03
it's a different topic :P

---

### Post by 4Orbs on 2009-05-03
Well... I'm off to the refrigerator. You cats take it easy. I'll look in on it again tomorrow.

---

### Post by BslBryan on 2009-05-03
See you later, buddy.  I'm going to hit the sack pretty soon.

I'll think about what else could be wrong tonight.  

nVIDIA is funny stuff.  :P

---

### Post by 2Real on 2009-05-03
thanks for the help :P

---

### Post by 4Orbs on 2009-05-03
Sorry we couldn't get it working today. Possibly a fresh Jaunty install could fix it right up.

---

### Post by 2Real on 2009-05-03
> **4Orbs said:**
> Sorry we couldn't get it working today. Possibly a fresh Jaunty install could fix it right up.
that will have to wait about a month :P i don't wanna have to reinstall all my programs right now :P i'm in the middle of writing a compiler for one of my classes

---

### Post by BslBryan on 2009-05-03
Why don't you back 'er up?  Then you could do a fresh install, pop in the disc, voila.  

That seems pretty sensible.

---

### Post by doas777 on 2009-05-03
Thank you all! I've learned a good bit from watching this thread. I have to say I would have given up and tried a reinstall long ago. I admire your stick-to-it-iveness.

one last peice of advice, if you rebuild, create a seperate home partition, so that reinstalls and upgrades are as painless as possible from a data and settings backup perspective.

best regards

---

### Post by Racecar56 on 2009-05-03
all i can say is...
please get a reinstall
sorry you never got this to work :(

---

### Post by 4Orbs on 2009-05-03
I think he actually had it working right for a few moments. Then someone suggested an additional tweak. And....

EDIT: Tomorrow we'll probably do the same thing again.

---

### Post by BslBryan on 2009-05-03
Haha, probably. :lol:  He mentioned in one of the first posts that the 180 drivers seemed to install without a hitch.  

Now it's time to think about how to configure them properly... :popcorn:

---

### Post by 2Real on 2009-05-03
> **doas777 said:**
> Thank you all! I've learned a good bit from watching this thread. I have to say I would have given up and tried a reinstall long ago. I admire your stick-to-it-iveness.

one last peice of advice, if you rebuild, create a seperate home partition, so that reinstalls and upgrades are as painless as possible from a data and settings backup perspective.

best regards
Yea thanks for the help :)
I've learned so much from these posts.

---

### Post by BslBryan on 2009-05-03
In fact, if you have stuff you don't want to lose from this install, you can set up a separate home partition by checking [this]("www.psychocats.net/ubuntu/separatehome") out.  :)

---

### Post by BslBryan on 2009-05-03
Actually, I've just read a groundbreaking post in, of all places, The Community Cafe.  This looks like it would have worked with my driver without any trouble.  It may or may not apply to you.  

After I found this, I was thinking about something else I asked you to do, which was wrong.  I've corrected the error if this doesn't work out.  

Again, good luck. :)

> **Kosimo said:**
> I've been always disappointed with all video drivers we had in linux, (AMD or nVidia)  Very ugly 2D performance (specially nvidia) and tons of issues when mixing compiz and 3D or Video. 
Now, it's been almost a week that I've installed nVidia BETA drivers 180.06 which includes for the first time ever Pure Video on Linux. 
I am impressed with the general performance and stability, compiz have never been that smooth, video has an amazing quality even when I'm moving my desktop cube, any 3D app can perfectly run with no issues or performance problems. In one word. IMPRESSIVE. I hope that this is not the final step but only the first one of a new nVidia drivers series that can finally put Linux at the same level than Windows Drivers stability and performance. I would like to ask you guys if anyone else is using 180.XX drivers, let's talk about how you feel with them! 


*Edit April 17 2009*: Latest nVidia 180.xx (STABLE) drivers: **[COLOR="Red"]180.51[/COLOR]**  [ Download]("http://www.nvnews.net/vbulletin/showthread.php?p=1985816")


*Edit April 23 2009*: Latest nVidia 180.xx (PRE) Drivers: **[COLOR="Red"]180.53[/COLOR]**  [ Download]("http://www.nvnews.net/vbulletin/showthread.php?t=131874")


*Edit April 24 2009*: Latest nVidia 185.xx (BETA) Drivers: **[COLOR="Red"]185.18.04[/COLOR]**  [ Download]("http://www.nvnews.net/vbulletin/showthread.php?p=1990290")


_**How to install this drivers:**_

It is very easy and you can do it by just following this steps. Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver **first** and then restart your computer before you start. **_[COLOR="Red"]THIS IS MANDATORY![/COLOR]_**

*Note: Follow this instructions at your own risk*

**[COLOR="Red"]1[/COLOR])** Download the driver (for example in your desktop) - *Get the pkg1, Right Click, Save As...* 

**[COLOR="Red"]2[/COLOR])** Enter in a real terminal mode: CONTROL + ALT + F1, then login (don't do it now as you wouldn't be able to keep reading)

**[COLOR="Red"]3[/COLOR])** Go to your desktop:  ```
cd Desktop
```

**[COLOR="Red"]4[/COLOR])** Turn off X.org/GDM (Gnome Display Manager):  ```
sudo /etc/init.d/gdm stop
```

**[COLOR="Red"]5[/COLOR])** Run the installer:  ```
sudo sh ./Nxxx.run
```   (If you hit TAB after the first N the rest of the filename will automatically appear. Remember, Linux is case sensitive) 

**[COLOR="Red"]6[/COLOR])** _**Choose x.org automatic configuration at the last step inside the installation program**._

**[COLOR="Red"]7[/COLOR])** Then restart your computer   ```
sudo reboot
```

**[COLOR="Red"]8[/COLOR])** Enjoy!


**Important note**: In some instances, after a kernel upgrade you won't be able to load x.org. "**sdennie**" made a very useful post where explains how to create a script that will automatically install the drivers when your kernel is upgraded. Have a look [here]("http://ubuntuforums.org/showthread.php?t=835573")

**ps**: If anything goes wrong, you can easily uninstall this drivers by following the same steps and when running the installer type: 


**ps2**: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.




Legacy releases for GeForce 5 series GPUs **[COLOR="Red"]173.14.18[/COLOR]** [32 Bits, ]("http://www.nvidia.com/object/linux_display_ia32_173.14.18.html") / [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_173.14.18.html")

Legacy releases for GeForce 2 through GeForce 4 series **[COLOR="Red"]96.43.11[/COLOR]** [32 bits]("http://www.nvidia.com/object/linux_display_x86_96.43.11.html") , [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_96.43.11.html")

Legacy releases for Riva TNT, TNT2, GeForce, and some GeForce 2 **[COLOR="Red"]71.86.09[/COLOR]** [32 Bits]("http://www.nvidia.com/object/linux_display_x86_71.86.09.html"), [64 Bits]("http://www.nvidia.com/object/linux_display_amd64_71.86.09.html")

*note*: Legacy drivers are being updated as well.

Good luck ;)

---

### Post by 2Real on 2009-05-03
> **BslBryan said:**
> In fact, if you have stuff you don't want to lose from this install, you can set up a separate home partition by checking [this]("http://www.psychocats.net/ubuntu/separatehome") out.  :)
haha I'll check it all out once i get my homework done :P

---

### Post by 4Orbs on 2009-05-03
2Real, I can tell from your posts you have a vibrant sense of adventure. In the time you spent troubleshooting yesterday, you could have instead downloaded Jaunty live cd, done a new install and customized it, imported all the important files back in and taken your great-grandmother out for pizza. And your driver probably would have worked on the first try. And pizza sounds like a good idea.

---

### Post by 2Real on 2009-05-03
> **4Orbs said:**
> 2Real, I can tell from your posts you have a vibrant sense of adventure. In the time you spent troubleshooting yesterday, you could have instead downloaded Jaunty live cd, done a new install and customized it, imported all the important files back in and taken your great-grandmother out for pizza. And your driver probably would have worked on the first try. And pizza sounds like a good idea.

haha I use the excuse of reinstall windows when things don't work on it. I was hoping this wasn't the case with linux for a simple driver :P 

It was fun because I was learning a lot about Ubuntu

---

### Post by 4Orbs on 2009-05-03
I don't think you really need a reinstall, you'll get the driver working.

BslBryan's pointing you to the beta driver looks like a good idea, especially since you already know the process of manually installing the driver. Your initial problem with the manual install could have simply been because you used the pkg1 version rather than the pkg0 version (or 0<->1).

---

### Post by doas777 on 2009-05-03
> **2Real said:**
> haha I use the excuse of reinstall windows when things don't work on it. I was hoping this wasn't the case with linux for a simple driver :P 

It was fun because I was learning a lot about Ubuntu

lol. I'm the same way. I try to find ways to avoid rebuilding in favor of fixing the actual issue, though at the beginning I did have to rebuild a few times. I also find that it's hard to remember exactly what tweaks I made 2 years ago, so i think of upgrades as an opportunity to refresh back to predictability.

I've also found in linux that "simple drivers" are about as complex and risky as it gets, so don't feel at all bad about it. you put up a valient struggle.

have fun

---

