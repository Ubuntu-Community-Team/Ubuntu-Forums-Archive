---
title: "Google Earth graphics problem"
date: 2009-03-04
forum: General Help
---

### Post by Firebat451 on 2009-03-04
When I try to run Google Earth on Ubuntu 8.10 the graphic of Earth does not display correctly at all.  All I get is a gray flickering box over the whole display area with an intermittent flash of the globe.  I'm pretty sure this is because I'm using on board video and it's not powerful enough for Google Earth.  My desktop is a Sony Vaio (not my choice) with a pcie4 slot and I'm looking to get a video card to fill my needs.  I don't need to do much, not a big 3d gamer or anything, so what suggestions do people have for a card I could get?  Thanks a bunch.

---

### Post by solwic on 2009-03-04
> **Firebat451 said:**
> When I try to run Google Earth on Ubuntu 8.10 the graphic of Earth does not display correctly at all.  All I get is a gray flickering box over the whole display area with an intermittent flash of the globe.  I'm pretty sure this is because I'm using on board video and it's not powerful enough for Google Earth.  My desktop is a Sony Vaio (not my choice) with a pcie4 slot and I'm looking to get a video card to fill my needs.  I don't need to do much, not a big 3d gamer or anything, so what suggestions do people have for a card I could get?  Thanks a bunch.

Are you running an ATI video card?  If so, do you have desktop effects enabled?  ATI drivers don't like composited video.

Try turning off desktop effects (Right click on desktop, change background, Visual effects) and see if that fixes it.  

Good luck.  

As for a card, nVidia works much better than ATI with Linux.  :)

EDIT:  If it's an ATI/Desktop Effects problem, you should have the same trouble with watching movies (MPlayer, VLC, etc.).  Turning off the effects will fix that, too.  

Also, if you are using an ATI, they supposedly released a new driver, on their site, that "fixes" the compositing issues.  I haven't tried it, so don't know if it works or not.  :)

---

### Post by Firebat451 on 2009-03-04
> **jrock612 said:**
> Are you running an ATI video card?  If so, do you have desktop effects enabled?  ATI drivers don't like composited video.

Try turning off desktop effects (Right click on desktop, change background, Visual effects) and see if that fixes it.  

Good luck.  

As for a card, nVidia works much better than ATI with Linux.  :)

EDIT:  If it's an ATI/Desktop Effects problem, you should have the same trouble with watching movies (MPlayer, VLC, etc.).  Turning off the effects will fix that, too.  

Also, if you are using an ATI, they supposedly released a new driver, on their site, that "fixes" the compositing issues.  I haven't tried it, so don't know if it works or not.  :)

While I don't have a problem with movies, that did solve the flickering problem, and after disabling atmosphere the problem of running impractically slow changed to a somewhat jerky, which I can live with.  However there is still a problem with the text in the 3d display.  Only about 10% of the characters show correctly, the rest is just distorted pixels.  The characters which display also changes randomly when I move around and zoom.

I'll try to update my driver, but how do I find out what video card I have?  My searching before hand came up empty.

---

