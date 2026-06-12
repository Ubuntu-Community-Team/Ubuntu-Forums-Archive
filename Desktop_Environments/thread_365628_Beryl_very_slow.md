---
title: "Beryl very slow"
date: 2007-02-19
forum: Desktop Environments
---

### Post by psychok9 on 2007-02-19
I've configured and installed Beryl and Beryl themes with AIGLX and ATi default ubuntu ati driver (with fglrx don't work)... but it's very slow...
I have read that with AIGLX it's fast... what's wrong?
Direct Rendering is enabled.

My system spec:
ATi X800 AGP
AsRock 939-DualSata2
AMD Athlon 64 X2 2.5GHz/500MHz DDR/5100+

---

### Post by orb9220 on 2007-02-19
A search of forums on ati x800
gave this thread you might try searching first.

[http://www.ubuntuforums.org/showthread.php?t=177184&highlight=ATi+X800](http://www.ubuntuforums.org/showthread.php?t=177184&highlight=ATi+X800)

---

### Post by psychok9 on 2007-02-20
Beryl don't work with fglrx driver! :(

---

### Post by igknighted on 2007-02-20
Keep in mind that the open-source radeon drivers are reverse engineered and not perfect... in fact the 3d support for the x800 is experimental at best.  A while back i wrote a tutorial using this card as an example, you could probably find it in a search.  It lists all the tweaks I know for that card that work.  I managed to get beryl running in a livable (albeit still very slow) state.  I later got fed up and stopped running beryl.  In Sabayon I use XGL and fglrx and the performance is almost 10x better (as judged by the beryl benchmark plugin).  If you really want beryl, look into fglrx/xgl.  Otherwise, I'd wait for ATI to add support for AIGLX or the radeon driver team to unlock some more potential from your card.

---

### Post by psychok9 on 2007-02-20
so, if i have understood, you know that i can't solve this very hard performance problem with ati generic driver?

In the past, with XGL, i have get crash problem...

I go to re-try.

Thank you.

---

### Post by igknighted on 2007-02-20
> **psychok9 said:**
> so, if i have understood, you know that i can't solve this very hard performance problem with ati generic driver?

In the past, with XGL, i have get crash problem...

I go to re-try.

Thank you.

The open source driver works great for non-3d applications, but the 3d support is still experimental and not quite ready for everyday use.  I agree that XGL is a pain, but if you want a really workable, fast beryl install it's the only option at this point.

---

