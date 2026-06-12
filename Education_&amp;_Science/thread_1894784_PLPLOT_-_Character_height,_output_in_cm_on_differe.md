---
title: "PLPLOT - Character height, output in cm on different PCs"
date: 2011-12-13
forum: Education &amp; Science
---

### Post by the_flo on 2011-12-13
Hi,  

I got a problem with the character output of plplots plschr() function  on different PCs.  
I tried my code on several different computers. On most PCs, the plot was as desired (default character height output in millimeter). But on two machines the character size in the plot was way too big. I realized that the character size on those machines is in centimeter instead of millimeter. So I tried to scale the default value to 1/10 of the size or to set plschr(0.1, 1) instead of plschr(1, 1), which worked both.  

But I think that's not the general solution. All PCs have the same plplot packages installed and the same Ubuntu distribution (11.10).  Any ideas? Btw, the same problem happened to a colleague several months ago, but disappeared for some reason.

Cheers,
F.

---

