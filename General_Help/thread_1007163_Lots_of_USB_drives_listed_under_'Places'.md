---
title: "Lots of USB drives listed under 'Places'"
date: 2008-12-10
forum: General Help
---

### Post by jcoglan on 2008-12-10
I've just done a fresh install of Intrepid on a Dell Studio desktop, and there are several anonymous USB drives listed under 'Places'. They don't point to filesystems and don't seem to be mounted, but offer an option to 'Rescan' them (what does this mean?). My system has 6 USB ports, which are currently running a keyboard and mouse (no hard drives, cameras etc.) Anybody know why this is happening, and how to remove them from the list? If it's any help, here's my lspci:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation Device 0605 (rev a2)
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by jcoglan on 2008-12-12
I'm attaching a screenshot of the drives under 'Computer'. All their properties are listed as 'unknown'. Can anybody help me remove them?

---

### Post by hikaricore on 2008-12-12
I've seen something similar in systems with a built-in multi format flash memory card reader.
If you don't have such a memory card reader I'm not sure what to tell you.

Is simply ignoring them an option?  I don't see the harm in them just sitting there if you're not having any problems.

---

### Post by fragos on 2008-12-12
Computer will list removeable drives currently without content. For example if your system has a card reader with separate slots for different kinds of media, each slot will show as a drive. Empty CD/DVD drives also show this way. LSPCI always shows lots of USB ports based on what the mother board provides. This has nothing to do with a device being connected. Most systems will show 8 USB ports in LSPCI.

---

### Post by jcoglan on 2008-12-12
Thanks, hikaricore. Turns out it is the various card readers built into my machine. Bonus discovery: Ubuntu happily reads my SD cards and ufraw-batch extracts my photos to a bunch of different formats. I was expecting to carry on relying on Adobe Bridge in my Windows VM for this job, so I'm very pleasantly surprised.

---

