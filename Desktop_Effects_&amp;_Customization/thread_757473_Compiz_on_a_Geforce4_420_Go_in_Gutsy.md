---
title: "Compiz on a Geforce4 420 Go in Gutsy"
date: 2008-04-16
forum: Desktop Effects &amp; Customization
---

### Post by bacardiandwatermelon on 2008-04-16
Hey guys, I had Compiz running sweet as on my old laptop running edgy but then I did the leap to Gutsy and I couldn't get it going, well this afternoon I finally managed to get it to work so I thought I better write it down just incase someone else is having a similar issue.

First off I downloaded the NVidia 96.43 driver and installed it.

I downloaded a edid.bin file which is somewhere here on this forum.

I added the following lines to my xorg.conf file..
Under section Screen..

Option         "UseDisplayDevice" "DFP-0"
Option         "CustomEDID" "DFP-0:/etc/X11/edid.bin"
Option         "XAANoOffscreenPixmaps" "True"
Option         "UseEvents" "True"
Option         "DamageEvents" "True"
Option         "DisbleGLXRootClipping" "True"
Option         "AddARGBVisuals" "True"
Option         "AddARGBGLXVisuals" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "true"
Option         "TripleBuffer" "True"
Option         "RenderAccel" "True"
Option         "DRI" "True"

Not sure if I needed all of those, but it helped :-P

Compiz would work at this stage but I kept getting black windows whenever I would have a window running at fullscreen. So I played around with the settings and ended up adding the following command to the startup programs.

compiz --replace --indirect-rendering --force-fglrx

So yeah I'm still experimenting with this, so can't say if it is going to work in the long term, but if it helps someone out, sweet as.

---

### Post by bacardiandwatermelon on 2008-04-17
Oh and if you run emerald --replace after it, that fixes the themes.

---

