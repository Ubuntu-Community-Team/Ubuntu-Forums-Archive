---
title: "I got 3 questions..."
date: 2009-05-24
forum: General Help
---

### Post by bradshaw_2k9 on 2009-05-24
Hi
Ive recently installed Ubuntu 9.04 after my M$ XP install died from swine flu or something :P. I managed to get everything working and began to customise the desktop using compiz fusion.
 
My first question is how to disable Compiz? I enabled the "Blur Window" Effect and this has resulted in all the windows becoming black squares and eventually the entire screen becoming black. I have tryed to disable it by guessing where buttons were but, unsuprissingly that didnt work.
 
The second is I have been experiencing very long boot times aprox. 5 mins. and i cannot work out the cause for it. 
 
And finally the third is a problem installing M$ Office 2007 when i do:
 
**sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1**
 
in the console i get a Connection Refused Error and it retrys about 20 times.
 
Thanks in advance
Dan
 
PS i want to use Office 2007 for One Note :) It isnt better than Open office i just like One Note. :P

---

### Post by wbee on 2009-05-24
I won't confuse the issue for one and three,but I'll take a crack at two.

Go to your motherboard's web site,download,and install the latest driver for your bios.

Hope that helps.

---

### Post by fiddler616 on 2009-05-24
You'll probably do better if you have a separate thread for each question, and put the one about Wine in the "Wine" subforum.

---

### Post by themusicalduck on 2009-05-24
The best way to disable compiz is to first install simple-ccsm

```
sudo apt-get install simple-ccsm
```

in a terminal.

Then once it's installed, go to System > Preferences > Appearance

On the Visual Effects tab, select none.

For the bootup problem, it might be worth starting ubuntu in verbose mode and looking for any obvious error messages that come up.

First, make a backup of your grub menu.lst

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Then open it up in gedit

```
sudo gedit /boot/grub/menu.lst
```

Find the first entry for Ubuntu (For the title line, it'll say something like 'Ubuntu 9.04, kernel 2.6.28-11-generic' and come after '## ## End Default Options ##')

On the 'kernel line' delete the word 'quiet' and save the file.

Reboot and if you can see any obvious errors then report them here and we'll see if we can help.

As for Office, I had problems installing it in wine and was only able to install it using crossover in the end.

---

### Post by fillintheblanks on 2009-05-24
supposedly this resets your compiz settings to defaults

> gconftool-2 --recursive-unset -a /apps/compiz


[how to install Office 2007 in Wine]("http://wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html")

---

### Post by b@sh_n3rd on 2009-05-24
> And finally the third is a problem installing M$ Office 2007
You can try this; download POL (PlayOnLinux) from, [here]("http://www.playonlinux.com/en/"). POL 3.5 doesn't have "Office 2007" on it's list of supported programs, but you can insert your Office 2007 CD in your CD-ROM drive and then click, "Tools > Autorun", Follow the instructions on screen. Hope this helps, I've done it before and it worked for me, but it wasn't office I tried :D

---

### Post by bradshaw_2k9 on 2009-05-24
[COLOR=black][]("http://ubuntuforums.org/member.php?u=519677")thanks [/COLOR][fillintheblanks]("http://ubuntuforums.org/member.php?u=519677")[COLOR=black] that cmd worked a treat :)  i will try all of the other suggestions now :)
PS thanks for the quick replys :D
[]("http://ubuntuforums.org/member.php?u=519677")[/COLOR]

---

### Post by bradshaw_2k9 on 2009-06-01
> **themusicalduck said:**
> Reboot and if you can see any obvious errors then report them here and we'll see if we can help.

I tried that and came out with this when it paused:

```
[  8.776014] phy0: Selected rate control algorithm. ‘pid’ 
[  0.829763] Registered led device: rt73usb-phy0:radio 
[  8.829871] Registered led device: rt73usb-phy0:assoc 
[  8.829976] Registered led device: rt73usb-ph0:quality 
[  0.830484] usbcore: registered new interface driver rt73usb 
[  9.987236] zc3xx: probe 2wr ov vga Ox0000 
[ 10.031235] zc3xx: probe sensor —> 11 
[ 10.031280] zc3xx: Find Sensor HV7131R(c) 
[ 10.036413] gspca: probe Ok 
[ 10.036496] usbcore registered new interface driver zc3xx 
[ 10.036584] zc3xx: registered 

```not sure what that means :( but I hope it helps.

It then continued as normal about 4 minutes later.

---

### Post by albinootje on 2009-06-01
> **bradshaw_2k9 said:**
>  It then continued as normal about 4 minutes later.

Please post the output of :
```

dmesg

```

---

### Post by bradshaw_2k9 on 2009-06-01
> **albinootje said:**
> Please post the output of :
```

dmesg

```

```
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7c0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7c0000 - 000000003f7ce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f7ce000 - 000000003f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3f7c0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f7c0000 (usable)
[    0.000000]  modified: 000000003f7c0000 - 000000003f7ce000 (ACPI data)
[    0.000000]  modified: 000000003f7ce000 - 000000003f800000 (ACPI NVS)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fef7f4
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb27f4
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef7f3 to 00881000 - 00fb27f3
[    0.000000] ACPI: RSDP 000F9050, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 3F7C0100, 004C (r1 DSGLTD DSGVISTA 20070330 MSFT       97)
[    0.000000] ACPI: FACP 3F7C0290, 00F4 (r3 033007 FACP1039 20070330 MSFT       97)
[    0.000000] ACPI: DSDT 3F7C05B0, 3835 (r1  TGDII TGDII300      300 INTL 20051117)
[    0.000000] ACPI: FACS 3F7CE000, 0040
[    0.000000] ACPI: APIC 3F7C0390, 005C (r1 033007 APIC1039 20070330 MSFT       97)
[    0.000000] ACPI: MCFG 3F7C03F0, 003C (r1 033007 OEMMCFG  20070330 MSFT       97)
[    0.000000] ACPI: SLIC 3F7C0430, 0176 (r1 DSGLTD DSGVISTA 20070330 MSFT       97)
[    0.000000] ACPI: OEMB 3F7CE040, 0071 (r1 033007 OEMB1039 20070330 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 131MB HIGHMEM available.
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
[    0.000000]   #7 [0000881000 - 0000fb27f4]      NEW RAMDISK ==> [0000881000 - 0000fb27f4]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0003f7c0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f7c0
[    0.000000] On node 0 totalpages: 259919
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 264 pages used for memmap
[    0.000000]   HighMem zone: 33466 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:bf600000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257887
[    0.000000] Kernel command line: root=UUID=272d9032-d9a0-4fa2-8c3c-ca9ba0607a8d ro  single
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.119 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5200320 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1010112k/1040128k available (4126k kernel code, 29188k reserved, 2208k data, 532k init, 134920k highmem)
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
[    0.004013] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.23 BogoMIPS (lpj=6384476)
[    0.004125] Security Framework initialized
[    0.004178] SELinux:  Disabled at boot.
[    0.004244] AppArmor: AppArmor initialized
[    0.004295] Mount-cache hash table entries: 512
[    0.004493] Initializing cgroup subsys ns
[    0.004541] Initializing cgroup subsys cpuacct
[    0.004587] Initializing cgroup subsys memory
[    0.004634] Initializing cgroup subsys freezer
[    0.004694] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004766] CPU: L2 cache: 1024K
[    0.004812] CPU: Physical Processor ID: 0
[    0.004856] CPU: Processor Core ID: 0
[    0.004902] using mwait in idle threads.
[    0.004956] Checking 'hlt' instruction... OK.
[    0.023475] ACPI: Core revision 20080926
[    0.025020] ACPI: Checking initramfs for custom DSDT
[    0.404524] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.445747] CPU0: Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[    0.448001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4469.04 BogoMIPS (lpj=8938093)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.532385] CPU1: Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[    0.532781] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.536055] Brought up 2 CPUs
[    0.536103] Total of 2 processors activated (7661.28 BogoMIPS).
[    0.536210] CPU0 attaching sched-domain:
[    0.536213]  domain 0: span 0-1 level MC
[    0.536216]   groups: 0 1
[    0.536224] CPU1 attaching sched-domain:
[    0.536227]  domain 0: span 0-1 level MC
[    0.536229]   groups: 1 0
[    0.536323] net_namespace: 776 bytes
[    0.536323] Booting paravirtualized kernel on bare hardware
[    0.536555] Time: 19:24:42  Date: 06/01/09
[    0.536555] regulator: core version 0.5
[    0.536555] NET: Registered protocol family 16
[    0.536555] EISA bus registered
[    0.536555] ACPI: bus type pci registered
[    0.536555] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.536590] PCI: Not using MMCONFIG.
[    0.536818] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.536866] PCI: Using configuration type 1 for base access
[    0.540786] ACPI: EC: Look up EC in DSDT
[    0.547989] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.548136] ACPI: Interpreter enabled
[    0.548154] ACPI: (supports S0 S1 S3 S4 S5)
[    0.548353] ACPI: Using IOAPIC for interrupt routing
[    0.548458] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.554230] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.554281] PCI: updated MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.554343] PCI: Using MMCONFIG for extended config space
[    0.560781] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.560831] ACPI: EC: driver started in interrupt mode
[    0.561018] ACPI: No dock devices found.
[    0.561129] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.561279] pci 0000:00:02.0: reg 10 32bit mmio: [0xfea00000-0xfea7ffff]
[    0.561285] pci 0000:00:02.0: reg 14 io port: [0xd400-0xd407]
[    0.561291] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.561298] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfea80000-0xfeabffff]
[    0.561337] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe980000-0xfe9fffff]
[    0.561450] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfeaf8000-0xfeafbfff]
[    0.561490] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.561540] pci 0000:00:1b.0: PME# disabled
[    0.561649] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.561699] pci 0000:00:1c.0: PME# disabled
[    0.561810] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.561860] pci 0000:00:1c.2: PME# disabled
[    0.561968] pci 0000:00:1d.0: reg 20 io port: [0xdc00-0xdc1f]
[    0.562031] pci 0000:00:1d.1: reg 20 io port: [0xd880-0xd89f]
[    0.562093] pci 0000:00:1d.2: reg 20 io port: [0xd800-0xd81f]
[    0.562156] pci 0000:00:1d.3: reg 20 io port: [0xd480-0xd49f]
[    0.562225] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfeaffc00-0xfeafffff]
[    0.562275] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.563087] pci 0000:00:1d.7: PME# disabled
[    0.563286] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.563293] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.563356] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.563450] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.563458] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.563466] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.563474] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.563482] pci 0000:00:1f.2: reg 20 io port: [0xffa0-0xffaf]
[    0.563506] pci 0000:00:1f.2: PME# supported from D3hot
[    0.563556] pci 0000:00:1f.2: PME# disabled
[    0.563656] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.563858] pci 0000:01:05.0: reg 10 32bit mmio: [0xfebff000-0xfebff7ff]
[    0.563910] pci 0000:01:05.0: supports D1 D2
[    0.563956] pci 0000:01:08.0: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]
[    0.563966] pci 0000:01:08.0: reg 14 io port: [0xec00-0xec3f]
[    0.564018] pci 0000:01:08.0: supports D1 D2
[    0.564020] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.564072] pci 0000:01:08.0: PME# disabled
[    0.564165] pci 0000:01:0a.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]
[    0.564174] pci 0000:01:0a.0: reg 14 32bit mmio: [0xfebf8000-0xfebfbfff]
[    0.564221] pci 0000:01:0a.0: supports D1 D2
[    0.564223] pci 0000:01:0a.0: PME# supported from D0 D1 D2 D3hot
[    0.564274] pci 0000:01:0a.0: PME# disabled
[    0.564361] pci 0000:00:1e.0: transparent bridge
[    0.564410] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.564416] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.564443] bus 00 -> node 0
[    0.564450] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.564739] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.564898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.575022] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.575533] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.576113] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.576617] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.577124] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.577630] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.578201] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.578772] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.579360] ACPI: WMI: Mapper loaded
[    0.579467] SCSI subsystem initialized
[    0.579467] libata version 3.00 loaded.
[    0.579467] usbcore: registered new interface driver usbfs
[    0.579467] usbcore: registered new interface driver hub
[    0.579467] usbcore: registered new device driver usb
[    0.580075] PCI: Using ACPI for IRQ routing
[    0.584015] Bluetooth: Core ver 2.13
[    0.584077] NET: Registered protocol family 31
[    0.584077] Bluetooth: HCI device and connection manager initialized
[    0.584114] Bluetooth: HCI socket layer initialized
[    0.584160] NET: Registered protocol family 8
[    0.584206] NET: Registered protocol family 20
[    0.584262] NetLabel: Initializing
[    0.584306] NetLabel:  domain hash size = 128
[    0.584351] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.584411] NetLabel:  unlabeled traffic allowed by default
[    0.584616] hpet clockevent registered
[    0.584620] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.584673] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.584829] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.588083] AppArmor: AppArmor Filesystem Enabled
[    0.596011] pnp: PnP ACPI init
[    0.596066] ACPI: bus type pnp registered
[    0.598170] pnp: PnP ACPI: found 11 devices
[    0.598217] ACPI: ACPI bus type pnp unregistered
[    0.598264] PnPBIOS: Disabled by ACPI PNP
[    0.598319] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.598377] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.598426] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.598476] system 00:07: ioport range 0x480-0x4bf has been reserved
[    0.598525] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.598575] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.598626] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved
[    0.598680] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.598730] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.598783] system 00:09: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.598837] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.598887] system 00:0a: iomem range 0xc0000-0xcffff could not be reserved
[    0.598937] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    0.598987] system 00:0a: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.599049] system 00:0a: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.633857] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.633906] pci 0000:00:1c.0:   IO window: disabled
[    0.633956] pci 0000:00:1c.0:   MEM window: disabled
[    0.634005] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.634058] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.634105] pci 0000:00:1c.2:   IO window: disabled
[    0.634155] pci 0000:00:1c.2:   MEM window: disabled
[    0.634203] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.634256] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.634306] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.634356] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.634407] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.634470] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.634522] pci 0000:00:1c.0: setting latency timer to 64
[    0.634533] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.634584] pci 0000:00:1c.2: setting latency timer to 64
[    0.634593] pci 0000:00:1e.0: setting latency timer to 64
[    0.634598] bus: 00 index 0 io port: [0x00-0xffff]
[    0.634644] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.634691] bus: 02 index 0 mmio: [0x0-0x0]
[    0.634735] bus: 02 index 1 mmio: [0x0-0x0]
[    0.634780] bus: 02 index 2 mmio: [0x0-0x0]
[    0.634825] bus: 02 index 3 mmio: [0x0-0x0]
[    0.634870] bus: 03 index 0 mmio: [0x0-0x0]
[    0.634915] bus: 03 index 1 mmio: [0x0-0x0]
[    0.634960] bus: 03 index 2 mmio: [0x0-0x0]
[    0.635005] bus: 03 index 3 mmio: [0x0-0x0]
[    0.635050] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.635097] bus: 01 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.635144] bus: 01 index 2 mmio: [0x0-0x0]
[    0.635189] bus: 01 index 3 io port: [0x00-0xffff]
[    0.635235] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.635291] NET: Registered protocol family 2
[    0.648066] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.648435] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.649127] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.649530] TCP: Hash tables configured (established 131072 bind 65536)
[    0.649582] TCP reno registered
[    0.656117] NET: Registered protocol family 1
[    0.656313] checking if image is initramfs... it is
[    1.084894] Switched to high resolution mode on CPU 1
[    1.087986] Switched to high resolution mode on CPU 0
[    1.428657] Freeing initrd memory: 7365k freed
[    1.428977] cpufreq: No nForce2 chipset.
[    1.429221] audit: initializing netlink socket (disabled)
[    1.429293] type=2000 audit(1243884282.429:1): initialized
[    1.438532] highmem bounce pool size: 64 pages
[    1.438583] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.440359] VFS: Disk quotas dquot_6.5.1
[    1.440475] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.441293] fuse init (API version 7.10)
[    1.441442] msgmni has been set to 1724
[    1.441713] alg: No test for stdrng (krng)
[    1.441772] io scheduler noop registered
[    1.441819] io scheduler anticipatory registered
[    1.441864] io scheduler deadline registered
[    1.441925] io scheduler cfq registered (default)
[    1.441984] pci 0000:00:02.0: Boot video device
[    1.442117] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    1.443532] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.443581] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.443664] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.443680] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.443702] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.443717] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.443791] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.443837] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.443913] pcieport-driver 0000:00:1c.2: irq 2302 for MSI/MSI-X
[    1.443929] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.443945] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.443961] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.444052] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.444423] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.444638] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.444700] ACPI: Power Button (FF) [PWRF]
[    1.444807] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.444870] ACPI: Power Button (CM) [PWRB]
[    1.445719] processor ACPI_CPU:00: registered as cooling_device0
[    1.446282] processor ACPI_CPU:01: registered as cooling_device1
[    1.448137] thermal LNXTHERM:01: registered as thermal_zone0
[    1.448372] ACPI: Thermal Zone [THRM] (60 C)
[    1.448472] isapnp: Scanning for PnP cards...
[    1.942611] isapnp: No Plug & Play device found
[    1.949158] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.950466] brd: module loaded
[    1.950916] loop: module loaded
[    1.951038] Fixed MDIO Bus: probed
[    1.951087] PPP generic driver version 2.4.2
[    1.951205] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.951301] Driver 'sd' needs updating - please use bus_type methods
[    1.951358] Driver 'sr' needs updating - please use bus_type methods
[    1.951499] ata_piix 0000:00:1f.2: version 2.12
[    1.951520] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.951573] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.951770] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.951880] scsi0 : ata_piix
[    1.952045] scsi1 : ata_piix
[    1.953980] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.954031] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.153002] ata1.00: ATA-7: ST3160815AS, 3.AAC, max UDMA/133
[    2.153052] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.219659] ata1.00: configured for UDMA/133
[    2.396435] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, TG00, max UDMA/33
[    2.428391] ata2.00: configured for UDMA/33
[    2.436851] scsi 0:0:0:0: Direct-Access     ATA      ST3160815AS      3.AA PQ: 0 ANSI: 5
[    2.437049] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.437130] sd 0:0:0:0: [sda] Write Protect is off
[    2.437176] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.437211] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.437361] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.437439] sd 0:0:0:0: [sda] Write Protect is off
[    2.437487] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.437519] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.437586]  sda: sda1 sda2 < sda5 >
[    2.485401] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.485505] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.500392] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D TG00 PQ: 0 ANSI: 5
[    2.564525] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.564588] Uniform CD-ROM driver Revision: 3.20
[    2.564747] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.564796] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.565630] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.565707] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.565785] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.565789] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.565918] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.570642] ehci_hcd 0000:00:1d.7: debug port 1
[    2.570692] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.570710] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaffc00
[    2.584012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.584152] usb usb1: configuration #1 chosen from 1 choice
[    2.584237] hub 1-0:1.0: USB hub found
[    2.584289] hub 1-0:1.0: 8 ports detected
[    2.584481] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.584547] uhci_hcd: USB Universal Host Controller Interface driver
[    2.584624] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.584679] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.584684] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.584788] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.584873] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000dc00
[    2.585007] usb usb2: configuration #1 chosen from 1 choice
[    2.585083] hub 2-0:1.0: USB hub found
[    2.585134] hub 2-0:1.0: 2 ports detected
[    2.585278] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.585334] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.585338] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.585431] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.585526] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d880
[    2.585663] usb usb3: configuration #1 chosen from 1 choice
[    2.585739] hub 3-0:1.0: USB hub found
[    2.585789] hub 3-0:1.0: 2 ports detected
[    2.585932] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.585987] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.585991] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.586085] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.586178] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    2.586312] usb usb4: configuration #1 chosen from 1 choice
[    2.586389] hub 4-0:1.0: USB hub found
[    2.586438] hub 4-0:1.0: 2 ports detected
[    2.586578] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.586633] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.586637] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.586735] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.586828] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d480
[    2.586961] usb usb5: configuration #1 chosen from 1 choice
[    2.587037] hub 5-0:1.0: USB hub found
[    2.587087] hub 5-0:1.0: 2 ports detected
[    2.587277] usbcore: registered new interface driver libusual
[    2.587358] usbcore: registered new interface driver usbserial
[    2.587417] USB Serial support registered for generic
[    2.587482] usbcore: registered new interface driver usbserial_generic
[    2.587531] usbserial: USB Serial Driver core
[    2.587625] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.587673] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.588324] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.592050] mice: PS/2 mouse device common for all mice
[    2.604090] rtc_cmos 00:03: RTC can wake from S4
[    2.604179] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.604256] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.604398] device-mapper: uevent: version 1.0.3
[    2.604568] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.604736] device-mapper: multipath: version 1.0.5 loaded
[    2.604784] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.604939] EISA: Probing bus 0 at eisa.0
[    2.605020] EISA: Detected 0 cards.
[    2.605131] cpuidle: using governor ladder
[    2.605177] cpuidle: using governor menu
[    2.605852] TCP cubic registered
[    2.606019] NET: Registered protocol family 10
[    2.606585] lo: Disabled Privacy Extensions
[    2.607032] NET: Registered protocol family 17
[    2.607096] Bluetooth: L2CAP ver 2.11
[    2.607140] Bluetooth: L2CAP socket layer initialized
[    2.607187] Bluetooth: SCO (Voice Link) ver 0.6
[    2.607232] Bluetooth: SCO socket layer initialized
[    2.607318] Bluetooth: RFCOMM socket layer initialized
[    2.607371] Bluetooth: RFCOMM TTY layer initialized
[    2.607416] Bluetooth: RFCOMM ver 1.10
[    2.607535] Using IPI No-Shortcut mode
[    2.607672] registered taskstats version 1
[    2.607842]   Magic number: 13:463:444
[    2.607969] rtc_cmos 00:03: setting system clock to 2009-06-01 19:24:44 UTC (1243884284)
[    2.608031] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.608078] EDD information not available.
[    2.608350] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.608457] Freeing unused kernel memory: 532k freed
[    2.608676] Write protecting the kernel text: 4128k
[    2.608780] Write protecting the kernel read-only data: 1532k
[    2.824306] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    2.824362] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.824472] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.851229] e100 0000:01:08.0: PME# disabled
[    2.852231] e100: eth0: e100_probe: addr 0xfebfe000, irq 20, MAC addr 00:03:0d:65:a0:18
[    2.871832] ohci1394 0000:01:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.921984] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.121033] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    3.213488] PM: Starting manual resume from disk
[    3.213536] PM: Resume from partition 8:5
[    3.213538] PM: Checking hibernation image.
[    3.213723] PM: Resume from disk failed.
[    3.261308] kjournald starting.  Commit interval 5 seconds
[    3.261318] EXT3-fs: mounted filesystem with ordered data mode.
[    3.391721] usb 1-6: configuration #1 chosen from 1 choice
[    3.632019] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.816967] usb 2-1: configuration #1 chosen from 1 choice
[    4.060022] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    4.192145] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d49d000312c]
[    4.211260] usb 4-1: configuration #1 chosen from 1 choice
[    4.214195] hub 4-1:1.0: USB hub found
[    4.216145] hub 4-1:1.0: 4 ports detected
[    4.513129] usb 4-1.1: new full speed USB device using uhci_hcd and address 3
[    4.731248] usb 4-1.1: configuration #1 chosen from 1 choice
[    4.825103] usb 4-1.2: new full speed USB device using uhci_hcd and address 4
[    4.974174] usb 4-1.2: configuration #1 chosen from 1 choice
[    5.069083] usb 4-1.4: new low speed USB device using uhci_hcd and address 5
[    5.224134] usb 4-1.4: configuration #1 chosen from 1 choice
[    7.622914] udev: starting version 141
[    7.876112] cfg80211: Calling CRDA to update world regulatory domain
[    8.212800] cfg80211: World regulatory domain updated:
[    8.212855]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.212917]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.212966]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.213017]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.213066]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.213116]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.320909] Linux video capture interface: v2.00
[    8.440416] usbcore: registered new interface driver hiddev
[    8.440905] usbcore: registered new interface driver usbhid
[    8.440959] usbhid: v2.6:USB HID core driver
[    8.581126] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    8.590422] Linux agpgart interface v0.103
[    8.595191] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    8.596228] intel_rng: FWH not detected
[    8.596788] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    8.600463] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    8.608417] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
[    8.622516] pegasus 2-1:1.0: setup Pegasus II specific registers
[    8.746395] pegasus 2-1:1.0: eth1, Belkin F5D5050 USB Ethernet, 00:05:1b:00:40:be
[    8.746524] usbcore: registered new interface driver pegasus
[    8.752972] gspca: main v2.3.0 registered
[    8.780409] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.4/4-1.4:1.0/input/input5
[    8.788226] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.2-1.4/input0
[    8.816829] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    8.818152] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.4/4-1.4:1.1/input/input6
[    8.828268] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1.4/input1
[    8.842728] gspca: probing 041e:403a
[    8.860448] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.0/input/input7
[    8.870329] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.2/input/input8
[    8.881083] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.4/input/input9
[    8.887405] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.6/input/input10
[    8.892124] usbcore: registered new interface driver xpad
[    8.892178] xpad: X-Box pad driver
[    8.918601] iTCO_vendor_support: vendor-support=0
[    8.944816] saa7130/34: v4l2 driver version 0.2.14 loaded
[    8.946280] saa7134 0000:01:05.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.946346] saa7133[0]: found at 0000:01:05.0, rev: 209, irq: 19, latency: 64, mmio: 0xfebff000
[    8.946417] saa7133[0]: subsystem: 1461:f636, board: AVerMedia MiniPCI DVB-T Hybrid M103 [card=145,autodetected]
[    8.946559] saa7133[0]: board init: gpio is 220000
[    8.969729] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.969937] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x0860)
[    8.970082] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.100165] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.100318] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.116012] saa7133[0]: i2c eeprom 00: 61 14 36 f6 00 00 00 00 00 00 00 00 00 00 00 00
[    9.116548] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[    9.117090] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 0e ff ff ff ff
[    9.117620] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.118160] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[    9.118686] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.119221] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.119749] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.120295] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.120827] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.121360] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.121887] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.122414] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.122945] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.123476] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.124019] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.131175] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.144016] tuner' 0-0061: chip found @ 0xc2 (saa7133[0])
[    9.174581] xc2028 0-0061: creating new instance
[    9.174635] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[    9.174701] BUG: unable to handle kernel paging request at fffffff4
[    9.174809] IP: [<f80392c0>] saa7134_board_init2+0x140/0x710 [saa7134]
[    9.174897] *pde = 007bd067 *pte = 00000000 
[    9.175002] Oops: 0000 [#1] SMP 
[    9.175108] last sysfs file: /sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer/dev
[    9.175175] Dumping ftrace buffer:
[    9.175222]    (ftrace buffer empty)
[    9.175270] Modules linked in: tuner_xc2028 tuner snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi iTCO_wdt rt73usb(+) crc_itu_t snd_rawmidi saa7134(+) iTCO_vendor_support joydev rt2x00usb snd_seq_midi_event xpad ir_common gspca_zc3xx(+) rt2x00lib snd_seq compat_ioctl32 hid_logitech gspca_main snd_timer snd_seq_device led_class pegasus intel_agp agpgart pcspkr ff_memless v4l2_common videobuf_dma_sg videobuf_core tveeprom usbhid videodev v4l1_compat mac80211 snd soundcore snd_page_alloc cfg80211 ohci1394 ieee1394 e100 mii fbcon tileblit font bitblit softcursor
[    9.177115] 
[    9.177159] Pid: 1531, comm: modprobe Not tainted (2.6.28-11-generic #42-Ubuntu) Little LLUON S2
[    9.177224] EIP: 0060:[<f80392c0>] EFLAGS: 00010292 CPU: 0
[    9.177284] EIP is at saa7134_board_init2+0x140/0x710 [saa7134]
[    9.177333] EAX: 00000000 EBX: 00000000 ECX: 00000000 EDX: 00000000
[    9.177383] ESI: 00000000 EDI: 00000000 EBP: 00000000 ESP: f60b7c54
[    9.177437]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[    9.177443] Process modprobe (pid: 1531, ti=f60b6000 task=f61e6480 task.ti=f60b6000)
[    9.177443] Stack:
[    9.177443]  00000303 f60b7c58 f60b7c58 f66d9000 f6fab800 f66d9000 f60b7cd0 c014ade7
[    9.177443]  000000d0 f803b889 656e7574 00000072 000000f0 f66d94b0 00000000 f66d9140
[    9.177443]  f8045490 f66d94b0 f60b7cd0 f803b94d 65626f72 642d7000 006d6561 000005fb
[    9.177443] Call Trace:
[    9.177443]  [<c014ade7>] ? request_module+0x97/0xf0
[    9.177443]  [<f803b889>] ? saa7134_i2c_eeprom+0xe9/0x110 [saa7134]
[    9.177443]  [<f803b94d>] ? saa7134_i2c_register+0x9d/0x120 [saa7134]
[    9.177443]  [<f80445fc>] ? saa7134_initdev+0x3cc/0x8d5 [saa7134]
[    9.177443]  [<c02dc3fe>] ? pci_device_probe+0x5e/0x80
[    9.177443]  [<c034f004>] ? really_probe+0x54/0x180
[    9.177443]  [<c02dbc2e>] ? pci_match_device+0xbe/0xd0
[    9.177443]  [<c034f16e>] ? driver_probe_device+0x3e/0x50
[    9.177443]  [<c034f209>] ? __driver_attach+0x89/0x90
[    9.177443]  [<c034e943>] ? bus_for_each_dev+0x53/0x80
[    9.177443]  [<c02dc340>] ? pci_device_remove+0x0/0x40
[    9.177443]  [<c034eec9>] ? driver_attach+0x19/0x20
[    9.177443]  [<c034f180>] ? __driver_attach+0x0/0x90
[    9.177443]  [<c034e317>] ? bus_add_driver+0x1c7/0x240
[    9.177443]  [<c02dc340>] ? pci_device_remove+0x0/0x40
[    9.177443]  [<c034f3a9>] ? driver_register+0x69/0x140
[    9.177443]  [<f803b240>] ? saa7134_init+0x0/0x60 [saa7134]
[    9.177443]  [<c02dc65a>] ? __pci_register_driver+0x4a/0x90
[    9.177443]  [<f803b240>] ? saa7134_init+0x0/0x60 [saa7134]
[    9.177443]  [<f803b292>] ? saa7134_init+0x52/0x60 [saa7134]
[    9.177443]  [<c010111e>] ? _stext+0x2e/0x170
[    9.177443]  [<c01a908c>] ? __vunmap+0x9c/0xe0
[    9.177443]  [<c01a908c>] ? __vunmap+0x9c/0xe0
[    9.177443]  [<c0127c8d>] ? update_curr+0x8d/0x1e0
[    9.177443]  [<c012c6fc>] ? enqueue_entity+0x13c/0x360
[    9.177443]  [<c0131bfe>] ? resched_task+0x1e/0x70
[    9.177443]  [<c0133b74>] ? try_to_wake_up+0x104/0x290
[    9.177443]  [<c0163fc8>] ? sys_init_module+0x88/0x1b0
[    9.177443]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[    9.177443]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[    9.177443] Code: 15 78 4c c8 8b 55 90 8b 82 2c 01 00 00 89 5c 24 04 c7 04 24 b8 63 04 f8 89 44 24 08 e8 f8 77 4c c8 66 90 8b 45 90 e8 40 fd ff ff <8b> 5d f4 31 c0 8b 75 f8 8b 7d fc 89 ec 5d c3 90 8b 4d 90 8b 71 
[    9.177443] EIP: [<f80392c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ESP 0068:f60b7c54
[    9.177443] ---[ end trace fbdd03cf23619787 ]---
[    9.231448] phy0: Selected rate control algorithm 'pid'
[    9.285155] Registered led device: rt73usb-phy0:radio
[    9.285264] Registered led device: rt73usb-phy0:assoc
[    9.285364] Registered led device: rt73usb-phy0:quality
[    9.285966] usbcore: registered new interface driver rt73usb
[   10.515673] zc3xx: probe 2wr ov vga 0x0000
[   10.559669] zc3xx: probe sensor -> 11
[   10.559714] zc3xx: Find Sensor HV7131R(c)
[   10.564818] gspca: probe ok
[   10.564900] usbcore: registered new interface driver zc3xx
[   10.564980] zc3xx: registered
[  187.965008] lp: driver loaded but no devices found
[  188.081652] Adding 2980016k swap on /dev/sda5.  Priority:-1 extents:1 across:2980016k
[  188.429589] EXT3 FS on sda1, internal journal
[  188.903805] type=1505 audit(1243884470.792:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2130
[  188.966851] type=1505 audit(1243884470.856:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2134
[  188.967014] type=1505 audit(1243884470.856:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2134
[  188.967078] type=1505 audit(1243884470.856:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2134
[  188.967135] type=1505 audit(1243884470.856:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2134
[  189.149129] type=1505 audit(1243884471.040:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2139
[  189.149372] type=1505 audit(1243884471.040:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2139
[  189.189140] type=1505 audit(1243884471.080:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2143
[  201.555671] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  201.555677] vboxdrv: Successfully done.
[  201.555679] vboxdrv: Found 2 processor cores.
[  201.557081] vboxdrv: fAsync=0 offMin=0x390 offMax=0x1218
[  201.557155] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  201.557164] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[  202.910388] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  202.910392] Bluetooth: BNEP filters: protocol multicast
[  202.932865] Bridge firewalling registered
[  203.598649] ppdev: user-space parallel port driver
[  205.365679] [drm] Initialized drm 1.1.0 20060810
[  205.372807] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  205.372816] pci 0000:00:02.0: setting latency timer to 64
[  205.373014] [drm] Initialized i915 1.6.0 20080730 on minor 0
[  205.376957] [drm:i915_setparam] *ERROR* unknown parameter 4
[  205.376989] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  206.381298] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  207.126770] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  207.140703] eth1: set allmulti
[  207.140728] eth1: set allmulti
[  207.140731] pegasus 2-1:1.0: update_eth_regs_async, status -22
[  207.141001] eth1: set allmulti
[  207.141004] pegasus 2-1:1.0: update_eth_regs_async, status -22
[  207.141019] eth1: set allmulti
[  207.141021] pegasus 2-1:1.0: update_eth_regs_async, status -22
[  207.158014] rt73usb 1-6:1.0: firmware: requesting rt73.bin
[  207.279157] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  210.252401] eth1: set allmulti
[  217.140006] eth1: no IPv6 routers present
[  224.296015] usb 1-3: new high speed USB device using ehci_hcd and address 5
[  224.445229] usb 1-3: configuration #1 chosen from 1 choice
[  224.460942] Initializing USB Mass Storage driver...
[  224.462333] scsi2 : SCSI emulation for USB Mass Storage devices
[  224.462566] usb-storage: device found at 5
[  224.462569] usb-storage: waiting for device to settle before scanning
[  224.462582] usbcore: registered new interface driver usb-storage
[  224.462586] USB Mass Storage support registered.
[  229.466837] usb-storage: device scan complete
[  229.469132] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[  236.139470] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  239.064526] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[  239.066195] sd 2:0:0:0: [sdb] Write Protect is off
[  239.066200] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[  239.066204] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  239.068559] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[  239.070071] sd 2:0:0:0: [sdb] Write Protect is off
[  239.070076] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[  239.070079] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  239.070086]  sdb: sdb1
[  239.071623] sd 2:0:0:0: [sdb] Attached SCSI disk
[  239.071748] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  242.952689] wlan0: authenticate with AP 00:0f:66:5b:40:61
[  242.958320] wlan0: authenticated
[  242.958325] wlan0: associate with AP 00:0f:66:5b:40:61
[  242.960819] wlan0: RX AssocResp from 00:0f:66:5b:40:61 (capab=0x411 status=0 aid=4)
[  242.960823] wlan0: associated
[  242.963311] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  253.824016] wlan0: no IPv6 routers present
[  289.317084] wlan0: disassociating by local choice (reason=3)
[  294.340036] usb 2-2: new full speed USB device using uhci_hcd and address 3
[  294.567938] usb 2-2: configuration #1 chosen from 1 choice
[  294.609463] scsi3 : SCSI emulation for USB Mass Storage devices
[  294.623279] usb-storage: device found at 3
[  294.623284] usb-storage: waiting for device to settle before scanning
[  299.621574] usb-storage: device scan complete
[  299.624555] scsi 3:0:0:0: Direct-Access     Nokia    Nokia N95        1.0  PQ: 0 ANSI: 0
[  299.636224] sd 3:0:0:0: [sdc] 15954944 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[  299.638544] sd 3:0:0:0: [sdc] Write Protect is off
[  299.638549] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  299.638553] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  299.657095] sd 3:0:0:0: [sdc] 15954944 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[  299.659527] sd 3:0:0:0: [sdc] Write Protect is off
[  299.659532] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  299.659536] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  299.659544]  sdc: sdc1
[  299.803696] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[  299.803841] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  339.085177] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  430.960306] [drm:i915_getparam] *ERROR* Unknown parameter 6

```

there you go ;)

---

### Post by albinootje on 2009-06-01
Thanks for that output, you got a kernel oops about your sound card it looks like.

Can you also post the output of the following :
```

lspci
aplay -l

```

---

