---
title: "Low Graphics Mode - Borked Driver? Xorg.conf?"
date: 2009-01-20
forum: General Help
---

### Post by brendanodork on 2009-01-20
Hola!

I've got a laptop (Compaq V2000) that's been running ubuntu (Hardy) nicely out of the box.  I tried to get fancy and install the ati video drivers for it so that i could get svideo out to my TV.  Got it working for a while (downloaded from the ATI site), was playing around with many different settings trying to get it to work the way i wanted it.  I didn't keep particularly good track of what i was doing and at some point, the laptop started booting into what it calmly and repetitively informs me is Low Graphics Mode because it cannot detect my defice.  So that's sad.  At some point in there i upgraded to Intrepid.  :-/  Too many upgrades at once - i know i shouldn't have.

I tried all of the "fix me" options in Recovery Mode.  I tried replacing /etc/X11/xorg.conf with a few different ones, including a very empty-looking one, and the one that results when i type "sudo dpkg-reconfigure -p high xserver-xorg".  I replaced it with one that was (i believe) marked "xorg.conf.original" from recovery mode, and that worked very nicely...once.  When i rebooted, back to low graphics mode.  Further replacements do not seem to be yielding me any results.

Does this sound familiar to anyone?  Is there a diagnostic path that seems useful to someone?  I was next going to try making a live CD to make sure it really was my system that was borked rather than the hardware parts.

Thanks!
     - Brendan

---

