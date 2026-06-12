---
title: "Open source Radeon driver breaks Steam overlay for me."
date: 2014-03-03
forum: Gaming &amp; Leisure
---

### Post by immerohnegott2 on 2014-03-03
On my machine (AMD A8-3500M/Radeon 6620G) using the r600 Gallium3D driver as shipped in Ubuntu 14.04 (SO, Mesa 10.1 + kernel 3.13) causes the Steam Overlay to simply not run. 

It gives me errors about gameoverlayrenderer.so not being the right ELF class and Shift+TAB just starts cycling backwards through the game menu. Games themselves all run on r600g, and surprisingly well at that, I just can't use the overlay.

Using Catalyst results in the overlay working like it should, although my machine then becomes a little less stable. I tried using the updated Mesa/DRM from oibaf's PPA, but it didn't help. Tried using the latest beta of the Steam client, also no change. Tried purging and reinstalling Steam, also no change.

---

### Post by mastablasta on 2014-03-04
might be good to report this on launchpad so developers know about the issue and can fix it by the time when 14.04 is released.. 

also Ubuntu +1 i believe is the place for 14.04 threads. 14.04 was not released yet.

---

