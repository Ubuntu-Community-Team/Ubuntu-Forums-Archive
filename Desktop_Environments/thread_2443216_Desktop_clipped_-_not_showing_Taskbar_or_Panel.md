---
title: "Desktop clipped - not showing Taskbar or Panel"
date: 2020-05-12
forum: Desktop Environments
---

### Post by kickingken on 2020-05-12
HI!
I've searched the forums but can't find an answer to my question - I'm not duplicating...but another answer asked the user to run 'lspci' in Terminal.
I've done that and the result is below.
I'm new so apologies if some of my terminology is awry.

I'm 1 week in to a fresh install of Ubuntu 20.04.
The problem: 
The desktop is sometimes too big for my monitor to display. 
The bottom Taskbar is half-on/half-off the screen, and the top panel, showing date/time etc is not visible at all.
If the monitor goes to sleep through inactivity, sometimes when it wakes up, the problem spontaneously fixes itself and adjusts to display perfectly.

I'm using Intel integrated graphics.
Monitor is Samsung P2450 connected via DVI
The Display Settings are set to the correct resolution for my monitor.
There is no Zoom applied.
Running lspci outputs:

```
apollo@OLYMPUS:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #3 (rev f1)
00:1c.3 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #4 (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1e.4 SD Host controller: Intel Corporation Device 9d2b (rev 21)
00:1e.6 SD Host controller: Intel Corporation Sunrise Point-LP Secure Digital IO Controller (rev 21)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
02:00.0 Network controller: Intel Corporation WiFi Link 5100

```

Thanks for giving my problem a look and stay safe everyone!

---

### Post by anarchy-x on 2020-06-29
The monitor itself doesn't have manual zoom/cropping adjustments?

---

