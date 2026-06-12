---
title: "Frequently slow interface on Ubuntu 12.10, 12.04, . ."
date: 2014-01-13
forum: Desktop Environments
---

### Post by msinfo on 2014-01-13
Hi,
About my system : 
Dual boot Window7/Ubuntu
RAM : 1 GB
CPU : Intel® Pentium(R) 4 CPU 3.20GHz × 2 
OS type: 32 bit
Disk : 50 GB
Driver : VESA: Intel(r)915G/915GV/910GL Graphics
Experience : Standard

I have been using on this machine since, version 8.04 LTS. But from, 10.04, I have been having problem of slow interface, which happens, most of times, whenever I install updates. But not all update makes interface slow. So sometimes, I enjoy Ubuntu with fast navigation. 

Unity, GNOME, Unity 2D, all suffer from this problem. I also tried various kernel versions, but no change.

Slow interface : A[COLOR=#000000]pp laoding speeds, maximise minimise and everything else is sluggish and feels unresponsive.[/COLOR]

Can some one give me idea, how to diagnose this issue, and resolve it, because it has been pestering since long time.

]This is result of top command (when chrome, gedit, and one terminal was open, but still interface/gui navigation was slow) :
```

top - 05:05:36 up 19 min,  2 users,  load average: 3.25, 2.72, 1.86
Tasks: 162 total,   1 running, 161 sleeping,   0 stopped,   0 zombie
%Cpu(s): 47.6 us,  5.5 sy,  0.2 ni, 24.2 id, 22.5 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   1018804 total,   942812 used,    75992 free,    10404 buffers
KiB Swap:  1951740 total,     2612 used,  1949128 free,   364448 cached


  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 2162 someone   20   0  407m 175m  31m S  81.9 17.6  14:07.98 compiz            
 1592 root      20   0  104m  49m 7348 S  18.9  5.0   1:58.85 Xorg              
 3082 someone   20   0 95752  15m  10m S   6.3  1.5   0:02.26 gnome-terminal    
 3156 someone   20   0  5204 1276  980 R   6.3  0.1   0:00.01 top               
    1 root      20   0  3624 1892 1240 S   0.0  0.2   0:00.99 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.16 ksoftirqd/0       
    5 root      20   0     0    0    0 S   0.0  0.0   0:00.53 kworker/u:0       
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.01 migration/0       
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/0        
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/1       
    9 root      20   0     0    0    0 S   0.0  0.0   0:00.10 kworker/1:0       
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.15 ksoftirqd/1       
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/1        
   12 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 cpuset            
   13 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 khelper           
   14 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kdevtmpfs 

```

---

### Post by varunendra on 2014-01-14
Sluggishness problems are almost always caused due to improper drivers, most often the display driver. And this doesn't look good to me -
> **msinfo said:**
> 
Driver : **[COLOR="#FF0000"]VESA[/COLOR]**: Intel(r)915G/915GV/910GL Graphics
How did you get the above output?

For Intel 915 series graphics, I believe the correct driver is i915 which is part of the Linux kernel. So why are you using the Vesa driver (if I am interpreting the output correctly)?

If you are indeed using the vesa driver, I'm sure that is what is causing the sluggishness. The rest of your hardware is although old, yet sufficient enough to give decent performance with Ubuntu (assuming the CPU is a dual core, or hyper-threading enabled).

The CPU usage by compiz, as shown in your above outputs, is insane (about 82%). But I think it should go down once the proper driver is loaded. Otherwise you may have to consider lighter variants of Ubuntu.

Also, you may get better help if you could post a detailed report of your hardware, which means the output of -
```
sudo lshw -numeric -sanitize
```

---

### Post by msinfo on 2014-01-16
> **varunendra said:**
> 
How did you get the above output?

I got output by clicking right most icon on task bar > About this computer.

> **varunendra said:**
> 
So why are you using the Vesa driver (if I am interpreting the output correctly)?

I don't know how one configure, this drivers. I am using defaults. But still, some days, it works just fine.

> **varunendra said:**
> 
If you are indeed using the vesa driver, I'm sure that is what is causing the sluggishness. 

How do we check that? And how should I switch, to another one?

> **varunendra said:**
> 
The CPU usage by compiz, as shown in your above outputs, is insane (about 82%). But I think it should go down once the proper driver is loaded. Otherwise you may have to consider lighter variants of Ubuntu.

I started, checking on it, during initial start up of Ubuntu, indeed it goes up to 80-90%, but gradually moves between, 40-60%. Is it normal? Is compiz very essential component? What I understand, from reading Wikipedia, it is just related to effects. So is it possible to remove it completely, or install some other alternative?

> **varunendra said:**
> 
Also, you may get better help if you could post a detailed report of your hardware, which means the output of -
```
sudo lshw -numeric -sanitize
```

```

computer
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 8I915ME
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F5
          date: 01/03/2006
          size: 128KiB
          capacity: 320KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: [REMOVED]
          slot: Socket 775
          size: 3200MHz
          capacity: 4GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
        *-bank:1
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: [REMOVED]
             slot: A2
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: [REMOVED]
             slot: A3
     *-cpu:1
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@1
          version: 15.4.1
          serial: [REMOVED]
          size: 3200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580]
          vendor: Intel Corporation [8086]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0e
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller [8086:2582]
             vendor: Intel Corporation [8086]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:f0100000-f017ffff ioport:c000(size=8) memory:e0000000-efffffff memory:f0180000-f01bffff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge [8086:244E]
             vendor: Intel Corporation [8086]
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:a000(size=4096) memory:f0000000-f00fffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+ [10EC:8139]
                vendor: Realtek Semiconductor Co., Ltd. [10EC]
                physical id: 5
                bus info: pci@0000:01:05.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:21 ioport:a000(size=256) memory:f0000000-f00001ff
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266E]
             vendor: Intel Corporation [8086]
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: ioport:c400(size=256) ioport:c800(size=64) memory:f01c1000-f01c11ff memory:f01c2000-f01c20ff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640]
             vendor: Intel Corporation [8086]
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651]
             vendor: Intel Corporation [8086]
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266A]
             vendor: Intel Corporation [8086]
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3500418AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC46
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=20d43eee
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-12-10 05:12:32 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 93GiB
                capacity: 93GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-12-10 05:12:38 filesystem=ntfs state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: [REMOVED]
                size: 217GiB
                capacity: 218GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-12-09 15:21:45 filesystem=ntfs label=New Volume state=clean
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 154GiB
                capacity: 154GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 245MiB
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 1906MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 105GiB
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   logical name: /
                   capacity: 46GiB
                   configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=remount-ro state=mounted       

```

---

### Post by mörgæs on 2014-01-16
A fresh install of X/Lubuntu 13.10 is a better option than Ubuntu.

---

### Post by msinfo on 2014-01-21
What I end up doing is :
Installed gnome fallback session, and it's working fine. But don't know whether this thing, give rise to problem of missing sound card from audio devices.
Currently enjoying fast navigation and interface, but without sound.

Thanks for your thoughts.

---

### Post by msinfo on 2014-01-21
I heard from my other peers too. They said, "indeed, Lubuntu, is good for my kind of machine. Will try it soon.

---

