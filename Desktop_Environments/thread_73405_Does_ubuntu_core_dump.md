---
title: "Does ubuntu core dump ?"
date: 2005-10-09
forum: Desktop Environments
---

### Post by dbee on 2005-10-09
Hi guys,

I'm just wondering is there any ubuntu equiv of Dr. Watson in windows, where I can have a look at the core dump after a system crash ??

cheers,

---

### Post by Zwack on 2005-10-09
Depending on what you are trying to analyse then, yes there are special tools...

Did the whole system crash (Oops/Kernel Panic) or just an application (core)...

If it's just an application you might want to check the ulimit settings... By default it should be for a 0 byte core file.  this stops your disk from filling up with data you're ignoring...

If you do have a core file then you might want to run gdb on it... 

If it's a Panic/Oops then there are things you can look at...

[http://iven.home.cern.ch/iven/linux_debug/linux_crash.html]("http://iven.home.cern.ch/iven/linux_debug/linux_crash.html")

Z.

---

### Post by skoal on 2005-10-09
There's a blast from the past.  I haven't seen a core dump in ages on a linux box.  I remember way back when on prior Redhat <5.0 days, those things use to show up as "skull and cross bones" or a "black timebomb with a fuse" icon in the file manager.  I forget which one.  I just deleted them all and went about my merry ignorant way...

\\//_

---

### Post by Zwack on 2005-10-09
[QUOTE=skoal]There's a blast from the past.  I haven't seen a core dump in ages on a linux box.  I remember way back when on prior Redhat <5.0 days, those things use to show up as "skull and cross bones" or a "black timebomb with a fuse" icon in the file manager.  I forget which one.  I just deleted them all and went about my merry ignorant way...

\\//_[/QUOTE]

Frankly unless you a) know what you're doing and b) are getting irritated by the problem (it's not just a once in a blue moon thing) then delete and move on is about all you can do...

Z.

---

