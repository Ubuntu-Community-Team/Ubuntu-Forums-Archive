---
title: "Slow internet / Network Fixed?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Profusion on 2006-06-29
I think I may have fixed my slow internet / network lag problems.
Can someone with the same problems confirm its not just me?

In your Terminal cut and past this will force your network card to perform at 10mbps full duplex.

sudo mii-tool --force 10baseT-FD

Let me know.

---

