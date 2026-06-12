---
title: "L3 cache"
date: 2009-03-16
forum: General Help
---

### Post by bobmatino17 on 2009-03-16
what is L3 cache compared to L1 and L2?

---

### Post by Chops II on 2009-03-16
The higher the number of cache generally means physically further from the processor, faster more expensive memory and less storage space. L3 caches are generally large and are sometimes off chip.

[Link to Wiki article on CPU Cache - Multi-level Caches]("http://en.wikipedia.org/wiki/CPU_cache#Multi-level_caches")

---

### Post by sdennie on 2009-03-16
Caches are used to hide latencies for getting information to the CPU.  Linux caches disk reads to hide the latency of going to disk, Samba probably caches network reads to hide the latency of going to the network.  Without even looking up what an L3 cache is, I can guess that it's a cache to hide the latency of going from memory to L2 cache/L1 cache/CPU.  So, like all caches in computers, it makes commonly used things faster by storing them "closer" to the CPU.

Though, googling for "L3 cache" could probably provide you with a more accurate and detailed definition.

---

