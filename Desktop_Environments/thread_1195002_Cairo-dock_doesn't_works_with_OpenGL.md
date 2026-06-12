---
title: "Cairo-dock doesn't works with OpenGL"
date: 2009-06-23
forum: Desktop Environments
---

### Post by utdaoops on 2009-06-23
[FONT=Courier New]```
jeta@jeta-laptop:~$ sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```[/FONT]

When I type command "cairo-dock -C" then it works perfectly.
But if I do "cairo-dock -O", it shows black background.

I installed python-opengl and use compiz-fusion, AWN, XBMC.
And xserver-xorg-video-intel is newest version.

I don't know what to do. :confused:

Help me, PLZ.




Oh, I'm on Jaunty.

---

### Post by fabounet on 2009-06-24
see the cairo-dock's wiki.
your drivers are probably not enough.
If it's an Intel card, you can try the latest X available on Karmic, and activate the UXA in xorg.conf, but be aware that it is still in an early stage.

---

