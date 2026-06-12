---
title: "boot time"
date: 2008-08-06
forum: Desktop Environments
---

### Post by Chillawowa on 2008-08-06
So what is the average boot time for ubuntu on recent systems?

Just wondering as most boot speed tests show 20 to 40 seconds, while mine takes a bit under 2 min:(, even after following several boot speed up tutorials, including removiong unwanted servivces, readahead...

Moritz

---

### Post by DaneM on 2008-08-07
When you get the GRUB prompt (you may have to press escape after the POST screen), select your kernel, then press "e".  Go the "kernel" line and press "e".  At the end, remove the "quiet" and "splash" options, and post any error messages you see.  You can press the scroll lock button on your keyboard to pause the output so you can write it down.

--Dane

---

