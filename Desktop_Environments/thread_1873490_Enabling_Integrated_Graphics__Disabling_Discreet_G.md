---
title: "Enabling Integrated Graphics / Disabling Discreet Graphics in 11.10"
date: 2011-11-01
forum: Desktop Environments
---

### Post by geudrik on 2011-11-01
How does one go about doing this.. I have zero use for running my discrete card in Ubuntu, and need only the functionality of my integrated graphics... I have an Asus N53SV laptop, and it was my understanding that the 3.x kernel now offers native support for vga switching (via switcheroo if I'm correct).

I'm less interested in being able to switch it on and off than I am just saying screw it and leaving it to run off the Intel integrated.  How can I go about doing this?  Both cards show up as devices, but I can only so far seem to make the nVidia card work.  

Any ideas?

Edit:
By the way... 
```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)

```

---

### Post by diegueus9 on 2011-11-02
How do you can run nvidia? I installed ubuntu 11.10 but nvida doesn't works

> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by 3Miro on 2011-11-02
You are using Optimus and Nvidia doesn't provide drivers for Optimus on Linux. Basically, things will not work well.

Your best bet is to look at the BIOS and try to disable one of the cards completely, however, not all BIOS would support that.

---

