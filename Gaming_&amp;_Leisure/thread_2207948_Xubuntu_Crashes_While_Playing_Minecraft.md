---
title: "Xubuntu Crashes While Playing Minecraft"
date: 2014-02-25
forum: Gaming &amp; Leisure
---

### Post by austinrandy0209 on 2014-02-25
Hello,
I recently installed Xubuntu 13.10 and I noticed that while playing Minecraft, after about a hour the whole system freezes and I can't do anything at all. I am forced to do a hard reset.

How can I fix this?

**SOLVED:**
Followed monkeybrain20122's instructions and upgraded drivers using:
```
sudo apt-add-repository ppa:oibaf/graphics-drivers
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel[FONT=arial]
sudo apt-get -y dist-upgrade
sudo apt-get upgrade[/FONT]
```

---

### Post by austinrandy0209 on 2014-02-27
If any extra info is needed about my system, I will provide. Just tell me how I can get said info cause I am new to Ubuntu. I've also noticed this doesn't just happen in Minecraft, but it happens in other games. (It just happened in Garry's Mod)

---

### Post by mörgæs on 2014-02-28
Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by austinrandy0209 on 2014-02-28
I recently switched from SNA to UXA cause I saw that it fixed it for this guy: [http://unix.stackexchange.com/questions/102315/video-freezes-on-xubuntu-13-10-with-intel-graphics](http://unix.stackexchange.com/questions/102315/video-freezes-on-xubuntu-13-10-with-intel-graphics)
I'll let you know the results as soon as I test it.
**EDIT:**
Switching from SNA to UXA did not solve the problem :(
> **mörgæs said:**
> Please run
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags. 
Here you go:
```
computer
    description: Notebook
    product: X501A1 (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=X sku=ASUS-NotebookSKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: X501A1
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: [REMOVED]
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: X501A1.211
          date: 08/20/2012
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-cache:0
          description: L2 cache
          physical id: 8
          slot: CPU Internal L2
          size: 512KiB
          capacity: 512KiB
          capabilities: internal write-through unified
     *-cache:1
          description: L1 cache
          physical id: 9
          slot: CPU Internal L1
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-through data
     *-cache:2
          description: L3 cache
          physical id: a
          slot: CPU Internal L3
          size: 2MiB
          capacity: 2MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CK0
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [REMOVED]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [REMOVED]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [REMOVED]
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU B980 @ 2.40GHz
          vendor: Intel Corp.
          physical id: c
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU B980 @ 2.40GHz
          slot: SOCKET 0
          size: 800MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave lahf_lm arat epb xsaveopt pln pts dtherm cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:40 memory:f7e00000-f7e0ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:44 memory:f7e1a000-f7e1a00f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7e18000-f7e183ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:f7e10000-f7e13fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f7d00000-f7dfffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.11.0-17-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:e000(size=4096) memory:f7c00000-f7cfffff ioport:f0000000(size=1048576)
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:41 memory:f7c00000-f7c0ffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.2
                bus info: pci@0000:03:00.2
                logical name: eth0
                version: 0a
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7e17000-f7e173ff
        *-isa
             description: ISA bridge
             product: 7 Series Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7e16000-f7e167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7e15000-f7e150ff ioport:f040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABD0
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: AX00
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=ac488b4c-0653-4108-8b8b-9bb7b94f4e39 sectorsize=4096
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: [REMOVED]
                size: 486MiB
                capacity: 486MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat
           *-volume:1
                description: EFI partition
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 244MiB
                capabilities: extended_attributes ext2 initialized
                configuration: filesystem=ext2 modified=2014-02-28 22:10:10 mount.fstype=ext2 mount.options=rw,relatime,errors=continue,user_xattr,acl state=mounted
           *-volume:2
                description: LVM Physical Volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: [REMOVED]
                size: 465GiB
                capabilities: multi lvm2


```

---

### Post by austinrandy0209 on 2014-03-01
Forgot to mention that I had this problem while using Mint, Zorin, and Linux Lite and fixed it.
This is the thread post: [http://forums.linuxmint.com/viewtopic.php?f=47&t=155201](http://forums.linuxmint.com/viewtopic.php?f=47&t=155201)
I will try using this fix and ill let you know the results as soon as possible.

**EDIT**:
Tried the fix and ended up with this at the second command:
```
E: Unable to locate package linux-generic-lts-quantal
E: Unable to locate package xserver-xorg-lts-quantal
E: Unable to locate package libgl1-mesa-glx-lts-quantal
```

---

### Post by monkeybrain20122 on 2014-03-01
Well obviously that ppa doesn't work with 13.10.

---

### Post by monkeybrain20122 on 2014-03-01
For your 13.10 you can use this ppa to upgrade your driver but do it at your own risks as it is really bleeding edge.
[https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)
Install ppa-purge just in case and if it works disable the ppa after upgrading.

Those three packages obviously have nothing to do with you, they are for 12.04 people to upgrade the graphic stacks to quantal's.

(**edited:** I use it on some intel and amd machines with  amazing results, but it is highly risky and volatile so I basically  clone the system partition everytime I do an upgrade from it, so as I  say, use at your own risks. On second thought it may not be such a  good idea if you don't know what you are doing, it may be my mistake for having brought it up)

---

### Post by austinrandy0209 on 2014-03-01
I'll try it out since I don't have any important files on this computer (important files are on my buisness computer). So I'm guessing I run the following commands to upgrade?:
```
sudo apt-add-repository ppa:oibaf/graphics-drivers
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel
```
Can you verify if this is correct? If not please give me instructions on how to install it.
Thank you!

---

### Post by monkeybrain20122 on 2014-03-01
and "sudo apt-get upgrade "

as you need to upgrade a whole bunch of other things as well.

---

### Post by austinrandy0209 on 2014-03-01
Ah, I see. Thanks for all your help and fast replies!
I'll let you know if it did anything about the problem as soon as I can.

**Edit:**
After the upgrade, everything is still working. It looks like the upgrade caused everything to load up faster. I still haven't tested if it fixed the problem, but I'll let you know as soon as possible.

---

### Post by dannyboy79 on 2014-03-01
It should've made everything run faster as that PPA has a way better driver for your GFX card. I am currently using Xubuntu 13.10 and play minecraft no problem BUT then again I am running a GTX 760 with the latest 331.38 driver

---

### Post by monkeybrain20122 on 2014-03-01
> **dannyboy79 said:**
> I am currently using Xubuntu 13.10 and play minecraft no problem BUT then again I am running a GTX 760 with the latest 331.38 driver

The latest driver is 331.49. :) [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by dannyboy79 on 2014-03-02
oh, i don't run drivers from that PPA. i only use nvidia binaries from nvidia website which i see is now at 331.49. thanks

---

### Post by monkeybrain20122 on 2014-03-03
> **dannyboy79 said:**
> oh, i don't run drivers from that PPA. i only use nvidia binaries from nvidia website which i see is now at 331.49. thanks

You are behind again, the 334.21 just came out today. :) I don't know what is the advantage to install from Nvidia except to prove that you can do that. I hate having to repeat the rather tedious process everytime I get a kernel upgrade. :)

---

