---
title: "Minecraft Black Screen of Death"
date: 2013-07-12
forum: Gaming &amp; Leisure
---

### Post by LordFran on 2013-07-12
I use Linux Ubuntu 12.04 LTS, and I am having trouble getting minecraft to run properly. I have Open Jdk Java 6, and since that didnt work I got Oracle Java 7, then Oracle Java 6 too. I updated the LWGJL to the newest version 2.9.0 and replaced the files I needed to and then I ran minecraft and it still didn't work. Here is my graphics card information:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, fast devsel, latency 0
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: [e4] Vendor Specific Information: Len=06 <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Dell Dimension 3000
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ed98 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [d0] Power Management version 1
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
    Flags: fast devsel
    Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-feafffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: medium devsel, IRQ 3
    I/O ports at eda0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ee00 [size=256]
    I/O ports at edc0 [size=64]
    Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
    Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_intel8x0
    Kernel modules: snd-intel8x0

01:00.0 Ethernet controller: D-Link System Inc Gigabit Ethernet Adapter (rev 11)
    Subsystem: D-Link System Inc DGE-530T Gigabit Ethernet Adapter
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
    Memory at fe9ec000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at de00 [size=256]
    Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Vital Product Data
    Kernel driver in use: skge
    Kernel modules: skge

01:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Dimension 3000
    Flags: bus master, medium devsel, latency 64, IRQ 9
    Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at ddb8 [size=8]
    Capabilities: [40] Power Management version 2

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
    Subsystem: Dell Dimension 3000
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at fe9eb000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ddc0 [size=64]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: e100
    Kernel modules: e100
```

I have a pretty old computer and am not sure if the driver is outdated, and if it is, where can I find a new one?

Please help

-Fran

---

### Post by LordFran on 2013-07-12
Please help

---

### Post by Hexxus on 2013-07-12
K, it looks like you're running the integrated intel video chipset on that rig. I'm not sure how to specifically update that but you could do:

```
sudo apt-get update && sudo apt-get upgrade 
```

That will have your computer check for updates, then install them. 

On my work computer (its graphics card sucks) I had MC a few times on 12.04LTS go black, so I opened it in a smaller window and let it sit and render then it worked fine. But for some reason changing the 
window size right away caused the black screen.

Hope this helps!

---

### Post by regor210 on 2013-07-12
This looks like a video driver issue.

Test 

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one at a time minus $. And post what you get.

$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

Now run

$ lspci -vmk | grep -A 8 -B 2 VGA && lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

Were looking for something like this at the end

direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 210/PCIe/SSE2
OpenGL version string: 3.3.0 NVIDIA 310.44
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:

If you fail like I think you will 
**direct rendering: No**

I would suggest a new install of Lubuntu.

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

I recommend Lubuntu over Ubuntu as my Dell Dimension 3000 will not run Ubuntu 13.04 out of the box. I think the hardware is just too old. And Lubuntu will fit on a CD rom plus it uses fewer resources ie will likely run faster.

I went over this video driver issue in this thread.

[http://ubuntuforums.org/showthread.php?t=2149317](http://ubuntuforums.org/showthread.php?t=2149317)

---

### Post by LordFran on 2013-07-12
Thanks ill try it as soon as i get home

---

### Post by LordFran on 2013-07-12
BTW, I tried upgrading to 12.10 but it glitched, and I wanted to dual-boot, but Windows XP needed a recovery disc i did not have

---

### Post by regor210 on 2013-07-12
I would look at the Dell website 1st to recover XP.


[http://search.euro.dell.com/results.aspx?smh=sup&c=uk&l=en&s=biz&cat=sup&k=recovery%20disk](http://search.euro.dell.com/results.aspx?smh=sup&c=uk&l=en&s=biz&cat=sup&k=recovery%20disk)


[http://www.dell.com/support/troubleshooting/uk/en/ukbsdt1/Servicetag/htcc971?s=BIZ](http://www.dell.com/support/troubleshooting/uk/en/ukbsdt1/Servicetag/htcc971?s=BIZ)

Fix XP first then install Lubuntu 13.04 by  replacing Ubuntu 12.04, this way grub ( the menu that lets you choose what you would like to run Windows/Lubuntu) will be installed as fixing XP will likely Brake Grub making your system boot into XP only.  Installing Lubuntu 13.04  after fixing XP will reinstall Grub.

---

### Post by soloman469 on 2013-07-14
First of all, Intel Integrated Graphics is horrible. I say that because I used to have an Integrated Graphics card myself. You should invest on getting a new video card, since it can greatly increase gaming performance.

Or you could get a new rig period, if that's the case...

---

### Post by LordFran on 2013-07-18
> **soloman469 said:**
> First of all, Intel Integrated Graphics is horrible. I say that because I used to have an Integrated Graphics card myself. You should invest on getting a new video card, since it can greatly increase gaming performance.

Or you could get a new rig period, if that's the case...

I can't afford one right now is there any update for my video card that'll at least LET me PLAY minecraft?

---

### Post by regor210 on 2013-07-18
Hey there LordFran,  a video card update wouldn't be of much use on a  Dell Dimension 3000 as you only have 3 pci expansion slots. Using a pci bus will only give you x1 speed thats what you have now. Apg is x8 and pci-e is x16 but a  Dell Dimension 3000 is and old office computer so they didn't put them in it.

As for a video driver update I went over the options in this thread

[http://ubuntuforums.org/showthread.php?t=2149317&page=2](http://ubuntuforums.org/showthread.php?t=2149317&page=2)

----------------------------------------------------------------------
&#8220;I was looking over the bug report and it looks like your 3D problem is fixed in Ubuntu 13.04.

I looked into updating your Mesa video drivers but to get the newer mesa 9.2 driver you would need a 3.6 or newer kernel. The kernel is paired to the software in the redepositors so upgrading to a newer kernel is likely to to fix one problem but make more problems with other things.

So if you can get Lubuntu 13.04 up and running on a live cd/usb and run 

$ glxinfo 
------------------------------------------------------------------------
So its like this. The kernel is the heart of the operating system. Get a newer  kernel to get the latest video drivers.   Lubuntu 13.04 has a newer  kernel and video driver than Ubuntu 12.04. I know the drivers in  Lubuntu 13.04 work because I have a  Dell Dimension 3000 sitting on the counter next to me and I tried it and it works.
--------------------------------------------------
user@user-Dimension-3000:~$ lspci -vmk | grep -A 8 -B 2 VGA && lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'

Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	82865G Integrated Graphics Controller
SVendor:	Dell
SDevice:	Dimension 3000
Rev:	02
Driver:	i915

Device:	00:06.0
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
direct rendering: Yes
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 865G x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 9.1.3
OpenGL extensions:
---------------------------------------------------------

Here is where you find Lubuntu 13.04
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by LordFran on 2013-07-19
Thank you! It works!

---

