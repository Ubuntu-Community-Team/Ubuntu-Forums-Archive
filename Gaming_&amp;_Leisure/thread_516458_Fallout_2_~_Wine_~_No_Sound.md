---
title: "Fallout 2 ~ Wine ~ No Sound"
date: 2007-08-03
forum: Gaming &amp; Leisure
---

### Post by darkadvice on 2007-08-03
After looking around the forums, I can't find an answer to this problem i've been having with fallout 2, there is no sound whatsoever in movies/gameplay. And it's not some volume control panel overlook, it's just not coming up at all in this game. Has anybody had this/ or knows a solution to it?

---

### Post by benx009 on 2007-08-03
try "winecfg" in a terminal and click on the audio tab.  there are some settings there you may want to check out  (for example trying using the ALSA driver instead of OSS)

---

### Post by benx009 on 2007-08-03
also: install the libjack0-dev package (available in the ubuntu repos) and see if using the JACK driver works for you.

---

### Post by darkadvice on 2007-08-03
> **benx009 said:**
> try "winecfg" in a terminal and click on the audio tab.  there are some settings there you may want to check out  (for example trying using the ALSA driver instead of OSS)

Thank you very much, this worked perfectly.

---

### Post by Duncan_Idaho on 2007-08-03
darkadvice, a quick question
the fadein-fadeout effect is "fixed"?
I remember I tried playing FO2 last year, but those effects where incredible slow :confused:

by fadein-fadeout I mean when the screen goes dark and then returns to normal, when an event happens or when you change area :P

---

### Post by shad0w_walker on 2007-08-03
Its not fixed, but if you use this command it goes basically normal speed:

```
nice -19 wine <path to fallout>
```

It should run nice and fast for you now. Enjoy.

---

### Post by Duncan_Idaho on 2007-08-03
> **shad0w_walker said:**
> Its not fixed, but if you use this command it goes basically normal speed:

```
nice -19 wine <path to fallout>
```

It should run nice and fast for you now. Enjoy.

well, I'll try that, thanks :)

---

### Post by darkadvice on 2007-08-04
> **Duncan_Idaho said:**
> darkadvice, a quick question
the fadein-fadeout effect is "fixed"?
I remember I tried playing FO2 last year, but those effects where incredible slow :confused:

by fadein-fadeout I mean when the screen goes dark and then returns to normal, when an event happens or when you change area :P

Actually mine just skips them (Or it's going to fast for me to see them) but I really don't mind that at all.

---

