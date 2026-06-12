---
title: "No sound in Firefox this time :-)"
date: 2005-10-06
forum: Desktop Environments
---

### Post by Jackster on 2005-10-06
Hey people, another sound problem, this time to do with Firefox, not ScummVM :) .
Basicall,y there is no sound in Flash or Shockwave, i've not tested other sound things in FF but i dont suppose they'll work either.
It used to work, but it isnt now for some reason, must have messed something up while trying to fix ScummVM's sound (Which still isn't working!). Using ALSA.

Using Ubuntu 5.04, but installed KDE 3.4.1 and im using it mainly.

---

### Post by Dolphin on 2005-10-06
Try this:

type
```
killall esd
```

then open firefox.

---

### Post by Jackster on 2005-10-06
Nope, still no sound, I get the message when I type killall esd
esd: no process killed
:confused:

---

