---
title: "Ati + VLC + compiz = crash"
date: 2009-06-01
forum: General Help
---

### Post by SpinningAround on 2009-06-01
When I activate compiz (medium or extra) and run a movie in fullscreen will Xorg crash (sound still playing) this only happen when compiz is activated if I do the same without compiz is everything working fine. 

ati HD 4670 card
Ubuntu 9.04

---

### Post by Legace on 2009-06-01
It's a issue with the FGLRX drivers. There is no true fix abailable at the moment.

For a partial fix, change the video output of VLC in the settings. Try X11 first, and if it doesn't work, then try the others :)

---

