---
title: "Steam games in source give openGL error"
date: 2015-07-08
forum: Gaming &amp; Leisure
---

### Post by jedijon567 on 2015-07-08
I think this is where this goes, but when I try to start a source game, It give me the OpenGL entry point 'glColormaskindexedEXT' error. I can not find help for my graphics card, which when I type the command to find out, I get this

```
*-display:0             
       description: VGA compatible controller
       product: RV516 [Radeon X1300/X1550 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:16 memory:c0000000-cfffffff memory:dfde0000-dfdeffff ioport:dc00(size=256) memory:dfe00000-dfe1ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV516 [Radeon X1300/X1550 Series] (Secondary)
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dfdf0000-dfdfffff


```

Please help me fix this! I want to play other games than Half-Life 1 on linux!

---

### Post by MikeCyber on 2015-07-08
I've a GTX770 but I guess you might need to install the proprietary AMD drivers.

---

### Post by efflandt on 2015-07-08
The X1300 or related is an old legacy card from before AMD bought ATI. So even AMD considers it "Legacy" and I believe the only support it currently has in Linux is the default radeon driver, so it will do no good to try a proprietary driver for it. Although, that chip or similar has been around for a long time, so the radeon driver works well for most things. I have an X1300 on an old PC and X1300 mobile on a laptop from 2005, but neither has current Ubuntu versions and even then they did not work with fglrx driver, so I have not tried them with Steam.

Linux Steam and Steam games seem to work best with Nvidia graphics and drivers. But if it is an old computer with AGP slot instead of PCI-E, I am not sure what better graphic cards are still available or easy to find for that.

---

### Post by jedijon567 on 2015-07-09
> **efflandt said:**
> The X1300 or related is an old legacy card from before AMD bought ATI. So even AMD considers it "Legacy" and I believe the only support it currently has in Linux is the default radeon driver, so it will do no good to try a proprietary driver for it. Although, that chip or similar has been around for a long time, so the radeon driver works well for most things. I have an X1300 on an old PC and X1300 mobile on a laptop from 2005, but neither has current Ubuntu versions and even then they did not work with fglrx driver, so I have not tried them with Steam.

Linux Steam and Steam games seem to work best with Nvidia graphics and drivers. But if it is an old computer with AGP slot instead of PCI-E, I am not sure what better graphic cards are still available or easy to find for that.

Thanks for telling me D:, I'm a broke 13 year old who can't buy an Nvidia card, and I'm just reusing our old 06 dell xps 410 (I thinks that's its name) at one point running windows vista. if I could play steam games with that driver, how would I go about getting that driver? NOTE-Never looked inside this computer, so I don't Know what slots it has.

---

### Post by QIII on 2015-07-09
Hello!

The default open source Radeon driver is installed by default when you install Ubuntu on a machine with ATI/AMD graphics.

If you see the desktop, then that driver is running.

The combination of such an old card and the Radeon driver may simply not under any circumstances be up to the task of the demands of Steam games.

With regard to NVIDIA/ATI, the question is more about brand loyalty than actual functionality.  And ATI/AMD's reputation still suffers from the abysmal Linux driver support prior to AMD's purchase of ATI in 2008.  AMD is a member of the Linux Foundation (NVIDIA joined much later) and AMD's engineers have been instrumental in the rapid development improving the performance of the Radeon driver.

Yours is just a very old card from before AMD bought ATI and AMD has moved on.

I have a review of the AMD R9 290X in the blog link (theleftcoastgeek.net) in my signature if you are interested.

---

### Post by jedijon567 on 2015-07-09
> **QIII said:**
> Hello!
Yours is just a very old card from before AMD bought ATI and AMD has moved on.

Okay, so I cant play steam games D:
also, so AMD bought ATI in 2006 ish, cause thats when I bought this pc

---

