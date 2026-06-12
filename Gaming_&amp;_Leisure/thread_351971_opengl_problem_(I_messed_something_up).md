---
title: "opengl problem (I messed something up)"
date: 2007-02-02
forum: Gaming &amp; Leisure
---

### Post by jaytek13 on 2007-02-02
So, I was playing around with the xorg.conf file, as someone mentioned to me that adding option "NvAGP" "1" might improve performance. So, I added that, and then I proceeded to blacklist nvidia_agp and AGPGART in the modprobe.d/blacklist file. 

Turns out, it didn't improve performance at all. What it did do what cause a stuttering problem that is extremely annoying in any opengl app. Even in glxgears, the fps will run smoothly for about 5-10 seconds, then for 5 seconds there is a stuttering that knocks my FPS down from 7000 to 3000. Wouldn't be a problem, but the exact same thing happens in WoW, making it virtually unplayable.

So, easy solution is to remove what I changed, right? Wrong! I changed everything back to how it was before I started playing around, and the problem is still there. 

I know I've encountered this problem with Ubuntu before, and before I decided to just do a complete reinstall. This time I am curious if anyone else has experienced this problem or knows of a fix or at least what's causing it?

---

