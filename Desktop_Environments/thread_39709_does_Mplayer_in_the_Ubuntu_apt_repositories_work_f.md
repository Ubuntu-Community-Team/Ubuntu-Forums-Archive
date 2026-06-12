---
title: "does Mplayer in the Ubuntu apt repositories work for you?"
date: 2005-06-06
forum: Desktop Environments
---

### Post by hkl8324 on 2005-06-06
i cant get it to run.

i can get Mplayer to run by compling source, though.

Dev please fix the problem.

---

### Post by darky83 on 2005-06-06
Any details why it doesn't work (error msgs, logfiles etc?)..

I had to install libmikmod2 see also:


[http://www.haverlach.nl/archives/cat_4.html](http://www.haverlach.nl/archives/cat_4.html)

---

### Post by xao on 2005-06-06
There is a nice little walkthrough  at [http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer).

Just follow the directions he has laid out for you. Worked like a charm for me.

---

### Post by bored2k on 2005-06-06
[QUOTE=darky83]Any details why it doesn't work (error msgs, logfiles etc?)..

I had to install libmikmod2 see also:


[http://www.haverlach.nl/archives/cat_4.html](http://www.haverlach.nl/archives/cat_4.html)[/QUOTE]
 It's of common knowledge you to install codecs in Ubuntu: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by betrayed on 2005-06-06
[QUOTE=hkl8324]i cant get it to run.

i can get Mplayer to run by compling source, though.

Dev please fix the problem.[/QUOTE]
 well I could get the non gui one to run(the version I use anyway) but it choked on dvd's something with the 5.1 audio playback.  I compiled my own using the debian/rules included with the source(modified a bit though, I prefer it to be optimized for my cpu no runtime checking), got my deb package and installed.  Works fine, the firefox player plugin works as well.

---

### Post by hkl8324 on 2005-06-07
[QUOTE=darky83]Any details why it doesn't work (error msgs, logfiles etc?)..

I had to install libmikmod2 see also:


[http://www.haverlach.nl/archives/cat_4.html](http://www.haverlach.nl/archives/cat_4.html)[/QUOTE]

gmplayer does start, but when i press the "open" button, it hangs.

no error if i bulid mplayer from source.....

---

