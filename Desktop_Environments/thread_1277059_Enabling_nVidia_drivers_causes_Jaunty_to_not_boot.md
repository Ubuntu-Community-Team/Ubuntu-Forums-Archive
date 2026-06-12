---
title: "Enabling nVidia drivers causes Jaunty to not boot"
date: 2009-09-27
forum: Desktop Environments
---

### Post by Wintaru on 2009-09-27
Greetings, hopefully someone can help me out.  I have a desktop with dual GT 260 nVidia cards, and while the install of Ubuntu went fine, whenever I try to enable the nVidia restricted drivers upon reboot it hangs after the Checking battery state [OK].  The only way to get back to my desktop is to uninstall the nVidia drivers.

This is my current (read: working) xorg.conf file:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option	"NoLogo"	"True"
	Driver	"nv"
EndSection
```

I've tried adding the BusID entry with either card's ID, but that doesn't seem to be the issue either.

Any thoughts?  3 hours of googling hasn't helped me find an answer yet.

---

### Post by ~sHyLoCk~ on 2009-09-27
Change driver from "nv" to "nvidia" and see if that helps.

EDIT: Ok, re-install the driver and show us the changed Xorg.conf

---

### Post by Wintaru on 2009-09-27
Before reboot?  Because if I reboot it then I won't be able to copy and paste it.

---

### Post by Wintaru on 2009-09-27
Here it is after installing the driver but before rebooting:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Thanks for the help!

---

### Post by ~sHyLoCk~ on 2009-09-27
Seems fine to me. Try using ```
nvidia-xconfig
``` and see if that helps.

---

### Post by Wintaru on 2009-09-27
Ok, before reboot I get this, and it's probably expected:

```
WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.
```

I'll go ahead and reboot and if I have the same problem I'll Alt+F1 and see if it works from the command line.  Will post shortly.

---

### Post by Wintaru on 2009-09-27
Oops, forgot sudo.  With that added I get this:

```
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

xorg.conf now looks like this:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

---

### Post by Wintaru on 2009-09-27
Just tried rebooting to no avail.  Uninstalled the nVidia driver and I'm back.  I forgot to mention I tried the sudo dpkg etc. to rebuild my xorg.conf file after this happens, that doesn't work either.  Very much a bummer right now, I have my desktop but no 3D acceleration.

---

### Post by ~sHyLoCk~ on 2009-09-28
How about trying the nvidia drver from their website an compiling it?

---

### Post by Wintaru on 2009-09-28
One step ahead of you, downloaded the 185 driver and followed the steps on the NvidiaManual page with no luck :(

---

### Post by krazyd on 2009-09-28
you're probably better off searching and asking on [http://nvnews.net](http://nvnews.net)

nvidia dev's hang out there and they're the only ones who can help with driver bugs..

---

### Post by karlson on 2009-09-28
can you boot it into command line mode.

Login as Root and run "startx"  to see what happens?

Also dmesg output would be helpful.

---

### Post by Wintaru on 2009-09-28
I'll try both of those, give me a moment...

---

### Post by Wintaru on 2009-09-28
Ok, when I log in on the command line, I then typed "sudo bash" to get root, then typed "startx".

Obviously no copy and paste (typing this from my Mac), so forgive any typing errors as I recreate what I'm seeing:

```

(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation Support
       at http://wiki.x.org
  for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

  ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

```

I'll check for that log file when I roll back the driver, but now I'm trying dmesg now, dumping its results to a log file and I'll post those after I roll the driver back.  One moment.

---

### Post by Wintaru on 2009-09-28
Yikes, the dmesg output is long!  Here you go :)

```
[    0.000000] BIOS EBDA/lowmem at: 0009b800/0009b800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009fef0000 (usable)
[    0.000000]  BIOS-e820: 000000009fef0000 - 000000009fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fef3000 - 000000009ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000260000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x9fef0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009b800 (usable)
[    0.000000]  modified: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009fef0000 (usable)
[    0.000000]  modified: 000000009fef0000 - 000000009fef3000 (ACPI NVS)
[    0.000000]  modified: 000000009fef3000 - 000000009ff00000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000260000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378ba000 - 37fef2e4
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb22e4
[    0.000000] Move RAMDISK from 00000000378ba000 - 0000000037fef2e3 to 0087d000 - 00fb22e3
[    0.000000] ACPI: RSDP 000F7FA0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 9FEF3040, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 9FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: DSDT 9FEF3180, 5411 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 9FEF0000, 0040
[    0.000000] ACPI: HPET 9FEF8700, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: WDRT 9FEF8780, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: MCFG 9FEF8840, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 9FEF8600, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: OEMN 9FEF88C0, 4AED (r1 NVIDIA NTUNEOEM 20302E31 NVDA        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1674MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009b800 - 0000100000]    BIOS reserved ==> [000009b800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fb22e4]      NEW RAMDISK ==> [000087d000 - 0000fb22e4]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f3fd0] 000f3fd0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0009fef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0009fef0
[    0.000000] On node 0 totalpages: 654971
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3350 pages used for memmap
[    0.000000]   HighMem zone: 425436 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: 9ff00000:40100000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 649853
[    0.000000] Kernel command line: root=UUID=c6d623c0-7579-4ec1-b056-31be90d741fa ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2500.059 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 13101440 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2569660k/2620352k available (4115k kernel code, 49364k reserved, 2199k data, 532k init, 1715144k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5000.11 BogoMIPS (lpj=10000236)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017999] ACPI: Core revision 20080926
[    0.018881] ACPI: Checking initramfs for custom DSDT
[    0.256469] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.297341] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[    0.300001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4999.90 BogoMIPS (lpj=9999806)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.384480] CPU1: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[    0.384492] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.388085] Booting processor 2 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4999.95 BogoMIPS (lpj=9999904)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.476516] CPU2: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[    0.476528] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.480077] Booting processor 3 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4999.92 BogoMIPS (lpj=9999845)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.568449] CPU3: Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz stepping 07
[    0.568462] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.572019] Brought up 4 CPUs
[    0.572022] Total of 4 processors activated (19999.89 BogoMIPS).
[    0.572106] CPU0 attaching sched-domain:
[    0.572108]  domain 0: span 0-1 level MC
[    0.572110]   groups: 0 1
[    0.572113]   domain 1: span 0-3 level CPU
[    0.572115]    groups: 0-1 2-3
[    0.572119] CPU1 attaching sched-domain:
[    0.572120]  domain 0: span 0-1 level MC
[    0.572122]   groups: 1 0
[    0.572124]   domain 1: span 0-3 level CPU
[    0.572126]    groups: 0-1 2-3
[    0.572129] CPU2 attaching sched-domain:
[    0.572130]  domain 0: span 2-3 level MC
[    0.572132]   groups: 2 3
[    0.572135]   domain 1: span 0-3 level CPU
[    0.572136]    groups: 2-3 0-1
[    0.572140] CPU3 attaching sched-domain:
[    0.572141]  domain 0: span 2-3 level MC
[    0.572143]   groups: 3 2
[    0.572145]   domain 1: span 0-3 level CPU
[    0.572147]    groups: 2-3 0-1
[    0.572245] net_namespace: 776 bytes
[    0.572245] Booting paravirtualized kernel on bare hardware
[    0.572256] Time: 15:51:16  Date: 09/28/09
[    0.572256] regulator: core version 0.5
[    0.572256] NET: Registered protocol family 16
[    0.572256] EISA bus registered
[    0.572256] ACPI: bus type pci registered
[    0.572256] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.572256] PCI: MCFG area at e0000000 reserved in E820
[    0.572256] PCI: Using MMCONFIG for extended config space
[    0.572256] PCI: Using configuration type 1 for base access
[    0.572855] ACPI: EC: Look up EC in DSDT
[    0.581389] ACPI: Interpreter enabled
[    0.581396] ACPI: (supports S0 S3 S4 S5)
[    0.581412] ACPI: Using IOAPIC for interrupt routing
[    0.581628] ACPI: BIOS _OSI(Linux) query ignored
[    0.588264] ACPI: No dock devices found.
[    0.588273] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.588962] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.588966] pci 0000:00:02.0: PME# disabled
[    0.589038] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.589042] pci 0000:00:04.0: PME# disabled
[    0.589222] pci 0000:00:0a.0: reg 10 io port: [0xfc00-0xfc7f]
[    0.589268] pci 0000:00:0a.1: reg 10 io port: [0xf800-0xf83f]
[    0.589282] pci 0000:00:0a.1: reg 20 io port: [0xf400-0xf43f]
[    0.589287] pci 0000:00:0a.1: reg 24 io port: [0xf000-0xf03f]
[    0.589300] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.589305] pci 0000:00:0a.1: PME# disabled
[    0.589334] pci 0000:00:0b.0: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.589357] pci 0000:00:0b.0: supports D1 D2
[    0.589359] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.589362] pci 0000:00:0b.0: PME# disabled
[    0.589386] pci 0000:00:0b.1: reg 10 32bit mmio: [0xdfffe000-0xdfffe0ff]
[    0.589409] pci 0000:00:0b.1: supports D1 D2
[    0.589410] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.589413] pci 0000:00:0b.1: PME# disabled
[    0.589450] pci 0000:00:0d.0: reg 20 io port: [0xec00-0xec0f]
[    0.589486] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
[    0.589490] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
[    0.589494] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
[    0.589498] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
[    0.589502] pci 0000:00:0e.0: reg 20 io port: [0xd800-0xd80f]
[    0.589507] pci 0000:00:0e.0: reg 24 32bit mmio: [0xdfffd000-0xdfffdfff]
[    0.589542] pci 0000:00:0e.1: reg 10 io port: [0x9e0-0x9e7]
[    0.589546] pci 0000:00:0e.1: reg 14 io port: [0xbe0-0xbe3]
[    0.589550] pci 0000:00:0e.1: reg 18 io port: [0x960-0x967]
[    0.589554] pci 0000:00:0e.1: reg 1c io port: [0xb60-0xb63]
[    0.589558] pci 0000:00:0e.1: reg 20 io port: [0xc400-0xc40f]
[    0.589563] pci 0000:00:0e.1: reg 24 32bit mmio: [0xdfffc000-0xdfffcfff]
[    0.589598] pci 0000:00:0e.2: reg 10 io port: [0xc000-0xc007]
[    0.589602] pci 0000:00:0e.2: reg 14 io port: [0xbc00-0xbc03]
[    0.589606] pci 0000:00:0e.2: reg 18 io port: [0xb800-0xb807]
[    0.589610] pci 0000:00:0e.2: reg 1c io port: [0xb400-0xb403]
[    0.589614] pci 0000:00:0e.2: reg 20 io port: [0xb000-0xb00f]
[    0.589619] pci 0000:00:0e.2: reg 24 32bit mmio: [0xdfffb000-0xdfffbfff]
[    0.589691] pci 0000:00:0f.1: reg 10 32bit mmio: [0xdfff0000-0xdfff3fff]
[    0.589714] pci 0000:00:0f.1: PME# supported from D3hot D3cold
[    0.589717] pci 0000:00:0f.1: PME# disabled
[    0.589763] pci 0000:00:11.0: reg 10 32bit mmio: [0xdfffa000-0xdfffafff]
[    0.589768] pci 0000:00:11.0: reg 14 io port: [0xac00-0xac07]
[    0.589772] pci 0000:00:11.0: reg 18 32bit mmio: [0xdfff9000-0xdfff90ff]
[    0.589776] pci 0000:00:11.0: reg 1c 32bit mmio: [0xdfff8000-0xdfff800f]
[    0.589791] pci 0000:00:11.0: supports D1 D2
[    0.589792] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.589797] pci 0000:00:11.0: PME# disabled
[    0.589838] pci 0000:00:12.0: reg 10 32bit mmio: [0xdfff7000-0xdfff7fff]
[    0.589842] pci 0000:00:12.0: reg 14 io port: [0xa800-0xa807]
[    0.589846] pci 0000:00:12.0: reg 18 32bit mmio: [0xdfff6000-0xdfff60ff]
[    0.589851] pci 0000:00:12.0: reg 1c 32bit mmio: [0xdfff5000-0xdfff500f]
[    0.589865] pci 0000:00:12.0: supports D1 D2
[    0.589867] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.589871] pci 0000:00:12.0: PME# disabled
[    0.589910] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.589913] pci 0000:00:15.0: PME# disabled
[    0.589954] pci 0000:01:00.0: reg 10 32bit mmio: [0xd8000000-0xd8ffffff]
[    0.589962] pci 0000:01:00.0: reg 14 64bit mmio: [0xb0000000-0xbfffffff]
[    0.589970] pci 0000:01:00.0: reg 1c 64bit mmio: [0xd6000000-0xd7ffffff]
[    0.589975] pci 0000:01:00.0: reg 24 io port: [0x9c00-0x9c7f]
[    0.589979] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.590028] pci 0000:00:02.0: bridge io port: [0x9000-0x9fff]
[    0.590032] pci 0000:00:02.0: bridge 32bit mmio: [0xd6000000-0xd9ffffff]
[    0.590038] pci 0000:00:02.0: bridge 64bit mmio pref: [0xb0000000-0xbfffffff]
[    0.590064] pci 0000:02:00.0: reg 10 32bit mmio: [0xdc000000-0xdcffffff]
[    0.590071] pci 0000:02:00.0: reg 14 64bit mmio: [0xa0000000-0xafffffff]
[    0.590079] pci 0000:02:00.0: reg 1c 64bit mmio: [0xda000000-0xdbffffff]
[    0.590084] pci 0000:02:00.0: reg 24 io port: [0x8c00-0x8c7f]
[    0.590088] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.590137] pci 0000:00:04.0: bridge io port: [0x8000-0x8fff]
[    0.590141] pci 0000:00:04.0: bridge 32bit mmio: [0xda000000-0xddffffff]
[    0.590146] pci 0000:00:04.0: bridge 64bit mmio pref: [0xa0000000-0xafffffff]
[    0.590180] pci 0000:03:07.0: reg 10 32bit mmio: [0xd3fff000-0xd3fff7ff]
[    0.590185] pci 0000:03:07.0: reg 14 32bit mmio: [0xd3ff8000-0xd3ffbfff]
[    0.590212] pci 0000:03:07.0: supports D1 D2
[    0.590213] pci 0000:03:07.0: PME# supported from D0 D1 D2 D3hot
[    0.590217] pci 0000:03:07.0: PME# disabled
[    0.590247] pci 0000:03:09.0: reg 10 32bit mmio: [0xcc000000-0xcfffffff]
[    0.590301] pci 0000:00:0f.0: transparent bridge
[    0.590305] pci 0000:00:0f.0: bridge 32bit mmio: [0xcc000000-0xd3ffffff]
[    0.590378] pci 0000:04:00.0: reg 24 32bit mmio: [0xdfefe000-0xdfefffff]
[    0.590394] pci 0000:04:00.0: PME# supported from D3hot
[    0.590399] pci 0000:04:00.0: PME# disabled
[    0.590440] pci 0000:04:00.1: reg 10 io port: [0x7c00-0x7c07]
[    0.590447] pci 0000:04:00.1: reg 14 io port: [0x7800-0x7803]
[    0.590454] pci 0000:04:00.1: reg 18 io port: [0x7400-0x7407]
[    0.590462] pci 0000:04:00.1: reg 1c io port: [0x7000-0x7003]
[    0.590469] pci 0000:04:00.1: reg 20 io port: [0x6c00-0x6c0f]
[    0.590539] pci 0000:00:15.0: bridge io port: [0x6000-0x7fff]
[    0.590542] pci 0000:00:15.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.590559] bus 00 -> node 0
[    0.590565] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.591048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.647780] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.647923] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[    0.648074] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.648215] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[    0.648354] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)
[    0.648494] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 *11 14 15)
[    0.648643] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 *11 14 15)
[    0.648783] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 *10 11 14 15)
[    0.648922] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.649061] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[    0.649201] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.649344] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.649483] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.649624] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.649763] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.649903] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 10 *11 14 15)
[    0.650043] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 *10 11 14 15)
[    0.650185] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 *11 14 15)
[    0.650356] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.650520] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.650684] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.650848] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.651011] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
[    0.651175] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0
[    0.651338] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0
[    0.651501] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0
[    0.651665] ACPI: PCI Interrupt Link [AUBA] (IRQs 22 23) *0
[    0.651831] ACPI: PCI Interrupt Link [AMA1] (IRQs 22 23) *0
[    0.652004] ACPI: PCI Interrupt Link [AMAC] (IRQs 22 23) *0
[    0.652169] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
[    0.652333] ACPI: PCI Interrupt Link [AACI] (IRQs 22 23) *0, disabled.
[    0.652497] ACPI: PCI Interrupt Link [AMCI] (IRQs 22 23) *0, disabled.
[    0.652669] ACPI: PCI Interrupt Link [ASMB] (IRQs 22 23) *0, disabled.
[    0.652833] ACPI: PCI Interrupt Link [AUS2] (IRQs 22 23) *0
[    0.652997] ACPI: PCI Interrupt Link [AIDE] (IRQs 22 23) *0, disabled.
[    0.653161] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21) *0
[    0.653325] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21) *0
[    0.653488] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21) *0
[    0.654371] ACPI: WMI: Mapper loaded
[    0.654403] SCSI subsystem initialized
[    0.654403] libata version 3.00 loaded.
[    0.654403] usbcore: registered new interface driver usbfs
[    0.654403] usbcore: registered new interface driver hub
[    0.654403] usbcore: registered new device driver usb
[    0.654403] PCI: Using ACPI for IRQ routing
[    0.660010] Bluetooth: Core ver 2.13
[    0.660024] NET: Registered protocol family 31
[    0.660024] Bluetooth: HCI device and connection manager initialized
[    0.660024] Bluetooth: HCI socket layer initialized
[    0.660024] NET: Registered protocol family 8
[    0.660024] NET: Registered protocol family 20
[    0.660033] NetLabel: Initializing
[    0.660035] NetLabel:  domain hash size = 128
[    0.660036] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.660047] NetLabel:  unlabeled traffic allowed by default
[    0.660079] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.660083] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.668051] AppArmor: AppArmor Filesystem Enabled
[    0.672008] Switched to high resolution mode on CPU 0
[    0.672507] Switched to high resolution mode on CPU 3
[    0.672518] Switched to high resolution mode on CPU 1
[    0.672570] Switched to high resolution mode on CPU 2
[    0.675998] pnp: PnP ACPI init
[    0.676009] ACPI: bus type pnp registered
[    0.679167] pnp: PnP ACPI: found 13 devices
[    0.679169] ACPI: ACPI bus type pnp unregistered
[    0.679172] PnPBIOS: Disabled by ACPI PNP
[    0.679179] system 00:00: ioport range 0x1000-0x107f has been reserved
[    0.679181] system 00:00: ioport range 0x1080-0x10ff has been reserved
[    0.679183] system 00:00: ioport range 0x1400-0x147f has been reserved
[    0.679185] system 00:00: ioport range 0x1480-0x14ff has been reserved
[    0.679187] system 00:00: ioport range 0x1800-0x187f has been reserved
[    0.679189] system 00:00: ioport range 0x1880-0x18ff has been reserved
[    0.679194] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.679196] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.679198] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.679206] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.679210] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[    0.679212] system 00:0c: iomem range 0xdf400-0xdffff has been reserved
[    0.679214] system 00:0c: iomem range 0xf0000-0xfbfff could not be reserved
[    0.679216] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.679218] system 00:0c: iomem range 0x9fef0000-0x9fefffff could not be reserved
[    0.679220] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.679223] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.679225] system 00:0c: iomem range 0x100000-0x9feeffff could not be reserved
[    0.679227] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.679229] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.679231] system 00:0c: iomem range 0xfeff0000-0xfeff0000 has been reserved
[    0.713893] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.713897] pci 0000:00:02.0:   IO window: 0x9000-0x9fff
[    0.713901] pci 0000:00:02.0:   MEM window: 0xd6000000-0xd9ffffff
[    0.713905] pci 0000:00:02.0:   PREFETCH window: 0x000000b0000000-0x000000bfffffff
[    0.713911] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.713914] pci 0000:00:04.0:   IO window: 0x8000-0x8fff
[    0.713918] pci 0000:00:04.0:   MEM window: 0xda000000-0xddffffff
[    0.713922] pci 0000:00:04.0:   PREFETCH window: 0x000000a0000000-0x000000afffffff
[    0.713928] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:03
[    0.713929] pci 0000:00:0f.0:   IO window: disabled
[    0.713932] pci 0000:00:0f.0:   MEM window: 0xcc000000-0xd3ffffff
[    0.713935] pci 0000:00:0f.0:   PREFETCH window: disabled
[    0.713939] pci 0000:00:15.0: PCI bridge, secondary bus 0000:04
[    0.713941] pci 0000:00:15.0:   IO window: 0x6000-0x7fff
[    0.713944] pci 0000:00:15.0:   MEM window: 0xdfe00000-0xdfefffff
[    0.713947] pci 0000:00:15.0:   PREFETCH window: disabled
[    0.714195] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[    0.714199] pci 0000:00:02.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[    0.714203] pci 0000:00:02.0: setting latency timer to 64
[    0.714443] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
[    0.714445] pci 0000:00:04.0: PCI INT A -> Link[AXV6] -> GSI 16 (level, low) -> IRQ 16
[    0.714449] pci 0000:00:04.0: setting latency timer to 64
[    0.714454] pci 0000:00:0f.0: setting latency timer to 64
[    0.714459] pci 0000:00:15.0: setting latency timer to 64
[    0.714462] bus: 00 index 0 io port: [0x00-0xffff]
[    0.714464] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.714466] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.714467] bus: 01 index 1 mmio: [0xd6000000-0xd9ffffff]
[    0.714469] bus: 01 index 2 mmio: [0xb0000000-0xbfffffff]
[    0.714470] bus: 01 index 3 mmio: [0x0-0x0]
[    0.714472] bus: 02 index 0 io port: [0x8000-0x8fff]
[    0.714474] bus: 02 index 1 mmio: [0xda000000-0xddffffff]
[    0.714475] bus: 02 index 2 mmio: [0xa0000000-0xafffffff]
[    0.714477] bus: 02 index 3 mmio: [0x0-0x0]
[    0.714478] bus: 03 index 0 mmio: [0x0-0x0]
[    0.714480] bus: 03 index 1 mmio: [0xcc000000-0xd3ffffff]
[    0.714481] bus: 03 index 2 mmio: [0x0-0x0]
[    0.714483] bus: 03 index 3 io port: [0x00-0xffff]
[    0.714484] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.714486] bus: 04 index 0 io port: [0x6000-0x7fff]
[    0.714488] bus: 04 index 1 mmio: [0xdfe00000-0xdfefffff]
[    0.714489] bus: 04 index 2 mmio: [0x0-0x0]
[    0.714490] bus: 04 index 3 mmio: [0x0-0x0]
[    0.714496] NET: Registered protocol family 2
[    0.728049] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.728231] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.728445] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.728564] TCP: Hash tables configured (established 131072 bind 65536)
[    0.728565] TCP reno registered
[    0.732066] NET: Registered protocol family 1
[    0.732161] checking if image is initramfs... it is
[    1.213924] Freeing initrd memory: 7380k freed
[    1.214216] cpufreq: No nForce2 chipset.
[    1.214310] audit: initializing netlink socket (disabled)
[    1.214322] type=2000 audit(1254153076.212:1): initialized
[    1.220337] highmem bounce pool size: 64 pages
[    1.220340] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.221447] VFS: Disk quotas dquot_6.5.1
[    1.221489] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.221971] fuse init (API version 7.10)
[    1.222033] msgmni has been set to 1685
[    1.222148] alg: No test for stdrng (krng)
[    1.222158] io scheduler noop registered
[    1.222160] io scheduler anticipatory registered
[    1.222161] io scheduler deadline registered
[    1.222171] io scheduler cfq registered (default)
[    1.222306] pci 0000:00:02.0: Disabling HT MSI mapping<6>pci 0000:00:04.0: Disabling HT MSI mapping<6>pci 0000:00:09.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0e.1: Disabling HT MSI mapping<6>pci 0000:00:0e.2: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:0f.1: Disabling HT MSI mapping<6>pci 0000:00:11.0: Disabling HT MSI mapping<6>pci 0000:00:12.0: Disabling HT MSI mapping<6>pci 0000:00:15.0: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
[    1.241860] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.241922] pcieport-driver 0000:00:02.0: found MSI capability
[    1.241954] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X
[    1.241968] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.242038] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.242099] pcieport-driver 0000:00:04.0: found MSI capability
[    1.242129] pcieport-driver 0000:00:04.0: irq 2302 for MSI/MSI-X
[    1.242142] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.242207] pcieport-driver 0000:00:15.0: setting latency timer to 64
[    1.242243] pcieport-driver 0000:00:15.0: found MSI capability
[    1.242261] pcieport-driver 0000:00:15.0: irq 2301 for MSI/MSI-X
[    1.242269] pci_express 0000:00:15.0:pcie00: allocate port service
[    1.242279] pci_express 0000:00:15.0:pcie03: allocate port service
[    1.242325] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.242332] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.242453] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.242455] ACPI: Power Button (FF) [PWRF]
[    1.242486] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.242488] ACPI: Power Button (CM) [PWRB]
[    1.242835] processor ACPI_CPU:00: registered as cooling_device0
[    1.242839] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.242886] processor ACPI_CPU:01: registered as cooling_device1
[    1.242913] processor ACPI_CPU:02: registered as cooling_device2
[    1.242941] processor ACPI_CPU:03: registered as cooling_device3
[    1.245542] isapnp: Scanning for PnP cards...
[    1.598281] isapnp: No Plug & Play device found
[    1.608206] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.608299] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.608627] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.609203] brd: module loaded
[    1.609441] loop: module loaded
[    1.609490] Fixed MDIO Bus: probed
[    1.609494] PPP generic driver version 2.4.2
[    1.609545] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.609565] Driver 'sd' needs updating - please use bus_type methods
[    1.609572] Driver 'sr' needs updating - please use bus_type methods
[    1.609608] ahci 0000:04:00.0: version 3.0
[    1.609864] ACPI: PCI Interrupt Link [AXV8] enabled at IRQ 16
[    1.609867] ahci 0000:04:00.0: PCI INT A -> Link[AXV8] -> GSI 16 (level, low) -> IRQ 16
[    1.624029] ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.624032] ahci 0000:04:00.0: flags: 64bit ncq led clo pmp pio 
[    1.624037] ahci 0000:04:00.0: setting latency timer to 64
[    1.624244] scsi0 : ahci
[    1.624376] scsi1 : ahci
[    1.624404] ata1: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe100 irq 16
[    1.624407] ata2: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe180 irq 16
[    1.944020] ata1: SATA link down (SStatus 0 SControl 300)
[    2.264019] ata2: SATA link down (SStatus 0 SControl 300)
[    2.264173] sata_nv 0000:00:0e.0: version 3.5
[    2.264418] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 21
[    2.264423] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21
[    2.264425] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.264625] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.264767] scsi2 : sata_nv
[    2.264861] scsi3 : sata_nv
[    2.264977] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[    2.264980] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[    3.144030] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.152822] ata3.00: ATA-7: WDC WD1500ADFS-00SLR5, 21.07QR5, max UDMA/133
[    3.152825] ata3.00: 293046768 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.168830] ata3.00: configured for UDMA/133
[    4.048030] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.056812] ata4.00: ATA-7: WDC WD1500ADFD-00NLR5, 21.07QR5, max UDMA/133
[    4.056815] ata4.00: 293046768 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.072840] ata4.00: configured for UDMA/133
[    4.072929] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1500ADFS-0 21.0 PQ: 0 ANSI: 5
[    4.072997] sd 2:0:0:0: [sda] 293046768 512-byte hardware sectors: (150 GB/139 GiB)
[    4.073009] sd 2:0:0:0: [sda] Write Protect is off
[    4.073011] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.073030] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.073073] sd 2:0:0:0: [sda] 293046768 512-byte hardware sectors: (150 GB/139 GiB)
[    4.073084] sd 2:0:0:0: [sda] Write Protect is off
[    4.073086] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.073104] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.073107]  sda: sda1
[    4.080785] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.080836] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    4.080888] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1500ADFD-0 21.0 PQ: 0 ANSI: 5
[    4.080948] sd 3:0:0:0: [sdb] 293046768 512-byte hardware sectors: (150 GB/139 GiB)
[    4.080959] sd 3:0:0:0: [sdb] Write Protect is off
[    4.080961] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.080980] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.081016] sd 3:0:0:0: [sdb] 293046768 512-byte hardware sectors: (150 GB/139 GiB)
[    4.081027] sd 3:0:0:0: [sdb] Write Protect is off
[    4.081029] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.081047] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.081050]  sdb: sdb1 sdb2 < sdb5 >
[    4.103026] sd 3:0:0:0: [sdb] Attached SCSI disk
[    4.103052] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    4.103306] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 20
[    4.103310] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20
[    4.103312] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    4.103338] sata_nv 0000:00:0e.1: setting latency timer to 64
[    4.103452] scsi4 : sata_nv
[    4.103556] scsi5 : sata_nv
[    4.103673] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[    4.103675] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[    4.980030] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.988138] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB03, max UDMA/100
[    5.005155] ata5.00: configured for UDMA/100
[    5.738356] ata6: SATA link down (SStatus 0 SControl 300)
[    5.738910] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB03 PQ: 0 ANSI: 5
[    5.743641] sr0: scsi3-mmc drive: 32x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.743644] Uniform CD-ROM driver Revision: 3.20
[    5.743720] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    5.743755] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    5.744018] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    5.744021] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    5.744023] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    5.744051] sata_nv 0000:00:0e.2: setting latency timer to 64
[    5.744157] scsi6 : sata_nv
[    5.744234] scsi7 : sata_nv
[    5.744359] ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    5.744361] ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    6.624030] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.632794] ata7.00: ATA-8: WDC WD1001FALS-00J7B0, 05.00K05, max UDMA/133
[    6.632796] ata7.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.640847] ata7.00: configured for UDMA/133
[    7.520030] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    7.528396] ata8.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
[    7.528398] ata8.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    7.544408] ata8.00: configured for UDMA/133
[    7.544481] scsi 6:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
[    7.544545] sd 6:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    7.544557] sd 6:0:0:0: [sdc] Write Protect is off
[    7.544558] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.544577] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.544614] sd 6:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    7.544625] sd 6:0:0:0: [sdc] Write Protect is off
[    7.544627] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.544646] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.544648]  sdc: sdc1 sdc2
[    7.556230] sd 6:0:0:0: [sdc] Attached SCSI disk
[    7.556258] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    7.556311] scsi 7:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
[    7.556373] sd 7:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    7.556384] sd 7:0:0:0: [sdd] Write Protect is off
[    7.556386] sd 7:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    7.556405] sd 7:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.556441] sd 7:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    7.556452] sd 7:0:0:0: [sdd] Write Protect is off
[    7.556454] sd 7:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    7.556473] sd 7:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.556475]  sdd: sdd1 sdd2
[    7.579348] sd 7:0:0:0: [sdd] Attached SCSI disk
[    7.579376] sd 7:0:0:0: Attached scsi generic sg4 type 0
[    7.579452] pata_amd 0000:00:0d.0: version 0.3.10
[    7.579477] pata_amd 0000:00:0d.0: setting latency timer to 64
[    7.579582] scsi8 : pata_amd
[    7.579675] scsi9 : pata_amd
[    7.580079] ata9: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    7.580082] ata10: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    7.746937] ata10: port disabled. ignoring.
[    7.747112] pata_jmicron 0000:04:00.1: enabling device (0000 -> 0001)
[    7.747118] pata_jmicron 0000:04:00.1: PCI INT B -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[    7.747143] pata_jmicron 0000:04:00.1: setting latency timer to 64
[    7.747208] scsi10 : pata_jmicron
[    7.747285] scsi11 : pata_jmicron
[    7.747319] ata11: PATA max UDMA/100 cmd 0x7c00 ctl 0x7800 bmdma 0x6c00 irq 16
[    7.747321] ata12: PATA max UDMA/100 cmd 0x7400 ctl 0x7000 bmdma 0x6c08 irq 16
[    8.067379] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    8.067635] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 23
[    8.067639] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 23 (level, low) -> IRQ 23
[    8.067647] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    8.067650] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    8.067690] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    8.067710] ehci_hcd 0000:00:0b.1: debug port 1
[    8.067714] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    8.067726] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xdfffe000
[    8.076010] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    8.076075] usb usb1: configuration #1 chosen from 1 choice
[    8.076105] hub 1-0:1.0: USB hub found
[    8.076110] hub 1-0:1.0: 10 ports detected
[    8.076190] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    8.076442] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 22
[    8.076446] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 22 (level, low) -> IRQ 22
[    8.076454] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    8.076456] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    8.076488] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    8.076505] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xdffff000
[    8.134035] usb usb2: configuration #1 chosen from 1 choice
[    8.134054] hub 2-0:1.0: USB hub found
[    8.134060] hub 2-0:1.0: 10 ports detected
[    8.134134] uhci_hcd: USB Universal Host Controller Interface driver
[    8.134195] PNP: No PS/2 controller found. Probing ports directly.
[    8.136995] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.137000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    8.144034] mice: PS/2 mouse device common for all mice
[    8.156075] rtc_cmos 00:05: RTC can wake from S4
[    8.156115] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    8.156148] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    8.156195] device-mapper: uevent: version 1.0.3
[    8.156303] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    8.156637] device-mapper: multipath: version 1.0.5 loaded
[    8.156639] device-mapper: multipath round-robin: version 1.0.0 loaded
[    8.156747] EISA: Probing bus 0 at eisa.0
[    8.156751] Cannot allocate resource for EISA slot 1
[    8.156762] Cannot allocate resource for EISA slot 6
[    8.156764] Cannot allocate resource for EISA slot 7
[    8.156766] Cannot allocate resource for EISA slot 8
[    8.156767] EISA: Detected 0 cards.
[    8.157043] cpuidle: using governor ladder
[    8.157044] cpuidle: using governor menu
[    8.157427] TCP cubic registered
[    8.157499] NET: Registered protocol family 10
[    8.157816] lo: Disabled Privacy Extensions
[    8.158062] NET: Registered protocol family 17
[    8.158073] Bluetooth: L2CAP ver 2.11
[    8.158075] Bluetooth: L2CAP socket layer initialized
[    8.158077] Bluetooth: SCO (Voice Link) ver 0.6
[    8.158078] Bluetooth: SCO socket layer initialized
[    8.158150] Bluetooth: RFCOMM socket layer initialized
[    8.158154] Bluetooth: RFCOMM TTY layer initialized
[    8.158155] Bluetooth: RFCOMM ver 1.10
[    8.158220] Using IPI No-Shortcut mode
[    8.158285] registered taskstats version 1
[    8.158425]   Magic number: 9:54:893
[    8.158495] rtc_cmos 00:05: setting system clock to 2009-09-28 15:51:24 UTC (1254153084)
[    8.158498] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    8.158499] EDD information not available.
[    8.158654] Freeing unused kernel memory: 532k freed
[    8.158763] Write protecting the kernel text: 4116k
[    8.158807] Write protecting the kernel read-only data: 1528k
[    8.334212] Floppy drive(s): fd0 is 1.44M
[    8.356249] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    8.356574] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[    8.356578] forcedeth 0000:00:11.0: PCI INT A -> Link[AMAC] -> GSI 23 (level, low) -> IRQ 23
[    8.356589] forcedeth 0000:00:11.0: setting latency timer to 64
[    8.356635] nv_probe: set workaround bit for reversed mac addr
[    8.356781] FDC 0 is a post-1991 82077
[    8.370246] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    8.370253] ohci1394 0000:03:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    8.419983] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[d3fff000-d3fff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    8.601517] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    8.733789] usb 1-3: configuration #1 chosen from 1 choice
[    8.737404] Initializing USB Mass Storage driver...
[    8.737597] scsi12 : SCSI emulation for USB Mass Storage devices
[    8.737759] usb-storage: device found at 4
[    8.737760] usb-storage: waiting for device to settle before scanning
[    8.737769] usbcore: registered new interface driver usb-storage
[    8.737772] USB Mass Storage support registered.
[    8.844019] usb 1-6: new high speed USB device using ehci_hcd and address 5
[    8.877902] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x50ef @ 0, addr 00:04:4b:16:ee:50
[    8.877906] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    8.878386] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[    8.878392] forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 22 (level, low) -> IRQ 22
[    8.878403] forcedeth 0000:00:12.0: setting latency timer to 64
[    8.878479] nv_probe: set workaround bit for reversed mac addr
[    8.977136] usb 1-6: configuration #1 chosen from 1 choice
[    8.977230] hub 1-6:1.0: USB hub found
[    8.977335] hub 1-6:1.0: 4 ports detected
[    9.392009] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    9.396686] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x50ef @ 1, addr 00:04:4b:16:ee:51
[    9.396689] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    9.413622] PM: Starting manual resume from disk
[    9.413625] PM: Resume from partition 8:21
[    9.413626] PM: Checking hibernation image.
[    9.413750] PM: Resume from disk failed.
[    9.435483] kjournald starting.  Commit interval 5 seconds
[    9.435490] EXT3-fs: mounted filesystem with ordered data mode.
[    9.605025] usb 2-1: configuration #1 chosen from 1 choice
[    9.607991] hub 2-1:1.0: USB hub found
[    9.610969] hub 2-1:1.0: 4 ports detected
[    9.760137] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[56a24ba600044b18]
[    9.932012] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   10.145004] usb 2-2: configuration #1 chosen from 1 choice
[   10.452011] usb 2-9: new full speed USB device using ohci_hcd and address 4
[   10.632009] usb 2-9: device descriptor read/64, error -71
[   10.916010] usb 2-9: device descriptor read/64, error -71
[   11.196009] usb 2-9: new full speed USB device using ohci_hcd and address 5
[   11.376010] usb 2-9: device descriptor read/64, error -71
[   11.660010] usb 2-9: device descriptor read/64, error -71
[   11.940010] usb 2-9: new full speed USB device using ohci_hcd and address 6
[   12.348008] usb 2-9: device not accepting address 6, error -71
[   12.524009] usb 2-9: new full speed USB device using ohci_hcd and address 7
[   12.932010] usb 2-9: device not accepting address 7, error -71
[   12.932021] hub 2-0:1.0: unable to enumerate USB device on port 9
[   13.009695] usb 1-6.2: new high speed USB device using ehci_hcd and address 7
[   13.063143] udev: starting version 141
[   13.113638] usb 1-6.2: configuration #1 chosen from 1 choice
[   13.114823] scsi13 : SCSI emulation for USB Mass Storage devices
[   13.115110] usb-storage: device found at 7
[   13.115111] usb-storage: waiting for device to settle before scanning
[   13.192690] usb 1-6.3: new full speed USB device using ehci_hcd and address 8
[   13.290640] usb 1-6.3: configuration #1 chosen from 1 choice
[   13.369831] usb 2-1.2: new low speed USB device using ohci_hcd and address 8
[   13.398624] Linux agpgart interface v0.103
[   13.481881] usb 2-1.2: configuration #1 chosen from 1 choice
[   13.512324] usbcore: registered new interface driver hiddev
[   13.512404] usbcore: registered new interface driver usbhid
[   13.512406] usbhid: v2.6:USB HID core driver
[   13.715516] nvidia: module license 'NVIDIA' taints kernel.
[   13.737186] usb-storage: device scan complete
[   13.738810] scsi 12:0:0:0: Direct-Access     HDT72252 5DLAT80          V44O PQ: 0 ANSI: 2
[   13.739917] sd 12:0:0:0: [sde] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   13.741671] sd 12:0:0:0: [sde] Write Protect is off
[   13.741674] sd 12:0:0:0: [sde] Mode Sense: 53 00 00 08
[   13.741676] sd 12:0:0:0: [sde] Assuming drive cache: write through
[   13.742687] sd 12:0:0:0: [sde] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   13.745672] sd 12:0:0:0: [sde] Write Protect is off
[   13.745674] sd 12:0:0:0: [sde] Mode Sense: 53 00 00 08
[   13.745676] sd 12:0:0:0: [sde] Assuming drive cache: write through
[   13.745679]  sde:<3>ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[   13.759426]  sde1
[   13.760276] sd 12:0:0:0: [sde] Attached SCSI disk
[   13.760370] sd 12:0:0:0: Attached scsi generic sg5 type 0
[   13.766081] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   13.814775] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
[   13.814807] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000
[   13.815827] lirc_dev: IR Remote Control driver registered, major 61 
[   13.828006] 
[   13.828009] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   13.828011] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   13.839356] input: GreenAsia Inc.    USB Joystick      as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input4
[   13.843223] Linux video capture interface: v2.00
[   13.845710] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[   13.865041] cx18:  Start initialization, version 1.0.1
[   13.865074] cx18-0: Initializing card #0
[   13.865075] cx18-0: Autodetected Hauppauge card
[   13.865450] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   13.865456] cx18 0000:03:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   13.865502] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   13.867262] cx18-0: cx23418 revision 01010000 (B)
[   13.906661] usb 1-6.3: reset full speed USB device using ehci_hcd and address 8
[   13.916155] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   13.916158] HDA Intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   13.916262] HDA Intel 0000:00:0f.1: setting latency timer to 64
[   13.967641] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[   13.967646] nvidia 0000:01:00.0: setting latency timer to 64
[   13.967757] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[   13.967762] nvidia 0000:02:00.0: PCI INT A -> Link[AXV6] -> GSI 16 (level, low) -> IRQ 16
[   13.967766] nvidia 0000:02:00.0: setting latency timer to 64
[   13.967898] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   13.999160] pantherlord 0003:0E8F:0003.0001: input,hidraw0: USB HID v1.10 Joystick [GreenAsia Inc.    USB Joystick     ] on usb-0000:00:0b.0-2/input0
[   13.999170] pantherlord 0003:0E8F:0003.0001: Force feedback for PantherLord/GreenAsia devices by Anssi Hannula <anssi.hannula@gmail.com>
[   14.001634] logitech 0003:046D:C517.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0b.0-1.2/input0
[   14.010807] logitech 0003:046D:C517.0003: fixing up Logitech keyboard report descriptor
[   14.011427] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input6
[   14.013529] lirc_dev: lirc_register_plugin: sample_rate: 0
[   14.014403] lirc_mceusb2[8]: Topseed eHome Infrared Transceiver on usb1:8
[   14.014484] usbcore: registered new interface driver lirc_mceusb2
[   14.017578] logitech 0003:046D:C517.0003: input,hiddev96,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-1.2/input1
[   14.084655] tveeprom 2-0050: Hauppauge model 74541, rev C6B6, serial# 3456990
[   14.084658] tveeprom 2-0050: MAC address is 00-0D-FE-34-BF-DE
[   14.084660] tveeprom 2-0050: tuner model is Philips FM1236 MK5 (idx 116, type 43)
[   14.084662] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   14.084663] tveeprom 2-0050: audio processor is CX23418 (idx 38)
[   14.084665] tveeprom 2-0050: decoder processor is CX23418 (idx 31)
[   14.084666] tveeprom 2-0050: has radio
[   14.084668] cx18-0: Autodetected Hauppauge HVR-1600
[   14.084669] cx18-0: VBI is not yet supported
[   14.189998] tuner 3-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   14.194972] tda9887 3-0043: creating new instance
[   14.194974] tda9887 3-0043: tda988[5/6/7] found
[   14.196211] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   14.196230] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   14.204127] tuner-simple 3-0061: creating new instance
[   14.204129] tuner-simple 3-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   14.206180] cx18-0: Disabled encoder IDX device
[   14.206223] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   14.206225] DVB: registering new adapter (cx18)
[   14.273068] MXL5005S: Attached at address 0x63
[   14.273070] DVB: registering adapter 0 frontend 134 (Samsung S5H1409 QAM/8VSB Frontend)...
[   14.273104] cx18-0: DVB Frontend registered
[   14.273121] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   14.273137] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   14.273152] cx18-0: Registered device radio0 for encoder radio
[   14.273154] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   14.273167] cx18:  End initialization
[   14.308008] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   18.112169] usb-storage: device scan complete
[   18.113651] scsi 13:0:0:0: Direct-Access     WD       2500BMV External 1.75 PQ: 0 ANSI: 4
[   18.115215] sd 13:0:0:0: [sdf] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   18.116508] sd 13:0:0:0: [sdf] Write Protect is off
[   18.116511] sd 13:0:0:0: [sdf] Mode Sense: 23 00 00 00
[   18.116513] sd 13:0:0:0: [sdf] Assuming drive cache: write through
[   18.117135] sd 13:0:0:0: [sdf] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   18.118507] sd 13:0:0:0: [sdf] Write Protect is off
[   18.118510] sd 13:0:0:0: [sdf] Mode Sense: 23 00 00 00
[   18.118512] sd 13:0:0:0: [sdf] Assuming drive cache: write through
[   18.118515]  sdf:<6>lp: driver loaded but no devices found
[   21.548303] Adding 5992204k swap on /dev/sdb5.  Priority:-1 extents:1 across:5992204k
[   21.926000]  sdf1
[   21.926110] sd 13:0:0:0: [sdf] Attached SCSI disk
[   21.926178] sd 13:0:0:0: Attached scsi generic sg6 type 0
[   22.077334] EXT3 FS on sdb1, internal journal
[   22.964879] type=1505 audit(1254153099.305:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2502
[   22.998786] type=1505 audit(1254153099.338:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2506
[   22.998853] type=1505 audit(1254153099.338:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2506
[   22.998884] type=1505 audit(1254153099.338:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2506
[   22.998914] type=1505 audit(1254153099.338:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2506
[   23.092484] type=1505 audit(1254153099.430:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2511
[   23.092606] type=1505 audit(1254153099.430:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2511
[   23.112492] type=1505 audit(1254153099.453:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2515
[   24.676029] cx18 0000:03:09.0: firmware: requesting v4l-cx23418-apu.fw
[   24.808490] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   25.304007] cx18 0000:03:09.0: firmware: requesting v4l-cx23418-cpu.fw
[   25.411685] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   25.418026] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   25.612015] cx18 0000:03:09.0: firmware: requesting v4l-cx23418-apu.fw
[   26.204006] cx18 0000:03:09.0: firmware: requesting v4l-cx23418-cpu.fw
[   26.508021] cx18 0000:03:09.0: firmware: requesting v4l-cx23418-dig.fw
[   26.693043] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   26.762232] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.762234] Bluetooth: BNEP filters: protocol multicast
[   26.769358] Bridge firewalling registered
[   27.643474] ppdev: user-space parallel port driver
[   31.660536] forcedeth 0000:00:12.0: irq 2300 for MSI/MSI-X
[   31.662602] forcedeth 0000:00:11.0: irq 2299 for MSI/MSI-X
[   31.662793] eth0: no link during initialization.
[   31.663202] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.224014] eth1: no IPv6 routers present
```

---

### Post by karlson on 2009-09-28
> **Wintaru said:**
> Ok, when I log in on the command line, I then typed "sudo bash" to get root, then typed "startx".

Obviously no copy and paste (typing this from my Mac), so forgive any typing errors as I recreate what I'm seeing:

```

(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation Support
       at http://wiki.x.org
  for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

  ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.

```

I'll check for that log file when I roll back the driver, but now I'm trying dmesg now, dumping its results to a log file and I'll post those after I roll the driver back.  One moment.

Don't do "sudo".

From the Console of your machine login as root.  Do CTRL+ALT+F1.  That should give you the first terminal if you are booting straight into X.  

Login as "root" from the command prompt and then run startx.

---

### Post by Wintaru on 2009-09-28
Same thing as before :(

---

### Post by YaKillaCJ on 2009-09-28
Im havin the EXACT same issues. Idk if its cause we both usin Dual Video cards but I seen some1 that had same problems on there labtop.

[IMG]http://i51.photobucket.com/albums/f392/YaBoiCJ/img_0669.jpg[/IMG]

---

### Post by Wintaru on 2009-09-28
I'm reaching the point where I'm going to try enabling with just one card in, then if that works install the other.  I'm prepping this rig to dual boot Ubuntu and Windows 7, as I'm getting a copy early since I'm hosting a house party and I've always wanted this computer to run Ubuntu as well.  I want to demo some games running in SLI so it's important that I can have both cards installed.  Will post back if it works.

---

### Post by Wintaru on 2009-09-28
It is definitely related to the dual cards, the driver works fine with one card, but as soon as I plug in the other it doesn't work anymore.

---

### Post by Wintaru on 2009-09-28
Well I managed to get it working, but I'm not sure how.  I'll try to carefully document my steps here and in the nvnews forums so if anyone else is looking they can try it too.

First, I started with a fresh install of Jaunty.  I don't remember all of the fiddling I had done and so I needed a clean slate.

After the install finished, I shut down the computer and took out one of the cards, leaving the "main" card in (I don't have anything plugged into the second card, it's for SLI only).

Then I started the machine, enabled the nVidia restricted driver using the Hardware Drivers interface built into Ubuntu.

Next I shut down the computer again, then installed the second card.  On boot I kept hitting ESC to catch Grub and started Ubuntu in recovery mode.

Once I got to the menu of options, I dropped into root, and first I tried to run this command:

```
nvidia-xconfig -a
```

This failed (again), I got the error:

```
WARNING: error opening libnvidia-cfg.so.1: libnvidia-cfg.so.1: cannot open 
shared object file: No such file or directory.


ERROR: Unable to determine number or location of GPUs in system; cannot honor 
'--separate-x-screens' option.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

I followed the instructions here: [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg586926.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg586926.html), and set up a symbolic link.  Note that you will have to change the path to fit the driver you are using.  So in the link, their command is this:

```
ln -s /usr/lib/nvidia/libnvidia-cfg.so.173.14.09 /usr/lib/libnvidia-cfg.so.1

```

Mine looks like this:

```
ln -s /usr/lib/nvidia/libnvidia-cfg.so.180.44 /usr/lib/libnvidia-cfg.so.1

```

Once I did that, I ran this again:

```
nvidia-xconfig -a
```

This time it works.  Now I tried these steps in the past, but the difference was I was not logged in as root, I was using sudo.  I don't know if that makes a difference or not, but I'm assuming it was either that or the fact I started with a fresh install of Ubuntu.

Now I have both cards in and its working perfectly.  Thanks to all for the tips and pointing me in the correct direction, hope this helps others.

---

