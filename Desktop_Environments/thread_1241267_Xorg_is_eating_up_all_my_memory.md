---
title: "Xorg is eating up all my memory"
date: 2009-08-15
forum: Desktop Environments
---

### Post by yeeeev on 2009-08-15
Dear compiz users support group:),

I've been using Ubuntu with compiz as a main OS on my laptop for over 6 months.
A few days ago I noticed that Xorg is inflating...
It starts out as ~100M and 1-2 days later it reaches even 1G.
I ran xrestop, and killed all the processes that consume most pixmaps (compiz included), but xorg's footprint remained unchanged.

2 major changes in the last few days:
* Started using Chrome as a main browser
* Enabled window previews in compiz

My video card: nVidia Corporation GeForce 8600M GT (rev a1)
I'm using the proprietary drivers, v. 180

Did anyone else experience such a problem?

---

### Post by coldReactive on 2009-08-15
It's probably Chrome. Internet Browsers are notorious for causing xorg to inflate, I even get firefox to push up xorg.

---

### Post by yeeeev on 2009-08-15
Thanks for your reply.
Any way to get proof of that? (besides trying to work without chrome). Are there any logs that can show it?
And most of all, if Xorg doesn't deflate when chrome is down, isn't it a Xorg bug?

---

### Post by signseeker on 2009-08-16
> **yeeeev said:**
> Thanks for your reply.
Any way to get proof of that? (besides trying to work without chrome). Are there any logs that can show it?
And most of all, if Xorg doesn't deflate when chrome is down, isn't it a Xorg bug?

You could try using top or conky to determine where the ram is going. 

I found that using particular websites can make firefox etc use way more ram (those that use flash etc) - so it could be just related to that. 

Good Luck.

---

### Post by coldReactive on 2009-08-16
> **signseeker said:**
> You could try using top or conky to determine where the ram is going. 

I found that using particular websites can make firefox etc use way more ram (those that use flash etc) - so it could be just related to that. 

Good Luck.

Should've seen what my ATI Radeon HD3200 did in Ubuntu 8.10:

[https://bugs.launchpad.net/fglrx/+bug/296497](https://bugs.launchpad.net/fglrx/+bug/296497)

---

### Post by signseeker on 2009-08-16
> **coldReactive said:**
> Should've seen what my ATI Radeon HD3200 did in Ubuntu 8.10:

[https://bugs.launchpad.net/fglrx/+bug/296497](https://bugs.launchpad.net/fglrx/+bug/296497)

Funky. I don't think I've ever owned an ATI card.

---

### Post by yeeeev on 2009-08-16
top shows that Xorg (/usr/X11R6/bin/X) is taking over ~700MB of memory (using top & ps)
I suspect it is somehow related to npviewer.bin (the flash player).
I found some weird logs in kern.log that seemed like their occurrences were somewhat related to the memory increases (even though I have no proof yet).
The log is:
kernel: [54560.404738] npviewer.bin[7996]: segfault at aff1d39f ip aff1d39f sp bf907690 error 4

Any thoughts?

---

