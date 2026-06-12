---
title: "wierd screen scramble after kernel upgrade"
date: 2008-12-17
forum: General Help
---

### Post by frogotronic on 2008-12-17
Hello,

I've just upgraded my kernel to the 2.6.24-23 version on Hardy.  My Hardy version now says 8.04.2 LTS.  I am using the FGLRX driver for an ATI Mobility Radeon x2300 card.

1) Everything works well except on the odd occasion the machine hangs (progress bar stops) on shutdown.  Have to do a hard reboot.

2) Associated with this new intermittent behaviour is the on startup just before my login screen for X, I get a weird distorted screen.  I was using this driver (ATI Catalyst 8.12) on the last kernel version and no issues.  This weird screen disappears, and then the machine behaves normally.  Is there a way to prevent that weirdness? Or I am just stuck with it?

Thanks,
CH

):P

---

### Post by Galoot on 2008-12-17
Well, you're not nuts. I haven't experienced the hang-before-shutdown problem (yet), but the distorted screen at startup happens for me, too. One tile of my tiled background shows up clearly at top-left, with the rest of the desktop looking borked. It then disappears, as you said.

This upgrade also seemed to cock up my laptop's wireless. I'm currently booting into 2.6.24-22 via the grub menu so I can connect.

---

### Post by frogotronic on 2008-12-17
> **Galoot said:**
> Well, you're not nuts. I haven't experienced the hang-before-shutdown problem (yet), but the distorted screen at startup happens for me, too. One tile of my tiled background shows up clearly at top-left, with the rest of the desktop looking borked. It then disappears, as you said.

This upgrade also seemed to cock up my laptop's wireless. I'm currently booting into 2.6.24-22 via the grub menu so I can connect.

Cheers Galoot, nice to know I'm not nuts.

Hey, I grew up on the Island - wish I was there now.

- CH   ):P

---

### Post by frogotronic on 2008-12-20
Well, seems to be solved (knock-on-wood) by switching back to the Catalyst ATI FGLRX 8.10 driver. :(

---

