---
title: "Install problem with dual monitors"
date: 2012-09-06
forum: Desktop Environments
---

### Post by chris954 on 2012-09-06
Installed Ubuntu 12.04 yesterday seemed to install pretty well no problems at all.
Did the usual upgrades restarted my computer.
Played around with my Display settings to get both my 21" AOC Screens working. 
Installed the upgrade to my Nvidia card and rebooted.
Everything was great.

Shut down my PC overnight and today whoa no dual monitor.

Checked my Display settings and it is showing that I LAPTOP not Desktop, and only showing 1 monitor which is Laptop.

How can I get my setup right ?

Results of xrandr:xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0     51.0* 
   1680x1050      52.0     53.0  
   1440x900       54.0  
   1400x1050      55.0     56.0  
   1360x768       57.0     58.0  
   1280x1024      59.0     60.0  
   1280x960       61.0  
   1152x864       62.0     63.0     64.0     65.0  
   1024x768       66.0     67.0     68.0  
   960x600        69.0  
   960x540        70.0  
   840x525        71.0     72.0     73.0  
   832x624        74.0  
   800x600        75.0     76.0     77.0     78.0  
   720x450        79.0  
   700x525        80.0  
   680x384        81.0     82.0  
   640x480        83.0     84.0     85.0     86.0     87.0  
   512x384        88.0     89.0  
   400x300        90.0  
   320x240        91.0     92.0  

Thank you in advance
Chris

---

### Post by lordievader on 2012-09-06
In the nVidia control panel you can not enable the external monitor? Or in Ubuntu's own display manager?
Also could you give a bit more information about your setup? I understand you are running a laptop with an nVidia card that combined with an external screen, correct? What nVidia card do you have? And what driver is installed?

---

### Post by chris954 on 2012-09-06
> **lordievader said:**
> In the nVidia control panel you can not enable the external monitor? Or in Ubuntu's own display manager?
Also could you give a bit more information about your setup? I understand you are running a laptop with an nVidia card that combined with an external screen, correct? What nVidia card do you have? And what driver is installed?

No I am running a desktop with 2 monitors.
PC details from using lshw

   description: Desktop Computer
    product: P67A-UD3-B3 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-AA0004000A04
  *-core
       description: Motherboard
       product: P67A-UD3-B3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2
          date: 02/22/2011
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600 CPU
          slot: Socket 1155
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 8MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 1
             slot: A1
             size: 4GiB
             width: 2244 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
        *-bank:3
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 3
             slot: A3
             size: 4GiB
             width: 2244 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f6000000-f9ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GF114 [GeForce GTX 560]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f6000000-f7ffffff memory:e0000000-e7ffffff memory:ec000000-efffffff ioport:ef00(size=128) memory:e8000000-e807ffff
           *-multimedia
                description: Audio device
                product: GF110 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f9ffc000-f9ffffff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:51 memory:fbfff000-fbfff00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fbffe000-fbffe3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:52 memory:fbff4000-fbff7fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:f4000000-f41fffff ioport:f4200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:fbd00000-fbdfffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:fbdfe000-fbdfffff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:d000(size=4096) ioport:fbe00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 06
                serial: aa:00:04:00:0a:04
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.131 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:50 ioport:de00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096)
           *-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
                resources: ioport:c000(size=4096)
              *-communication UNCLAIMED
                   description: Communication controller
                   product: Lucent V.92 Data/Fax Modem
                   vendor: LSI Corporation
                   physical id: 0
                   bus info: pci@0000:06:00.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: latency=32
                   resources: ioport:ce00(size=256)
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fbffd000-fbffd3ff
        *-isa
             description: ISA bridge
             product: P67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801 SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi3
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=32) memory:fbffc000-fbffc7ff
           *-disk:0
                description: ATA Disk
                product: ST31000524AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: JC45
                serial: 5VP93PSS
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001b51a
              *-volume:0
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: acc0ab5b-e9e4-4966-96fa-e5c030ffdcb2
                   size: 243MiB
                   capacity: 243MiB
                   capabilities: primary bootable ext2 initialized
                   configuration: filesystem=ext2 modified=2012-09-06 17:49:27 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux LVM Physical Volume partition
                      physical id: 5
                      logical name: /dev/sda5
                      serial: zNIe0P-UcNV-m8Me-5o16-moa9-YJ8R-hwUBQo
                      size: 931GiB
                      capacity: 931GiB
                      capabilities: multi lvm2
           *-disk:1
                description: ATA Disk
                product: ST31000524AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: JC45
                serial: 5VP911B1
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a8a8a8a8
              *-volume
                   description: FreeBSD partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 931GiB
                   capabilities: primary
           *-cdrom
                description: DVD-RAM writer
                product: BD-RE  BH10LS30
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /media/MFL_PRO
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/MFL_PRO
                   capabilities: partitioned partitioned:mac
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
                 *-volume:0 UNCLAIMED
                      description: Apple partition map
                      physical id: 1
                      capacity: 17KiB
                 *-volume:1 UNCLAIMED
                      description: Apple HFS
                      physical id: 2
                      size: 40MiB
                      capacity: 40MiB
                      capabilities: hfs initialized
                      configuration: created=2009-11-30 14:05:43 filesystem=hfs label=MFL_PRO Suite modified=2010-03-02 04:00:45 state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbffb000-fbffb0ff ioport:500(size=32)
     *-scsi
          physical id: 1
          bus info: usb@2:1.3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 9744
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdd
             version: 9744
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sde
             version: 9744
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sdf
             version: 9744
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
        *-disk:4
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.4
             bus info: scsi@6:0.0.4
             logical name: /dev/sdg
             version: 9744
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdg

---

### Post by lordievader on 2012-09-06
Sorry I misunderstood, so you have a desktop with a GeForce GTX560 and 2 screens.

Could you answer my other questions too please? I take it that the two screens are connected to the GeForce, correct?

---

### Post by ookooboontoo on 2012-09-06
I wonder is your problem that the two monitors are exactly the same? are they both on the same kind of port or different?
Just a thought

---

### Post by chris954 on 2012-09-07
Yes I am running both monitors off 1 card.
1 is on the VGA port with an adaptor
The other is on the DVI port
I was running the same set-up on a Debian desktop with no problems.
And as I indicated earlier it did work even after rebootinga couple of times. It was only after I did a Cold restart that I had this problem

---

### Post by chris954 on 2012-09-07
Okay, I have had some success using the following command ¨gksudo nvidia-settings"

However I still cannot change the screen setup. i.e. I cannot set my left hand screen to be the master screen. Currently they are individual but both contain the Side and top bars.
When I click on Display from System Settings I get the error message ¨Could not get Screen Information, RANDR extension is not available."

How can I change the System from showing as a laptop when I actually have a Desktop ?

---

### Post by lordievader on 2012-09-07
I have a feeling you enabled Xinerama, or at least I got similar messages when I had it enabled. However for two screens I never needed Xinerama, the normal mode is good enough.

You have succeeded in enabling both screens, I conclude from the previous message. I'd say use the same method just without enabling Xinerama.

---

### Post by Favux on 2012-09-07
The Nvidia binary blob is not compatible with RandR.  That's why:
> error message ¨Could not get Screen Information, RANDR extension is not available."
So you have to do the monitor setup through the Nvidia settings gui or command line commands not the GNOME Displays applet.  The binary blob was finally going to be compatible with RandR 1.4 but 1.4 was delayed.  Despite that the Nvidia 302 driver released in May is suppose to be compatible with RandR 1.2/1.3.  So Nvidia figured out a way despite the lack of 1.4.

At a wild guess you set up the monitors through the Display applet before installing the Nvidia binary blob and its dkms (dynamic kernel module setup) with Additional Drivers.  When you did the cold boot you now had the nvidia drivers loading and that's what broke your monitor configuration.  If you had done **lsmod** while doing the setup I bet you would have seen **nouveau** and now you see **nvidia**.

Nvidia is not compatible with Xinerama and uses TwinView instead.  You should look at and also post your xorg.conf (where Nvidia does its configurations) in /etc/X11 so someone can take a look at it too.  I think there is a cli command that will get nvidia-settings to redo your xorg.conf if needed.

---

### Post by chris954 on 2012-09-08
> **Favux said:**
> The Nvidia binary blob is not compatible with RandR.  That's why:
Nvidia is not compatible with Xinerama and uses TwinView instead.  You should look at and also post your xorg.conf (where Nvidia does its configurations) in /etc/X11 so someone can take a look at it too.  I think there is a cli command that will get nvidia-settings to redo your xorg.conf if needed.

Thank you for your help. Here is the XORG.CONF
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 15:25:24 UTC 2012

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-06.nvidia.com)  Thu Apr  5 22:40:54 PDT 2012

Section "ServerLayout"

# Removed Option "Xinerama" "0"
    Identifier     "Layout0"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 1920 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AOC 2237"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "AOC 2237"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 560"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 560"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1920x1080_60_0 +0+0; CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-2"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

---

### Post by Favux on 2012-09-08
I'm not a video guru but nothing in your xorg.conf jumps out at me as being a problem.

The obvious question is what happens when you use the nvidia settings gui to try and configure things?  Can you activate your second monitor that way?

There should be a backup xorg.conf in /etc/X11 that nvidia-xconfig made when it first created its xorg.conf.  You could look that over for educational purposes.

You could also, with both monitors connected, rename your current xorg.conf and then run:
```
sudo nvidia-xconfig
```
to generate a new one and compare the two.  See if there is a difference.  Do this without rebooting and make sure you know how to restore your working xorg.conf from the command line if it comes to that.

xconfig manual:  [http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html](http://manpages.ubuntu.com/manpages/precise/man1/alt-nvidia-current-xconfig.1.html)

---

### Post by chris954 on 2012-09-24
Thank you for everyone who contributed.
I Reinstalled UBUNTU 12.04 and my dual monitors are now running as I wanted them to. 
After reinstalling I did not have to change any settings, it just worked.
 
Thanks again.

---

### Post by Bobhuber on 2012-09-25
> **chris954 said:**
> Yes I am running both monitors off 1 card.
1 is on the VGA port with an adaptor
The other is on the DVI port
I was running the same set-up on a Debian desktop with no problems.
And as I indicated earlier it did work even after rebootinga couple of times. It was only after I did a Cold restart that I had this problem
  I you use the 295.59 drivers because of similar problems but I do notice 2 entries for the pci bus ID which I don't think you need.  Here's mine. Your Bus ID is probably correct so leave it at 1. I also use absolute which produces a clone of the original on both monitors. I can post my entire xorg.conf if you want to try it with that setup.

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 550 Ti"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GTX 550 Ti"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection
```

---

### Post by Colo993 on 2012-09-25
I've had similar problems on my Dell laptop with dual screens and I  ONLY use the 295.59 drivers.  I've tried the newer drivers but due to various issues have reverted back to 295.59.

---

### Post by CJ_Hudson on 2012-10-19
I'm having similar issues with my NVisia GS8400 card and a monitor and a TFT TV.
Would updating my BIOS to the latest version help at all?! ;-)

---

