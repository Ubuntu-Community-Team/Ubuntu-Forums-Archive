---
title: "Neither Chrome nor Chromium run in  my pc"
date: 2016-01-19
forum: Desktop Environments
---

### Post by williepabon on 2016-01-19
Hi!:
I recently revived an old Compaq Presario desktop (475 MB RAM, 80 G disk) by the installation of XUbuntu 12.04 LTS (32 bit). The installation went without problems. Firefox browser worked fine (slow, though), but I needed Google Chrome. It seemed that the installation of the browser went ok, but when I run it, I get the message: "[COLOR=#333333][FONT=Ubuntu]This computer can no longer run Google Chrome because its hardware is no longer supported." Then, I installed Chromium, but again, even [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]though [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]the installation seemed to work ok,  the application didn't run.  Is there a way to make either of the browsers to work in my machine? Your help is appreciated. Thanks.
wp

[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-01-19
More RAM & a more powerful graphic adapter, I would guess.

According to this web site Chrome uses 656MB of memory and that machine only has 475MB. Firefox uses 610MB and that is why it runs slowly. And we have not yet got into the amount of system resources that web sites use with embedded images files & flash & videos.

[http://web-browsers.softwareinsider.com/l/3/Chrome](http://web-browsers.softwareinsider.com/l/3/Chrome)

Regards

---

### Post by mörgæs on 2016-01-19
While I believe the post above is correct it's always good to see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by williepabon on 2016-01-19
mörgæs

> **mörgæs said:**
> While I believe the post above is correct it's always good to see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Thanks for answering. Here is the information you requested:

```
computer
    description: Desktop Computer
    version: 0n41411RE101SALSA10
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: KM266-8235
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: AM37317
          date: 07/04/2003
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2400+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 2GHz
          capacity: 3GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up vmmcall
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
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 256MiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 256MiB
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: [REMOVED]
             slot: A2
     *-pci
          description: Host bridge
          product: VT8375 [KM266/KL266] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: VT8633 [Apollo Pro266 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:ec000000-edffffff memory:e0000000-e7ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: VT8375 [ProSavage8 KM266/KL266]
                vendor: S3 Graphics Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=32 maxlatency=255 mingnt=4
                resources: memory:ed000000-ed07ffff memory:e0000000-e7ffffff memory:ec000000-ec00ffff
        *-communication UNCLAIMED
             description: Modem
             product: SM56 Data Fax Modem
             vendor: Motorola
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=32 maxlatency=62 mingnt=1
             resources: memory:ef001000-ef001fff ioport:d000(size=256)
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 10
             serial: [REMOVED]
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
             resources: irq:18 ioport:d400(size=256) memory:ef000000-ef0000ff memory:20000000-2000ffff
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:dc00(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:e000(size=32)
        *-usb:3
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:ef002000-ef0020ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e400(size=16)
           *-disk:0
                description: ATA Disk
                product: Maxtor 4R080J0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: RAMB
                serial: [REMOVED]
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00080fff
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 75GiB
                   capacity: 75GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2016-01-14 06:47:53 filesystem=ext4 lastmountpoint=/ modified=2016-01-14 11:11:09 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2016-01-19 14:01:19 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 478MiB
                   capacity: 478MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 478MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD RW DW-Q30A
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: YYS1
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: SCSI Disk
                product: ZIP 100
                vendor: IOMEGA
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: 12.A
                capabilities: removable
                configuration: ansiversion=5
              *-medium
                   physical id: 0
                   logical name: /dev/sdb
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:22 ioport:e800(size=256)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.2.0-97-generic firmware=N/A ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg

```

Are there any other browser that can can sync with Google and may work with with the RAM limitation I have in my machine?. Thanks.
wp

---

### Post by mörgæs on 2016-01-19
Your computer has several limitations. Lack of SSE2, small memory (but you have an empty slot for adding more) and a graphics processor from S3. 

If you follow the link in my signature you will see a collection of advice. Remember that a browser is one of the heaviest applications for a normal user so test a number of them before deciding.

By the way, Xubuntu 12.04 is out of support. I suggest Lubuntu 14.04.3 or 15.10.

---

### Post by williepabon on 2016-01-19
[                                                       ]("http://ubuntuforums.org/member.php?u=939075")[B][URL="http://ubuntuforums.org/member.php?u=939075"][COLOR=#DD4814][B]mörgæs

[/B][/COLOR][/URL][/B]Yes. I think I will have to spend about 40USD to add more memory to solve the situation. Thanks.
[URL="http://ubuntuforums.org/member.php?u=939075"]
[/URL]

---

### Post by $yl9pAR%t on 2016-01-19
More RAM will not help. As mentioned above SSE2 is your problem, it depends on your CPU unit.

---

### Post by mörgæs on 2016-01-20
Browsers don't need SSE2.

Yes, more memory will help but I would take a look around and see what else is available for $40. Maybe you could get a complete (used) computer with a stronger graphics card.

---

### Post by $yl9pAR%t on 2016-01-20
If I remember right SSE2 is needed since Chrome version 35.
[URL="http://askubuntu.com/questions/584115/chromium-wont-start-on-lubuntu-14-10"]
http://askubuntu.com/questions/584115/chromium-wont-start-on-lubuntu-14-10[/URL]

---

### Post by mörgæs on 2016-01-20
That was news to me. Thanks for posting. 

I'll see if I have some old Athlon XP around for testing.

---

### Post by williepabon on 2016-01-20
> **mefisto888 said:**
> If I remember right SSE2 is needed since Chrome version 35.
[URL="http://askubuntu.com/questions/584115/chromium-wont-start-on-lubuntu-14-10"]
http://askubuntu.com/questions/584115/chromium-wont-start-on-lubuntu-14-10[/URL]

What about  if the flags on my cpu only say sse? How do I find the version of chrome that would work in my pc? Thanks for the help.
wp

---

### Post by Vladlenin5000 on 2016-01-22
There's no way around an hardware limitation and the bad news is it's gonna be even worse soon: [http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)

---

### Post by Nuno_Abreu on 2016-01-22
If you really need Chrome/Chromium, it's complicated - mostly because of your lack of RAM memory.

If you don't, you have some good lightweight alternatives that might lack in the functionality you're looking for - one example is **Midori**, available on the repositories.

---

### Post by mörgæs on 2016-01-22
I managed to dig out an even older Athlon XP (but with a faster graphics card), testing 16.04 and a number of browsers.

**Chrome**: Fails with the message 'This computer can no longer run Google Chrome because its hardware is no longer supported.' SSE2 is not mentioned but according to the links provided in this thread it's the only probable reason. At the very least Google could have revealed this in the error message.

**Chromium**: Crashes before getting to the opening screen. If started from the command line it fails with the message 'Illegal instruction (core dumped)'. No message if started from the icon.

**Midori**: Opens but crashes during browsing with the same message as above: 'Illegal instruction (core dumped)'.

**Firefox**: Everything works, but as expected it's a heavy application for such old hardware. The Reader View feature is worth trying.

**Links2**: My favourite for old hardware (and in part for new, too). Very fast and stable also for complicated web sites because it only shows text and a few pictures. Pages have another layout than in most other browsers and more scrolling is necessary. Get into the habit of using Page Up and Page Down! Maximum safety and no adds because the browser does not run scripts, in fact it offers by default the same as people try to obtain by using plug-ins in other browsers.


The errors mentioned above could be due to 16.04 being still in the making. Results might have been different in a mature release like 15.10.

---

### Post by williepabon on 2016-01-22
> **Vladlenin5000 said:**
> There's no way around an hardware limitation and the bad news is it's gonna be even worse soon: [http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)

It seems that I will have to do two things to have a usable machine: (1) Upgrade RAM. For this machine the maximum is 2Gig. And, (2) Upgrade the OS to 14.04. Still, I would need a version of Chromium 34 or less. Where can I find such?. I will post my progress. Thanks.

---

### Post by $yl9pAR%t on 2016-01-22
Crazy idea, but perhaps you can do fresh install of Xubuntu 12.04 and before any update install chromium browser.
I am still not sure if it was 34 or 35 last working version of Chrome/Chomium, but if it was 34, you can install Lubuntu/Xubuntu 14.04.01.

---

### Post by mörgæs on 2016-01-22
Don't install unsupported software, especially not a browser. It's a security breach.

---

### Post by Nuno_Abreu on 2016-01-23
It could be a 16.04 bug, but I suspect it is from the hardware itself.

Another option could be **Qupzilla **- it's not as featured as some mentioned here, but it serves its purpose.

---

### Post by williepabon on 2016-01-24
Someone taught me how to install Chromium version34 on the pc and it works nicely. See the the instruction [here]("https://answers.launchpad.net/ubuntu/+question/283108"). Will wait and see about any security breach.

---

