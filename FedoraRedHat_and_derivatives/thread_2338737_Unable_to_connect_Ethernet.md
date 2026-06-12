---
title: "Unable to connect Ethernet"
date: 2016-10-01
forum: Fedora/RedHat and derivatives
---

### Post by nixon-ashlon1 on 2016-10-01
Hi everyone, this has been a long and frustrating day trying different os's and the only time I have had an ethernet connection is during the installation of Fedora and Ubuntu.


**Things I've tried:**
Model and Cable work perfectly fine on other PC's/Laptops
Iommu is enabled.
Networking is enabled in the bios
Cannot find drivers for my motherboard/ethernet for download as .tar or any other variant as my other pc's are all windows.


[B]My specifications are as follows:
[/B]Gigabyte 990 UD3 motherboard
AMD FX 8350 stock cpu
16gb of avexir and corsair ram (gb each 4x2)
Gigabyte 970 G1-G gpu
and 2 separate 1tb HDD's


I need to connect to the internet as soon as possible for my job, please respond with any and all fixes you can think of and I will respond as son as I see them.
If you need any additional information let me know and as stated, I'll respond when I see your question.


Thank you, hopefully this can easily be resolved.

---

### Post by Bucky Ball on 2016-10-01
Welcome. Which do you want help with? Ubuntu or Fedora?

You are posted in an area for Fedora which, frankly, is not the best place to be if you need help fast. Suggest you post on a Fedora forum. Mostly volunteer Ubuntu enthusiasts here and you have a small chance of getting lucky. Not a main forum support area.

If you want help with Ubuntu, say so and will move this to the appropriate area, but one or the other, thanks. Not both. ;)

---

### Post by nixon-ashlon1 on 2016-10-01
I need help with Fedora.

---

### Post by nixon-ashlon1 on 2016-10-01
Also the LSPCI output was
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
02:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 12)
04:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
06:00.0 Network controller: Ralink corp. RT5592 PCIe Wireless Network Adapter
```

---

### Post by cariboo on 2016-10-01
Could you post the output of:

```
sudo lshw -C network
```

this will let us see if the drivers for your NIC are in use.

---

### Post by nixon-ashlon1 on 2016-10-01
lshw command not found

---

### Post by nixon-ashlon1 on 2016-10-01
Also to update ip ad sho outputs the following
mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp5s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether fc:aa:14:94:a4:aa brd ff:ff:ff:ff:ff:ff

---

### Post by cariboo on 2016-10-01
From the looks of it, Fedora doesn't have the tools most of us using Ubuntu expect to see in a default installation, which makes it pretty hard to help you with your problem. If you have lsmod installed, check to see if the r8169 driver is listed.

```
 lsmod | grep r8169
r8169                  81920  0
mii                    16384  1 r8169
```

---

### Post by nixon-ashlon1 on 2016-10-01
Mine looks identical to what you posted.

---

