---
title: "Unity not working (PLEASE HELP)"
date: 2011-07-10
forum: Desktop Environments
---

### Post by TomCol on 2011-07-10
I have problems with unity.  It only shows a white menubar and a black sidebar.
I use Ubuntu 11.04 running in Parallels on iMac.  Classic gnome works with 3d effects.  Tested unity in terminal with a command and everything was green (yes).  But starting unity shows only white menubar and a black sidebar without icons and text.
What can I do?

---

### Post by wildmanne39 on 2011-07-10
> **TomCol said:**
> I have problems with unity.  It only shows a white menubar and a black sidebar.
I use Ubuntu 11.04 running in Parallels on iMac.  Classic gnome works with 3d effects.  Tested unity in terminal with a command and everything was green (yes).  But starting unity shows only white menubar and a black sidebar without icons and text.
What can I do?Hi, have a look at this link.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)
Also run these commands in a terminal
```
/usr/lib/nux/unity_support_test -p
```
```
lspci | grep VGA

```
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Please include a screenshot.

---

### Post by TomCol on 2011-07-11
tom@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Parallels and ATI Technologies Inc.
OpenGL renderer string: Parallels using ATI Radeon X1600 OpenGL Engine
OpenGL version string:  2.0 ATI-1.6.36

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

---

### Post by TomCol on 2011-07-11
tom@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Device 1ab8:4005

---

### Post by TomCol on 2011-07-11
```
tom@ubuntu:~$ sudo lshw
[sudo] password for tom: 
ubuntu                    
    description: Computer
    version: None
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal cpus=2 uuid=6EF18683-2C92-44E6-A337-62F0DCAAADF6
  *-core
       description: Motherboard
       product: Parallels Virtual Platform
       vendor: Parallels Software International Inc.
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Parallels Software International Inc.
          physical id: 0
          version: 6.0.12092.670880
          date: 10/26/2007
          size: 64KiB
          capabilities: isa pci pnp apm vesa cdboot int9keyboard int14serial int17printer int10video acpi
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: CPU Socket #0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 333MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss ht syscall nx x86-64 constant_tsc arch_perfmon aperfmperf pni ssse3 cx16 x2apic hypervisor lahf_lm dts
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM DRAM EDO 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM #0
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM EDO 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM #1
             size: 512MiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DRAM EDO 667 MHz (1.5 ns) [empty]
             physical id: 2
             slot: DIMM #2
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DRAM EDO 667 MHz (1.5 ns) [empty]
             physical id: 3
             slot: DIMM #3
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 2GHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G35 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress subtractive_decode bus_master cap_list
             resources: ioport:6000(size=8192) memory:e2000000-edffffff ioport:b0000000(size=805306368)
           *-display
                description: VGA compatible controller
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller rom
                configuration: driver=prl_tg latency=0
                resources: irq:21 ioport:6000(size=32) memory:b0000000-b3ffffff memory:e2000000-e200ffff
        *-generic
             description: Unassigned class
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=prl_tg latency=0
             resources: irq:22 ioport:8000(size=32)
        *-network
             description: Ethernet interface
             product: 82545EM Gigabit Ethernet Controller (Copper)
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: eth0
             version: 00
             serial: 00:1c:42:f0:73:1f
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=10.211.55.4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:23 memory:ee000000-ee01ffff ioport:8200(size=32)
        *-pci:1
             description: PCI bridge
             product: DECchip 21150
             vendor: Digital Equipment Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:9000(size=8192) memory:ee100000-ef0fffff memory:e0000000-e0ffffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b000(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:ef100000-ef1003ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:c000(size=8192) memory:ef200000-f01fffff ioport:e1000000(size=16777216)
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
             resources: memory:f0200000-f020000f memory:f0300000-f030000f
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e200(size=16)
        *-storage
             description: SATA controller
             product: 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: storage ahci_1.0 emulated
             configuration: driver=ahci latency=0
             resources: irq:16 ioport:e400(size=8) ioport:e600(size=4) ioport:e800(size=8) ioport:ea00(size=4) ioport:ec00(size=16) memory:f0400000-f0401fff
           *-disk
                description: ATA Disk
                product: Virtual  HDD [0]
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: FWR1
                serial: 01415926535897932384
                size: 64GiB (68GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0004fd12
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 5d14acd2-ae01-4b32-9f9a-dd6865e86cdb
                   size: 62GiB
                   capacity: 62GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-02 19:06:45 filesystem=ext4 lastmountpoint=/ modified=2011-07-10 17:38:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-07-11 10:20:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1534MiB
                   capacity: 1534MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1534MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD-RW  DVR-K06
                vendor: PIONEER
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: Q609
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:f000(size=256)

```

---

### Post by garvinrick4 on 2011-07-11
Have you reset unity
ctrl/alt/F2
```
 
unity --reset

```

---

### Post by garvinrick4 on 2011-07-11
Go to software center and install
ccsm
It is compiz management package:

---

### Post by TomCol on 2011-07-11
CCSM is installed
+ unity --reset is also done

No improvements.

[IMG]http://users.telenet.be/tom.collignon/unity.png[/IMG]

---

### Post by TomCol on 2011-07-11
I think it is a bug with ATI X1600

Bug #676814   

[https://bugs.launchpad.net/unity/+bug/676814](https://bugs.launchpad.net/unity/+bug/676814)

---

### Post by wildmanne39 on 2011-07-11
Hi, here is a link for ati driver issues.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
Hopefully this will help.

---

### Post by TomCol on 2011-07-12
Thanks for the replies.

But still no go with Unity.

Installed Unity 2D.  And it will have to do for now.
I tried the 3d version on my dad's laptop, at first it did not work (ATI), but then I installed the drivers from ATI and that did the trick.  I really like the new interface.

---

### Post by wildmanne39 on 2011-07-12
Hi, am glad you installed unity 2d, it looks like it is a bug with that card.

---

