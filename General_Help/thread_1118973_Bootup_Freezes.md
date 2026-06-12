---
title: "Bootup Freezes"
date: 2009-04-07
forum: General Help
---

### Post by tp-owner on 2009-04-07
When I turn my computer on it freezes, So I went into recovery mode and I get:

common problems:
boot args (cat/proc/cmdline)
check rootdelay=(did the system wait long enough?)
check root=(did the system wait for the right device?)
missing modules (cat/proc/modules; ls dev)

Alert! does not exist. dropping to a shell


I cannot get back into ubuntu anymore. I had recently changed the file /etc/modprobe.d/alsa-base... When I say changed I mean deleted and put something else in. Reason: [this thread]("http://ubuntuforums.org/showthread.php?t=188736&highlight=tweaking+the+thinkpad")

*exit does NOT work*

---

### Post by tp-owner on 2009-04-07
SORTED

I re-installed ubuntu!

---

