---
title: "GRUB - fsck problems"
date: 2009-02-25
forum: General Help
---

### Post by p3ta on 2009-02-25
hi all

after a power outage i had problems with GRUB and i booted on Ubuntu live CD (a copy i have since Hardy i think) and went on to run fsck from Gparted

i am using one disk in ntfs with windows on (sda) and another in ext3 with ubuntu on (sdb).

i've had several problems over the last few weeks but havent had time to deal with them being in exam period and all.

my number two problems right now are:

my entire ext3 is now a /lost+found directory. gparted shows the disk at the same size it used to be before this mess so i think all my files are in there.

i thought about reinstalling GRUB so i can at least boot windows and not be stuck with live CD (it's all i have now) but i cant find /boot/grub/stage1 (i installed GRUB months ago i dont remember exactly where i put it but apparently it's in sdb)

any suggestions (or even better solutions) are most welcome

cheers

---

### Post by digitalbenji on 2009-02-25
If I read this correctly, you have 2 hard drives.  If sdb is the 2nd drive, it will be hd1 in grub.  Grub is most likely in (hd1,0)/boot/grub/.  Second, can you post the output of dmesg and sudo fdisk -l from the livecd?  It could be that one of your hard drives has crashed, and that is why everything is stranded into lost+found.

Thanks,

---

### Post by caljohnsmith on 2009-02-25
If you want to get your Windows sda drive booting while you sort through your linux files on your sdb drive, you can do the following to install a Windows equivalent MBR to your Windows drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Then you should be able to boot into Windows again, but let me know if you run into problems.

---

### Post by p3ta on 2009-03-01
many thx caljohnsmith.. i'm in windows the last few days

and the fdisk output benji asked:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ba90ba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bb281

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60049   482343561   83  Linux
/dev/sdb2           60050       60801     6040440    5  Extended
/dev/sdb5           60050       60801     6040408+  82  Linux swap / Solaris

Disk /dev/sdc: 40.0 GB, 40007630848 bytes
64 heads, 32 sectors/track, 38154 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x14d8c9c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38154    39069680    b  W95 FAT32


sdc is a small portable usb hd

and dmesg

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FAA60 checksum 0
[    0.000000] ACPI: RSDP 000FAA60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFB0000, 0038 (r1 122407 RSDT1648 20071224 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0200, 0084 (r2 122407 FACP1648 20071224 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB0440, 71E2 (r1  1ADSL 1ADSL000        0 INTL 20051117)
[    0.000000] ACPI: FACS 7FFBE000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 006C (r1 122407 APIC1648 20071224 MSFT       97)
[    0.000000] ACPI: MCFG 7FFB0400, 003C (r1 122407 OEMMCFG  20071224 MSFT       97)
[    0.000000] ACPI: OEMB 7FFBE040, 0071 (r1 122407 OEMB1648 20071224 MSFT       97)
[    0.000000] ACPI: EPTH 7FFB7630, 0038 (r1 122407 OEMHPET  20071224 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ffb0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524208
[    0.000000] On node 0 totalpages: 524111
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1220 pages reserved
[    0.000000]   DMA zone: 2723 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 513002 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ff00000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515725
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   34.909312] Marking TSC unstable due to TSCs unsynchronized
[   34.909314] time.c: Detected 2200.152 MHz processor.
[   34.910831] Console: colour VGA+ 80x25
[   34.910834] console [tty0] enabled
[   34.910849] Checking aperture...
[   34.910852] CPU 0: aperture @ 3590000000 size 32 MB
[   34.910853] Aperture too small (32 MB)
[   34.921793] No AGP bridge found
[   34.938192] Memory: 2054448k/2096832k available (2489k kernel code, 41996k reserved, 1318k data, 320k init)
[   34.938224] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   35.015559] Calibrating delay using timer specific routine.. 4599.98 BogoMIPS (lpj=9199973)
[   35.015587] Security Framework initialized
[   35.015593] SELinux:  Disabled at boot.
[   35.015604] AppArmor: AppArmor initialized
[   35.015607] Failure registering capabilities with primary security module.
[   35.015778] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   35.016918] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   35.017456] Mount-cache hash table entries: 256
[   35.017560] Initializing cgroup subsys ns
[   35.017563] Initializing cgroup subsys cpuacct
[   35.017575] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.017577] CPU: L2 Cache: 512K (64 bytes/line)
[   35.017579] CPU 0/0 -> Node 0
[   35.017581] CPU: Physical Processor ID: 0
[   35.017583] CPU: Processor Core ID: 0
[   35.017603] SMP alternatives: switching to UP code
[   35.018110] Early unpacking initramfs... done
[   35.323703] ACPI: Core revision 20070126
[   35.323758] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   35.368553] Using local APIC timer interrupts.
[   35.413972] APIC timer calibration result 12500860
[   35.413973] Detected 12.500 MHz APIC timer.
[   35.414049] SMP alternatives: switching to SMP code
[   35.414470] Booting processor 1/4 APIC 0x1
[   35.425180] Initializing CPU#1
[   35.505905] Calibrating delay using timer specific routine.. 4400.44 BogoMIPS (lpj=8800888)
[   35.505910] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.505912] CPU: L2 Cache: 512K (64 bytes/line)
[   35.505914] CPU 1/1 -> Node 0
[   35.505916] CPU: Physical Processor ID: 0
[   35.505917] CPU: Processor Core ID: 1
[   35.506202] AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[   35.506283] SMP alternatives: switching to SMP code
[   35.506609] Booting processor 2/4 APIC 0x2
[   35.517318] Initializing CPU#2
[   35.597822] Calibrating delay using timer specific routine.. 4400.36 BogoMIPS (lpj=8800739)
[   35.597827] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.597829] CPU: L2 Cache: 512K (64 bytes/line)
[   35.597831] CPU 2/2 -> Node 0
[   35.597833] CPU: Physical Processor ID: 0
[   35.597834] CPU: Processor Core ID: 2
[   35.598120] AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[   35.598207] SMP alternatives: switching to SMP code
[   35.598527] Booting processor 3/4 APIC 0x3
[   35.609236] Initializing CPU#3
[   35.689738] Calibrating delay using timer specific routine.. 4400.38 BogoMIPS (lpj=8800776)
[   35.689744] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.689746] CPU: L2 Cache: 512K (64 bytes/line)
[   35.689748] CPU 3/3 -> Node 0
[   35.689749] CPU: Physical Processor ID: 0
[   35.689750] CPU: Processor Core ID: 3
[   35.690037] AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[   35.690095] Brought up 4 CPUs
[   35.690208] CPU0 attaching sched-domain:
[   35.690210]  domain 0: span 0f
[   35.690211]   groups: 01 02 04 08
[   35.690214]   domain 1: span 0f
[   35.690216]    groups: 0f
[   35.690217] CPU1 attaching sched-domain:
[   35.690218]  domain 0: span 0f
[   35.690219]   groups: 02 04 08 01
[   35.690222]   domain 1: span 0f
[   35.690223]    groups: 0f
[   35.690224] CPU2 attaching sched-domain:
[   35.690225]  domain 0: span 0f
[   35.690226]   groups: 04 08 01 02
[   35.690228]   domain 1: span 0f
[   35.690229]    groups: 0f
[   35.690231] CPU3 attaching sched-domain:
[   35.690232]  domain 0: span 0f
[   35.690233]   groups: 08 01 02 04
[   35.690235]   domain 1: span 0f
[   35.690236]    groups: 0f
[   35.690474] net_namespace: 120 bytes
[   35.690844] Time: 14:50:43  Date: 03/01/09
[   35.690866] NET: Registered protocol family 16
[   35.691008] ACPI: bus type pci registered
[   35.691067] PCI: Using configuration type 1
[   35.694986] ACPI: EC: Look up EC in DSDT
[   35.698788] ACPI: Interpreter enabled
[   35.698790] ACPI: (supports S0 S1 S3 S4 S5)
[   35.698804] ACPI: Using IOAPIC for interrupt routing
[   35.699061] Error attaching device data
[   35.699065] Error attaching device data
[   35.699069] Error attaching device data
[   35.699072] Error attaching device data
[   35.705657] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   35.705876] pci 0000:00:12.0: set SATA to AHCI mode
[   35.706858] PCI: Transparent bridge - 0000:00:14.4
[   35.706882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   35.707114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[   35.707220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[   35.707341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[   35.710105] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[   35.710223] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 *15)
[   35.710343] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[   35.710463] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   35.710586] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   35.710708] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   35.710826] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
[   35.710939] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   35.711049] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  CA, should be C1 [20070126]
[   35.711057] Linux Plug and Play Support v0.97 (c) Adam Belay
[   35.711079] pnp: PnP ACPI init
[   35.711085] ACPI: bus type pnp registered
[   35.714039] pnp: PnP ACPI: found 13 devices
[   35.714041] ACPI: ACPI bus type pnp unregistered
[   35.714219] PCI: Using ACPI for IRQ routing
[   35.714221] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   35.729727] NET: Registered protocol family 8
[   35.729728] NET: Registered protocol family 20
[   35.729812] AppArmor: AppArmor Filesystem Enabled
[   35.741729] system 00:07: iomem range 0xfec00000-0xfec00fff has been reserved
[   35.741732] system 00:07: iomem range 0xfee00000-0xfee00fff could not be reserved
[   35.741736] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   35.741738] system 00:08: ioport range 0x40b-0x40b has been reserved
[   35.741740] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   35.741742] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   35.741744] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   35.741746] system 00:08: ioport range 0xc50-0xc51 has been reserved
[   35.741748] system 00:08: ioport range 0xc52-0xc52 has been reserved
[   35.741750] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   35.741752] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   35.741754] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[   35.741756] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[   35.741758] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   35.741760] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   35.741762] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   35.741766] system 00:08: ioport range 0x800-0x89f has been reserved
[   35.741768] system 00:08: ioport range 0xb10-0xb1f has been reserved
[   35.741770] system 00:08: ioport range 0x900-0x90f has been reserved
[   35.741772] system 00:08: ioport range 0x910-0x91f has been reserved
[   35.741780] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[   35.741782] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[   35.741785] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   35.741790] system 00:0a: ioport range 0x600-0x6df has been reserved
[   35.741792] system 00:0a: ioport range 0xae0-0xaef has been reserved
[   35.741796] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   35.741800] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   35.741802] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[   35.741804] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   35.741807] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[   35.741809] system 00:0c: iomem range 0xfed45000-0xffffffff could not be reserved
[   35.742087] PCI: Bridge: 0000:00:02.0
[   35.742089]   IO window: d000-dfff
[   35.742092]   MEM window: fa000000-feafffff
[   35.742094]   PREFETCH window: d0000000-dfffffff
[   35.742097] PCI: Bridge: 0000:00:06.0
[   35.742099]   IO window: e000-efff
[   35.742101]   MEM window: feb00000-febfffff
[   35.742103]   PREFETCH window: disabled.
[   35.742106] PCI: Bridge: 0000:00:14.4
[   35.742107]   IO window: disabled.
[   35.742112]   MEM window: disabled.
[   35.742115]   PREFETCH window: disabled.
[   35.742129] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   35.742136] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   35.742150] NET: Registered protocol family 2
[   35.745698] Time: acpi_pm clocksource has been installed.
[   35.745710] Switched to high resolution mode on CPU 0
[   35.746028] Switched to high resolution mode on CPU 1
[   35.746031] Switched to high resolution mode on CPU 3
[   35.746037] Switched to high resolution mode on CPU 2
[   35.777718] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   35.778388] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   35.780485] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   35.781008] TCP: Hash tables configured (established 262144 bind 65536)
[   35.781010] TCP reno registered
[   35.789767] checking if image is initramfs... it is
[   36.330371] Freeing initrd memory: 8171k freed
[   36.335060] audit: initializing netlink socket (disabled)
[   36.335072] audit(1235919043.388:1): initialized
[   36.336768] VFS: Disk quotas dquot_6.5.1
[   36.336832] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   36.336937] io scheduler noop registered
[   36.336939] io scheduler anticipatory registered
[   36.336941] io scheduler deadline registered
[   36.337020] io scheduler cfq registered (default)
[   36.458708] Boot video device is 0000:01:00.0
[   36.458851] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   36.458874] assign_interrupt_mode Found MSI capability
[   36.458899] Allocate Port Service[0000:00:02.0:pcie00]
[   36.458958] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   36.458980] assign_interrupt_mode Found MSI capability
[   36.459001] Allocate Port Service[0000:00:06.0:pcie00]
[   36.479562] Real Time Clock Driver v1.12ac
[   36.479641] Linux agpgart interface v0.102
[   36.479644] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   36.479770] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   36.480222] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   36.480778] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   36.480829] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   36.480891] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   36.480893] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   36.481207] serio: i8042 KBD port at 0x60,0x64 irq 1
[   36.493093] mice: PS/2 mouse device common for all mice
[   36.493121] cpuidle: using governor ladder
[   36.493123] cpuidle: using governor menu
[   36.493252] NET: Registered protocol family 1
[   36.493331] registered taskstats version 1
[   36.493437]   Magic number: 1:327:838
[   36.493486]   hash matches device ptyu4
[   36.493521] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   36.493524] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   36.493525] EDD information not available.
[   36.493532] Freeing unused kernel memory: 320k freed
[   36.511578] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   37.788882] fuse init (API version 7.9)
[   37.816545] ACPI: duty_cycle spans bit 4
[   38.029585] SCSI subsystem initialized
[   38.033953] usbcore: registered new interface driver usbfs
[   38.033978] usbcore: registered new interface driver hub
[   38.034079] r8169 Gigabit Ethernet driver 2.2LK loaded
[   38.034114] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   38.034136] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   38.034402] eth0: RTL8168b/8111b at 0xffffc200008b8000, 00:1d:92:32:05:3f, XID 38000000 IRQ 509
[   38.035515] usbcore: registered new device driver usb
[   38.090122] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   38.090180] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.090822] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   38.091069] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   38.091095] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf9ffe000
[   38.102971] libata version 3.00 loaded.
[   38.119980] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.119988] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.148548] usb usb1: configuration #1 chosen from 1 choice
[   38.148573] hub 1-0:1.0: USB hub found
[   38.148582] hub 1-0:1.0: 2 ports detected
[   38.149816] Floppy drive(s): fd0 is 1.44M
[   38.171690] FDC 0 is a post-1991 82077
[   38.252418] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   38.253088] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   38.253169] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   38.253233] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf9ffd000
[   38.312375] usb usb2: configuration #1 chosen from 1 choice
[   38.312400] hub 2-0:1.0: USB hub found
[   38.312408] hub 2-0:1.0: 2 ports detected
[   38.416174] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   38.416828] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   38.416909] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   38.416938] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf9ffc000
[   38.475168] usb usb3: configuration #1 chosen from 1 choice
[   38.475191] hub 3-0:1.0: USB hub found
[   38.475198] hub 3-0:1.0: 2 ports detected
[   38.564008] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   38.576054] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   38.576730] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   38.576810] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   38.576831] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf9ffb000
[   38.635999] usb usb4: configuration #1 chosen from 1 choice
[   38.636020] hub 4-0:1.0: USB hub found
[   38.636028] hub 4-0:1.0: 2 ports detected
[   38.739890] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   38.740559] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   38.740638] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   38.740660] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf9ffa000
[   38.783936] usb 1-1: configuration #1 chosen from 1 choice
[   38.799825] usb usb5: configuration #1 chosen from 1 choice
[   38.799846] hub 5-0:1.0: USB hub found
[   38.799853] hub 5-0:1.0: 2 ports detected
[   38.903780] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   38.904445] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   38.904541] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   38.904585] ehci_hcd 0000:00:13.5: debug port 1
[   38.904603] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf9fff000
[   38.914638] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   38.914735] usb usb6: configuration #1 chosen from 1 choice
[   38.914757] hub 6-0:1.0: USB hub found
[   38.914761] hub 6-0:1.0: 10 ports detected
[   39.021660] ahci 0000:00:12.0: version 3.0
[   39.021693] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   39.022350] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   39.022357] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   39.038569] usb 1-1: USB disconnect, address 2
[   39.166453] usbcore: registered new interface driver hiddev
[   39.370214] end_request: I/O error, dev fd0, sector 0
[   39.717876] usb 6-2: new high speed USB device using ehci_hcd and address 3
[   39.853099] usb 6-2: configuration #1 chosen from 1 choice
[   40.022114] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   40.022120] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   40.022388] scsi0 : ahci
[   40.022445] scsi1 : ahci
[   40.022479] scsi2 : ahci
[   40.022516] scsi3 : ahci
[   40.022582] ata1: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fff900 irq 22
[   40.022585] ata2: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fff980 irq 22
[   40.022588] ata3: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fffa00 irq 22
[   40.022591] ata4: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fffa80 irq 22
[   40.089519] usb 6-4: new high speed USB device using ehci_hcd and address 4
[   40.223929] usb 6-4: configuration #1 chosen from 1 choice
[   40.224216] usbcore: registered new interface driver usbhid
[   40.224221] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.426694] end_request: I/O error, dev fd0, sector 0
[   40.497139] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   40.497793] ata1.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[   40.497797] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   40.498529] ata1.00: configured for UDMA/133
[   40.533091] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   40.754418] usb 1-1: configuration #1 chosen from 1 choice
[   40.760272] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input2
[   40.778409] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.0-1
[   40.813817] ata2: SATA link down (SStatus 0 SControl 300)
[   41.124518] ata3: SATA link down (SStatus 0 SControl 300)
[   41.473685] end_request: I/O error, dev fd0, sector 0
[   41.600078] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   41.601396] ata4.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   41.601400] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   41.603075] ata4.00: configured for UDMA/133
[   41.603185] scsi 0:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   41.603284] scsi 3:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[   41.603389] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
[   41.603408] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   41.603428] SB600_PATA: not 100% native mode: will probe irqs later
[   41.603438]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[   41.603452] Probing IDE interface ide0...
[   41.624174] usbcore: registered new interface driver libusual
[   41.627890] Initializing USB Mass Storage driver...
[   41.627991] scsi4 : SCSI emulation for USB Mass Storage devices
[   41.628057] usbcore: registered new interface driver usb-storage
[   41.628060] USB Mass Storage support registered.
[   41.628213] usb-storage: device found at 3
[   41.628217] usb-storage: waiting for device to settle before scanning
[   42.395628] hdb: ASUS DVD-E616P2, ATAPI CD/DVD-ROM drive
[   42.520676] end_request: I/O error, dev fd0, sector 0
[   43.178872] hda: ASUS DRW-1608P, ATAPI CD/DVD-ROM drive
[   43.178886] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   43.178955] hda: UDMA/66 mode selected
[   43.179023] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
[   43.179027] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
[   43.179031] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   43.179281] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   43.179528] hdb: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   43.179530] hdb: UDMA/33 mode selected
[   43.179828] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   43.197585] Driver 'sd' needs updating - please use bus_type methods
[   43.197676] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   43.197686] sd 0:0:0:0: [sda] Write Protect is off
[   43.197688] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   43.197698] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.197744] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   43.197755] sd 0:0:0:0: [sda] Write Protect is off
[   43.197756] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   43.197775] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.197778]  sda:<6>hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
[   43.200736] Uniform CD-ROM driver Revision: 3.20
[   43.217115]  sda1
[   43.217186] sd 0:0:0:0: [sda] Attached SCSI disk
[   43.217244] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   43.217253] sd 3:0:0:0: [sdb] Write Protect is off
[   43.217255] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   43.217265] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.217301] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   43.217307] sd 3:0:0:0: [sdb] Write Protect is off
[   43.217309] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   43.217318] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   43.217321]  sdb: sdb1 sdb2 < sdb5 >
[   43.242576] sd 3:0:0:0: [sdb] Attached SCSI disk
[   43.247169] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   43.247189] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   43.509743] hdb: ATAPI 48X DVD-ROM drive, 512kB Cache
[   43.571663] end_request: I/O error, dev fd0, sector 0
[   43.983178] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.024945] ISO 9660 Extensions: RRIP_1991A
[   44.303516] Registering unionfs 1.4
[   44.303521] unionfs: debugging is not enabled
[   44.316677] loop: module loaded
[   44.641836] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   46.628424] usb-storage: device scan complete
[   49.869293] scsi 4:0:0:0: Direct-Access     TOSHIBA  MK4025GAS        2.00 PQ: 0 ANSI: 2
[   49.917048] sd 4:0:0:0: [sdc] 78139904 512-byte hardware sectors (40008 MB)
[   49.924514] sd 4:0:0:0: [sdc] Write Protect is off
[   49.924519] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   49.924522] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   49.927090] sd 4:0:0:0: [sdc] 78139904 512-byte hardware sectors (40008 MB)
[   49.927716] sd 4:0:0:0: [sdc] Write Protect is off
[   49.927718] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   49.927719] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   49.927722]  sdc: sdc1
[   49.959029] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   49.959068] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  112.419127] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  112.891621] input: PC Speaker as /devices/platform/pcspkr/input/input3
[  114.219000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  114.244073] ACPI: WMI-Acer: Mapper loaded
[  114.245850] input: Power Button (FF) as /devices/virtual/input/input4
[  114.317909] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[  114.430855] ACPI: Power Button (FF) [PWRF]
[  114.430942] input: Power Button (CM) as /devices/virtual/input/input5
[  114.518775] ACPI: Power Button (CM) [PWRB]
[  115.939392] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[  115.984785] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[  118.561409] Adding 6040400k swap on /dev/sdb5.  Priority:-1 extents:1 across:6040400k
[  119.450365] ip_tables: (C) 2000-2006 Netfilter Core Team
[  121.497227] No dock devices found.
[  127.890865] lp: driver loaded but no devices found
[  127.988071] ppdev: user-space parallel port driver
[  137.975448] r8169: eth0: link up
[  137.975461] r8169: eth0: link up
[  138.794658] Bluetooth: Core ver 2.11
[  138.794883] NET: Registered protocol family 31
[  138.794886] Bluetooth: HCI device and connection manager initialized
[  138.794892] Bluetooth: HCI socket layer initialized
[  138.855735] Bluetooth: L2CAP ver 2.9
[  138.855740] Bluetooth: L2CAP socket layer initialized
[  139.510441] Bluetooth: RFCOMM socket layer initialized
[  139.510463] Bluetooth: RFCOMM TTY layer initialized
[  139.510465] Bluetooth: RFCOMM ver 1.8
[  141.057768] NET: Registered protocol family 17
[  151.420824] NET: Registered protocol family 10
[  151.421063] lo: Disabled Privacy Extensions
[  161.796082] eth0: no IPv6 routers present
[  177.210082] hda-intel: Invalid position buffer, using LPIB read method instead.
[  368.225506] kjournald starting.  Commit interval 5 seconds
[  368.225516] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[  368.233279] EXT3 FS on sdb1, internal journal
[  368.233284] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by digitalbenji on 2009-05-12
Hi,
   Sorry it's taken forever for me to reply.  It doesn't look like your drive crashed physically, instead I think the logical structure of it crashed.  I would recommend running a deep fsck to try to repair the errors, and probably taking a few passes at it.

The command will be, from the livecd:
sudo umount /dev/sdb1 
fsck -fy /dev/sdb1

You can repeat the fsck portion until it comes back clean.  The umount is because you don't want to to an fsck on a mounted partition.

Good luck, 
Thanks,

---

