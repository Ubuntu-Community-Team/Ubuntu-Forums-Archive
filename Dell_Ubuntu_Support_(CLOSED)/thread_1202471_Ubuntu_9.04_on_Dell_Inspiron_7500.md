---
title: "Ubuntu 9.04 on Dell Inspiron 7500"
date: 2009-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by idave78 on 2009-07-02
Hi, all !!! I am a novice in linux (ubuntu) and are trying to install ubuntu 9.04 on Dell inspiron 7500. It went smooth with ubuntu 8.10, but going no further down of the loading screen with ubuntu 9.04. I've tried Live CD and the upgrade option from 8.10 (after restart same thing). If anyone can help with that, please. Appreciate  any tips in advance.

---

### Post by coffeeaddict22 on 2009-07-05
Hi iDave,
Sounds odd.  Can you be a little more specific:
1) Can you run Ubuntu off the live CD without any problem?
2) From the sound of it, you've got at least one OS installed.  So, how many, what, and how have you partitioned?
3) Exactly what happens when you try to install?  Is it doing a loading... forever, or crashing out somewhere?
4) Can you boot into a recovery console?  On booting up, instead of going into the system normally, the option below that on the boot menu is usually the recovery console.  Can you get into that OK?

---

### Post by idave78 on 2009-07-06
Hi, Coffeeaddict22!
I have Ubuntu 8.10 on my Dell Inspiron 7500 (Installed with no problems). That is the only OS I have on it. I was trying to upgrade to Ubuntu 9.04 and after it passed all the stages -> restart and nothing go on. Only I could get to flash screen with the bar showing loading process. It get to about 10-15% and stopped forever. Same thing with Live CD. Tried to boot with ACPI=OFF, no apic, no lapic (same thing): stopped at 10-15% of loading process.
Today I 've got the Ubuntu 9.10 Alpha 2 Live CD and was able to boot with no problems. I hope it would be OK with the final release, but if you can help me to get into Ubuntu 9.04 that would be a big help.

---

### Post by coffeeaddict22 on 2009-07-06
Do you know the CD works?  Have you done the md5sum on it? Have a look at [https://help.ubuntu.com/community/HowToMD5SUM#md5sum]("https://help.ubuntu.com/community/HowToMD5SUM#md5sum")

---

### Post by idave78 on 2009-07-07
Yes it works fine. I used it to install Ubuntu on HP Compaq with no problems.

---

### Post by coffeeaddict22 on 2009-07-08
OK.  Can you get into a recovery console?

---

### Post by idave78 on 2009-07-08
I have now Ubuntu 8.10 installed and yes I can get into recovery console with no problems on it. And I can see the recovery menu. But if you mean to get into recovery console after installing Ubuntu 9.04, then I did not try this one. And for this to check would have to install it again.

---

### Post by coffeeaddict22 on 2009-07-09
Just a thought.  If you want to play but need to keep your existing setup, it's not a problem.  Create another partition and install the OS into that; that way you can get it working how you want but still go to the other setup anytime you want to.

---

### Post by idave78 on 2009-07-09
Thank you for suggestion.

---

### Post by idave78 on 2009-07-10
I just installed Ubuntu 9.04 to another partition as you suggested. And no luck. I can't boot into recovery console. It stopes at "loading manual drivers". The kernel is 2.6.28.13. But the ubuntu 9.04 installation picked up kernel from my ubuntu 8.10 (2.6.27.14) and at the boot menu I can choose to boot into that one. Actually it bootes fine: normal boot and recovery console as well. I think that would be kind of OK, but if you have any thoughts let me know. Thank you for your time though.

---

### Post by coffeeaddict22 on 2009-07-10
If you try booting up and walk away, does it eventually manage to do so?  Reading around, the likelihood is it's a driver snafu.  If I had to guess, it'll be an Intel graphics driver; they're known to not work in 9.04.  If you post back the output of ```
lshw
``` to confirm that'd be nice.

---

### Post by idave78 on 2009-07-11
Hi, coffeeaddict22 ... here is the output of command you've asked: lshw
```

dell                      
    description: Computer
    product: Inspiron 7500
    vendor: Dell Computer Corporation
    version: Revision B0
    serial: 123456789
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: 440BX Desktop Reference Platform
       vendor: Compal Electronics, Inc.
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: A14 (11/08/2000)
          size: 87KiB
          capacity: 192KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: *Socket 5*
          size: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 319MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous [empty]
             physical id: 0
             slot: U5
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: U6
             size: 256MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 64
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 pm bus_master cap_list
                configuration: latency=66 mingnt=8
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64 module=ata_piix
           *-disk
                description: ATA Disk
                product: SAMSUNG HM160HC
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LQ10
                serial: S12TJD0Q332530
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fccc8892
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 95d3942a-2030-4472-80e0-dcc58e3c5420
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-06-22 10:27:53 filesystem=ext3 modified=2009-07-10 17:30:03 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-07-10 17:11:00 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 47GiB
                   capacity: 47GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 13GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4769MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: W95 FAT32 partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /STORAGE
                      capacity: 29GiB
                      configuration: mount.fstype=vfat mount.options=rw,gid=46,fmask=0007,dmask=0007,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,utf8 state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: 04e66bee-11ea-49ab-bf01-7d876dc0e839
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-07-09 15:53:15 filesystem=ext3 modified=2009-07-10 17:08:36 mounted=2009-07-10 16:51:05 state=clean
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-C2402
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1009
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-multimedia
             description: Multimedia audio controller
             product: ES1978 Maestro 2E
             vendor: ESS Technology
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ES1968 (ESS Maestro) latency=64 maxlatency=24 mingnt=2 module=snd_es1968
        *-communication UNCLAIMED
             description: Communication controller
             product: WinModem 56k
             vendor: Agere Systems
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0 maxlatency=14 mingnt=252
     *-network
          description: Wireless interface
          product: Belkin
          vendor: Belkin
          physical id: 1
          bus info: pci@0000:06:00.0
          logical name: wlan0
          version: 20
          serial: 00:17:3f:2e:2f:e1
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+blkwgnv7 driverversion=1.53+Belkin,10/19/2006,5.87.19.1 latency=64 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-battery
       physical id: 1
       slot: Left Front
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 92:cc:2f:34:a0:78
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by xd9x19 on 2009-07-29
I'm having issues with my Dell Inspiron 7500, also.  Works fine with v8.10, but when I update to v9.04, it locks up on boot-up.  :(

Last night it booted up to the login screen, but the keyboard didn't work.  So I rebooted and it blew up with some kind of error message, a different one on two different reboots.

****

9.04 loaded up once the following evening....then shut down and wouldn't boot up.  Gone back to 8.10....I'll just wait for 9.10 in a couple of months and try again.

---

