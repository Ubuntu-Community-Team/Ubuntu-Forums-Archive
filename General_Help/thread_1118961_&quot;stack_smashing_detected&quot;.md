---
title: "&quot;stack smashing detected&quot;"
date: 2009-04-07
forum: General Help
---

### Post by ema24 on 2009-04-07
Hello!
I am a beginner.
Can anybody help me with the following problem:

*** stack smashing detected ***: 
executable file terminated
======= Backtrace: =========
....
======= Memory map: ========
....
09a84000-09aa5000 rw-p 09a84000 00:00 0          [heap]
b80d9000-b80dc000 rw-p b80d9000 00:00 0
bf8d3000-bf8e8000 rw-p bffeb000 00:00 0          [stack]

Thanx in advance.

---

### Post by rnjn.sinha on 2009-04-08
Can you elaborate a bit? Which application were you trying to execute when this happened? Can this be reproduced consistently. In any case this looks like a bug in the application and should be reported.

---

### Post by SBob on 2009-05-06
My own presumption is that this may have something to do with upgrading the system; My schism tracker said the same

> 
*** stack smashing detected ***: schism terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d77da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7d77d60]
schism[0x8094046]
schism[0x80855ec]
schism[0x807b085]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c90775]
schism(__gxx_personality_v0+0x2a9)[0x804c5c1]


The problem is that this happens to be my favorite program that has never failed for me... before the upgrade. And asked from the authors forum, it seems that this program has popped up in a rather large amount with specifically Ubuntu, lately, and the author knows not of what the error actually stands for (or that is the impression I'm under).

What we are interested is: What does "Stack Smashing" mean (I doubt it's an anime attack).

[edit:] fixed quote and disabled smileys.

---

