---
title: "x.org on one monitor/gfx card, DirectFB on the other?"
date: 2006-02-17
forum: Desktop Environments
---

### Post by jejones3141 on 2006-02-17
I want to experiment with DirectFB, and it seemed to me that the way to go about it is to have two graphics cards and two monitors, and to run plain vanilla x.org on one and DirectFB on the other. (Yes, I know that there's a version of x.org that lives atop DirectFB, but I figured it would be better to keep them separated, like the song says.)

The packages are there, and installed. Plain x.org w/the nvidia driver is running on the PCI graphics card, because I couldn't figure out how to get a framebuffer associated with the PCI graphics card, and so decided to go ahead and let DirectFB have the AGP card. (I'm not clear on how to make x.org use the USB keyboard and leave the PS/2 keyboard alone for use wth DirectFB.)

Has someone attempted this arrangement before? Is there a HOWTO out there already? (Googling doesn't turn up much in the way of DirectFB documentation.) Any pointer would be greatly appreciated.

---

