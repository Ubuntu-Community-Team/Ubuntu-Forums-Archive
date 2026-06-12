---
title: "Performance Question - Quad Core Xeon (5500)"
date: 2009-05-06
forum: Education &amp; Science
---

### Post by toddpedlar on 2009-05-06
This is a generic performance question for those of you doing modelling with your linux boxes... I'm likely to be purchasing several rack-mounted machines in the very near future, and am considering single Quad-Core Xeons in the Newhalem (5500) series, which seem to be fantastic performance-wise.  But - I'm curious about your experience with them, if any has any wisdom to offer.

---

### Post by Xnst on 2009-05-15
Hi toddpedlar,

at my institute we run a linux cluster for our FE-calculation and we had some performance issues with the quad core CPUs. It seemed the memory bus was too slow and we did not see any performance increase when all quad cores were used. We now have, in the cue handler, blocked two cores at each processor.

Just to be clear, FE-calculations are intense in memory usage and if you intend to do other types of modelling quad cores could be just what you are looking for.

---

