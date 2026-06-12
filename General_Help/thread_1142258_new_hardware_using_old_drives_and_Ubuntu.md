---
title: "new hardware using old drives and Ubuntu"
date: 2009-04-29
forum: General Help
---

### Post by cornflake000 on 2009-04-29
hello...

I am putting a new computer together and was wondering whether moving the hard drives strait across from the old system will work OK.  I have done this a couple of times with other OS's without too many problems but never with a Linux box.  More specific, should I expect Ubuntu to recognize the different cpu, mobo, ram, nic. etc. and gather the necessary information to update itself or should I just plan on reinstalling the root partition?

I'm running Jaunty and Intrepid.

Thank you!

---

### Post by cariboo on 2009-04-29
You can move your drives to your new hardware with less problems than doing the same thing with Windows.

---

### Post by mb_webguy on 2009-04-29
You shouldn't have any problems, as long as you're not changing architectures (e.g. AMD64 to i386, or either to ppc).  You might have to boot into recovery mode first and reconfigure xorg.conf for your new video card and monitor, but otherwise you should be fine.

---

### Post by cornflake000 on 2009-04-29
Fantastic!  Thanks....

---

