---
title: "Dell XPS Studio 7100"
date: 2010-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cool_penguin on 2010-10-06
Hi everybody,

I have been using Ubuntu for the past four years and this is the first time, I am really running into trouble. I recently got myself a Dell XPS Studio 7100 desktop computer at work. As usual it came with Windows 7, which I wiped clean and installed 64 bit Ubuntu 10.04. This system has an AMD Athlon II Quad core processor, ATI Graphics, 6 GB RAM and a 500 GB HDD (7200 rpm). These specs are very good and should run Ubuntu very well. While it does work well most times, I often find my computer freezing randomly. Sometimes, it freezes and I am unable to move the mouse or do anything on the keyboard and sometimes it freezes suddenly with a dark black screen. The only option I am left with is to hard boot the system using the power button. Every time I do that I hear the hard drive make a click sound and I am really worried that I am damaging the hard drive. Any help from you guys will be greatly appreciated. 

Thanks very much for reading my post. 

I am looking forward to hearing from you.

Have a nice day.

Cheers,
Harry

---

### Post by jwaclawsky on 2010-10-06
I just bought a Dell desktop (StudioXPS 7100) with AMD Phenom™ II X4 + ATI Radeon HD 5770 1GB  a month ago and wiped the hard drive and installed Ubuntu 10.04 I have been running fine. 

You might want to reinstall Ubuntu 10.04 (or an earlier version as a test 9.10) and get all the updates through the update manager and see if the problem persists. If it does my "guess" is you may have a hardware problem. I am out of town at the moment and not near my machine but I believe I there is access to some hardware diagnostics ...during boot-up, in Bios maybe??? Sorry I can't help more because I am away from my machine and I didn't have a need to play with the hardware or have any freezing problems.

---

### Post by boondocks on 2011-04-27
I have the same problem on the Dell Studio XPS 7100.
It came with Windows 7 installed.
It was wiped clean and 64 bit Ubuntu 10.04 was installed.

Every few days, the system just freezes.
I have to hit the power button to turn if off and then power it back on.

I have turned off the screensaver.  It did not make any difference.
I booted the system with a SystemRescueCd and ran MemTest on several occasions.
Each time for more than 12 hours. No memory errors.

Is there any way to find out what is causing this random freezing?

Here are the hardware details, as per the brochure:

```
Processor & Memory:
*   Studio AMD Phenom II X6 1035T Processor at 2.6GHz
*   16GB DDR3 SDRAM at 1333MHz (4 x 4GB)

Drives:
*   1.5TB 7200RPM SATA II Hard Drive
*   16X DVD±RW Drive

Graphics & Video:
*   Dell ST2410 24" Full HD Widescreen LCD
*   1GB ATI Radeon HD5670 GDDR5 Graphics

Communications:
*   Integrated 10/1000 Ethernet
*   Dell 1525 WLAN PCIe Card with 11n mini-card and external antenna
*   Dell Wireless 365 Bluetooth 2.1 Module

Audio:
*   Integrated Audio
*   Dell AX210 USB Stereo Speaker

Keyboard & Mouse:
*   Dell Wireless Keyboard and Mouse

Slots:
*   PCIe x 1: 2 slots
*   PCIe x 16: 1 slot
*   PCI: 1 slot
*   SATA: 4

Top Ports:
*   2 USB 2.0 ports
*   Headphone port
*   Microphone/Line-in port

Front Ports:
*   2 USB 2.0 ports
*   19-in-1 Media Card Reader

Rear Ports:
*   HDMI
*   DVI
*   Gigabit Ethernet Connection
*   4 USB 2.0 ports
*   eSata
*   S/PDIF connector

Drive Bays:
*   Two 3.5": (Internally accessible)
*   Two 5.25"
*   One 3.5" FlexBay

Chassis:
*   CPU Dimensions (H x W x D): 16.02" x 7.31" x 17.9"
*   Weight: approximately 22.4 lbs.
*   460 Watt Power Supply

```


According to  "hwinfo  --short" here are some details about the hardware:
```
cpu:
                       AMD Phenom(tm) II X6 1035T Processor
                       AMD Phenom(tm) II X6 1035T Processor
                       AMD Phenom(tm) II X6 1035T Processor
                       AMD Phenom(tm) II X6 1035T Processor
                       AMD Phenom(tm) II X6 1035T Processor
                       AMD Phenom(tm) II X6 1035T Processor
keyboard:
  /dev/input/event3    GASIA PS2toUSB Adapter
  /dev/input/event5    Dell Keyboard
mouse:
  /dev/input/mice      GASIA PS2toUSB Adapter
                       Dell Generic USB Mouse
  /dev/input/mice      Macintosh mouse button emulation
graphics card:
                       ATI VGA compatible controller
sound:
                       ATI SBx00 Azalia (Intel HDA)
                       ATI Audio device
storage:
                       ATI SB700/SB800 SATA Controller [AHCI mode]
                       ATI SB700/SB800 IDE Controller
network:
  eth0                 Broadcom Ethernet controller
  wlan0                Atheros AR928X Wireless Network Adapter (PCI-Express)
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wlan0                WLAN network interface
  pan0                 Ethernet network interface
disk:
  /dev/sda             ST31500341AS
  /dev/sdb             Generic SD/MMC
  /dev/sdc             Generic Compact Flash
  /dev/sdd             Generic SM/xD-Picture
  /dev/sde             Generic MS/MS-Pro
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVD+-RW GH50N
usb controller:
                       ATI SB700/SB800 USB OHCI0 Controller
                       ATI SB700 USB OHCI1 Controller
                       ATI SB700/SB800 USB EHCI Controller
                       ATI SB700/SB800 USB OHCI0 Controller
                       ATI SB700 USB OHCI1 Controller
                       ATI SB700/SB800 USB EHCI Controller
                       ATI SB700/SB800 USB OHCI2 Controller
bios:
                       BIOS
bridge:
                       AMD RS780 Host Bridge Alternate
                       AMD RS780 PCI to PCI bridge (ext gfx port 0)
                       AMD RS780 PCI to PCI bridge (PCIE port 2)
                       AMD RS780 PCI to PCI bridge (PCIE port 4)
                       ATI SB700/SB800 LPC host controller
                       ATI SBx00 PCI to PCI Bridge
                       AMD Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
                       AMD Family 10h [Opteron, Athlon64, Sempron] Address Map
                       AMD Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
                       AMD Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
                       AMD Family 10h [Opteron, Athlon64, Sempron] Link Control
hub:
                       Linux 2.6.32-31-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-31-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-31-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.32-31-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.32-31-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.32-31-generic ohci_hcd OHCI Host Controller
                       Linux 2.6.32-31-generic ohci_hcd OHCI Host Controller
                       Broadcom BCM2046B1
memory:
                       Main Memory
bluetooth:
                       Dell Wireless 365 Bluetooth Module
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       ATI SBx00 SMBus Controller

```

---

### Post by mörgæs on 2011-04-28
It might be hard to find the reason, but as a solution I would try a fresh install of 10.10 and / or 11.04.

---

### Post by mcwood on 2011-08-07
Also, had the same problem so my solution was go to power management & under Actions [put computer to sleep when inactive for:] Changed to Never.

under Display [put computer to sleep when inactive for:] changed also to Disable.

Problem Solved.

---

