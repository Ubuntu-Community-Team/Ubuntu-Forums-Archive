---
title: "No sound in Frozen Synapse"
date: 2013-06-29
forum: Gaming &amp; Leisure
---

### Post by ninjaondemand on 2013-06-29
I recently downloaded frozen synapse from the humblebundle. My game does not have any music or sound (that plays). I already checked the volume settings, so it is not that.

---

### Post by tidalwave on 2013-07-01
> **ninjaondemand said:**
> I recently downloaded frozen synapse from the humblebundle. My game does not have any music or sound (that plays). I already checked the volume settings, so it is not that.

Worked for me:

sudo ln -s libopenal.so.1 /usr/lib/i386-linux-gnu/libopenal.so

That's the dirty way that works. Others have reported that putting the symlink in the frozensynapse works.

---

