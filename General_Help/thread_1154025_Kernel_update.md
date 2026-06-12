---
title: "Kernel update"
date: 2009-05-09
forum: General Help
---

### Post by RedSingularity on 2009-05-09
I was just wondering why a kernel update would adversely effect the operation of hardware on your computer?  Say a wireless device in working perfectly, then you update the kernel and you looses functionality all together.  I would think that the newer kernel would still support what it used to as well as some other added features......thus making it a "newer" kernel.

---

### Post by mb_webguy on 2009-05-09
Sometimes support for legacy hardware is dropped from recent kernel builds, but more likely loss of functionality is a regression in an updated driver.

---

### Post by RedSingularity on 2009-05-09
What do you mean by a regression?

---

### Post by alexcckll on 2009-05-10
> **Shadow121 said:**
> What do you mean by a regression?
Google is your best friend in this situation - [http://en.wikipedia.org/wiki/Software_regression](http://en.wikipedia.org/wiki/Software_regression)

It's something that just should not happen, and should be caught before release... as it's one of the most infuriating things for downstream users.

---

### Post by collinp on 2009-05-10
Major code changes, software regression (as said above), and a multitude of other things can cause problems like you described. Its the nature of software.

---

### Post by RedSingularity on 2009-05-10
Ohhh i see.  Thanks guys.  That question has always been on my mind.

---

