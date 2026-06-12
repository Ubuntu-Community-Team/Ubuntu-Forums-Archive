---
title: "Will additional desktop environments slow down my OS?"
date: 2011-10-20
forum: Desktop Environments
---

### Post by woodyg on 2011-10-20
Hi,
this may or may not be a stupid question... but running Ubuntu, will installing additional desktop environments, such as xfce, lxde and kde, slow down the overall performance of my OS, or will it make absolutely no difference? My general feeling from installing additional applications is that eventually the OS will start to feel a bit sluggish. This may due to some other issue, but that is my feeling.

So can I install additional desktop environments without any slowdown in performance?

---

### Post by snowpine on 2011-10-20
Nope, additional DE's will just sit there taking up space on your hard drive until you actually use them, at which point they are loaded into RAM.

---

### Post by woodyg on 2011-10-20
And is it the same with installing additional applications, i.e. no impact on the overall performance (and they aren't running in the background)? That is my first thought, that it will have no impact, it seems logical, but my experience says something different... 

If installing additional applications have no impact on performance, why would my OS feel sluggish after a while?

---

### Post by snowpine on 2011-10-20
> **woodyg said:**
> If installing additional applications have no impact on performance, why would my OS feel sluggish after a while?

You can use the terminal command 'top' to see which processes are using your CPU and RAM.

---

### Post by randywilharm on 2011-10-20
System Monitor/Processes should give you a good idea about CPU usage
and other specs but click the tab at top of memory column several times to
make highest usage show at top of column.

It's a little friendlier than HTOP & no, applications don't run in the background
enough to affect your system when they're off.

---

