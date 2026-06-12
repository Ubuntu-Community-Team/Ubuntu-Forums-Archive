---
title: "can't get dual monitors, can get one or other, not both"
date: 2011-04-21
forum: Desktop Environments
---

### Post by rocket777 on 2011-04-21
I have an asus p5kpl-cm MB. I plugged in a radeon 9200 pci card. In the bios, I can set up:

pci/igd
igd/pci
igd

etc.

This determines which of the 2 displays (pci card or internal graphics on the MB) is the boot display. That determines which comes up with the bios screen and then once booted into ubuntu (10.04), this is the only adapter/monitor seen. The button detect monitors doesn't do anything.

lspci sees both my internal and pci card graphics. So, I can get either to work just fine (auto detected etc.) just not both at the same time.

I've tried all of the 3 above settings, and even when I set it to just igd, lspci still sees both my adapters. It identifies them correctly, and it works perfectly, detecting the monitor and knows the resolutions for each - just not both at the same time.

Does ubuntu know how to automatically configure more than one display w/o doing something else, or must I do something else to get both going together?

Thanks.

```
$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
03:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
```

More info:

This is lshw -C display   with only the pci (radeon) working

```
  *-display UNCLAIMED
       description: Display controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm cap_list
       configuration: latency=0
       resources: memory:fe880000-fe8fffff ioport:cc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fe700000-fe7fffff
  *-display:0
       description: VGA compatible controller
       product: RV280 [Radeon 9200 SE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:19 memory:e0000000-e7ffffff(prefetchable) ioport:e000(size=256) memory:fea00000-fea0ffff memory:fea20000-fea3ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 SE] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:03:00.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:e8000000-efffffff(prefetchable) memory:febf0000-febfffff

```

This is lshw -C display   with only the internal working

```
  *-display
       description: Display controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:fe880000-fe8fffff ioport:cc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fe700000-fe7fffff
  *-display:0
       description: VGA compatible controller
       product: RV280 [Radeon 9200 SE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:19 memory:e0000000-e7ffffff(prefetchable) ioport:e000(size=256) memory:fea00000-fea0ffff memory:fea20000-fea3ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 SE] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:03:00.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:e8000000-efffffff(prefetchable) memory:febf0000-febfffff

```

---

### Post by rocket777 on 2011-04-22
I can get both displays, but only by using two monitors attached to my radeon card. One using the vga and the second on the dvi.

I wonder, does this mean that my motherboard really only allows me to use a pci card OR the internal graphics? To make it work, I have to set the MB to pci/igd setting. Then only the pci card graphics works.

I know on my other computer, with an intel mb board, if I plug in an extra pci card, it works, but if I plug in a pci express x16 card, then it can't also use the internal graphics. I wonder if this is the case for my asus MB except it doesn't allow both pci graphics and internal graphics?

If so, then I can't eventually hook up a third display. My MB documentation doesn't mention anything about this.

There's also a setting for plug n play OS on the MB, I wonder if this should be turned on.

---

### Post by rocket777 on 2011-04-23
Well, I now know that the problem is with ubuntu.

I tried an old windows 2000 system, and while this card has crappy drivers (and in ubuntu the open source version ain't too hot either) windows still is able to see both my internal graphics and the 9200 pci card. It just can't play games or show videos on that screen, but it does work for regular stuff - so it's not the motherboard stopping things.

Is there somewhere I can report this ubuntu bug - that will be listened to? I have a feeling nobody is very concerned about this older video card.

This is an issue where it can't properly use the card at all - unless I make it the primary monitor in the bios. Then it won't properly use my internal graphics. That might be a more general problem, worth the time for someone to look into.

---

### Post by Krytarik on 2011-04-23
Could you check if that issue re-occurs with the latest beta of Natty 11.04?
Maybe it was fixed since, it also uses Xorg-Edgers' "radeon" driver now, but that may only affect newer cards, 9500 upwards.
[http://www.ubuntu.com/testing/natty/beta](http://www.ubuntu.com/testing/natty/beta)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by |{urse on 2011-04-23
Try this, It works for me perfectly.

[http://www.jejik.com/articles/2008/10/setting_up_dual_monitors_system-wide_with_xrandr_on_debian_lenny/](http://www.jejik.com/articles/2008/10/setting_up_dual_monitors_system-wide_with_xrandr_on_debian_lenny/)

*use the command 

> xrandr -q

to find the adaptor alias for each screen :D

---

### Post by rocket777 on 2011-04-24
> *use the command


xrandr -q
to find the adaptor alias for each screen 

The problem is lower down than that. 

xrandr also only shows one adapter, same as the gui configure display settings. 

Only lspci can see both interfaces.

I'll give natty 11.04 a try to see what it says.

---

### Post by rocket777 on 2011-04-24
11.04 is the same, xrandr also the same.

One thing interesting, during the boot up, it used my pci graphics to show the startup display with the rolling dots. As soon as it got through that, it then changed over to the other screen on the igd (I have it set igd) and turned off the pci screen. This is different than before.

(I didn't install, I'm just running from the cd)

So at some point it knows to use both. However, while running, it only sees one display as before.

Also, on shutdown, it reverts back to the pci graphics. Strange.

edit: well, after playing around, it appears that my results are not always the same. Sometimes it comes up on the pci, sometimes on the igd. Sometimes there's a switch to... in the menu, sometimes not. I can't figure out how to logout so I can setup the classic interface, but one time, when it did come up on my 32 inch monitor, it used the classic interface. I verified that the cd was valid. I've tried all the combination I could think of. It rarely acts the same twice. Seems like a timing bug to me.

---

