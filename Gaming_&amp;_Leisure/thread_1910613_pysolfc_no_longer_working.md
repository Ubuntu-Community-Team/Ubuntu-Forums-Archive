---
title: "pysolfc no longer working"
date: 2012-01-17
forum: Gaming &amp; Leisure
---

### Post by a z on 2012-01-17
running Lubuntu 11.10 on an hp-mini 110
PySol Fan Club (solitaire) used to work great - now it starts to run, and that little load-bar gets about half way, and nothing... re-installed it - removed it and re-installed - even downloaded it from the pysolfc website - still the same results...
and yes, i have python2.7 installed as well as python-tk (in fact, i have a nearly identical Lubuntu desktop box, on which pysolfc runs fine, so i searched "python" on synaptic on that box, then duplicated all-things-python on my hp-mini) still nothing. 
any ideas?
thank you

---

### Post by DoktorSeven on 2012-01-17
Try removing your settings (~/.pysolfc) and running again.

---

### Post by a z on 2012-01-17
no settings in there. they're created when you successfully run the game. 
even after deleting everyything on the entire computer having to do with pysolfc (including my ~/.pysolfc folder), and re-installing, it doesn't fully start, so it doesn't write any settings. i even tried to fake it out, and copied my ~/.pysolfc folder from my other computer (where it works fine) to my hp-mini, but that didn't work either.
rrrr

---

### Post by a z on 2012-01-17
okay, got it.. 
i'd removed pulseaudio for some other reason, and that was apparently what it wanted. i discovered this by running 'pysolfc' in a terminal (instead of the menu), to see if it mentioned any errors - and sure enough, it said, "sound system not found" or something like that.
cool

---

### Post by a z on 2012-01-17
okay, got it.. 
i'd removed pulseaudio for some other reason, and that was apparently what it wanted. i discovered this by running 'pysolfc' in a terminal (instead of the menu), to see if it mentioned any errors - and sure enough, it said, "sound system not found" or something like that.
cool

---

### Post by a z on 2012-01-17
now how do i change the heading in the first post to [SOLVED] again?

---

### Post by a z on 2012-01-17
got it
peace,
a z

---

### Post by Soulcage on 2012-01-17
Click on thread tools if the feature still exists. I think it comes and goes.

---

