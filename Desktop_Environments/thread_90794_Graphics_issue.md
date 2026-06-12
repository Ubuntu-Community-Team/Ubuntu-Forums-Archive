---
title: "Graphics issue"
date: 2005-11-15
forum: Desktop Environments
---

### Post by andril on 2005-11-15
Can anyone help me? I am using ATI Radeon 9200 SE as a video card. The problem is that all of my themes are supposed to have transparent sides but this is what i get

---

### Post by Remmelas on 2005-11-15
I'd love to be shown I'm wrong, but if I understand everything i've read correctly, ATI cards don't have hardware accelerated compositing necessary for transparencies yet(though work is underway on the xorg ati drivers), so you'd have to use a 'compositing manager' that would do the work in software.  I've not played with this on my ATI card yet, as I'm not a big enough fan of transparency to accept the performance hit of software rendering.

---

### Post by mcduck on 2005-11-16
I'm sure that's not because of using ATI card, window corners should be transparent without any hardware acceleration, as they work for with my ATI card (without any compositing manager, or hardware acceleration), as well as my old machine with integrated Trident Blade 3D..

I suppose that this doesn't help anything, as I have no idea how to fix that problem :/

---

### Post by Cufishing on 2005-11-16
As stated, ATI and transparebt windows 'do not compute'. Sounds like a config issue. As my windows are transparent with my ATI card.

But, to get your card back to smoking that other card brand, go here for the driver install update.

[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+driver](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+driver)

---

