---
title: "Boot is no longer &quot;quiet&quot; although flag is still there"
date: 2008-12-28
forum: General Help
---

### Post by aheckler on 2008-12-28
I recently noticed that my Intrepid boot process is no longer "quiet". That is, it spits out all the info about various processes it's starting and the progress bar doesn't show up anymore. But the "quiet" and "splash" flags in my /boot/grub/menu.lst are still there:

Relevant line is in bold red:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b521f678-a290-4664-9544-5a0f00b2a619 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b521f678-a290-4664-9544-5a0f00b2a619

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		b521f678-a290-4664-9544-5a0f00b2a619
**[COLOR="Red"]kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b521f678-a290-4664-9544-5a0f00b2a619 ro quiet splash [/COLOR]**
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b521f678-a290-4664-9544-5a0f00b2a619
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b521f678-a290-4664-9544-5a0f00b2a619 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		b521f678-a290-4664-9544-5a0f00b2a619
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Arch Linux
root       (hd0,1)
kernel    /boot/vmlinuz26 root=/dev/sda2 ro vga=775
initrd      /boot/kernel26.img

title          Arch Linux (fallback)
root         (hd0,1)
kernel      /boot/vmlinuz26 root=/dev/sda2 ro vga=775
initrd        /boot/kernel26-fallback.img
```

I think it may have something to do with the fact that I recently repartitioned my drive and installed Arch on another section. However, I didn't overwrite GRUB while doing so, and added the Arch lines later, so I'm not sure what's wrong. Halp!

---

### Post by anubhavrocks on 2008-12-28
After you boot up into Ubuntu can you post the output of
```
dmesg
```

---

### Post by aheckler on 2008-12-28
dmesg after bootup:

```
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 513890
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=b521f678-a290-4664-9544-5a0f00b2a619 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 3013.261 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2047064k/2095996k available (3112k kernel code, 48544k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 6026.52 BogoMIPS (lpj=12053044)
[    0.004043] Security Framework initialized
[    0.004051] SELinux:  Disabled at boot.
[    0.004070] AppArmor: AppArmor initialized
[    0.004435] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.005744] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.006308] Mount-cache hash table entries: 256
[    0.006550] Initializing cgroup subsys ns
[    0.006556] Initializing cgroup subsys cpuacct
[    0.006559] Initializing cgroup subsys memory
[    0.006584] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.006588] CPU: L2 cache: 2048K
[    0.006591] CPU 0/0 -> Node 0
[    0.006594] CPU: Physical Processor ID: 0
[    0.006596] CPU: Processor Core ID: 0
[    0.006611] CPU0: Thermal monitoring enabled (TM1)
[    0.006615] using mwait in idle threads.
[    0.008019] ACPI: Core revision 20080609
[    0.010739] ACPI: Checking initramfs for custom DSDT
[    0.384464] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.424161] CPU0:               Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[    0.424166] Using local APIC timer interrupts.
[    0.428029] APIC timer calibration result 12555288
[    0.428032] Detected 12.555 MHz APIC timer.
[    0.428215] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6026.75 BogoMIPS (lpj=12053515)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.516593] CPU1:               Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[    0.516627] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.520060] Brought up 2 CPUs
[    0.520064] Total of 2 processors activated (12053.27 BogoMIPS).
[    0.520115] CPU0 attaching sched-domain:
[    0.520118]  domain 0: span 0-1 level CPU
[    0.520121]   groups: 0 1
[    0.520127]   domain 1: span 0-1 level NODE
[    0.520129]    groups: 0-1
[    0.520135] CPU1 attaching sched-domain:
[    0.520137]  domain 0: span 0-1 level CPU
[    0.520140]   groups: 1 0
[    0.520144]   domain 1: span 0-1 level NODE
[    0.520146]    groups: 0-1
[    0.520244] net_namespace: 1552 bytes
[    0.520244] Booting paravirtualized kernel on bare hardware
[    0.520321] Time:  4:08:05  Date: 12/29/08
[    0.520366] NET: Registered protocol family 16
[    0.520391] ACPI: bus type pci registered
[    0.520391] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.520391] PCI: MCFG area at e0000000 reserved in E820
[    0.532743] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.532746] PCI: Using configuration type 1 for base access
[    0.532882] ACPI: EC: Look up EC in DSDT
[    0.545275] ACPI: Interpreter enabled
[    0.545279] ACPI: (supports S0 S3 S4 S5)
[    0.545301] ACPI: Using IOAPIC for interrupt routing
[    0.553493] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.556062] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.556067] pci 0000:00:01.0: PME# disabled
[    0.556134] PCI: 0000:00:1d.0 reg 20 io port: [ff00, ff1f]
[    0.556185] PCI: 0000:00:1d.1 reg 20 io port: [fe00, fe1f]
[    0.556236] PCI: 0000:00:1d.2 reg 20 io port: [fd00, fd1f]
[    0.556288] PCI: 0000:00:1d.3 reg 20 io port: [fc00, fc1f]
[    0.556337] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fdfff000, fdfff3ff]
[    0.556383] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.556388] pci 0000:00:1d.7: PME# disabled
[    0.556461] PCI: 0000:00:1e.2 reg 10 io port: [f000, f0ff]
[    0.556468] PCI: 0000:00:1e.2 reg 14 io port: [fb00, fb3f]
[    0.556474] PCI: 0000:00:1e.2 reg 18 32bit mmio: [fdffe000, fdffe1ff]
[    0.556481] PCI: 0000:00:1e.2 reg 1c 32bit mmio: [fdffd000, fdffd0ff]
[    0.556508] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.556512] pci 0000:00:1e.2: PME# disabled
[    0.556601] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.556607] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.556611] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.556636] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.556643] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.556650] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.556657] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.556665] PCI: 0000:00:1f.1 reg 20 io port: [f900, f90f]
[    0.556707] PCI: 0000:00:1f.2 reg 10 io port: [f800, f807]
[    0.556713] PCI: 0000:00:1f.2 reg 14 io port: [f700, f703]
[    0.556720] PCI: 0000:00:1f.2 reg 18 io port: [f600, f607]
[    0.556726] PCI: 0000:00:1f.2 reg 1c io port: [f500, f503]
[    0.556733] PCI: 0000:00:1f.2 reg 20 io port: [f400, f40f]
[    0.556739] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fdffc000, fdffc3ff]
[    0.556758] pci 0000:00:1f.2: PME# supported from D3hot
[    0.556763] pci 0000:00:1f.2: PME# disabled
[    0.556806] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f]
[    0.556861] PCI: 0000:01:00.0 reg 10 32bit mmio: [fa000000, faffffff]
[    0.556868] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.556881] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fb000000, fbffffff]
[    0.556892] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.556941] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.556945] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, fcffffff]
[    0.556951] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.557001] PCI: 0000:02:03.0 reg 10 32bit mmio: [fddfc000, fddfffff]
[    0.557009] PCI: 0000:02:03.0 reg 14 io port: [de00, deff]
[    0.557037] PCI: 0000:02:03.0 reg 30 32bit mmio: [0, 1ffff]
[    0.557055] pci 0000:02:03.0: supports D1
[    0.557057] pci 0000:02:03.0: supports D2
[    0.557059] pci 0000:02:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.557064] pci 0000:02:03.0: PME# disabled
[    0.557104] pci 0000:00:1e.0: transparent bridge
[    0.557108] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
[    0.557113] PCI: bridge 0000:00:1e.0 32bit mmio: [fdd00000, fddfffff]
[    0.557120] PCI: bridge 0000:00:1e.0 64bit mmio pref: [fde00000, fdefffff]
[    0.557139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.557519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.573301] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.573301] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.573301] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 *15)
[    0.573301] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 11 12 14 *15)
[    0.573301] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.576214] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.576405] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.576595] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.576684] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.576684] pnp: PnP ACPI init
[    0.576684] ACPI: bus type pnp registered
[    0.580968] pnp: PnP ACPI: found 15 devices
[    0.580968] ACPI: ACPI bus type pnp unregistered
[    0.584080] PCI: Using ACPI for IRQ routing
[    0.616069] NET: Registered protocol family 8
[    0.616072] NET: Registered protocol family 20
[    0.616094] NetLabel: Initializing
[    0.616094] NetLabel:  domain hash size = 128
[    0.616094] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.616094] NetLabel:  unlabeled traffic allowed by default
[    0.616113] PCI-GART: No AMD northbridge found.
[    0.616198] hpet clockevent registered
[    0.616203] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.616209] hpet0: 3 64-bit timers, 14318180 Hz
[    0.621180] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.621184]    actual entries 65586
[    0.621317] AppArmor: AppArmor Filesystem Enabled
[    0.621339] ACPI: RTC can wake from S4
[    0.636067] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.636071] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.636074] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.636077] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.636080] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.636095] system 00:0b: ioport range 0x400-0x4bf could not be reserved
[    0.636104] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.636112] system 00:0e: iomem range 0xd1800-0xd3fff has been reserved
[    0.636115] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[    0.636118] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.636121] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.636125] system 00:0e: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.636128] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.636131] system 00:0e: iomem range 0x100000-0x7fedffff could not be reserved
[    0.636135] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.636138] system 00:0e: iomem range 0xfed13000-0xfed1dfff could not be reserved
[    0.636142] system 00:0e: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.636145] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.636148] system 00:0e: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.636152] system 00:0e: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.636155] system 00:0e: iomem range 0xe0000-0xeffff has been reserved
[    0.641760] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.641765] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.641770] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfcffffff
[    0.641774] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.641781] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.641785] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.641790] pci 0000:00:1e.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.641795] pci 0000:00:1e.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.641814] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.641819] pci 0000:00:01.0: setting latency timer to 64
[    0.641827] pci 0000:00:1e.0: setting latency timer to 64
[    0.641831] bus: 00 index 0 io port: [0, ffff]
[    0.641834] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.641836] bus: 01 index 0 io port: [c000, cfff]
[    0.641838] bus: 01 index 1 mmio: [fa000000, fcffffff]
[    0.641841] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.641843] bus: 01 index 3 mmio: [0, 0]
[    0.641845] bus: 02 index 0 io port: [d000, dfff]
[    0.641847] bus: 02 index 1 mmio: [fdd00000, fddfffff]
[    0.641850] bus: 02 index 2 mmio: [fde00000, fdefffff]
[    0.641852] bus: 02 index 3 io port: [0, ffff]
[    0.641854] bus: 02 index 4 mmio: [0, ffffffffffffffff]
[    0.641869] NET: Registered protocol family 2
[    0.680273] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.681392] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.683554] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.684124] TCP: Hash tables configured (established 262144 bind 65536)
[    0.684129] TCP reno registered
[    0.696253] NET: Registered protocol family 1
[    0.696412] checking if image is initramfs... it is
[    1.119978] Switched to high resolution mode on CPU 1
[    1.120112] Switched to high resolution mode on CPU 0
[    1.453885] Freeing initrd memory: 8462k freed
[    1.460329] audit: initializing netlink socket (disabled)
[    1.460363] type=2000 audit(1230523685.456:1): initialized
[    1.465998] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.470433] VFS: Disk quotas dquot_6.5.1
[    1.470578] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.470737] msgmni has been set to 4014
[    1.470936] io scheduler noop registered
[    1.470939] io scheduler anticipatory registered
[    1.470942] io scheduler deadline registered
[    1.471143] io scheduler cfq registered (default)
[    1.471285] pci 0000:01:00.0: Boot video device
[    1.471437] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.471484] pcieport-driver 0000:00:01.0: found MSI capability
[    1.471525] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.471619] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.530485] Linux agpgart interface v0.103
[    1.530492] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.530656] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.530820] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.531524] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.531840] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.534932] brd: module loaded
[    1.535051] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.535255] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.535259] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.535458] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.556810] mice: PS/2 mouse device common for all mice
[    1.557017] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.557046] rtc0: alarms up to one month, hpet irqs
[    1.557125] cpuidle: using governor ladder
[    1.557129] cpuidle: using governor menu
[    1.557618] TCP cubic registered
[    1.557946] registered taskstats version 1
[    1.558080]   Magic number: 4:702:111
[    1.558214] rtc_cmos 00:03: setting system clock to 2008-12-29 04:08:06 UTC (1230523686)
[    1.558219] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.558221] EDD information not available.
[    1.558275] Freeing unused kernel memory: 536k freed
[    1.558556] Write protecting the kernel read-only data: 4348k
[    1.770417] fuse init (API version 7.9)
[    1.812277] fan PNP0C0B:00: registered as cooling_device0
[    1.812286] ACPI: Fan [FAN] (on)
[    1.848249] processor ACPI0007:00: registered as cooling_device1
[    1.848600] ACPI: SSDT 7FEE7C00, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[    1.848945] processor ACPI0007:01: registered as cooling_device2
[    1.854583] thermal LNXTHERM:01: registered as thermal_zone0
[    1.855010] ACPI: Thermal Zone [THRM] (40 C)
[    2.040632] usbcore: registered new interface driver usbfs
[    2.040663] usbcore: registered new interface driver hub
[    2.044113] usbcore: registered new device driver usb
[    2.050869] USB Universal Host Controller Interface driver v3.0
[    2.050930] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.050945] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.050949] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.051010] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.051052] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
[    2.051251] usb usb1: configuration #1 chosen from 1 choice
[    2.051289] hub 1-0:1.0: USB hub found
[    2.051298] hub 1-0:1.0: 2 ports detected
[    2.260320] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.260333] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.260337] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.260372] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.260414] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
[    2.260533] usb usb2: configuration #1 chosen from 1 choice
[    2.260568] hub 2-0:1.0: USB hub found
[    2.260577] hub 2-0:1.0: 2 ports detected
[    2.287382] No dock devices found.
[    2.309118] SCSI subsystem initialized
[    2.324100] libata version 3.00 loaded.
[    2.368576] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.368589] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.368594] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.368628] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.368669] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
[    2.368787] usb usb3: configuration #1 chosen from 1 choice
[    2.368821] hub 3-0:1.0: USB hub found
[    2.368830] hub 3-0:1.0: 2 ports detected
[    2.376026] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    2.476853] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.476866] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.476870] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.476903] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.476944] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
[    2.477065] usb usb4: configuration #1 chosen from 1 choice
[    2.477101] hub 4-0:1.0: USB hub found
[    2.477111] hub 4-0:1.0: 2 ports detected
[    2.557327] usb 1-1: configuration #1 chosen from 1 choice
[    2.688461] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.688481] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.688485] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.688548] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.692459] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.692470] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    2.796585] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    2.808538] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.808755] usb usb5: configuration #1 chosen from 1 choice
[    2.808792] hub 5-0:1.0: USB hub found
[    2.808803] hub 5-0:1.0: 8 ports detected
[    2.864608] hub 4-0:1.0: unable to enumerate USB device on port 2
[    2.884068] usb 1-1: USB disconnect, address 2
[    3.017284] skge 0000:02:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.017329] skge 1.13 addr 0xfddfc000 irq 16 chip Yukon-Lite rev 9
[    3.017852] skge eth0: addr 00:15:58:96:f6:e0
[    3.021723] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.021759] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.021777] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.021797] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.021819] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.021831] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.025552] ata_piix 0000:00:1f.1: version 2.12
[    3.025564] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.025603] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.028822] scsi0 : ata_piix
[    3.028957] scsi1 : ata_piix
[    3.030029] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    3.030033] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    3.184249] usb 5-8: new high speed USB device using ehci_hcd and address 3
[    3.192396] ata1.00: ATAPI: SONY    DVD RW AW-Q170A, 1.73, max UDMA/66
[    3.208318] ata1.00: configured for UDMA/66
[    3.208368] ata2: port disabled. ignoring.
[    3.208417] isa bounce pool size: 16 pages
[    3.209373] scsi 0:0:0:0: CD-ROM            SONY     DVD RW AW-Q170A  1.73 PQ: 0 ANSI: 5
[    3.209528] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.209534] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.209583] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.209748] scsi2 : ata_piix
[    3.209852] scsi3 : ata_piix
[    3.210949] ata3: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf400 irq 19
[    3.210952] ata4: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf408 irq 19
[    3.325376] usb 5-8: configuration #1 chosen from 1 choice
[    3.326049] hub 5-8:1.0: USB hub found
[    3.326744] hub 5-8:1.0: 3 ports detected
[    3.533541] usbcore: registered new interface driver hiddev
[    3.599069] ata4.01: ATA-7: ST380815AS, 3.AAD, max UDMA/133
[    3.599075] ata4.01: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.665702] ata4.01: configured for UDMA/133
[    3.665884] scsi 3:0:1:0: Direct-Access     ATA      ST380815AS       3.AA PQ: 0 ANSI: 5
[    3.678547] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.678599] scsi 3:0:1:0: Attached scsi generic sg1 type 0
[    3.698499] Driver 'sr' needs updating - please use bus_type methods
[    3.704485] Driver 'sd' needs updating - please use bus_type methods
[    3.705041] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.705046] Uniform CD-ROM driver Revision: 3.20
[    3.705154] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.705570] sd 3:0:1:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.705601] sd 3:0:1:0: [sda] Write Protect is off
[    3.705605] sd 3:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    3.705658] sd 3:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.705747] sd 3:0:1:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.705776] sd 3:0:1:0: [sda] Write Protect is off
[    3.705779] sd 3:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    3.705831] sd 3:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.705837]  sda: sda1 sda2
[    3.722318] sd 3:0:1:0: [sda] Attached SCSI disk
[    3.772037] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    3.949917] usb 1-1: configuration #1 chosen from 1 choice
[    4.040119] usb 5-8.2: new low speed USB device using ehci_hcd and address 4
[    4.139566] usb 5-8.2: configuration #1 chosen from 1 choice
[    4.155491] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input1
[    4.180184] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[    4.210367] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input2
[    4.220142] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1
[    4.223555] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8.2/5-8.2:1.0/input/input3
[    4.232144] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-8.2
[    4.235069] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8.2/5-8.2:1.1/input/input4
[    4.264115] input,hidraw3: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-8.2
[    4.264140] usbcore: registered new interface driver usbhid
[    4.264145] usbhid: v2.6:USB HID core driver
[    9.405435] kjournald starting.  Commit interval 5 seconds
[    9.405456] EXT3-fs: mounted filesystem with ordered data mode.
[   14.435030] udevd version 124 started
[   14.827807] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.866632] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.950107] intel_rng: FWH not detected
[   15.027740] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   15.040037] ACPI: Power Button (FF) [PWRF]
[   15.040144] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   15.072048] ACPI: Power Button (CM) [PWRB]
[   15.126748] iTCO_vendor_support: vendor-support=0
[   15.175035] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   15.175139] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   15.175482] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.294737] parport_pc 00:09: reported by Plug and Play ACPI
[   15.294791] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.724857] nvidia: module license 'NVIDIA' taints kernel.
[   15.999566] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.999577] nvidia 0000:01:00.0: setting latency timer to 64
[   15.999824] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   16.429805] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.429830] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   16.752035] intel8x0_measure_ac97_clock: measured 54621 usecs
[   16.752040] intel8x0: clocking to 48000
[   18.358857] lp0: using parport0 (interrupt-driven).
[   18.424562] it87: Found IT8718F chip at 0x290, revision 1
[   18.424572] it87: in3 is VCC (+5V)
[   18.424574] it87: in7 is VCCH (+5V Stand-By)
[   18.975859] EXT3 FS on sda1, internal journal
[   19.566741] type=1505 audit(1230523704.331:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4323
[   19.741391] type=1505 audit(1230523704.507:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4328
[   19.741579] type=1505 audit(1230523704.507:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4328
[   19.894090] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.562032] ACPI: WMI: Mapper loaded
[   21.646183] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.848312] ppdev: user-space parallel port driver
[   23.876874] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   23.876889] vboxdrv: Successfully done.
[   23.876891] vboxdrv: Found 2 processor cores.
[   23.881682] vboxdrv: fAsync=0 offMin=0x654 offMax=0x2e3b
[   23.881693] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   23.881695] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   29.425039] skge eth0: enabling interface
[   31.103492] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   31.179790] NET: Registered protocol family 17
[   49.084439] canberra-gtk-pl[5875]: segfault at 10069eb80 ip 00007fffd564d6ec sp 00000000423e2bd0 error 6 in libc-2.8.90.so[7fffd55d1000+169000]
```

---

### Post by anubhavrocks on 2008-12-28
I guess this is a bug:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/284996](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/284996)

---

### Post by aheckler on 2008-12-28
I don't know. In the bug description he says that " 'quiet splash' works as normal" for him, but that is not the case for me.

This was working fine just a few days ago, could a very recent update done this?

---

### Post by anubhavrocks on 2008-12-28
Why don't you try the older kernel image?You might need to apt-get it.

---

### Post by caljohnsmith on 2008-12-29
Please post the output of the following:
```
sudo blkid
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by serapis5 on 2008-12-29
@aheckler:

I've run into this same problem with several versions of Ubuntu after updates.  In my case, it seems to happen whenever there is an update to the Usplash files.  In VGA mode (ie during startup) many monitors can only see a max of 1024 X 768 but recent usplash.conf files default to 1280 X 1024.  Try opening a terminal and type the following:

code:
sudo gedit /etc/usplash.conf

it should read something like this:

# Usplash configuration file
xres=1024
yres=768

If you have startup-manager installed you can also check the Boot Options tab for resolution and color depth (should not be more than 16 bit for most cards).  On the Appearance tab, under Usplash Themes, make sure that you still have usplash-theme-ubuntu selected in the dialog box.

good luck

---

### Post by serapis5 on 2008-12-29
Sorry, double posted

---

### Post by aheckler on 2008-12-29
blkid:
```
/dev/sda1: UUID="b521f678-a290-4664-9544-5a0f00b2a619" TYPE="ext3" 
/dev/sda5: UUID="bd8fab02-7197-453a-b592-2e0c191512dc" TYPE="swap" 
/dev/sda2: UUID="d7c83cbb-2f5f-4dcb-981c-bcd148e90b71" SEC_TYPE="ext2" TYPE="ext3" 
```

fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b521f678-a290-4664-9544-5a0f00b2a619 /               ext3    relatime,errors=remount-ro,noatime,nodiratime 0       1
# /dev/sda5
UUID=bd8fab02-7197-453a-b592-2e0c191512dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

/etc/initramfs-tools/conf.d/resume:
```
RESUME=UUID=bd8fab02-7197-453a-b592-2e0c191512dc
```

Now that I see these outputs, they seem very weird because **I do not have a swap partition**. (I just double-checked in gparted.) Could this be causing the problem?

---

### Post by aheckler on 2008-12-29
@**serapis5**: my usplash.conf is set at 1280x1024, which is the correct resolution for my monitor. Are you advising I "downgrade" to 1024x768?

---

### Post by caljohnsmith on 2008-12-29
You don't have a swap partition? That's strange, because according to the blkid output you still do. Did you try to delete your swap partition at some point, or why do you say you don't have a swap partition? How about also posting:
```
sudo fdisk -l
```

---

### Post by aheckler on 2008-12-29
"fdisk -l" confirms no swap. Just sda1 and sda2, Ubuntu and Arch. Is there a way to regenerate the erroneous files to reflect the correct state of my partition table?

---

### Post by dcstar on 2008-12-29
> **aheckler said:**
> I recently noticed that my Intrepid boot process is no longer "quiet". That is, it spits out all the info about various processes it's starting and the progress bar doesn't show up anymore. But the "quiet" and "splash" flags in my /boot/grub/menu.lst are still there:
.......
I think it may have something to do with the fact that I recently repartitioned my drive and installed Arch on another section. However, I didn't overwrite GRUB while doing so, and added the Arch lines later, so I'm not sure what's wrong. Halp!

Try:
```
sudo update-initramfs -k all -u
```

---

### Post by caljohnsmith on 2008-12-29
> **aheckler said:**
> "fdisk -l" confirms no swap. Just sda1 and sda2, Ubuntu and Arch. Is there a way to regenerate the erroneous files to reflect the correct state of my partition table?
OK, at least that explains then why you don't have a splash screen: a missing Ubuntu splash screen is one of the symptoms of when the initrd boot images point to a non-existent swap partition, which would be your case. But since you don't have a swap partition, I think I would try the following:
```
sudo mv /etc/initramfs-tools/conf.d/resume /etc/initramfs-tools/conf.d/resume.backup
```
And then you can run the command that dcstar gave:
```
sudo update-initramfs -u -k all
```
If you run the command that dcstar gave without changing your UUID in the resume file or making the resume file inaccessible as done above, it unfortunately won't help you since you will be regenerating your initrd images with the same non-existent swap partition UUID. How about trying the above commands and let me know if it makes any difference or not.

---

### Post by aheckler on 2008-12-29
"blkid" and "fstab" still show a swap, while "/etc/initramfs-tools/conf.d/resume" returns a "no such file".

Problem still exists.

---

### Post by caljohnsmith on 2008-12-29
So I can get a better idea of what's going on, how about actually posting the output of:
```

sudo fdisk -l
sudo blkid -c /dev/null
```
I think you should go ahead and get rid of the swap partition line in your /etc/fstab since that partition doesn't exist, so next do:
```
gksudo gedit /etc/fstab
```
And instead of actually deleting the lines, I would comment it out:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b521f678-a290-4664-9544-5a0f00b2a619 /               ext3    relatime,errors=remount-ro,noatime,nodiratime 0       1
# /dev/sda5
[COLOR="Red"]#[/COLOR] UUID=bd8fab02-7197-453a-b592-2e0c191512dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by aheckler on 2008-12-29
fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008577f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7012    56323858+  83  Linux
/dev/sda2            7013        9729    21824302+  83  Linux
```

blkid -c /dev/null:
```
/dev/sda1: UUID="b521f678-a290-4664-9544-5a0f00b2a619" TYPE="ext3" 
/dev/sda2: UUID="d7c83cbb-2f5f-4dcb-981c-bcd148e90b71" SEC_TYPE="ext2" TYPE="ext3" 
```

---

### Post by aheckler on 2008-12-29
Commenting out swap in fstab had no effect.

---

### Post by serapis5 on 2008-12-31
@aheckler:

To an extent,yes that was my suggestion (dg to 1024X768).  In this instance, it's not a downgrade for your entire experience, only for the boot process (vga mode, before the display manager takes over).  All of my monitors are native 1280 X 1024, but I have noticed that on all of my machines, I have to set the usplash.conf at 1024 X 768 and (fairly) low color resolution or...no boot screen.  Just system processes.  Once your DM takes over (login screen), you will be at 1280 X 1024. Since we are only talking about the boot process, I doubt you will ever notice the resolution thing, most splash images are fairly low-res anyway.  At any rate, it's easily reversible if it doesn't solve your issue.  Good luck.

---

### Post by aheckler on 2008-12-31
Well at this point it seems like the underlying problem is my partition table, where ubuntu seems to think I have a swap when actually I don't. I am still trying to find out how I can "refresh" the bootup process so that Ubuntu isn't looking for a swap partition, and thus falling back on text output instead of the splash screen.

---

### Post by serapis5 on 2008-12-31
I'm sorry I couldn't help.  It sounded so exactly like what I ran into time and again, and with multiple distros, I just thought I would throw it out there (and if it was a butt-in, I apologize).  In any case, I wish you the best of luck with your /swap issue.  Since all of my machines run with /swap files, I'm afraid I can't offer any advice on that front.  I'm intrigued now, though, so I hope I'll see a resolution to your problem soon.

Best regards

---

### Post by dcstar on 2008-12-31
> **aheckler said:**
> Well at this point it seems like the underlying problem is my partition table, where ubuntu seems to think I have a swap when actually I don't. I am still trying to find out how I can "refresh" the bootup process so that Ubuntu isn't looking for a swap partition, and thus falling back on text output instead of the splash screen.

Simply make a new Swap partition, fix the fstab & resume files to suit and your problem will be fixed.

---

### Post by djbushido on 2008-12-31
I don't think that the swap partition add in is exactly the best of ideas. Might work. here is a question though (because this is intriguing me as well:happening to me after a repartition, for fedora): do you have a graphical loadup on the arch machine? or did it come with one? I assume it does, but just checking.

---

### Post by aheckler on 2009-01-01
No graphical boot on Arch. I think that's by default though, so I don't know if that's indicative of anything.

---

### Post by David D. on 2009-01-01
My boot is also no longer "quiet".  The flag is still in the menu.lst. Just prior to losing the "quiet" on boot, I used gparted on a live CD to change the size of my partitions (increase Ubuntu and swap, decrease Windows).  The repartitioning is a common element with the original post.  Could the repartitioning have caused the problem?

---

### Post by djbushido on 2009-01-01
I agree, this repartitioning thing definitely seems to be the problem. do we just need to update fstab with the new UUID's? or is it something more...

---

### Post by caljohnsmith on 2009-01-01
David D. and djbushido: if you have a swap partition and its UUID changed, that would cause you to lose your Ubuntu splash screen. One way to fix it is by simply changing the swap UUID back to what it originally was:

[http://ubuntuforums.org/showthread.php?t=1021981](http://ubuntuforums.org/showthread.php?t=1021981)

Let me know if that helps.

---

### Post by David D. on 2009-01-01
The solution caljohnsmith has in the thread link has solved the problem for me.  The UUID for the swap partition must have changed when I used gparted to modify the partition sizes.

---

### Post by djbushido on 2009-01-02
Yep, mine got fixed too. Thanks a lot!

---

