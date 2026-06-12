---
title: "More Nvidia Problems - Low Resolutions"
date: 2011-01-19
forum: Desktop Environments
---

### Post by killersoap on 2011-01-19
I know I'm not the only one who has had problems with Nvidia drivers/video cards, but I am at a loss with this $#!t-storm...

It is an older desktop (HP Pavilion 541c) that I had running Ubuntu in the past (8.10 I believe) and it ran fine. I remember tinkering with xorg.conf and all that jazz to get it working. Since then I turned it into a headless media server, and now have it back to a 'normal' desktop, running 10.10.

Since the installation of 10.10, I have not been able to get a resolution higher than 1040x768. It is very usable but has no desktop effects and I am pretty darn sure the resolution can go higher.

I have messed with xorg.conf's to no avail, downloaded just about every driver Nvidia offers, both from their site and from Synaptic. 'Additional Drivers' under System>Admin shows the drivers are activated, but never in use. If I force X to use them through the xorg.conf (instead of Nouveau) I get no graphic environment until I rm /etc/X11/xorg.conf and start again (sometimes needing to ssh just to do that).

I am assuming it has something to do with either the driver or xorg.conf but am at a loss as to what I should try next. I would be more than happy to provide any outputs/screenshots/whatever and have my trusty laptop next to me to seek help should I seriously screw anything up (and everything is backed-up). I also have a LiveCD handy should that be needed.

I'm sitting around all day with nothing to do except figure this out so if anyone has any ideas please share, we can go through it one step at a time if it's easier. I am comfortable with the command line and all that so don't be afraid to throw code at me.

It's somewhat frustrating but I am trying to see it as a reason to learn something new so if you can teach me something in the process, kudos.

lshw:
```
bigdaddy                  
    description: Desktop Computer
    product: P8328A-ABA 541C
    vendor: HP Pavilion 04
    version: 70000TG101SAMBA
    serial: MX22390822 NA601
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=E073A019-8779-D611-B7BE-EFEB2A183C84
  *-core
       description: Motherboard
       product: MS-6367
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: MS-6367 (03/18/2002)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: Socket 7
          size: 1666MHz
          capacity: 2GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
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
          physical id: 1a
          slot: System board or motherboard
          size: 512MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 256MiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MiB
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
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
          resources: irq:0 memory:e8000000-ebffffff
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
             resources: irq:255 ioport:5000(size=16) ioport:5020(size=16) ioport:6000(size=32)
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
             resources: irq:20 memory:ee183000-ee183fff
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
             resources: irq:21 memory:ee181000-ee181fff
        *-network
             description: Ethernet interface
             product: nForce Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: c2
             serial: 00:10:dc:45:b0:b2
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
             resources: irq:22 memory:ee182000-ee1823ff ioport:d800(size=8)
        *-multimedia:0 UNCLAIMED
             description: Multimedia audio controller
             product: nForce Audio Processing Unit
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: c2
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0 maxlatency=12 mingnt=1
             resources: memory:ee100000-ee17ffff
        *-multimedia:1
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
             resources: irq:21 ioport:dc00(size=256) ioport:e000(size=128) memory:ee180000-ee180fff
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
             resources: ioport:c000(size=4096) memory:ee000000-ee0fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323
                vendor: Agere Systems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12
                resources: irq:16 memory:ee000000-ee000fff
           *-communication UNCLAIMED
                description: Communication controller
                product: LT WinModem
                vendor: Agere Systems
                physical id: 2
                bus info: pci@0000:01:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252
                resources: memory:ee001000-ee0010ff ioport:c000(size=8) ioport:c400(size=256)
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
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e800(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD800BB-75CA
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 16.0
                serial: WD-WMA8E8925561
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0005a19b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 07236038-1cc5-413e-8298-289351b09417
                   size: 44GiB
                   capacity: 44GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-13 16:18:54 filesystem=ext4 lastmountpoint=/?y&#65533;&#65533;Mw&#1728;&#65533;&#1766;&#65533;P^s&#65533;Dq!&#65533;&#65533;&#65533;&#65533;@^s&#65533;pa&#65533;pa&#65533;Mw&#65533;h^s&#65533;&#65533;s!&#65533; j modified=2011-01-13 16:43:21 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-19 14:54:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 28GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1360MiB
                      capabilities: nofs
           *-cdrom:0
                description: CD-R/CD-RW writer
                product: CD-R/RW SW-224B
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: R206
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM SD-616F
                vendor: SAMSUNG
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: F100
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
             resources: memory:ec000000-edffffff memory:e0000000-e7ffffff
           *-display
                description: VGA compatible controller
                product: NVCrush11 [GeForce2 MX Integrated Graphics]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:16 memory:ec000000-ecffffff memory:e0000000-e7ffffff memory:ed000000-ed00ffff

```

lspci:
```
00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation nForce 420 Memory Controller (DDR) (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce AC'97 Audio Controller (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:00.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 04)
01:02.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

```

---

### Post by Krytarik on 2011-01-19
Hi,

in the first of your outputs one can see that the so-called "nouveau" driver is used, its the open source rebuild of the proprietary driver. Remove it with
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```
and re-install all "nvidia" related packages found in Synaptic. Since your chip is a"legacy" one, as mine, the appropriate driver version is 96. Look if you have all necessary packages installed:
```
krytarik@krytarik-desktop:~$ dpkg -l |grep nvidia
ii  nvidia-173-modaliases                 173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96                             96.43.17-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and
ii  nvidia-96-modaliases                  96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                         0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases             195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-settings                       195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv

```
After this, choose your desired mode and save it to your "xorg.conf":
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Good luck!

---

### Post by killersoap on 2011-01-19
I feel like that was one of the many guides I have tried out, but I will go through those steps and see what happens and give an update.

Thank you for the reply.

---

### Post by killersoap on 2011-01-19
Well, I got to your first step in 
> After this, choose your desired mode and save it to your "xorg.conf":
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

There was no NVIDIA Settings in any menu, so I did a
```

su
(password)
nvidia-settings

```

Upon opening it informed me that:
> 
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.


When I did the nvidia-xconfig the command was not found, and I could not find a way to install it. I assume it is supposed to come included with one of the other packages you listed, all of which I marked for reinstallation (save the 173-modalias, this was just an installation).

I'm going to do a quick reboot and try again but wanted to get this post up in case I get denied a GUI.

---

### Post by killersoap on 2011-01-19
Well I still have a GUI, but no progress.

Maybe a reinstall of Nouveau (just to have a driver), purge all Nvidia stuff, then go back through those steps to see if I get nvidia-xconfig to work?

Any thoughts?

---

### Post by Krytarik on 2011-01-19
Check if you have all the packages installed I posted, I've installed the proprietary driver right after fresh install via "Hardware Drivers", so this will be quite the default install for version 96.

---

### Post by killersoap on 2011-01-19
I've purged *everything* and started fresh, triple-checked that those packages you listed are installed, and still have made no advances. That is, the Nvidia driver is not being used, the nvidia-settings tells me to run nvidia-xconfig before I can do anything, and the command nvidia-xconfig is not found.

In 'Additional Drivers' (System>Admin) the nvidia_96 is the only one listed, but its status is 'activated but not currently in use,' for what it's worth. I have no xorg.conf but if I made one and threw in a line forcing X to use the Nvidia, would that do any good? What sort of syntax would make that happen?

I appreciate the help thus far.

---

### Post by robert shearer on 2011-01-19
From the release notes for Maverick 10.10 here...
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

> The new Xorg 1.9 available in Maverick is **not **compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers. (626974) 

Either drop back to 10.04 or accept 1024x768.

---

### Post by killersoap on 2011-01-19
Well thanks for bursting my bubble... ;)

At least I can stop going crazy now that I know its a wild goose chase.

Kudos for teaching me something, and thank you for trying Krytarik.

---

### Post by Krytarik on 2011-01-19
> **robert shearer said:**
> From the release notes for Maverick 10.10 here...
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)



Either drop back to 10.04 or accept 1024x768.
I didn't know this, that's quite ugly. Then old ATI cards could even end up having better support at least by the Open Source Edge drivers, I considered that even bad before.:-(

---

### Post by robert shearer on 2011-01-19
This bug report...
[https://bugs.launchpad.net/ubuntu/maverick/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/maverick/+source/xorg-server/+bug/626974)

has details of progress with the 96 and 173 drivers.

seems 173 now works and 96 may using ppa ?

Will read through again but worth checking for you both..

---

