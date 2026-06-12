---
title: "Laptop for light gaming on linux"
date: 2013-12-09
forum: Gaming &amp; Leisure
---

### Post by shinkaide on 2013-12-09
Hi, I was wondering if I could get some advice from folks who know better than I do: what are some good basic hardware specs I should look for in a light gaming laptop? I've been trying to read up as a much as I can on NVIDIA, AMD, and the new Intel HD 4400's the past couple of weeks, but I feel like I still don't know enough to make a good decision. I've been searching on Google a lot, but I've decided I could maybe go ahead and ask around forums.

I plan to use this new laptop mostly for work (mostly office work, then maybe some light video editing), then definitely some light gaming - e.g., some platformers like Fez, maybe light 3D gaming, heaviest might be Portal and some such (nothing like Crysis and the like).

I'm really interested in the Intel HD 4400 because of the recent post on Phoronix showing some really nice results. But then I look at the specs of one of the laptops I'm looking at - it's got 128MB dedicated video memory - and then I look at some of the basic requirements of the Steam games I'm looking at - 256MB video memory. 

[LIST=1]
[*]Does it mean that if the game requires more than what dedicated video memory I have, the excess load will necessitate the use of RAM? 
[*]If it does, will my using an Intel HD4400 not be a problem, if say, I have at least 4GB RAM? Will I still get smooth performance?
[*]What other things should I consider if I plan to also record gameplay?
[/LIST]

Thanks in advance.

---

### Post by DanglingPointer on 2013-12-09
If you can wait 2-4 months wait for the best Kaveri-based laptops.  Most future AAA games running on the new next-gen consoles will be automatically optimised for Kaveri based laptops due to Mantle-pc porting.
That said, it will only mature for Linux perhaps by the second half of next year (accelerated by SteamOs and SteamMachines).
Caveat is that all of this is based on press material from EA-DICE and AMD.  Nothing is proven yet but it looks promising.

If you can't wait and need to get a laptop now, a Dell XPS 13 Sputnik 3 could probably play many lite games.  I have no experience with those laptops though.

As for your questions...


[LIST=1]
[*]Does it mean that if the game requires more than what dedicated video memory I have, the excess load will necessitate the use of RAM?
[*]If it does, will my using an Intel HD4400 not be a problem, if say, I have at least 4GB RAM? Will I still get smooth performance?
[*]What other things should I consider if I plan to also record gameplay?
[/LIST]


1a) For current gen cpus with iGPU, YES (all Intel and all AMD). For Kaveri with HSA and Mantle in action, NO it is more like a console; according to the AMD and DICE press material, there is NO dedicated memory allocated to the iGPU; there is only the ONE pool with NO delineation. Memory is allocated to whatever when required.  Similar to XBOX 360's, PS4's, and XBONE's use of memory.  It is a lot more streamlined and nothing is wasted.  Wasted by not being used, which tends to happen when a portion of RAM is dedicated to an iGPU.  If the iGPU has lets say used 128MB and you have allocated 256MB, then the remainder is wasted and can't be used by the system for other things.

2a) I am not sure to be honest however based on what I have come across in the literature from the net; when memory is dedicated to the iGPU and the v-memory is used up; it has to go through switching with the system RAM.  This switching has an algorithm-overhead.  So there will be a performance penalty I would assume.  But whether it is discernible, I do not know.

3a) Perhaps don't play on a laptop and wait for a SteamMachine or use a portable low-profile desktop running a micro-ITX system with a dGPU.  :D

---

### Post by Ranko Kohime on 2013-12-09
Portal runs decently on HD3000, so should run better on HD4000+.  (No 60fps here, but 24+ (which is playable for Portal) is pretty much guaranteed throughout most of the game, with 30 being attainable in some portions of the maps)

Graphics memory isn't really an issue, but DanglingPointer covered that.

But 4GB isn't really enough*, trust me.  I can run out with 16.  :lolflag:

*Only true if you use Google Chrome or Chromium, with >50 tabs, or more than 5 virtual machines at once

---

### Post by papibe on 2013-12-09
Hi shinkaide.

I'd recommend taking a look at this video review: [System76 Kudu Professional and Galago UltraPro Review]("http://www.jupiterbroadcasting.com/47712/system76-laptop-special-las-s29e10/").

I almost sure the review even includes some gaming.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by shinkaide on 2013-12-09
Thanks for the reply, DanglingPointer - I learned a lot from just that one post!

Also, I've looked up Kaveri/HSA, and man does that sound good, but it might take too long to get to my part of the world. I originally wanted to buy a laptop a few months ago, but decided to wait for Haswell since I'd been reading so many good things about it - primarily, massive improvements in battery life, and bumped-up graphics performance on Linux for the HD4000+ series (via [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=intel_haswell_hd4400&num=1")). That's always the way: something cool is released in the US, then it takes four or more months to get to my country. That sort of wait is agonizing for me! Kaveri looks to be released this January; then I'd wait for testers to review, then I'd wait for it to get here (you can see my predicament, eh? :-? ). Right now I'm kind of looking at haswell-based laptops as a nice middle ground for casual gamers like me (but of course I'm here because I want to learn more. :) ). 

This is [the laptop I'm looking at]("http://www.villman.com/Product-Detail/Acer_v5-473P-34014G50A") getting at the moment, BTW (gonna be dual-booting it). From what I've learned from your post, I'm thinking maybe if I up the RAM to 8GB, it could pretty much run reasonably well, say maybe even games that require 1GB VRAM (although I don't think I'd be playing a lot of those). (By comparison, there's similar model that's got an i5 and a discrete GT620, but it's got three hours less battery life). 

Some other notebooks I was considering were some laptops that had the surprisingly affordable AMD E-2000s, or even the A6/A8/A10s. I know that they're significantly less powerful CPUs than the current gen-Intel ones, but they've got enticingly good battery life, plus I've heard a lot of positives about the AMD APUs. I'd do the the same thing as the above - jack up the RAM to 8GB.

---

### Post by shinkaide on 2013-12-09
> **Ranko Kohime said:**
> Portal runs decently on HD3000, so should run better on HD4000+.  (No 60fps here, but 24+ (which is playable for Portal) is pretty much guaranteed throughout most of the game, with 30 being attainable in some portions of the maps)

Graphics memory isn't really an issue, but DanglingPointer covered that.

But 4GB isn't really enough*, trust me.  I can run out with 16.  :lolflag:

*Only true if you use Google Chrome or Chromium, with >50 tabs, or more than 5 virtual machines at once

Yeah, I'd been seeing a few forum posts to that effect. This kind of pushes me a bit more toward the HD4400 option versus the discrete video card one. Chrome with 50 tabs? however do you get any work done? :D

---

### Post by Ranko Kohime on 2013-12-10
Work, what is that?  :D

---

### Post by shinkaide on 2013-12-10
Papibe, I just finished watching that entire episode, and man, I am convinced - I think I'm going for the lappy with the HD4400. I'm certainly not going to be playing anything that would seriously tax that GFX setup anyway, and I definitely would love to have that much longer battery life for work purposes.

Everyone, thanks a lot for chipping in your 2 cents and helping a guy out! :D

---

### Post by Arthur_D on 2013-12-11
HD4400 is definitely good enough for light 3D gaming - maybe not every option maxed out but the most important stuff like anti-aliasing should work acceptably. Good choice.

---

### Post by jaime3 on 2013-12-16
> **shinkaide said:**
> Hi, I was wondering if I could get some advice from folks who know better than I do: what are some good basic hardware specs I should look for in a light gaming laptop? I've been trying to read up as a much as I can on NVIDIA, AMD, and the new Intel HD 4400's the past couple of weeks, but I feel like I still don't know enough to make a good decision. I've been searching on Google a lot, but I've decided I could maybe go ahead and ask around forums.

I plan to use this new laptop mostly for work (mostly office work, then maybe some light video editing), then definitely some light gaming - e.g., some platformers like Fez, maybe light 3D gaming, heaviest might be Portal and some such (nothing like Crysis and the like).

I'm really interested in the Intel HD 4400 because of the recent post on Phoronix showing some really nice results. But then I look at the specs of one of the laptops I'm looking at - it's got 128MB dedicated video memory - and then I look at some of the basic requirements of the Steam games I'm looking at - 256MB video memory. 

[LIST=1]
[*]Does it mean that if the game requires more than what dedicated video memory I have, the excess load will necessitate the use of RAM?
[*]If it does, will my using an Intel HD4400 not be a problem, if say, I have at least 4GB RAM? Will I still get smooth performance?
[*]What other things should I consider if I plan to also record gameplay?
[/LIST]

Thanks in advance.

Can you afford a HP Envy DV7t-7200? 
[LIST]
[*][COLOR=#333333]Windows 8 64[/COLOR]
[*][COLOR=#333333]3rd generation Intel Core i7-3630QM Processor (2.4GHz, 6MB L3 Cache)[/COLOR]
[*][COLOR=#333333]NVIDIA(R) GeForce(R) GT 630M Graphics with 2GB of dedicated video memory[/COLOR]
[*][COLOR=#333333]8GB DDR3 System Memory (2 Dimm) ,1tb 5400 rpm HDD,6 Cell Lithium Ion Battery[/COLOR]
[*][COLOR=#333333]17.3-inch diagonal HD BrightView LED-backlit Display (1600 x 900) ,Blu-ray player & SuperMulti DVD burner ,HP TrueVision HD Webcam with integrated dual array digital microphone [/COLOR]
[/LIST]
[COLOR=#333333][FONT=Verdana]
Anyway's mine i[/FONT][/COLOR][COLOR=#333333]mine is a bit different version but very simular but with 1920- 1080 matt display.  Nvidia Geforce GT 630 m 
[/COLOR][COLOR=#333333][FONT=Verdana]2gb and has a Intel 4000 hd? [/FONT][/COLOR][COLOR=#333333]Has finger scanner, 4 speaker with 1 sub woofer. 750 gb storage. What I done to mine is 
[/COLOR][COLOR=#333333][FONT=Verdana]I added a hp (PNY) 120gb ssd on first bay and second of course the hdd that came with. I have installed Window 8 on the
SSD and its super fast but Ubuntu 12.04 is working really good. Gaming on this machine is super. But this laptop is a 1,000-
2,000 dollar laptop. I bought mine as refurbish and gotten a 60 day or 90 days warranty from hp. I paid less then 700 dollars in ebay. I was going to get a laptop with the Intel vid you mention from System 76 oh wait i think it was a 4200 but i back off because was going to cost me over 1,000 with california tax. I made a smart move. I wouldn't bother running less then 8gb of ram. Some games love ram and having extra for reserve is great. Recording I dunno I do use fraps in Windows. I never own a great laptop that is super fast in Linux and play so well in games and look so great especially comes with bluray. If I want I can upgrade to 16gb of ram and run two ssd in raid 0. Woah. Did I mention it sound sooo good with 4.1 speakers? But Nvidia has better support and much powerful graphics. I'll pick Nvidia over ATI and Intel. 



[/FONT][/COLOR]jaime@HP-ENVY-dv7-Notebook-PC:~$ sudo lshw
[sudo] password for jaime: 
hp-envy-dv7-notebook-pc   
    description: Notebook
    product: HP ENVY dv7 Notebook PC (B6B75AAR#ABA)
    vendor: Hewlett-Packard
    version: 088A110000305920000620100
    serial: 4CB2521169
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=ENV frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=B6B75AAR#ABA uuid=4C055121-C11F-11E2-8B90-4FA66BF23A85
  *-core
       description: Motherboard
       product: 181D
       vendor: Hewlett-Packard
       physical id: 0
       version: 52.24
       serial: PCUUD3C2F3R22S
       slot: Type2 - Board Chassis Location
     *-memory
          description: System Memory
          physical id: 0
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: AM1U16BC4P2-B19H
             vendor: A-DATA Technology
             physical id: 0
             serial: 000050AC
             slot: Bottom-Slot 1(top)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: AM1U16BC4P2-B19H
             vendor: A-DATA Technology
             physical id: 1
             serial: 00005052
             slot: Bottom-Slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: c
          version: F.28
          date: 07/25/2013
          size: 128KiB
          capacity: 4544KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 39
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2401MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 3b
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 3c
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 3d
             slot: L3 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: 3a
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:d2000000-d3ffffff ioport:a0000000(size=536870912)
           *-display
                description: VGA compatible controller
                product: GF108M [GeForce GT 630M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:d4000000-d43fffff memory:c0000000-cfffffff ioport:5000(size=64)
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
             resources: irq:41 memory:d4600000-d460ffff
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
             configuration: driver=mei latency=0
             resources: irq:48 memory:d4614000-d461400f
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
             resources: irq:16 memory:d4619000-d46193ff
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
             resources: irq:45 memory:d4610000-d4613fff
        *-pci:1
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
             resources: irq:17
        *-pci:2
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
             resources: irq:16 ioport:3000(size=4096) memory:d1000000-d1ffffff ioport:d0000000(size=16777216)
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:42 memory:d1000000-d1000fff
        *-pci:3
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
             resources: irq:19 memory:d4500000-d45fffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 2230
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: wlan0
                version: c4
                serial: 84:a6:c8:ff:04:47
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-34-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:46 memory:d4500000-d4501fff
        *-pci:4
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:d4400000-d44fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: eth0
                version: 07
                serial: a0:b3:cc:4c:b1:1e
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.108 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:43 ioport:2000(size=256) memory:d4404000-d4404fff memory:d4400000-d4403fff
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
             resources: irq:23 memory:d4618000-d46183ff
        *-isa
             description: ISA bridge
             product: HM77 Express Chipset LPC Controller
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
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:5088(size=8) ioport:5094(size=4) ioport:5080(size=8) ioport:5090(size=4) ioport:5060(size=32) memory:d4617000-d46177ff
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
             resources: memory:d4615000-d46150ff ioport:5040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: hp ssd v300a
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 505A
             serial: HP313130000158180509
             size: 111GiB (120GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=b10a0546-6a40-47b0-84e9-ff56a2904eda
           *-volume:0
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: b6e5-cae9
                size: 93MiB
                capacity: 93MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: c9f511f7-2804-44d9-83cf-3f3ae1669863
                size: 103GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-12-14 07:38:22 filesystem=ext4 lastmountpoint=/ modified=2013-12-15 08:45:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-12-16 03:35:45 state=mounted
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 88c1b910-ab54-4a46-a9c4-a8022fefa1f6
                size: 8079MiB
                capacity: 8080MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST750LM022 HN-M7
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 2AR1
             serial: S2SUJ9BCB13858
             size: 698GiB (750GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=7124b9d3-c1a5-479e-b190-f47613352e95
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: 42787486-a1e6-904f-a2e9-2325f535452d
                size: 606GiB
                capacity: 606GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2013-09-27 19:03:20 filesystem=ntfs label=HP Backup modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: 2ca7-95bb
                size: 285MiB
                capacity: 299MiB
                capabilities: precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2013-12-14 03:57:25 filesystem=ntfs label=Recovery modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sdb3
                version: FAT32
                serial: 68a9-b7be
                size: 70MiB
                capacity: 99MiB
                capabilities: boot precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat name=EFI system partition
           *-volume:3
                description: Windows reserved partition
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sdb4
                serial: d2abbd4c-650d-493e-a205-82a950ce1a7a
                capacity: 127MiB
                capabilities: nofs precious readonly hidden nomount
                configuration: name=Microsoft reserved partition
           *-volume:4
                description: Windows NTFS volume
                physical id: 5
                bus info: scsi@2:0.0.0,5
                logical name: /dev/sdb5
                version: 3.1
                serial: 065ba5ae-04ea-1f45-871a-07057c46acf4
                size: 91GiB
                capacity: 91GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2013-12-14 03:57:48 filesystem=ntfs name=Basic data partition state=clean
     *-scsi:2
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD CMB UJ160
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: MO06062
       vendor: Conexant (Rockwell)
       physical id: 1
       slot: Primary
       capacity: 61993mWh
       configuration: voltage=11.1V
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 2
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
jaime@HP-ENVY-dv7-Notebook-PC:~$

---

### Post by jaime3 on 2013-12-16
Oh Forgot the link. [http://www.amazon.com/HP-ENVY-dv7t-7200-Edition-Notebook/dp/B009XCXCTM](http://www.amazon.com/HP-ENVY-dv7t-7200-Edition-Notebook/dp/B009XCXCTM)

---

### Post by mips on 2013-12-18
> **shinkaide said:**
> Papibe, I just finished watching that entire episode, and man, I am convinced - I think I'm going for the lappy with the HD4400.

You are comparing apples with oranges, the laptop ([14.1" Galago UltraPro]("https://www.system76.com/laptops/model/galu1")) they demoed in that review does not use the HD4400, it uses a Intel Iris Pro Graphics 5200 with dedicated 128 MB eDRAM.

The Iris Pro has has about 2x better performance than the HD4400, They are also used in the new macbooks for example.

[http://www.anandtech.com/show/6993/](http://www.anandtech.com/show/6993/)
[http://www.macrumors.com/2013/10/25/intels-iris-graphics-boost-13-inch-retina-macbook-pro-gpu-performance-by-50-or-more/](http://www.macrumors.com/2013/10/25/intels-iris-graphics-boost-13-inch-retina-macbook-pro-gpu-performance-by-50-or-more/)
[http://news.cnet.com/8301-13579_3-57609045-37/dissecting-intels-top-graphics-in-apples-15-inch-macbook-pro/](http://news.cnet.com/8301-13579_3-57609045-37/dissecting-intels-top-graphics-in-apples-15-inch-macbook-pro/)
[http://en.wikipedia.org/wiki/Intel_HD_Graphics#History](http://en.wikipedia.org/wiki/Intel_HD_Graphics#History)
[http://www.intel.com/content/www/us/en/architecture-and-technology/hd-graphics/hd-graphics-developer.html](http://www.intel.com/content/www/us/en/architecture-and-technology/hd-graphics/hd-graphics-developer.html)

So if you are gonna get a HD4400 based laptop then expect at least half the performance you saw in that video.

---

### Post by jaime3 on 2013-12-19
> **mips said:**
> You are comparing apples with oranges, the laptop ([14.1" Galago UltraPro]("https://www.system76.com/laptops/model/galu1")) they demoed in that review does not use the HD4400, it uses a Intel Iris Pro Graphics 5200 with dedicated 128 MB eDRAM.

The Iris Pro has has about 2x better performance than the HD4400, They are also used in the new macbooks for example.

[http://www.anandtech.com/show/6993/](http://www.anandtech.com/show/6993/)
[http://www.macrumors.com/2013/10/25/intels-iris-graphics-boost-13-inch-retina-macbook-pro-gpu-performance-by-50-or-more/](http://www.macrumors.com/2013/10/25/intels-iris-graphics-boost-13-inch-retina-macbook-pro-gpu-performance-by-50-or-more/)
[http://news.cnet.com/8301-13579_3-57609045-37/dissecting-intels-top-graphics-in-apples-15-inch-macbook-pro/](http://news.cnet.com/8301-13579_3-57609045-37/dissecting-intels-top-graphics-in-apples-15-inch-macbook-pro/)
[http://en.wikipedia.org/wiki/Intel_HD_Graphics#History](http://en.wikipedia.org/wiki/Intel_HD_Graphics#History)
[http://www.intel.com/content/www/us/en/architecture-and-technology/hd-graphics/hd-graphics-developer.html](http://www.intel.com/content/www/us/en/architecture-and-technology/hd-graphics/hd-graphics-developer.html)

So if you are gonna get a HD4400 based laptop then expect at least half the performance you saw in that video.


But what so special anyway's with Intel compare to Nvidia and ATI? Wouldn't people reather have a Nvidia with Linux since it's more supportive then ATI and Intel? 128 mb eDRAM for a IGP is very low for dedicated and most other intel uses ram for
IGP yuck.

---

