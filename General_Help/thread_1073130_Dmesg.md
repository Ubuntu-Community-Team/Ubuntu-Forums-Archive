---
title: "Dmesg"
date: 2009-02-18
forum: General Help
---

### Post by Lekshmi on 2009-02-18
i have some doubts on command dmesg.
i got the information like number associated with the information printed by dmesg is the seconds from startup.
How can it be??

i got like this..
[66389.777510] Goodbye, cruel world

which one is second?? what representation is this?

---

### Post by dcstar on 2009-02-18
> **Lekshmi said:**
> i have some doubts on command dmesg.
i got the information like number associated with the information printed by dmesg is the seconds from startup.
How can it be??

i got like this..
[66389.777510] Goodbye, cruel world

which one is second?? what representation is this?

------
`dmesg` output contains the record of the bootup process annotated with time since loading the kernel with sub-second timestamp resolution
------

---

### Post by Lekshmi on 2009-02-18
Thank you.........

---

