---
title: "Xgl/Compiz with Dual SLI?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by smallville on 2006-08-25
Hey, I just ordered a second sli card to snap in my motherboard next to my other sli card. Shipment's in and I'm curious, before I snap in this 2nd card... I want to know a few things:

1) How do I set up SLI in Ubuntu?
2) SLI Compatible with Compiz/Xgl?
3) Will my current working configuration of XGL/Compiz need to be re-configured/reinstalled?

4) I've a Leadtek GeForce FX 6800 w/ 256MBs
   and a Asus GeForce FX 6800 w/ 256MBs of ram.
On Nvidia's site, they say that with the latest drivers, in order for sli to work, is to have the same GPU.
Is that currently a Windows only feature? or does linux have that support also?

Any responses would be much appreciated. I've not found any posts so far in the ubuntuforums, compiz.net, and ubuntuguide.org forums.
So, bring on the savvy?

-Smallville

---

### Post by RAOF on 2006-08-25
The recent nVidia linux drivers support SLI, so I'd imagine the answers would be
1) Run nvidia-x-config (with the --sli=auto switch, it would seem.  Or something similar).
2) Yes.  It may not actually **help** XGL, though.  From memory, the drivers needed to specifically support a game for SLI to work properly.  I don't think you'd notice the difference with XGL effects, anyway :)
3) Probably not.  Unless you change which card your monitor is plugged in to, or something.

---

