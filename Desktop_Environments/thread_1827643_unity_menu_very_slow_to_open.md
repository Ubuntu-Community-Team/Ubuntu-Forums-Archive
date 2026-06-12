---
title: "unity menu very slow to open"
date: 2011-08-18
forum: Desktop Environments
---

### Post by kandros on 2011-08-18
hello im using ubuntu 11.04 on a pretty old but not that bad pc, the problems i have is that when i click on the top left corner in unity to open the menu il takes a lot tof time to open like 5 o 6 seconds, this is really a lot even for a old computer because cpu and ram load is always quite low. any suggestion? at also takes about 5 sec to open home folder, everything else is fine 


unity is 2D version



```
kandros@kandros-ubuntu:~$ top

top - 11:56:33 up 4 min,  2 users,  load average: 0.34, 0.49, 0.24
Tasks: 123 total,   1 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.6%us,  2.7%sy,  0.0%ni, 83.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1542832k total,   536128k used,  1006704k free,    45992k buffers
Swap:  1562620k total,        0k used,  1562620k free,   212496k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  877 root      20   0  200m  45m 8344 S  7.6  3.1   0:19.88 Xorg               
 1118 kandros   20   0  130m  29m  21m S  5.3  1.9   0:02.48 unity-2d-panel     
 1294 kandros   20   0  310m  54m  32m S  1.7  3.6   0:12.23 chromium-browse    
 1083 kandros   20   0  4528 1892  664 S  0.7  0.1   0:01.66 dbus-daemon        
  145 root      20   0     0    0    0 S  0.3  0.0   0:00.09 kworker/0:2        
 1160 kandros   20   0 63108 9460 6572 S  0.3  0.6   0:00.66 bamfdaemon         
 1418 kandros   20   0 92640  14m  10m S  0.3  1.0   0:02.17 gnome-terminal     
 1477 kandros   20   0  2628 1104  840 R  0.3  0.1   0:00.50 top                
 1478 kandros   20   0  162m  64m  20m S  0.3  4.2   0:13.44 chromium-browse    
    1 root      20   0  3044 1768 1212 S  0.0  0.1   0:00.71 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kworker/0:0        
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.48 kworker/u:0        
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset             

```
```
         kandros@kandros-ubuntu:~$ top

top - 11:57:52 up 5 min,  2 users,  load average: 0.65, 0.53, 0.27
Tasks: 122 total,   1 running, 121 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6%us,  2.6%sy,  0.0%ni, 89.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1542832k total,   563912k used,   978920k free,    46252k buffers
Swap:  1562620k total,        0k used,  1562620k free,   215796k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  877 root      20   0  204m  45m 7680 S  4.3  3.0   0:26.21 Xorg               
 1111 kandros   20   0 73892  12m 9408 S  2.0  0.8   0:00.91 metacity           
 1418 kandros   20   0 92640  14m  10m S  2.0  1.0   0:02.47 gnome-terminal     
 1122 kandros   20   0  246m  48m  24m S  1.0  3.2   0:04.01 unity-2d-launch    
 1294 kandros   20   0  311m  57m  33m S  1.0  3.8   0:17.86 chromium-browse    
 1083 kandros   20   0  4528 1892  664 S  0.3  0.1   0:02.16 dbus-daemon        
 1100 kandros   20   0 98.1m  11m 8608 S  0.3  0.8   0:00.64 gnome-settings-    
 1118 kandros   20   0  130m  29m  21m S  0.3  1.9   0:03.28 unity-2d-panel     
 1484 kandros   20   0  156m  54m  18m S  0.3  3.6   0:03.90 chromium-browse    
    1 root      20   0  3044 1768 1212 S  0.0  0.1   0:00.71 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.48 kworker/u:0        
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper            
kandros@kandros-ubuntu:~$ sudo lshw
[sudo] password for kandros: 
kandros-ubuntu            
    description: Desktop Computer
    version: P671000406
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=A034037A-A6BB-D611-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-6367
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG
          date: 05/28/2002
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2000+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: Socket 7
          size: 1666MHz
          capacity: 2GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1536MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
     *-pci
          description: Host bridge
          product: nForce CPU bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b2
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia
          resources: irq:0 memory:a0000000-bfffffff
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce 220/420 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce 220/420 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: b2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce 420 Memory Controller (DDR)
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: b2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: c3
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce PCI System Management
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=amd756_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:5030(size=16) ioport:5020(size=16) ioport:5000(size=32)
        *-usb:0
             description: USB Controller
             product: nForce USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: c3
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:11 memory:ca003000-ca003fff
        *-usb:1
             description: USB Controller
             product: nForce USB Controller
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: c3
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:3 memory:ca004000-ca004fff
        *-network
             description: Ethernet interface
             product: nForce Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: c2
             serial: 00:10:dc:63:82:a2
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.33.130.71 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
             resources: irq:11 memory:ca000000-ca0003ff ioport:e400(size=8)
        *-multimedia
             description: Multimedia audio controller
             product: nForce AC'97 Audio Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: c2
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
             resources: irq:3 ioport:d000(size=256) ioport:d400(size=128) memory:ca001000-ca001fff
        *-communication UNCLAIMED
             description: Modem
             product: nForce AC'97 Modem Controller
             vendor: nVidia Corporation
             physical id: 6.1
             bus info: pci@0000:00:06.1
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pm generic cap_list
             configuration: latency=0 maxlatency=5 mingnt=2
             resources: ioport:d800(size=256) ioport:dc00(size=128) memory:ca002000-ca002fff
        *-pci:0
             description: PCI bridge
             product: nForce PCI-to-PCI bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: c2
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master
        *-ide
             description: IDE interface
             product: nForce IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi0
             logical name: scsi1
             version: c3
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e000(size=16)
           *-disk
                description: ATA Disk
                product: ST340810A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.93
                serial: 5FB89CTB
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008f997
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: cecab75a-ee43-449b-9234-ffa7f3909e13
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-08-17 14:20:52 filesystem=ext4 lastmountpoint=/ modified=2011-08-18 10:54:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-08-18 11:52:35 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 927f256e-351e-4a88-8d14-f8a0bc460dbb
                   size: 1526MiB
                   capacity: 1526MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: 34621e08-397c-4e6b-9214-ea8ce36e41b4
                   size: 15GiB
                   capacity: 15GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-08-12 02:11:31 filesystem=ext4 lastmountpoint=/ modified=2011-08-18 01:24:42 mounted=2011-08-18 11:10:17 state=clean
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-616F
                vendor: SAMSUNG
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: F101
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-pci:1
             description: PCI bridge
             product: nForce AGP to PCI Bridge
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:c8000000-c9ffffff memory:c0000000-c7ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon RV200 QW [Radeon 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:c0000000-c7ffffff ioport:c000(size=256) memory:c9000000-c900ffff memory:c8000000-c801ffff
     *-scsi
          physical id: 1
          bus info: usb@1:4
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
kandros@kandros-ubuntu:~$ 
    

```

---

### Post by kandros on 2011-08-19
up

---

### Post by kandros on 2011-08-21
up

---

