---
title: "Single core showing up as dual core"
date: 2009-02-17
forum: General Help
---

### Post by jondecker76 on 2009-02-17
I just installed 0810 on an old Dell Dimension E310.
This computer has a single core P4 2.8 GHZ that is shown in system monitor as being a dual core. It even shows activity lines for both cores.

The machine is running incredibly slow (takes almost 45 seconds just to open a terminal window) and I'm wondering if it has anything to do with the CPU detection problem.

Any advice?

---

### Post by albandy on 2009-02-17
The system is reporting two cores because this machine has HT (Hyper Threading) capabilities.

Maybe you've a hw problem, reconfigure your BIOS, also you can disable HT if you think that this is the problem

---

