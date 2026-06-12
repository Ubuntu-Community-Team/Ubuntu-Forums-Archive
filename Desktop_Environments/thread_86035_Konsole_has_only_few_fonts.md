---
title: "Konsole has only few fonts"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Reaktor on 2005-11-04
Hi,

after being unable to find solution by myself, I'm asking what could be the problem for having only few fonts available in Konsole? Snapshot included, [http://reaktor.no-ip.info/jaettavat/fontprob.png](http://reaktor.no-ip.info/jaettavat/fontprob.png)

I have installed mscorefonts and those show up in other programs, but Konsole is lacking all additional fonts. Currently having this problem in fresh Kubuntu install. As you can see, running Irssi with such a poor font is annoying :p

---

### Post by Manny C on 2005-11-04
Ah...but this is normal. Konsole will only display monospace fonts....and there aren't that many.

CORRECTION: Konsole doesn't come with many fonts configured...it allows fonts other than monospace fonts. For example, Serif...

---

### Post by Reaktor on 2005-11-04
Well, still you should be able to tell that the fonts available on picture are NOT the ones preferred to use in any console...

Anyways, the problem was too simple. After installing MsCorefonts I didn't restart X, which seemed to be necessary for Konsole to recognize the new fonts.

---

