---
title: "Need help with CD ROM, it's gone???"
date: 2008-04-06
forum: Desktop Environments
---

### Post by tiger.woods on 2008-04-06
Everything was working fine and all of a sudden my CD-ROM won't launch amd I can't use it from CD/DVD creator?

I'm a bit new to the hardware side of things so I'm looking for some help in identifying what's going on. I've looked through the logs but don't see anything, any help would be appreciated.

From FSTAB:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I tried the following with these results.

 sudo mount /media/cdrom0/ -o unhide
mount: special device /dev/hdc does not exist


Thanks,

---

### Post by warp99 on 2008-04-06
Are the devices still listed in /dev? The device point could have changed. Run dmesg and scroll through the ouput looking for you cdrom device. If you find the device it will give the /dev terminal point. Here is an example:

```
:/$ dmesg  
...
[   78.866737] hda: LITE-ON DVDRW SOHW-1633S, ATAPI CD/DVD-ROM drive
[   79.898041] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
...

```

The device point is hda in this example.

---

### Post by tiger.woods on 2008-04-07
Thanks for the post.

I'm looking a little further and I think I may have found something but I'm not positive.

The DVD is plugged into IDE2 so shouldn't those devices show up on /dev/hdb..?

[I][B]$ ls /dev/hd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda3  /dev/hda4  /dev/hda5[/B][/I]

I don't even see /dev/hdb listed does that point back to a bios problem or even possibly a bad ide channel?

Thanks,

---

### Post by warp99 on 2008-04-07
> **tiger.woods said:**
> T
The DVD is plugged into IDE2 so shouldn't those devices show up on /dev/hdb..?


No, the device will be hdc or hdd. Run dmesg and see if the device is listed. Also run the following:
```
sudo lshw
```

If it's not in dmesg or lshw it's not being seen. Also does the BIOS see the drive? If it's not in the BIOS then it's the drive or the cable or the IDE channel.

Edit:

You can use makedev to make the device, type 'man MAKEDEV' for information, but first let's see if the device is listed in your BIOS.

---

### Post by tiger.woods on 2008-04-07
It's not showing in the BIOS, weird... I swapped the drive and it's also not the drive?

Here is the output from lshw, nice tool:

   [I][B] description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: nVidia-nForce
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/29/2004)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 1833MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GB
          capacity: 1536MB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MB
        *-bank:2
             description: DIMM
             physical id: 2
             slot: A2
             size: 512MB
     *-pci
          description: Host bridge
          product: nForce2 AGP (different version?)
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a1
             serial: 00:04:61:65:b1:14
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.111 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
        *-multimedia
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Network controller
                product: B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
                vendor: Techsan Electronics Co Ltd
                physical id: 7
                bus info: pci@0000:01:07.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b2c2_flexcop_pci latency=32 module=b2c2_flexcop_pci
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 6Y250P0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: YAR41BW0
                   serial: Y64GBVHE
                   size: 233GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma6 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 101MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 14GB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 509MB
                      capabilities: primary nofs
                 *-volume:3
                      description: Extended partition
                      physical id: 4
                      bus info: ide@0.0,4
                      logical name: /dev/hda4
                      size: 219GB
                      capacity: 219GB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux filesystem partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 219GB
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
[/B][/I]

Since  hda exists will the system have any issues if I plug the CDROM onto IDE0?

---

### Post by warp99 on 2008-04-07
Plug the drive into ide0 and it should become /dev/hdb. If not check your BIOS to make sure the drive is seen, then boot and enter the following:

```
cd /dev
sudo MAKEDEV hdb
```

Yes MAKEDEV is all capital letters. Only do a MAKEDEV if the kernel doesn't make the device point /dev/hdb. Also you may have to symlink the new device to 'dvd' and 'cdrom' if needed.

---

### Post by tiger.woods on 2008-04-07
Yep, throwing it on IDE0 worked the drive is back.

Will the following mount the device back to /dev/dvd?

[B][U]cd /dev
sudo MAKEDEV hdb[/U][/B]

Thanks.

TW,

---

### Post by warp99 on 2008-04-07
See if the dev point is made first:

```
cd /dev && ls hd*
```

If it's not there issue the 'MAKEDEV hdb' command. You're most likely going to need to make symlinks for 'dvd' and 'cdrom' to /dev/hdb:

```
sudo ln -s /dev/hdb /dev/dvd
sudo ln -s /dev/hdb /dev/cdrom
```

but make sure the device point is there before you make the symlinks.

Edit:

Symlinks are symbolic links pointing to the real device.

---

### Post by tiger.woods on 2008-04-07
Much appreciated! That solved the problem, the piece I'm alsways missing is the link. IS there a way to see the symlinks?

TW,

---

### Post by warp99 on 2008-04-07
If you issue a 'ls -l' command you'll see the details of the links:

```
:/dev$ ls -l
...
lrwxrwxrwx 1 root root           3 2008-04-07 19:33 cdrom -> hda
lrwxrwxrwx 1 root root           3 2008-04-07 19:33 cdrw -> hda
lrwxrwxrwx 1 root root          11 2008-04-07 19:33 core -> /proc/kcore
lrwxrwxrwx 1 root root           3 2008-04-07 19:33 dvd -> hda
lrwxrwxrwx 1 root root           3 2008-04-07 19:33 dvdrw -> hda
...

```

---

