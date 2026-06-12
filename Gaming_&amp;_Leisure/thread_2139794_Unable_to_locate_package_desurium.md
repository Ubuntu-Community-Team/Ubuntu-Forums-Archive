---
title: "Unable to locate package desurium"
date: 2013-04-27
forum: Gaming &amp; Leisure
---

### Post by rudeboyskunk on 2013-04-27
So, after installing Ubuntu 13.04 64-bit, I was adding all of my repositories like usual, including the Desurium repo.  However, when I sudo apt-get update and then "sudo apt-get install desurium," I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package desurium

```

Is anybody else having this problem?  I tried the "stable" ppa, got this message, so I purged it.  Then I tried the "weekly" ppa, and I still get this same message.  I checked sources.list, everything matches what it says on the ppa page, and I get no connection errors when I apt-get update, so I'm pretty much at a loss.

---

### Post by ibjsb4 on 2013-04-27
There is no 13.04 release for this package.  12.10 was the last build, maybe it will be out in a while.

---

### Post by rudeboyskunk on 2013-04-28
Ah, well that sucks.  Thanks for the info.

Can I just replace "raring" with "quantal" in sources.list?

---

