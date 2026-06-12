---
title: "Small Resolution"
date: 2006-09-02
forum: Desktop Environments
---

### Post by nee coa la on 2006-09-02
Okay, so this is really weird...one day I turn on my computer and the only resolution it will display is 600x400 when I was usually running it @ 1280x1024.

Any ideas on how to fix this problem?

---

### Post by coffeecat on 2006-09-02
Before you think of reconfiguring the xserver or editing xorg.conf, did you have the monitor switched off as you booted up? I too use a 1280 x 1024 monitor and use a kvm switch with three machines. One day I was working on one machine and started a bootup with Ubuntu on another. When I switched over I found that the resolution had gone down to either 800x600 or 640x480 - can't remember which. Like you I was puzzled and thought I would need to reconfigure something but a simple reboot (with the monitor connected through) put it back into 1280x1024.

I can only imagine that the xserver in Ubuntu reacts to the absence of a connected monitor. I haven't seen this behaviour in other distros, but I rarely do this sort of thing anyway so I can't be sure it doesn't happen. An experiment for the long winter evenings perhaps. :)

---

