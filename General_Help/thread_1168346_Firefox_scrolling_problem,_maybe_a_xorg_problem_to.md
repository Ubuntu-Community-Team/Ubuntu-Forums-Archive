---
title: "Firefox scrolling problem, maybe a xorg problem too."
date: 2009-05-24
forum: General Help
---

### Post by blindside on 2009-05-24
When scrolling with my keypad on my laptop firefox is very choppy. I followed the sticky for editing my xorg file and updating the kernel. Video seems to be working fine and everything else seems fine, but I'm kinda new with Linux so I dont know how to really test my system to see if anything else might be wrong. here is my lspci output
```
daniel@blindside:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```Any help at all would be appreciated. Oh yeah I almost forgot. I am using Jaunty 32bit, and my computer is a c762nr compaq.

---

### Post by blindside on 2009-05-24
bumpidy bump bump

---

### Post by blindside on 2009-05-25
this is the contents of xorg.conf file. Hopefully it helps

```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by blindside on 2009-05-27
??????????

---

### Post by Mirge on 2009-05-27
Sorry, I am not quite following. You fixed the scrolling problem, now you're just wanting to check other parts of the system for problems? I'd say just use it and let us know if you run into another problem and we can help.

---

### Post by blindside on 2009-05-27
No I haven't fixed anything, My problem is that firefox scrolls very slow, and very "glitchy" I am letting everyone know that I used the sticky on the intel performance guide, but I am still having what seems to be a 2D problem. 

Sorry if I wasn't clear. I am just wondering if I did it correctly, or if I need to do something else. Or what I can do to see if I have all my drivers and what not setup correctly.

---

