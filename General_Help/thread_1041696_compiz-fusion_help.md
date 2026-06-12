---
title: "compiz-fusion help"
date: 2009-01-16
forum: General Help
---

### Post by r4z0rw0lf on 2009-01-16
I have the *Intrepid Ibex* and i have tried to install compiz-fusion but it never seems to work... every time I try to enable desktop top effects it seems to redraw all the windows and spits out a message box at me saying: desktop effects could not be enabled and redraws everything again. and i have no idea how to fix this, and apparently google is mad at me and DOESNT want to be my friend so i cant find anything.

---

### Post by 2hot6ft2 on 2009-01-16
Did you install a graphics driver AND activate it in
System>Administration>Hardware Drivers
?

---

### Post by r4z0rw0lf on 2009-01-16
i think i have the nvidia grapics driver(?) but im not sure if i installed it right...

---

### Post by 2hot6ft2 on 2009-01-16
> **r4z0rw0lf said:**
> i think i have the nvidia grapics driver(?) but im not sure if i installed it right...
Then go to
System>Administration>Hardware Drivers
and find out

---

### Post by r4z0rw0lf on 2009-01-16
all it says is i have my wireless driver.

---

### Post by 2hot6ft2 on 2009-01-16
> **r4z0rw0lf said:**
> all it says is i have my wireless driver.
Does it show a graphics driver?

---

### Post by Wartender on 2009-01-16
try going to synaptic (system->administration-> synaptic package manager) and download compizconfig-settings-manager, see if you can activatr your desktop effects from there. it's probably a driver issue but it might work like this.

---

### Post by r4z0rw0lf on 2009-01-16
all it says is it has a b43legacy wireless driver

---

### Post by 2hot6ft2 on 2009-01-16
Might try using envy then.
In a terminal use
```
sudo apt-get install envy-ng
```
then it will be in
Applications>System Tools>EnvyNG

---

### Post by r4z0rw0lf on 2009-01-16
how? and sorry my previous post was a little pointless:(

---

### Post by r4z0rw0lf on 2009-01-16
it says it cannot be found. i will try synaptic

---

### Post by Wartender on 2009-01-16
what do you mean how? open a terminal (applications->accessories->terminal and type that code in to install envy

---

### Post by Wartender on 2009-01-16
never mind my post then

---

### Post by 2hot6ft2 on 2009-01-16
> **r4z0rw0lf said:**
> how? and sorry my previous post was a little pointless:(
Might try using envy then.
In a terminal
Applications>Accessories>Terminal
use
```
sudo apt-get install envy-ng
```
hit Enter then type in your password (it wont be displayed)
and hit Enter
then when it finishes, close the terminal and it will be in
Applications>System Tools>EnvyNG
Go there to start it choose your graphics card type, ati or nvidia and it will show an installed driver or ones you can install.
Choose the one it recommends and install it.

A reboot will be required after it installs.

---

### Post by r4z0rw0lf on 2009-01-16
sorry i've taken so long to reply, my internet connection keeps dropping

---

### Post by r4z0rw0lf on 2009-01-16
okay i got envyNG and where the driver are displayed it says none of them are compatible also it says none are recommended

---

### Post by 2hot6ft2 on 2009-01-16
wow, what graphics card do you have?
```
lshw
```
and / or
```
lspci
```
in a terminal

---

### Post by 2hot6ft2 on 2009-01-16
Is this a wubi install or a real install?

---

### Post by r4z0rw0lf on 2009-01-16
what am i looking for? both command spit out output and i have no idea on how to interpret either
should i post the output?

---

### Post by 2hot6ft2 on 2009-01-16
> **r4z0rw0lf said:**
> what am i looking for? both command spit out output and i have no idea on how to interpret either
should i post the output?
Yes post the output. Looking for the graphics card info

---

### Post by r4z0rw0lf on 2009-01-16
alright here goes:
output of lspci:
```

----@----laptop:~$ sudo lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
00:0b.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```
output of lpshw
```

----@----laptop:~$ sudo lshw
-----laptop               
    description: Desktop Computer
    product: Uknown
    vendor: American Megatrends Inc.
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: PT-2200
       vendor: American Megatrends Inc.
       physical id: 0
       version: 1.0
       serial: 00000000
       slot: ISA2
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01)
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: Slot-1
          size: 2800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 8KiB
             capacity: 1MiB
             clock: 25MHz (40.0ns)
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 512KiB
             capacity: 1MiB
             clock: 25MHz (40.0ns)
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 977MiB
     *-pci
          description: Host bridge
          product: 650/M650 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_palette cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-firewire
             description: FireWire (IEEE 1394)
             product: FireWire Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=12 mingnt=4 module=ohci1394
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-disk
                description: ATA Disk
                product: SAMSUNG MP0804H
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: UE10
                serial: S042J10X903070
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=bc4332f8
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/disk
                   version: 3.1
                   serial: e437aa1c-360a-4f4e-90d1-2b2b1b229682
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-09-18 16:20:04 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 478MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 19GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 18GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
           *-cdrom
                description: DVD reader
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd
                configuration: status=nodisc
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=64 maxlatency=11 mingnt=52
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:a0:cc:dd:b6:a4
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
        *-network:1
             description: Network controller
             product: BCM4303 802.11b Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=b43-pci-bridge latency=64 module=ssb
        *-pcmcia
             description: CardBus bridge
             product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:24:03:9f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:a6:12:4a:b5:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
does that help?

---

### Post by 2hot6ft2 on 2009-01-16
Ok first Is this a wubi install or a real install?

Here's the graphics info from them
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
and
> *-display [COLOR="Blue"]UNCLAIMED[/COLOR]
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_palette cap_list
                configuration: latency=0
I'm not familiar with that chipset. But it's unclaimed that's why you can't enable desktop effects.

---

### Post by r4z0rw0lf on 2009-01-16
well at first i had done a wubi install... but then i hadnt something went wrong--every time i tried to boot it said i could not find the hard drive image or something. and i went to my WUBI partition and tried the uninstall and i didnt work so i just removed the partition doing the non-wubi install. so it WAS both and theres my overly complicated description of my computers history with linux...

---

### Post by 2hot6ft2 on 2009-01-16
Not looking too good doing a search. So far I found this.
> 3D Graphical Acceleration
Asus L3355M's video controller is: "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter", as you can easily check with the "lspci" utility.
Let's start from saying that there are not Linux drivers for this chipset that allow hardware acceleration at the moment.
This simply means no Beryl, no Compiz, no 3d desktop, no full speed GoogleEarth for you. At least for the moment.
I know that is sad, but this is the truth.
Anyway, there are other ways to beautify your desktop. Let's see some of them.here [http://prof3ta.netsons.org/index.php?option=com_content&view=article&id=51&Itemid=72](http://prof3ta.netsons.org/index.php?option=com_content&view=article&id=51&Itemid=72)

Here's the search results so you can look thru them too for one that has been solved if there are any.[http://www.google.com/search?q=ubuntu+740+PCI%2FAGP&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=ubuntu+740+PCI%2FAGP&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by 2hot6ft2 on 2009-01-16
So far it's looking like you may have to get another graphics card for the effects to work.. That was the solution on this thread. [http://forum.compiz-fusion.org/archive/index.php/t-2487.html](http://forum.compiz-fusion.org/archive/index.php/t-2487.html)

Not seeing any that have it fixed. It's just not supported apparently. Only suggestion that's left would be to get a decent nvidia or ati card to put in it. Personally I prefer nvidia.

---

