---
title: "question about sleeping processes"
date: 2009-03-06
forum: General Help
---

### Post by eival on 2009-03-06
do sleeping processes still use/take up the Virtual, Resident, Writable, Shared memory that the system monitor says they are?

or is that only a reference for when it does start running?

---

### Post by murataht on 2009-03-06
According to the "Operating System" text books, they should reside somewhere in the memory or virtual memory, waiting for being woken up again by the system...

System should know where they are (has a reference to them), and they should take some memory to preserve their previous running states, so that they could start just from where they have stopped...

for more information, at least check wikipedia...

---

