---
title: "Cairo Dock glitch"
date: 2008-03-15
forum: Desktop Effects &amp; Customization
---

### Post by Vnepomuceno on 2008-03-15
Hey guys!

I've recently installed Cairo Dock in my Ubuntu 7.10, but I've noticed that when I initialize it, it has a big glitch. Check it out:

[[IMG]http://img142.imageshack.us/img142/3070/capturaecracpiazt8.th.png[/IMG]](http://img142.imageshack.us/my.php?image=capturaecracpiazt8.png)

Do you know how to solve this problem?

---

### Post by hyperair on 2008-03-15
If you're referring to the black portions, that's caused by Cairo Dock attempting to use compositing when a composite manager is not present. Solution: Use xcompmgr, or turn on desktop effects.

---

