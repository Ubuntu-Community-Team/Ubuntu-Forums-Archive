---
title: "Conky: keeps on flickering"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by oldcpu on 2007-05-26
It flickers really bad.  And frequently disappears for a few seconds.

"double buffer" is not working.

Take note that my CPU is 500MHz and it is on laptop.  I have almost the same specifications on my desktop, and it is nowhere this bad.

Please help.

---

### Post by chewearn on 2007-05-27
Did you add

Load "dbe"

to the Section "Module" in xorg.conf?

---

### Post by oldcpu on 2007-05-27
That solved it.  Thanks.

I did not know I had to do that.  From my previous experience, it worked fine without it.  I thought it was my low specifications causing it.

---

