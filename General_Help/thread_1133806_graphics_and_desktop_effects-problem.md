---
title: "graphics and desktop effects-problem"
date: 2009-04-23
forum: General Help
---

### Post by satti_dc on 2009-04-23
Hi all,
I have bought a new HP desktop with 2.5GHz Intel dual core processor. Thinking it to be fast and with Ubutnu being much user friendly, i tried installing it. Though everything went fine, but I cant even simple gui with normal desktop effects. I thought it would, as its a faster machine (the reason for which i shelled, rather then buying a laptop) but got disappointed. 
I feel the problem could be the integrated intel graphics card. I dont knwo how to fish the details and know what's the drivers required.
Thanks for your help!
cheers,
satti

---

### Post by Thelasko on 2009-04-23
> **satti_dc said:**
> I feel the problem could be the integrated intel graphics card.
You are correct, desktop effects are disabled for many intel graphics cards.  You likely have the correct drivers installed, but your card simply isn't able to produce those effects properly.

What kind of card is it?  You may be able to override Ubuntu's lockout on your graphics card, and enable the effects.  However, doing so may cause other problems.

---

### Post by LowSky on 2009-04-23
open a terminal (the app is under applcitions>accessories

type

```
lspci
```

post the output here and maybe we can get hte ball rolling

---

### Post by satti_dc on 2009-04-23
> **LowSky said:**
> open a terminal (the app is under applcitions>accessories

type

```
lspci
```post the output here and maybe we can get hte ball rolling

Here is the output of lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

thanks for looking into my problem
-satti

---

