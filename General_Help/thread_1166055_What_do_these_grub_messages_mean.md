---
title: "What do these grub messages mean?"
date: 2009-05-21
forum: General Help
---

### Post by inverseroom on 2009-05-21
When I boot up my fresh install of Jaunty (HP dv3 laptop, dual booted w/Vista), I get this on the screen for a moment before Ubuntu boots:

> Starting up...
[     2.840067] ata1: softreset failed (device not ready)
[     3.488062] ata2: softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

Did something fail during my install?  The word FATAL is a bit frightening.  Everything seems to be working OK in Jaunty, except Wine.

Thanks!

---

### Post by apjone on 2009-05-21
Please remember to search google / ubuntuforums - take a look at :-

[http://www.uluga.ubuntuforums.org/showthread.php?t=1162619](http://www.uluga.ubuntuforums.org/showthread.php?t=1162619)

I think wine not working is a seprate issue

---

### Post by inverseroom on 2009-05-21
Ah, thank you--sorry for repeating.  it didn't occur to me that this was a common error...

---

### Post by apjone on 2009-05-21
No problem, due to the wide use of grub, Linux and the way it works it is very rare if you are the only person to get a error.

---

### Post by inverseroom on 2009-05-21
That linked cured the fatal error!  Thanks a lot.  Now, onto the softresets...

---

### Post by inverseroom on 2009-05-21
Hmm, there seems to be some confusion about the softresets...for now I'll just leave it, since I'm booting up without any other problems.

---

