---
title: "Replaced CD Bruners w/ new SATA Burners and now Gnome is confused"
date: 2007-08-19
forum: Desktop Environments
---

### Post by jeepfreak2002 on 2007-08-19
I'm running Feisty.

I just replaced my 2 IDE CD Burners with 2 SATA CD/DVD Burners.

Problem is that in the "Computer" section it shows 2 "CD-Roms" and now only 1 DVD/CD Burner. If I stick a disk into both DVD Burner Drives, they will both mount and work, but it bothers me that the OS/GUI is not updating to display the correct drives.

How can I get the OS/GUI to display the 2 SATA DVD burners and remove the 2 old CD ROM Drives from the "Computer" section under "Places"?

---

### Post by Happy_Man on 2007-08-19
Delete their entries from /etc/fstab. If you don't know how, post the file here and one of us will help you.

---

### Post by jeepfreak2002 on 2007-08-19
FYI:  I have my hard drive plugged into SATA port #1 on the MOBO and the 2 SATA DVD Burners are on #4 and #5
Here ya go:



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=64b05d3d-c324-48b0-a572-251881c15ece /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6ba92431-7469-4993-9ea8-9ffc71b1f2d5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Happy_Man on 2007-08-19
Hmmm.... well, that's OK. Have you tried in Gconf editor? ```
gconf-editor
``` Go under apps/nautilus/desktop and see if the problem is there.

---

### Post by neaeo on 2007-08-20
nautilus shows icons on the desktop for the devices that are mounted  in /dev/media

So, you should change:
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0

into:
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdc1 /media/cdrom1 udf,iso9660 user,noauto 0 0

Don't forget to make a backup of your /etc/fstab in case something goes wrong!!

---

### Post by jeepfreak2002 on 2007-09-28
Actually, there is a bit of an update...

I have 2 SATA Hard Drives installed on the MOBO for dual Booting.

SATA 1 = Ubuntu
SATA 2 = Windows XP

SATA 4 = DVD Burner
SATA 5 = DVD Burner

Now from examining this fstab file I can understand why it would only see 1 HD, as the other is NTFS (right??), so the DVD burners default to the next available serial device (sdx1, right??)  so...  since they were previously IDE (hdx, Right??)  I just change them to the next serial device (sdx1, right???)  I'm trying, here!!!

Is there just a way to have the OS re-scan for hardware changes??  Can you just nuke it and let it re-find everything??  Just wondering. 

this is my current fstab file that I am referring to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=64b05d3d-c324-48b0-a572-251881c15ece /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6ba92431-7469-4993-9ea8-9ffc71b1f2d5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by dcstar on 2007-09-29
> **jeepfreak2002 said:**
> 
........
Is there just a way to have the OS re-scan for hardware changes??  Can you just nuke it and let it re-find everything??  Just wondering. 
........

```
lshw
``` will show you the detected hardware and the new designations, you can use these to manually modify your /etc/fstab file.

---

### Post by jeepfreak2002 on 2007-09-29
Well here is the output for that command:

adam@adam-desktop:~$ lshw
WARNING: you should run this program as super-user.
adam-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 2026MB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 7
          bus info: cpu@0
          version: 15.3.3
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-isa UNCLAIMED
          description: ISA bridge
          product: MCP55 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
     *-serial UNCLAIMED
          description: SMBus
          product: MCP55 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          resources: ioport:fc00-fc3f ioport:1c00-1c3f ioport:1c40-1c7f irq:255
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-usb:0
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:fe02f000-fe02ffff irq:66
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.17-12-generic ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=10 speed=12.0MB/s
           *-usb:0
                description: Printer
                product: Samsung ML-2010
                vendor: Samsung
                physical id: 2
                bus info: usb@1:2
                version: 1.00
                serial: 3A61BKBL608387L.
                capabilities: usb-1.10 bidirectional
                configuration: driver=usblp maxpower=0mA speed=12.0MB/s
           *-usb:1
                description: Mouse
                product: Microsoft 3-Button Mouse with IntelliEye(TM)
                vendor: Microsoft
                physical id: 3
                bus info: usb@1:3
                version: 3.00
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
           *-usb:2
                description: Keyboard
                product: Dell USB Keyboard
                vendor: Dell
                physical id: 4
                bus info: usb@1:4
                version: 3.01
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=70mA speed=1.5MB/s
     *-usb:1
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd
          resources: iomemory:fe02e000-fe02e0ff irq:233
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.17-12-generic ehci_hcd
             physical id: 1
             bus info: usb@3
             logical name: usb3
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s
     *-ide:0
          description: IDE interface
          product: MCP55 IDE
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE
          resources: ioport:f000-f00f
     *-ide:1
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv
          resources: ioport:9f0-9f7 ioport:bf0-bf3 ioport:970-977 ioport:b70-b73 ioport:dc00-dc0f iomemory:fe02d000-fe02dfff irq:233
     *-ide:2
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5.1
          bus info: pci@00:05.1
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv
          resources: ioport:9e0-9e7 ioport:be0-be3 ioport:960-967 ioport:b60-b63 ioport:c800-c80f iomemory:fe02c000-fe02cfff irq:50
     *-ide:3
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5.2
          bus info: pci@00:05.2
          logical name: scsi4
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv
          resources: ioport:c400-c407 ioport:c000-c003 ioport:bc00-bc07 ioport:b800-b803 ioport:b400-b40f iomemory:fe02b000-fe02bfff irq:58
     *-pci:0
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-usb:0
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 7
             bus info: pci@01:07.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:fdeff000-fdefffff irq:74
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-12-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 7.1
             bus info: pci@01:07.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:fdefe000-fdefefff irq:82
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-12-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 7.2
             bus info: pci@01:07.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:fdefd000-fdefd0ff irq:90
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-12-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=5 speed=480.0MB/s
     *-multimedia
          description: Audio device
          product: MCP55 High Definition Audio
          vendor: nVidia Corporation
          physical id: 6.1
          bus info: pci@00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel
          resources: iomemory:fe024000-fe027fff irq:58
     *-bridge
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: eth0
          version: a2
          serial: 00:1a:92:7c:19:46
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth ip=192.168.0.14 multicast=yes
          resources: iomemory:fe02a000-fe02afff ioport:b000-b007 iomemory:fe029000-fe0290ff iomemory:fe028000-fe02800f irq:50
     *-pci:1
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:5
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:6
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@07:00.0
             version: a1
             size: 256MB
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=nvidia
             resources: iomemory:fa000000-faffffff iomemory:e0000000-efffffff iomemory:fb000000-fbffffff ioport:ac00-ac7f irq:122
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by jeepfreak2002 on 2007-09-29
OK:

So I changed the fstab to read:

/dev/[COLOR="Lime"]sdb1[/COLOR] /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/[COLOR="Lime"]sdc1[/COLOR] /media/cdrom1 udf,iso9660 user,noauto 0 0

That appears to slightly corrected the issue.  Now instead of 2 "CD-ROM's" I now have 1 CD-ROM and 1 CD-RW/DVD+-RW Drive  - that is better... but not correct..  I believe that some answer lies in the /dev directory.

K3B is all confused, and sees 2 drives but it is calling them:

/dev/scd1 and /dev/scd0,   Not sdb1 and sdc1 ...  

it is looking in the /dev/ directory and finding this info.  Do in need to get into that directory and correct some info?

---

### Post by dcstar on 2007-09-29
> **jeepfreak2002 said:**
> Well here is the output for that command:

adam@adam-desktop:~$ lshw
**WARNING: you should run this program as super-user.**
adam-desktop              
    description: Computer
........

My output shows much more - including all the /dev/ stuff for my drives, try:

```
sudo lshw
```

---

### Post by jeepfreak2002 on 2007-09-29
Here it is under sudo - I will review right now.  Remember - I went from IDE to SATA    

 *-memory:0
          description: System Memory
          physical id: 3c
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: DIMM_B1
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.25ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: DIMM_B2
             width: 64 bits
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: DIMM_A1
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.25ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: DIMM_A2
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.1515ns)
          capabilities: bus_master cap_list
     *-isa UNCLAIMED
          description: ISA bridge
          product: MCP55 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
     *-serial UNCLAIMED
          description: SMBus
          product: MCP55 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          resources: ioport:fc00-fc3f ioport:1c00-1c3f ioport:1c40-1c7f irq:255
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.1515ns)
     *-usb:0
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd
          resources: iomemory:fe02f000-fe02ffff irq:66
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.17-12-generic ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=10 speed=12.0MB/s
           *-usb:0
                description: Printer
                product: Samsung ML-2010
                vendor: Samsung
                physical id: 2
                bus info: usb@1:2
                version: 1.00
                serial: 3A61BKBL608387L.
                capabilities: usb-1.10 bidirectional
                configuration: driver=usblp maxpower=0mA speed=12.0MB/s
           *-usb:1
                description: Mouse
                product: Microsoft 3-Button Mouse with IntelliEye(TM)
                vendor: Microsoft
                physical id: 3
                bus info: usb@1:3
                version: 3.00
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
           *-usb:2
                description: Keyboard
                product: Dell USB Keyboard
                vendor: Dell
                physical id: 4
                bus info: usb@1:4
                version: 3.01
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=70mA speed=1.5MB/s
     *-usb:1
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd
          resources: iomemory:fe02e000-fe02e0ff irq:233
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.17-12-generic ehci_hcd
             physical id: 1
             bus info: usb@3
             logical name: usb3
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s
     *-ide:0
          description: IDE interface
          product: MCP55 IDE
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE
          resources: ioport:f000-f00f
     *-ide:1
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated scsi-host
          configuration: driver=sata_nv
          resources: ioport:9f0-9f7 ioport:bf0-bf3 ioport:970-977 ioport:b70-b73 ioport:dc00-dc0f iomemory:fe02d000-fe02dfff irq:233
        *-disk:0
             description: SCSI Disk
             product: ST3500630NS
             vendor: ATA
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AE
             serial: 5QG1ERE2
             size: 465GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                capacity: 459GB
                capabilities: primary bootable
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                capacity: 5930MB
                capabilities: extended partitioned partitioned:extended
        *-disk:1
             description: SCSI Disk
             product: ST3160827AS
             vendor: ATA
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 3.42
             serial: 4MT059LD
             size: 149GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: HPFS/NTFS partition
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                capacity: 48GB
                capabilities: primary bootable
           *-volume:1
                description: W95 Ext'd (LBA) partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                capacity: 100GB
                capabilities: primary
     *-ide:2
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5.1
          bus info: pci@00:05.1
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv
          resources: ioport:9e0-9e7 ioport:be0-be3 ioport:960-967 ioport:b60-b63 ioport:c800-c80f iomemory:fe02c000-fe02cfff irq:50
     *-ide:3
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5.2
          bus info: pci@00:05.2
          logical name: scsi4
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated scsi-host
          configuration: driver=sata_nv
          resources: ioport:c400-c407 ioport:c000-c003 ioport:bc00-bc07 ioport:b800-b803 ioport:b400-b40f iomemory:fe02b000-fe02bfff irq:58
        *-cdrom:0 UNCLAIMED
             description: SCSI CD-ROM
             product: DVDRW LH-20A1S
             vendor: LITE-ON
             physical id: 0
             bus info: scsi@4:0.0.0
             version: 9L07
             capabilities: removable
             configuration: ansiversion=5
        *-cdrom:1 UNCLAIMED
             description: SCSI CD-ROM
             product: DVDRW LH-20A1S
             vendor: LITE-ON
             physical id: 1
             bus info: scsi@5:0.0.0
             version: 9L07
             capabilities: removable
             configuration: ansiversion=5
     *-pci:0
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-usb:0
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 7
             bus info: pci@01:07.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:fdeff000-fdefffff irq:74
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-12-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 7.1
             bus info: pci@01:07.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:fdefe000-fdefefff irq:82
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-12-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 7.2
             bus info: pci@01:07.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:fdefd000-fdefd0ff irq:90
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-12-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=5 speed=480.0MB/s
     *-multimedia
          description: Audio device
          product: MCP55 High Definition Audio
          vendor: nVidia Corporation
          physical id: 6.1
          bus info: pci@00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel
          resources: iomemory:fe024000-fe027fff irq:58
     *-bridge
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: eth0
          version: a2
          serial: 00:1a:92:7c:19:46
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
          configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.54 duplex=full ip=192.168.0.14 link=yes multicast=yes port=MII speed=100MB/s
          resources: iomemory:fe02a000-fe02afff ioport:b000-b007 iomemory:fe029000-fe0290ff iomemory:fe028000-fe02800f irq:50
     *-pci:1
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:5
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:6
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@07:00.0
             version: a1
             size: 256MB
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=nvidia
             resources: iomemory:fa000000-faffffff iomemory:e0000000-efffffff iomemory:fb000000-fbffffff ioport:ac00-ac7f irq:122
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by jeepfreak2002 on 2007-09-30
any other ideas?

---

### Post by jeepfreak2002 on 2007-10-02
What if I unplug both drives, reboot. Shut down, and plug only 1 in, reboot, plug the other one in???

Would unplugging both erase the record incorrectly created by swapping the IDE drives out with the SATA Burners?

---

