---
title: "RAM 95% full, system very slow"
date: 2008-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by keryonic on 2008-06-24
I have a Vostro 1310 with 2GB RAM, 4.5GB Swap

Sometimes my system becomes very slow and the hard disk starts spinning indefinitely. I opened (with a lot of patience) System Manager and I realized that my memory RAM was full at 95% (or more) and that Python was using about 1.5GB. I forced to close Python and I my computer returned to normal.

I think Emesene was causing the trouble (after closing Python, Emesene disappeared from Control Panel).

Last week I had the same problem with aMSN so I switched to Emesene. 

Anyone could explain me why that happened and what should I do to avoid further disturbances?

---

### Post by notwen on 2008-06-24
Open up a terminal and use the 'top' command and then open up either aMSN or Emesene and watch the memory usage for either.  If it continually rises for no reason, it would very likely be a memory leak.  Only thing you can really do is report it to the program's authors and hope they can locate and fix this issue.

Best of luck w/ your issue.  =]

---

