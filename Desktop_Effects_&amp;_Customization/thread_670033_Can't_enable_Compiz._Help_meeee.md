---
title: "Can't enable Compiz. Help meeee"
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by hlmijendrix on 2008-01-17
I can't select Custom in the appearance window...it just goes back to no effects. I had this thing working earlier today and now the whole bar looks different.

Help meee

---

### Post by Pandemic187 on 2008-01-17
Please list your system specifications to give forums members and idea as to what you're dealing with. Based on your hardware there could be several already known reasons why it's not working on your system.

---

### Post by hlmijendrix on 2008-01-17
How do I do that? All I know is that it has a Intel celeron M processor with 1gb RAM and it's dual booting with xp

---

### Post by Thanoulis on 2008-01-17
Post the output of the lshw command in a terminal.
```
sudo lshw > <somefile>
```
This will write down every component your computer has, in the file you specify to.

---

### Post by hlmijendrix on 2008-01-17
uhhh...

```
david@david-laptop:~$ sudo lshw > <somefile>
bash: syntax error near unexpected token `<'

```

---

### Post by zakaroo on 2008-01-17
> **hlmijendrix said:**
> uhhh...

```
david@david-laptop:~$ sudo lshw > <somefile>
bash: syntax error near unexpected token `<'

```

Hi David - 

When you use a > it writes the output no to you screen but to a file on your hard drive.  You have to tell the output what file.  Take away the <> around the file name and it will work perfectly.  Z

---

### Post by hlmijendrix on 2008-01-17
I still can't get it to work :( Linux hates me...

---

### Post by ram zu on 2008-01-17
Just be patient and take one step at time

```
sudo lshw > <somefile>
```

In this case you have to open a terminal and insert this:

 sudo lshw > specs

this will create a file named specs in your default dir, after you can do:

 sudo gedit specs

and this will open a file in editor were you will see you computer specs and hardwere instaled.

The name specs was an example, use whatever you want

---

### Post by hlmijendrix on 2008-01-17
Wow I suck with computers..thanks man. lol

```
david-laptop
    description: Notebook
    product: Aspire 3690
    vendor: Acer
    version: V3.23
    serial: LXAY90Y0406500A5271601
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=504BDE06-20EF-901F-01BE-0016D468F35E
  *-core
       description: Motherboard
       product: Grapevine
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAY90Y0406500A5271601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V3.23 (12/09/2006)
          size: 101KB
          capacity: 960KB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U1
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up pni monitor tm2 xtpr
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MB
             capacity: 2MB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 512MB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 512MB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 02
                serial: 00:16:d4:68:f3:5e
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
           *-network:1
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: eth1
                version: 02
                serial: 00:19:7d:20:9e:c7
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=10.28.240.196 latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
           *-system
                description: Generic system peripheral
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 maxlatency=72 mingnt=32 module=sdhci
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: latency=0 maxlatency=4 mingnt=1
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: driver=sdhci latency=0 maxlatency=72 mingnt=32 module=sdhci
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: Hitachi HTS54166
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SBBO
                serial: SB2B04SLG6612E
                size: 55GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 9538MB
                   capabilities: primary
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 478MB
                   capabilities: primary nofs
              *-volume:2
                   description: HPFS/NTFS partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 46GB
                   capabilities: primary bootable
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SCB5265
                vendor: PHILIPS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TX07
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
```

Now I'm also thinking I have the wrong video drivers installed..I was messing around and now when I try to change the appearance thing...it says "desktop effects could not be enabled" or something like that.

---

### Post by hlmijendrix on 2008-01-17
and now I can't even boot up in linux...i'll type in my login stuff..it'll change screens...then just keep coming back to the login screen.

I'm going to install the version before gutsy here pretty soon hopefully...

I want my cool effects back :( screw xp

---

### Post by karvec on 2008-01-24
i would just completely restart from scratch--  if you have an external hard drive, put everything of value on there(from the command line, to copy a file--  say your pictures(this is just an example) do "cp /home/user/Pictures/* /media/drivename/pictures" or wherever said drive is mounted.  then just restart from scratch--  i've done that many times.

---

