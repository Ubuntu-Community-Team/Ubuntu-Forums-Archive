---
title: "Linux: Wow w/Wine"
date: 2014-10-28
forum: Gaming &amp; Leisure
---

### Post by schema2 on 2014-10-28
I am not sure if this was supposed to go here or in wine category. I apologize. 

I am running Wow over wine, no serious performance problems to speak of. I am using mesa kernel graphics driver, it isn't causing any crashes or anything of the nature. My only problem is that charater outfits in the game aren't rendering: characters just appear to be blacked out. I've included a pic to illustrate. I've tried adjusting in game graphics settings to full blast. It doesn't fix this.  (link to image: [http://postimg.org/image/rkmvxhxq7/](http://postimg.org/image/rkmvxhxq7/))

 I am running kernel 3.13.0-37 on Mint Linux. This is my graphics info. I've tried installing a proprietary intel driver but I haven't had much luck. My questions are: What kind of problem is this? And can I fix it by tweaking the kernel driver or do I need to find the intel driver and install it? I have anxiety about the latter- I am a bit of  noob and haven't installed a proprietary graphics driver before from the cli. I've tried using the intel-graphics-installer but it wasn't able to load an intel driver. 

$ lspci -vnn | grep VGA -A 12

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:107b]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])




[IMG]http://postimg.org/image/rkmvxhxq7/[/IMG]

---

