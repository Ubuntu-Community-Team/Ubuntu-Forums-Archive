---
title: "OpenGL Shaders causes computer to crash..."
date: 2012-02-11
forum: Gaming &amp; Leisure
---

### Post by iamanidiot123 on 2012-02-11
... In Ubuntu 10.04
This is abnormal, my card has shader support
this has not happened before
Any ideas?

Here's my lspci output
```
daniel@daniel-desktop[16:20. Sat, Feb 11, 2012]:[~]                             
> lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```
This only happens in games, which is why I'm in this forum

---

### Post by Dlambert on 2012-02-11
Card model? Proper drivers? It says you're running intel

---

### Post by iamanidiot123 on 2012-02-12
> **Dlambert said:**
> Card model? Proper drivers? It says you're running intel

```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```

And I don't know where to get 'Proper drivers' because I have to use the open source drivers.

---

### Post by Dlambert on 2012-02-15
I meant upgrade MESA/Xorg edgers

---

### Post by iamanidiot123 on 2012-02-19
> **Dlambert said:**
> I meant upgrade MESA/Xorg edgers

Where?

---

### Post by efikkan on 2012-02-19
Paste the output from glxinfo in terminal

---

### Post by Dlambert on 2012-02-19
> **iamanidiot123 said:**
> Where?

32 bit:
[https://launchpad.net/~xorg-edgers/+archive/ppa/+build/3000836]("https://launchpad.net/~xorg-edgers/+archive/ppa/+build/3000836")

64 bit:
[https://launchpad.net/~xorg-edgers/+archive/ppa/+build/3000835]("https://launchpad.net/~xorg-edgers/+archive/ppa/+build/3000835")

---

