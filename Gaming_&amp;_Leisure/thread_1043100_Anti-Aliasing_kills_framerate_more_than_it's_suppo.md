---
title: "Anti-Aliasing kills framerate more than it's supposed too..."
date: 2009-01-18
forum: Gaming &amp; Leisure
---

### Post by cdahmedeh on 2009-01-18
Hello,

I have a Dell XPS m1530 with a 8600m GT video card. Drivers version 173,178 and 180 all have the same issue. In Windows, I was able to enable Anti-Aliasing without framerate dropping. However, in Linux the effect is very noticeable. For example, if I enabled anti-aliasing, everything is very sluggish. Without AA, moving the Windows with Compiz is very smooth, but with AA, the windows move slowly with low framerate. I also notice the same problem in many games espicially those in Wine. If I run Live for Speed for example, in Wine, I get 100+ FPS without Anti-Aliasing. However, when its enabled, I get less than 15 and that is without Compiz enabled.  In Windows, my framerate would always stay very high, even though I enabled 8x AA.

So how to solve such problem ?

Thanks

---

### Post by eragon100 on 2009-01-18
Have you checked your nvidia linux driver settings? Maybe you have accidently enabled AA there as well, which would mean it would be done twice.

If you have not it's certainly strange, since on my 512 MB GeForce 8600 GT
I can play Doom 3 on ultra quality at 1680x1050 with 16x AA without any slowdowns at all. ET:QW also runs at the same quality/framerate. And I have the same card.


For wine, it might just be that some direct3d functions that are used by windows games for AA haven't been (efficiently) included in the wine windows direct3d API tough,
which would make it very work-intensive to convert those function calls to OpenGL, thus making the game run slow.

---

