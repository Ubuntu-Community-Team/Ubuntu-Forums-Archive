---
title: "Wallpaper issue after login"
date: 2015-06-24
forum: Desktop Environments
---

### Post by mattDalm on 2015-06-24
Hi - 

After login when the environment loads, the wallpaper first displays correctly but then it gets messed up, I then have to change the wallpaper to have it back to normal. Please check the screenshot it makes it easier to understand. 

[ATTACH=CONFIG]262843[/ATTACH]

Using later ubuntu 15.04.

Where should I look to fix this issue. 

Thx

--Matt

---

### Post by mattDalm on 2015-06-26
Any info I can provide to fix this issue

---

### Post by Frogs Hair on 2015-06-26
This looks like it could be a graphics card/chip problem. Add some computer specs and the output of the following command will supply information about your graphics card/chip. ```
lspci 
```

---

### Post by mattDalm on 2015-06-28
Here you go:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)

Note that it was working before the upgrade to 15.04.

Thank you

--Matt

---

### Post by Frogs Hair on 2015-07-04
I'm running the same graphics , but a different rev and didn't see anything like this after an upgrade to 15.04.

---

