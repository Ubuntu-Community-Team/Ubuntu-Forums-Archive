---
title: "Desktop Effects on Dell Latitude D600"
date: 2007-04-22
forum: Desktop Environments
---

### Post by yang on 2007-04-22
My laptop should have an ATI Radeon Mobility 9000, and I do see "Radeon R250 [Mobility FireGL 9000]" under "82855PM Processor to AGP Controller" in Hardware Information/Device Manager, but Desktop Effects are leaving lots of garbage/producing lots of artifacts on the right third of my desktop, and the effects bog down my computer. Any hope for me?

---

### Post by rubinstein on 2007-04-22
If you change your color depth from 24 to 16 bit (in /etc/X11/xorg.conf) the artefacts should go away. I read somewhere that the card has not enough ram, so reducing the colors should help.

---

### Post by yang on 2007-04-22
Thanks, that worked. However it would be nice to be able to retain 24-bit depth. Can I expect this to be possible sometime down the road?

---

