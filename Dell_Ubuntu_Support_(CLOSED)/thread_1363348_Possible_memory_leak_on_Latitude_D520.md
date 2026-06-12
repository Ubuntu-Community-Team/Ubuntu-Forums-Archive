---
title: "Possible memory leak on Latitude D520"
date: 2009-12-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zslastman on 2009-12-24
Hi guys.System monitor is currently telling me that about 90% of my ram is in use. This is true even just after I've restarted, despite the fact that my base level used to be about 20% - 30% after a restart (with an identical set of programs installed, though I've just updated my 9.10 installation). "top" is telling me the same, but as far as I can see the memory usage for the programs being listed just doesn't add up. Whats going on? Incidentally, I've only got 512mb of ram on this thing, would I be better of with Xubuntu? (I've had vicious problems getting the wireless running on this thing so I'm reluctant to switch). And is there by the way some benifit to using the the Dell specific installation DVD (again, reluctant to reinstall unless it's a big one). Sorry bout the many questions. Heres the output of ps aux:

---

### Post by lloyd_b on 2009-12-24
Could you post the output from running "free" in a terminal window?  I'm curious to see if that "used" is actually mostly buffers/cache, or if it's actually being used by programs.

Lloyd B.

---

### Post by zslastman on 2009-12-27
Thanks anyway. The problem has fixed itself after a restart. Although for the record system monitor was telling me that most of the memory was in use rather than for cache or swap.

---

