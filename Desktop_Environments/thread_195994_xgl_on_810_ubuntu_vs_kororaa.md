---
title: "xgl on 810: ubuntu vs kororaa"
date: 2006-06-13
forum: Desktop Environments
---

### Post by rolfijn on 2006-06-13
Hello there,

There are several posts in this forum about getting xgl/compiz running on a computer with intel video card (extreme graphics and such, often found on centrino based laptops from ibm and hp) using the i810 driver. The posts are related to getting it running smooth, or at least at all. In on of this posts forum-poster "cruiser" claims he got xgl/compiz running smooth on his hardware using the kororaa live-cd, but using ubuntu dapper he was stuck with flickering and artefacts.
Now i've had the same experience. On my ibm thinkpad r51 with an 82852/855GM video adapter, performance is very poor. However,  using the kororaal live-cd it works like a charm, no performance-problem at all, very smooth. So, the hardware is not the problem. Does anybody have an idea what the difference may be between ubuntu dapper and kororaa as far as xgl/compiz is concerned.

Rolf Deenen

---

### Post by arrizaba on 2006-06-13
Perhaps it uses AIGLX?

Compiz works wonderfully in combination with AIGLX on intel graphics cards (using the i810 driver). Check:

[http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)

---

### Post by mrvw0169 on 2006-06-13
Yup, the only way I've had smooth 3d effects is to just use AIGLX and the difference in speed is like night and day using the above forum thread... XGL just won't work with any acceleration at all on these Intel cards...

---

### Post by yteh on 2006-06-13
Same here... aiglx+compiz on my acer laptop.... I followed the howto that arrizaba referred to.... worked like a charm.

---

### Post by rolfijn on 2006-06-14
Ok, going to try this evening! It sounds very plausible. Strange though that searching for aiglx on the kororaa site or wiki finds 0 results... :confused: But this is probably more a kororaa issue.

---

