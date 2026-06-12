---
title: "Desktop size smaller than display"
date: 2009-06-16
forum: Desktop Environments
---

### Post by soho on 2009-06-16
Hi,

I have a Mythbuntu box connected to a flatpanel TV with a HDMI cabel.
The NVidia config tells me that the EDID reports a native resolution of 1280x720, so this is the resolution I have set up in my xorg.conf.
The problem is, that the TV has some overhead, so the visual resolution is something close to 1176x666 with an offset of 50x30.
Mythtv allows me to configure the actual resolution and offset of the TV, but I also use the desktop from time to time and it's quite anoying to have the menus outside the desktop border.
Is there a way for me to setup xorg.conf to use a virtual screen smaller than the actual display mode?
I have tried using randr, but it complains if I specify a screen smaller than the display mode.

---

