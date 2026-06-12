---
title: "DELL Vostro 1400 - Laptop built in Web Camera, Mic and Speakers do not work."
date: 2008-12-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sakthidaran on 2008-12-21
I have a DELL Vostro 1400 Laptop came preloaded with MS Vista. It had endless problem and the system was all the time under service. The entire warranty period was spent in trouble shooting by DELL. They changed many hardware and they could not find out the actual problem.

Finally, I decided to go for Ubuntu as I had used it for some time 2 years back with my desktop system. This time, I decided to have only Ubuntu partition and no dual boot. Initially, I tried Ubuntu 8.04 LTS. Except the following most of the work I could do with out any problem:
1.[COLOR="Blue"] Laptop integrated web camera
2. Laptop built-in mic near the camera
3. Built-in speakers[/COLOR]
4. Wireless connectivity

I have a broadband connection and able to manage with out wireless connectivity. With vista, the first three was working well but wireless connectivity had problem.

I need to communicate with friends using videoconferencing.[COLOR="Blue"] Therefore, I want the first three problems to be solved together on priority basis.[/COLOR] Kindly help me with detailed instructions so that I can enjoy Ubuntu to the fullest extent.

For you information, I am attaching the system information.

Thanking you in advance,

sakthidaran

sakthi-laptop             
    description: Portable Computer
    product: Vostro 1400
    vendor: Dell Inc.
    serial: 1ZVHB2X
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-5A00-1056-8048-B1C04F423258
  *-core
       description: Motherboard
       product: 0TT359
       vendor: Dell Inc.
       physical id: 0
       serial: .1ZVHB2X.CN7878381V008R.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A09 (07/10/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Microprocessor
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
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
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: V916765G24QCFW-F5
             vendor: 4000000000000000
             physical id: 0
             serial: B988348B
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: V916765G24QCFW-F5
             vendor: 4000000000000000
             physical id: 1
             serial: 4ED23C00
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8400M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:09:6d:a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5906M Fast Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:c9:01:95:78
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.1.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ricoh-mmc latency=64 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
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
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD writer
                product: DVD+-RW DS-8W1P
                vendor: PBDS
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BD1B
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: ST9160821AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda[/CENTER]
                version: 3.CD
                serial: 5MA6M86T
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00000080
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: ecba9bc0-135f-48f6-be03-ca7c6aaef870
                   size: 143GiB
                   capacity: 143GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-03 08:49:55 filesystem=ext3 modified=2008-12-21 08:58:13 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-12-21 08:49:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5930MiB
                   capacity: 5930MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5930MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-battery
       product: DELL PR6937A
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:1f:14:2e:a8:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[CENTER]----------------------[/CENTER]

---

### Post by bigbrovar on 2008-12-21
@ sakthidaran the infor you displayed are just to much to go through can do this open your terminal  copy and paste this and enter.. ```
lspci
``` post the output ...

---

### Post by bigbrovar on 2008-12-21
for the sound problem i found this [http://tp0x45.blogspot.com/2008/05/hardy-heron-on-dell-vostro-1400-sound.html]("http://tp0x45.blogspot.com/2008/05/hardy-heron-on-dell-vostro-1400-sound.html") you might want to try it ..

---

### Post by bigbrovar on 2008-12-21
for the webcam try this 

Webcam
For some reasons the webcam driver that ships with ibex does not work with the m1330. so we would have to download and compile the one that works for it. again involves the commandline .. but again nothing serious.

we download the latest driver from here
[http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

you can download either the bz2 achieve or the gz i downloaded the gz
once down loaded right click driver and choose extract here. which would extract it the driver folder. now we need to enter into that folder from the commandline. to make this easy rename the extracted folder as just uvcvideo
then place it in your desktop then run this command

```
cd $HOME/Desktop/uvcvideo
```

your command line prompt should now look like this

```
:~/Desktop/uvcvideo$
```

now just copy paste and run the following commands one after the last one is done

```
sudo apt-get install build-essential cheese libjasper-runtime libjasper1
```

then

```
make
```

than finally

```
sudo make install
```

running make would sure take a while. but once done make install wont be that long. once everything is done reboot and start cheese. Appications/Graphic/Cheese.

for those who would like to use their web cam with yahoo the you can use kopete 

from my blog post on how i got [intrepid working on my dell m1330]("http://bigbrovar.wordpress.com/2008/11/20/ubuntu-intrepid-ibex-on-dell-xps-m1330/"). although its a different distro and a different laptop this part of the guide should work for your laptop's webcam.

---

### Post by sakthidaran on 2008-12-21
Thanks bigbrovar. Below is the output.

sakthi@sakthi-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
sakthi@sakthi-laptop:~$

---

### Post by sakthidaran on 2008-12-21
Thanks bigbrovar. This link [http://tp0x45.blogspot.com/2008/05/hardy-heron-on-dell-vostro-1400-sound.html](http://tp0x45.blogspot.com/2008/05/hardy-heron-on-dell-vostro-1400-sound.html) referred by you helped me fix the mic and speaker problem. It works in 'sound recorder' application.

[COLOR="Blue"]Thank you once again for helping me to set right the mic and speaker.[/COLOR]

---

### Post by bigbrovar on 2008-12-21
did the try the one for the webcam ... i posted a guide for the webcam did u try itn to see if it worked?

---

### Post by sakthidaran on 2008-12-22
> **bigbrovar said:**
> did the try the one for the webcam ... i posted a guide for the webcam did u try itn to see if it worked?

Before, trying that I checked and found that webcam works in Kopete but not in Cheese! Then I got a message that there is a system update ready. [COLOR="Blue"]I updated kernel 2.6.27-11-generic and after reboot I am not getting the internet connectivity. Both wireless and broadband connections have been lost.[/COLOR] This message I am trying sending from my desk top.

Now, my priority is to restore network connectivity. Will you please help me?

---

### Post by bigbrovar on 2008-12-22
you must have the proposed and backport repo enabled .. that is not always a good thing you know. am saying this because i dont have either of does repos (which has some buggy undates). enabled. so i am still using the Linux version 2.6.27-9-generic .. anyway .. you can always use the last working kernel before the update. and that should work fine. just press esc at once grub loads and choose the kernel you were using before the update. and things should be fine. you can install this tool .. startupmanager its in the repos .. from there u can make the working kernel the default when you boot your system. hope it works out fine .. sorry i can me of more help.

---

### Post by sakthidaran on 2008-12-23
> **bigbrovar said:**
> you must have the proposed and backport repo enabled .. that is not always a good thing you know. am saying this because i dont have either of does repos (which has some buggy undates). enabled. so i am still using the Linux version 2.6.27-9-generic .. anyway .. you can always use the last working kernel before the update. and that should work fine. just press esc at once grub loads and choose the kernel you were using before the update. and things should be fine. you can install this tool .. startupmanager its in the repos .. from there u can make the working kernel the default when you boot your system. hope it works out fine .. sorry i can me of more help.

Thank you for your information. I switched to my earlier kernel version no 2.6.27.10 and the Internet connectivity started working. I hope the concerned kernel designers will look into this problem.

:)

---

### Post by sakthidaran on 2008-12-23
> **bigbrovar said:**
> for the webcam try this 

Webcam
For some reasons the webcam driver that ships with ibex does not work with the m1330. so we would have to download and compile the one that works for it. again involves the commandline .. but again nothing serious.

we download the latest driver from here
[http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

you can download either the bz2 achieve or the gz i downloaded the gz
once down loaded right click driver and choose extract here. which would extract it the driver folder. now we need to enter into that folder from the commandline. to make this easy rename the extracted folder as just uvcvideo
then place it in your desktop then run this command

```
cd $HOME/Desktop/uvcvideo
```

your command line prompt should now look like this

```
:~/Desktop/uvcvideo$
```

now just copy paste and run the following commands one after the last one is done

```
sudo apt-get install build-essential cheese libjasper-runtime libjasper1
```

then

```
make
```

than finally

```
sudo make install
```

running make would sure take a while. but once done make install wont be that long. once everything is done reboot and start cheese. Appications/Graphic/Cheese.

for those who would like to use their web cam with yahoo the you can use kopete 

from my blog post on how i got [intrepid working on my dell m1330]("http://bigbrovar.wordpress.com/2008/11/20/ubuntu-intrepid-ibex-on-dell-xps-m1330/"). although its a different distro and a different laptop this part of the guide should work for your laptop's webcam.

I did all that you said. When I entered make, it returned the following error code and returned to prompt.

[COLOR="Blue"]make: *** No targets specified and no makefile found.  Stop.[/COLOR]

Is something missing in your command? Kindly tell me how to proceed further.

Thanking you for your interest and support.

---

### Post by sakthidaran on 2008-12-25
> **sakthidaran said:**
> I did all that you said. When I entered make, it returned the following error code and returned to prompt.

[COLOR="Blue"]make: *** No targets specified and no makefile found.  Stop.[/COLOR]

Is something missing in your command? Kindly tell me how to proceed further.

Thanking you for your interest and support.
I have somehow installed cheese. If I click photo, 3 2 1 but no image is photographed. Webcam works in Kopete and skype.

Will some one help me? I want to take video with the help of webcam.

---

### Post by sakthidaran on 2009-05-31
Last 5 months, I have been working peacefully with my Dell. The cheese problem was solved by changing the resolution to 800x640. The freezing problem was with higher resolution. Wireless problem was solved by proper configuration. It is a pleasure work with Ubuntu. No virus problem. No licensing threats. Dell Vostro 1400 works excellently with Ubuntu. No hardware problem ever reported after migration to [COLOR="Blue"]Ubuntu. Thanks [/COLOR]to everyone who contribute in the forum. help.:D

---

### Post by mayimbe on 2009-06-04
I also have Dell Vostro 1400,


Here is the weird problem. Everything works on my laptop
exept sounds on the speaker. I plug in external speakers
and there is sound.

I restored defaults second, after i did a bios update. I loaded
windows 7, and i have the same problems. 

No sound on the laptop but on the external speakers. Can anyone
help me with this problem.

Joshua
aim: JerezEngineering

---

