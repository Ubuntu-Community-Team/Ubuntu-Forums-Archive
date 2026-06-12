---
title: "Xubuntu graphics FS esprimo V5535"
date: 2017-04-21
forum: Desktop Environments
---

### Post by tagge2 on 2017-04-21
Hi, Im new to linux and installed the xubuntu on an old F/S V5535, but I cant get the graphics to be better than 640x480, VGA. I tryed to get the ubuntu updates but i doesnt help..

---

### Post by ajgreeny on 2017-04-21
It looks as if that machine has a SIS-Mirage-3-672MX graphics card and SIS have for a time presented some problems with Linux and Ubuntu.

I can not find any information regarding drivers for that card, so it is possible that you may have to think again, or possibly look at other distros that may support that legacy graphic card.

---

### Post by tagge2 on 2017-04-21
Ok, a pity, it seemed to be a nice op. Well, suppose I have to go back to windows :(

---

### Post by mörgæs on 2017-04-21
Don't jump to conclusions. 

Let's see the hardware details. Please copy ```
sudo lshw -sanitize > lshw.txt
``` into the terminal and run it. After that post lshw.txt here in CODE tags.

---

### Post by tagge2 on 2017-04-24
```
[COLOR=#000000][FONT=&quot] beskrivning: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-18 21:55+0000Last-Translator: Daniel Nylander <yeager@ubuntu.com>Language-Team: Swedish <sv@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-06-27 17:08+0000X-Generator: Launchpad (build 18115)[/FONT][/COLOR]    produkt: ESPRIMO Mobile V5535
    tillverkare: FUJITSU SIEMENS
    version: V1.03
    serienummer: [REMOVED]
    bredd: 32 bits
    förmågor: smbios-2.4 dmi-2.4 smp-1.4 smp
    konfiguration: administrator_password=disabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=[REMOVED]
  *-core
       beskrivning: Moderkort
       produkt: Z17M2.0
       tillverkare: FUJITSU SIEMENS
       physical id: 0
       version: V1.03
       serienummer: [REMOVED]
     *-firmware
          beskrivning: BIOS
          tillverkare: Phoenix
          physical id: 0
          version: V1.05
          date: 02/25/08
          storlek: 101KiB
          kapacitet: 448KiB
          förmågor: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          beskrivning: Processor
          produkt: Intel(R) Celeron(R) CPU          540  @ 1.86GHz
          tillverkare: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.6.1
          serienummer: [REMOVED]
          plats: uPGA 479M
          storlek: 1860MHz
          kapacitet: 3600MHz
          bredd: 64 bits
          klocka: 200MHz
          förmågor: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf eagerfpu pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
        *-cache:0
             beskrivning: L1 cache
             physical id: 5
             plats: L1 Cache
             storlek: 16KiB
             kapacitet: 16KiB
             förmågor: asynchronous internal write-back
             konfiguration: level=1
        *-cache:1
             beskrivning: L2 cache
             physical id: 6
             plats: L2 Cache
             storlek: 1MiB
             kapacitet: 1MiB
             förmågor: burst internal write-back
             konfiguration: level=2
     *-cache
          beskrivning: L3 cache
          physical id: 7
          plats: L3 Cache
          storlek: 1MiB
          förmågor: burst internal write-back
          konfiguration: level=3
     *-memory
          beskrivning: Systemminne
          physical id: e
          plats: System board or motherboard
          storlek: 2GiB
        *-bank:0
             beskrivning: DIMM DRAM Synkront
             physical id: 0
             plats: DIMM1
             storlek: 1GiB
             bredd: 64 bits
        *-bank:1
             beskrivning: DIMM DRAM Synkront
             physical id: 1
             plats: DIMM2
             storlek: 1GiB
             bredd: 64 bits
     *-pci
          beskrivning: Host bridge
          produkt: 671MX
          tillverkare: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          bredd: 32 bits
          klocka: 33MHz
          konfiguration: driver=agpgart-sis latency=32
          resurser: irq:0 memory:d0000000-d3ffffff
        *-pci:0
             beskrivning: PCI bridge
             produkt: AGP Port (virtual PCI-to-PCI bridge)
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             bredd: 32 bits
             klocka: 66MHz
             förmågor: pci normal_decode bus_master
             resurser: ioport:9000(storlek=4096) memory:d4000000-d40fffff memory:c0000000-cfffffff
           *-display UNCLAIMED
                beskrivning: VGA compatible controller
                produkt: 771/671 PCIE VGA Display Adapter
                tillverkare: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                bredd: 32 bits
                klocka: 66MHz
                förmågor: pm agp agp-3.0 vga_controller cap_list
                konfiguration: latency=0
                resurser: memory:c0000000-cfffffff memory:d4000000-d401ffff ioport:9000(storlek=128) memory:c0000-dffff
        *-isa
             beskrivning: ISA bridge
             produkt: SiS968 [MuTIOL Media IO]
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: isa bus_master
             konfiguration: latency=0
        *-ide:0
             beskrivning: IDE interface
             produkt: 5513 IDE Controller
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: ide pm bus_master cap_list
             konfiguration: driver=pata_sis latency=128
             resurser: irq:16 ioport:1f0(storlek=8) ioport:3f6 ioport:170(storlek=8) ioport:376 ioport:1000(storlek=16)
        *-usb:0
             beskrivning: USB controller
             produkt: USB 1.1 Controller
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             bredd: 32 bits
             klocka: 33MHz
             förmågor: ohci bus_master
             konfiguration: driver=ohci-pci latency=32 maxlatency=80
             resurser: irq:20 memory:d4204000-d4204fff
           *-usbhost
                produkt: OHCI PCI host controller
                tillverkare: Linux 4.8.0-46-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logiskt namn: usb2
                version: 4.08
                förmågor: usb-1.10
                konfiguration: driver=hub slots=4 speed=12Mbit/s
        *-usb:1
             beskrivning: USB controller
             produkt: USB 1.1 Controller
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             bredd: 32 bits
             klocka: 33MHz
             förmågor: ohci bus_master
             konfiguration: driver=ohci-pci latency=32 maxlatency=80
             resurser: irq:21 memory:d4205000-d4205fff
           *-usbhost
                produkt: OHCI PCI host controller
                tillverkare: Linux 4.8.0-46-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logiskt namn: usb3
                version: 4.08
                förmågor: usb-1.10
                konfiguration: driver=hub slots=4 speed=12Mbit/s
        *-usb:2
             beskrivning: USB controller
             produkt: USB 2.0 Controller
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pm debug ehci bus_master cap_list
             konfiguration: driver=ehci-pci latency=32 maxlatency=80
             resurser: irq:22 memory:d4206000-d4206fff
           *-usbhost
                produkt: EHCI Host Controller
                tillverkare: Linux 4.8.0-46-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logiskt namn: usb1
                version: 4.08
                förmågor: usb-2.00
                konfiguration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   beskrivning: Masslagringsenhet
                   produkt: JumpDrive
                   tillverkare: Lexar
                   physical id: 1
                   bus info: usb@1:1
                   logiskt namn: scsi4
                   version: 11.00
                   serienummer: [REMOVED]
                   förmågor: usb-2.00 scsi emulated scsi-host
                   konfiguration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      beskrivning: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logiskt namn: /dev/sdb
                      storlek: 3824MiB (4009MB)
                      förmågor: partitioned partitioned:dos
                      konfiguration: logicalsectorsize=512 sectorsize=512 signature=000c54c0
                    *-volume
                         beskrivning: Windows FAT volym
                         tillverkare: SYSLINUX
                         physical id: 1
                         bus info: scsi@4:0.0.0,1
                         logiskt namn: /dev/sdb1
                         logiskt namn: /media/leif/988E-90E5
                         version: FAT32
                         serienummer: [REMOVED]
                         storlek: 3821MiB
                         kapacitet: 3821MiB
                         förmågor: primary bootable fat initialized
                         konfiguration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
        *-network
             beskrivning: Ethernet interface
             produkt: 191 Gigabit Ethernet Adapter
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logiskt namn: enp0s4
             version: 02
             serienummer: [REMOVED]
             storlek: 100Mbit/s
             kapacitet: 100Mbit/s
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             konfiguration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.4 duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
             resurser: irq:19 memory:d4407000-d440707f ioport:1080(storlek=128)
        *-ide:1
             beskrivning: IDE interface
             produkt: SATA Controller / IDE mode
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 03
             bredd: 32 bits
             klocka: 33MHz
             förmågor: ide pm bus_master cap_list
             konfiguration: driver=sata_sis latency=32
             resurser: irq:17 ioport:1058(storlek=8) ioport:104c(storlek=4) ioport:1050(storlek=8) ioport:1048(storlek=4) ioport:1020(storlek=16)
        *-pci:1
             beskrivning: PCI bridge
             produkt: PCI-to-PCI bridge
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pci msi pciexpress pm normal_decode bus_master cap_list
             konfiguration: driver=pcieport
             resurser: irq:16 memory:d4100000-d41fffff
           *-network
                beskrivning: Trådlöst gränssnitt
                produkt: AR242x / AR542x Wireless Network Adapter (PCI-Express)
                tillverkare: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logiskt namn: wlp2s0
                version: 04
                serienummer: [REMOVED]
                bredd: 64 bits
                klocka: 33MHz
                förmågor: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                konfiguration: broadcast=yes driver=ath5k driverversion=4.8.0-46-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resurser: irq:16 memory:d4100000-d410ffff
        *-pci:2
             beskrivning: PCI bridge
             produkt: PCI-to-PCI bridge
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pci msi pciexpress pm normal_decode bus_master cap_list
             konfiguration: driver=pcieport
             resurser: irq:16 ioport:3000(storlek=8192) memory:dc000000-dfffffff ioport:70000000(storlek=2097152)
        *-multimedia
             beskrivning: Audio device
             produkt: Azalia Audio Controller
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pm bus_master cap_list
             konfiguration: driver=snd_hda_intel latency=0 maxlatency=11 mingnt=52
             resurser: irq:18 memory:d4200000-d4203fff
        *-pci:3
             beskrivning: PCI bridge
             produkt: PCI-to-PCI bridge
             tillverkare: Silicon Integrated Systems [SiS]
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pci pciexpress msi pm normal_decode bus_master cap_list
             konfiguration: driver=pcieport
             resurser: irq:0
     *-scsi:0
          physical id: 1
          logiskt namn: scsi0
          förmågor: emulated
        *-cdrom
             beskrivning: DVD-RAM writer
             produkt: DVD RW AD-7540A
             tillverkare: Optiarc
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logiskt namn: /dev/cdrom
             logiskt namn: /dev/cdrw
             logiskt namn: /dev/dvd
             logiskt namn: /dev/dvdrw
             logiskt namn: /dev/sr0
             version: 1.42
             serienummer: [REMOVED]
             förmågor: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             konfiguration: ansiversion=5 status=open
     *-scsi:1
          physical id: 2
          logiskt namn: scsi2
          förmågor: emulated
        *-disk
             beskrivning: ATA Disk
             produkt: WDC WD1600BEVS-0
             tillverkare: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logiskt namn: /dev/sda
             version: 1G04
             serienummer: [REMOVED]
             storlek: 149GiB (160GB)
             förmågor: partitioned partitioned:dos
             konfiguration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=e32fcc18
           *-volume:0
                beskrivning: EXT4-volym
                tillverkare: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logiskt namn: /dev/sda1
                logiskt namn: /
                version: 1.0
                serienummer: [REMOVED]
                storlek: 147GiB
                kapacitet: 147GiB
                förmågor: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                konfiguration: created=2017-04-19 12:20:54 filesystem=ext4 lastmountpoint=/ modified=2017-04-23 07:22:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-04-21 10:40:20 state=mounted
           *-volume:1
                beskrivning: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logiskt namn: /dev/sda2
                storlek: 1788MiB
                kapacitet: 1788MiB
                förmågor: primary extended partitioned partitioned:extended
              *-logicalvolume
                   beskrivning: Linux swap / Solaris partition
                   physical id: 5
                   logiskt namn: /dev/sda5
                   kapacitet: 1788MiB
                   förmågor: nofs
  *-battery
       beskrivning: Litiumjon Battery
       produkt: Simplo
       tillverkare: Simplo
       physical id: 1
       version: Samsung
       serienummer: [REMOVED]
       plats: main
       kapacitet: 32560mWh
       konfiguration: voltage=14,8V
  *-remoteaccess UNCLAIMED
       tillverkare: SiS
       physical id: 2
       förmågor: inbound

```

---

### Post by wildmanne39 on 2017-04-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by tagge2 on 2017-04-24
Sorry for the mess, did now as you adviced, thanks

---

### Post by mörgæs on 2017-04-24
This might help:
[https://ubuntuforums.org/showthread.php?t=2350126&page=4&p=13599531#post13599531](https://ubuntuforums.org/showthread.php?t=2350126&page=4&p=13599531#post13599531)

A lot of commands but it should all be copy-paste.

---

### Post by tagge2 on 2017-04-24
It refuses to start after this.

---

### Post by lah-ca on 2017-04-25
> **tagge2 said:**
> It refuses to start after this.

Hi,

Mörgæs and Temüjin helped me with this same problem earlier this year.  Mörgæs directed you to a thread with a tutorial/summary that I wrote up at the end.

If things are not working, my first _***guess***_ is that there is a problem with the xorg.conf file.  I had this problem when I tried to type out the file content rather than using copy/paste.  Then on reboot the X server crashed and the computer would not start.  So what I would suggest here is booting to the live CD and then using a text editor to re-edit xorg.conf.  Proof read it carefully.  If you can't see any mistakes, put the video driver back to the native VESA driver.  This should allow you to reboot the system in a lower but acceptable resolution.  You may have to launch the text editor from a terminal and use sudo to start it in order to get rights to X11 file on the hard drive - can't remember now - but it won't hurt to do it this way.  

Here is the code for the VESA driver to load.  

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection




Section "Monitor"
        Identifier      "Configured Monitor"
EndSection




Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

If this works, then we can look at loading the SIS drivers again.  You might also look for information in the X logs if you installed a log viewer.

All the best.

---

### Post by lah-ca on 2017-04-26
Hi again,

Mörgæs just pointed that Temüjin found a typo in the summary/tutorial I wrote up.  Perhaps this is the source of the problem.  Go back and look again.  I have corrected the typo.

One more thing, you might try is reloading the OS and doing the SIS driver build and loading before doing all the system updates.

All the best.

---

