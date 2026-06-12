---
title: "Core Temperatures Now Different While Idle"
date: 2009-01-25
forum: General Help
---

### Post by jpass on 2009-01-25
I'm running 8.10 with all updates as of this message.

I normally have the CPU temperature applet running because I'm paranoid about such things.  And until very recently when my system was idle, the temperatures for both cores were always within a degree of each other.

Now, that's no longer the case.  While idle, I see one core is typically 3 to 4 degrees hotter than the other.  When not idle, both cores are usually at the same temperature.

My concern here isn't the temperature difference.  Rather, what I'm curious about is if there has recently been a change to the Linux scheduler that would account for this difference?  I doubt it has anything to do with CPU frequency scaling, but if it matters, I usually have that set to "on demand".

---

### Post by sdennie on 2009-01-25
What CPU are you using?  Most (if not all) use a single temperature sensor for all cores.  Maybe you are seeing a difference because the two cores are polling at different intervals and reporting different temperatures.

---

