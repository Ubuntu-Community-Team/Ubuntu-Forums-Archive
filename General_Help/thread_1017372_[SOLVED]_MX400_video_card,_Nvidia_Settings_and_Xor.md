---
title: "[SOLVED] MX400 video card, Nvidia Settings and Xorg."
date: 2008-12-21
forum: General Help
---

### Post by yogo on 2008-12-21
After a long wait my video card arrived this evening and I installed it and basically if went problem free.

Everything is working, Compiz BUT it did start in low graphics mode so I edited values in Xorg.conf but I still remained in low graphics mode. I then did the dpkg-reconfigure -phigh xserver-xorg and that too did not help.

I then tried the Nvidia X Server settings and that was not able to parse the Xorg.conf  but I did manage to change the display in Nvidia settings and have a decent display running now BUT my Xorg.conf does not show the setting made by Nvidia setting. So where are the changes actually made?

My main thing is I am happy to finally have Compiz back running. In general, where will I notice improvements from the  graphics card?

I do not play games but can I expect web cam video to be smoother and Youtube

TIA

---

### Post by yogo on 2008-12-21
Today, unfortunately I am back in low graphics mode but this time I can not get out. Yesterday I was able to somehow change it in Nvidia setting but today, I have little or no control of changing settings there.

My graphis card is picked up in bios and terminal
 *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 440 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: c1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt

I have a feeling both drivers are being loaded but not sure how to go about getting this thing working so I do not have to continually mess with it.

TIA

After a whirlwind of restarts, reminded me of a Windows box, I finally got it right the second time around with Envy.

---

