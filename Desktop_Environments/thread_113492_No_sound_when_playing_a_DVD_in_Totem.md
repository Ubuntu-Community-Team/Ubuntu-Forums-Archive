---
title: "No sound when playing a DVD in Totem"
date: 2006-01-06
forum: Desktop Environments
---

### Post by magnusbb on 2006-01-06
Hello,

I am running Breezy, with the latest updates, and backports. I run Totem 1.2.1. When playing DVDs in Totem through xine, I have no sound. With xine-ui, I have sound. I've checked all the volume controls, but that's not the problem. 

Totem works great doing music and videos, but not DVDs.

Does someone else experience this?

---

### Post by mchatel on 2006-01-06
I had this same problem (once I switched from Hoary to Breezy).  I tried every sound setting recommendation that I could find, but I could never figure it out.  

Same issue as you...  everything (soundwise) seemed to work in Totem/XINE, except no sound in DVD playback.

I simply gave up on Totem, and just use G-XINE now.  It seems to work well.

---

### Post by magnusbb on 2006-01-06
Yes, that works. The only problem is that subtitles doesn't seem to work with the other players...

---

### Post by magnusbb on 2006-01-06
Problem solved!

**The version 1.2.1 in the backports was the problem.** I reverted to the old breezy version 1.2.0 - and that cured it. So, the Totem backport is problematic. If you have it, I would test it for the DVD problem.

I would reccommend any using the otherwise excellent backports mirror to **downgrade** their totem packages (if you have the problem) to the original version. This can be done by issuing "force package" in Synaptic.

You can also put this in your /etc/apt/preferences file if you want to pin the original version, so you make sure that the system will stick to that in the future:

> Package: totem
Pin: version 1.2.0-0ubuntu3
Pin-Priority: 1001

Package: totem-xine
Pin: version 1.2.0-0ubuntu3
Pin-Priority: 1001

Package: libtotem-plparser0
Pin: version 1.2.0-0ubuntu3
Pin-Priority: 1001


Hopes this helps.

---

