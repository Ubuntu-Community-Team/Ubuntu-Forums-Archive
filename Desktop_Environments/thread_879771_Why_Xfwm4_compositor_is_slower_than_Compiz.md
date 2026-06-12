---
title: "Why Xfwm4 compositor is slower than Compiz?"
date: 2008-08-04
forum: Desktop Environments
---

### Post by RadenMu'az on 2008-08-04
I'm currently running Xubuntu Hardy with downgraded Xorg (Gutsy Xorg with Feisty ATI driver) due to [some latest Xorg display bug on ATI IGP 320M]("http://bugs.freedesktop.org/show_bug.cgi?id=15708").

AIGLX/Compiz is enabled with [this hack]("http://ubuntuforums.org/showthread.php?t=764633&highlight=xgl+compiz+aiglx")

The problem is, when using AIGLX, why Xfce's Xfwm4's Compositor is darn slower than Compiz's?
But when using XGL, Xfwm4 is faster. Compiz just about the same though.
(I don't like XGL as it is a separate X server and have some keyboard issues.)


lspci> 00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
00:0c.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


thanks

---

### Post by overdrank on 2008-08-04
Closed duplicate thread [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/showthread.php?t=879778)

:)

---

