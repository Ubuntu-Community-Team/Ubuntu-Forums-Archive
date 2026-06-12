---
title: "Disappearing mouse pointer after &quot;lock&quot; and &quot;hibernation&quot;"
date: 2016-04-14
forum: Desktop Environments
---

### Post by andrewleepaul on 2016-04-14
Hello all

I have installed "Xubuntu 16.04, Xenial Xerus" on a new Lenovo T560. Everything works exactly as expected with the exception of the following:

When I lock the laptop, using the using "Lock Screen" icon in the menu, and then unlock it again, the mouse pointer disappears.

The mouse is still functional. It is possible to click on the icons in the panel, for example, however, the mouse pointer is invisible.

I experience the identical behavior after waking up from hibernation too.

When logging in for the first time, or after logging out, the problem does not occur.

As a workaround, I can switch TTY with:

Ctrl + Alt + F1
Ctrl + Alt + F7

And the mouse pointer magically re-appears.

Besides this workaround, is there a fix to the problem?

Here is the output of "lcpci", showing the hardware in the laptop:

[FONT=Courier New]00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
00:08.0 System peripheral: Intel Corporation Sky Lake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:16.3 Serial controller: Intel Corporation Device 9d3d (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Device 9d12 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-LM (rev 21)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
04:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)[/FONT]

Andrew

---

### Post by Martin_Pozdena on 2016-04-22
Thank you for the workaround :) 

I have exactly the same issue with Lenovo Thinkpad E531. 

martin@XXXXXXXXXXX:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)

It is worth mentioning that I also have the xubuntu 14.04 installed at the same machine (for more than a year) and this issue was never present in 14.04.

I am open to provide more information about my system if it helps in fixing this bug.

Martin

---

### Post by Urgazhi on 2016-04-22
Have the same issue with  Lenovo Yoga 2

```

$lspci
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
00:13.0 SATA controller: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0e)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation Atom Processor E3800 Series SMBus Controller (rev 0e)
01:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

---

### Post by Slowboyfast on 2016-04-22
I think it's lightdm related. Switched to GDM and the problem is gone.

---

### Post by PaulW2U on 2016-04-24
> **Slowboyfast said:**
> I think it's lightdm related. Switched to GDM and the problem is gone.
The bug report suggests otherwise - [Mouse cursor lost when unlocking with Intel graphics]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604") - the fix in Debian will hopefully find its way into Ubuntu soon.

---

### Post by akinetos on 2016-12-11
Im no master ubuntu user, but have been using since 2009. Anywas had this probelm and immediatley believed it to be something to do with the usuless screenscaver that comes shipped with xubuntu...i say its usueless because one cannot run surveillance software in the background while having the screen saver activated..and i suppose as icing on the cake, the mouse cursor disappears too boot...

anyways:

# apt-get remove light-locker
# apt-get install xscreensaver

---

