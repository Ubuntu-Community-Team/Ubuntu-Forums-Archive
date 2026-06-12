---
title: "HoN wont run"
date: 2009-10-25
forum: Gaming &amp; Leisure
---

### Post by m0sh on 2009-10-25
Hey everyone.. I went ahead and installed Heroes of Newerth but am having some trouble.  I did go around searching but was unable to find anything relating to my question so I'm hoping someone here will be able to help me.

Heres what I did...

I installed the linux version of HoN from the HoN website then right clicked on the .sh file and set the execute permission to allow it to do so.  I then clicked the file and ran through the installer and everything went smooth.  I installed the folder to my home directory (it wsa the default location so I thought that I would just leave it there).  I now have a folder in the directory with all the HoN files which you can see here...

[IMG]http://img7.imageshack.us/img7/2264/heroesofnewerth.png[/IMG]

Judging by the files I think I did everything right so far.. now heres my problem.  I go to click on the "hon-x86" file and my screen flickers black for about half a second but nothing happens.  Iv tried reinstalling it but I still get the same problem.. has anyone had experience with this.  Im still really new to Ubuntu so any suggestions would be awesome.  Thanks guys - doug

---

### Post by edin9 on 2009-10-25
> **m0sh said:**
> Hey everyone.. I went ahead and installed Heroes of Newerth but am having some trouble.  I did go around searching but was unable to find anything relating to my question so I'm hoping someone here will be able to help me.

Heres what I did...

I installed the linux version of HoN from the HoN website then right clicked on the .sh file and set the execute permission to allow it to do so.  I then clicked the file and ran through the installer and everything went smooth.  I installed the folder to my home directory (it wsa the default location so I thought that I would just leave it there).  I now have a folder in the directory with all the HoN files which you can see here...

[IMG]http://img7.imageshack.us/img7/2264/heroesofnewerth.png[/IMG]

Judging by the files I think I did everything right so far.. now heres my problem.  I go to click on the &quot;hon-x86&quot; file and my screen flickers black for about half a second but nothing happens.  Iv tried reinstalling it but I still get the same problem.. has anyone had experience with this.  Im still really new to Ubuntu so any suggestions would be awesome.  Thanks guys - doug

What graphics card/chip do you have?

---

### Post by m0sh on 2009-10-25
> *-cpu
          product: AMD Sempron(tm)   2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up


|-------- MSG to Short --------|

---

### Post by edin9 on 2009-10-25
> **m0sh said:**
> |-------- MSG to Short --------|

Huh? Copy and paste this into Terminal. ```
lspci -v
``` And copy and paste the result back here.

---

### Post by m0sh on 2009-10-25
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 8118
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at e0000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: e8000000-e9ffffff
    Prefetchable memory behind bridge: e4000000-e7ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Belkin Device 7000
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at ea000000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
    Subsystem: Agere Systems Device 044c
    Flags: bus master, medium devsel, latency 32, IRQ 255
    Memory at ea002000 (32-bit, non-prefetchable) [size=256]
    I/O ports at a000 [size=8]
    I/O ports at a400 [size=256]
    Capabilities: <access denied>

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 808a
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at ea003000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at a800 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 20
    I/O ports at ac00 [size=8]
    I/O ports at b000 [size=4]
    I/O ports at b400 [size=8]
    I/O ports at b800 [size=4]
    I/O ports at bc00 [size=16]
    I/O ports at c000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 20
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at c400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at c800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at cc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at ea004000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Subsystem: ASUSTeK Computer Inc. Device 810a
    Flags: medium devsel, IRQ 22
    I/O ports at d800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
    Flags: medium devsel, IRQ 22
    I/O ports at dc00 [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-via82xx-modem

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
    Subsystem: ASUSTeK Computer Inc. Device 80ff
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at e000 [size=256]
    Memory at ea005000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8118
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at e4000000 (32-bit, prefetchable) [size=64M]
    Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at e9000000 [disabled] [size=64K]
    Capabilities: <access denied>

---

### Post by edin9 on 2009-10-25
> **m0sh said:**
> 00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 8118
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at e0000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: e8000000-e9ffffff
    Prefetchable memory behind bridge: e4000000-e7ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Belkin Device 7000
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at ea000000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
    Subsystem: Agere Systems Device 044c
    Flags: bus master, medium devsel, latency 32, IRQ 255
    Memory at ea002000 (32-bit, non-prefetchable) [size=256]
    I/O ports at a000 [size=8]
    I/O ports at a400 [size=256]
    Capabilities: <access denied>

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 808a
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at ea003000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at a800 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 20
    I/O ports at ac00 [size=8]
    I/O ports at b000 [size=4]
    I/O ports at b400 [size=8]
    I/O ports at b800 [size=4]
    I/O ports at bc00 [size=16]
    I/O ports at c000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 20
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at c400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at c800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at cc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at ea004000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Subsystem: ASUSTeK Computer Inc. Device 810a
    Flags: medium devsel, IRQ 22
    I/O ports at d800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
    Flags: medium devsel, IRQ 22
    I/O ports at dc00 [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-via82xx-modem

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
    Subsystem: ASUSTeK Computer Inc. Device 80ff
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at e000 [size=256]
    Memory at ea005000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8118
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at e4000000 (32-bit, prefetchable) [size=64M]
    Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at e9000000 [disabled] [size=64K]
    Capabilities: <access denied>

Oh a VIA GPU? I don't know if theres a 3D driver for that in Linux.

---

### Post by edin9 on 2009-10-25
wHICH VERSION OF uBUNTU ARE YOU USING?

---

### Post by Sindwiller on 2009-10-25
Can you do

```
cd ~/HoN
./hon-x86
```

and paste what kind of output it gives out? Preferably into code tags, eg. 
[HTML]```
stuff comes in here
```[/HTML]

---

### Post by m0sh on 2009-10-25
Thanks for trying to help guys... here was the output of that

[html]
doug@UbuntuNET:~$ cd ~/HoN
doug@UbuntuNET:~/HoN$ ./hon-x86
warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: OpenGL 2.0 not available.
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  136 (XFree86-DRI)
  Minor opcode of failed request:  9 ()
  Resource id in failed request:  0x3600008
  Serial number of failed request:  101
  Current serial number in output stream:  101
doug@UbuntuNET:~/HoN$ 
[/html]

---

### Post by joeelmex on 2009-10-25
Dude Im going to be honest with you, you have a build in video card not made to play 3d games.  You could get away with 2d games but unfortunately this card is not to task.  In top of that I really have never seen a stable 3d drivers for a via video card.  

Even if you install windows and get the drivers that where made for that video card, HoN would run very choppy and unplayable if it even loads.  (Might give you this card does not mininum specs)

---

### Post by m0sh on 2009-10-25
> **joeelmex said:**
> Dude Im going to be honest with you, you have a build in video card not made to play 3d games.  You could get away with 2d games but unfortunately this card is not to task.  In top of that I really have never seen a stable 3d drivers for a via video card.  

Even if you install windows and get the drivers that where made for that video card, HoN would run very choppy and unplayable if it even loads.  (Might give you this card does not mininum specs)

Thanks for the reply... yeah im running on a 2002 compaq.  Im just not ready to fully install Ubuntu on the iMac yet.  If I went and got a new video card.. is there one around say $100 that would be worth getting?  I know this might be a very bad question but I grew up with Mac's and used them until I got this old Compaq and installed Ubuntu on it about 3 months ago so I don't really know much about PC's.

---

### Post by Vadi on 2009-10-25
The card might not fit into the computer if it's that old.

And yes, HoN is quite video-card demanding, that card definitely won't go :)

---

### Post by joeelmex on 2009-10-25
To be honest with you, 100 dollars wont get you much because your dealing with such an old chipset.  I would save up some money and get a better computer.  You can take a look at system76.com and those are pre-made pc with ubuntu all-ready installed.  Dell also sells some pc's with ubuntu but they are using an older version of ubuntu.  You can always build yourself something but with what you said as still learning your way it might not be the best choice.  I will not put no money on the compaq.

---

### Post by edin9 on 2009-10-25
To add to these other guys comments, if you do buy a new PC, make sure it has a nVIDIA graphics card. I would personally recommend a GeForce 9600 GT. It is pretty cheap and has good performance for the price.

---

### Post by m0sh on 2009-10-26
Thanks for all the input guys.. yeah this machine is pretty rough right now.  I think I'm going to do some research and work on putting together a new comp but it will take me a while as like I said iv always been a mac user and PC's are pretty new to me.  Thanks again guys.

---

