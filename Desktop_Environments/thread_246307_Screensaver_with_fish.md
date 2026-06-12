---
title: "Screensaver with fish?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by nocturn on 2006-08-29
Do any of you know a gnome-screensaver hack with fish?
It's for my 2year old son who loves to look at them.

A program simulating an aquarium or something similar would also be nice.

Thanks

---

### Post by mcduck on 2006-08-29
Sure!. Try Atlantis, it's in one of the screensaver packages available from repositories. Try searching for 'screensaver' (in synaptic) and you'll find the package :)

---

### Post by orb9220 on 2006-08-29
I searched for Atlantis and it wasn't there by name and screensaver.

Must be a dead fish?

---

### Post by nocturn on 2006-08-29
It's in xscreensaver-gl-extra.  I'll try it tonight, thanks

---

### Post by mcduck on 2006-08-29
> **nocturn said:**
> It's in xscreensaver-gl-extra.  I'll try it tonight, thanks
If you have XGL/Compiz installed install wxinwrap (from Compiz repositories) and you can have a nice animated underwater background on your desktop with something like this:
```
xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/atlantis -window-id WID -count 12 -gradient -texture
```

---

