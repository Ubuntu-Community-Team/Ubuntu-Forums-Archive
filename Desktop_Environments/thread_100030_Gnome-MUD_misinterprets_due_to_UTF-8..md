---
title: "Gnome-MUD misinterprets due to UTF-8."
date: 2005-12-06
forum: Desktop Environments
---

### Post by phibxr on 2005-12-06
I used to use GMuddix to connect to one of my most used MUDs, which is a Swedish MUD utilizing the special characters "å", "ä" and "ö" among others, bud had to switch to Gnome-MUD since i replaced my AMD with a PPC, for which no precompiled binaries of GMuddix are to be found (not to mention that the project really is quite outdated by now).

In GMuddix, however, I'm not given a choice of character encoding, so it expects that the data sent from the MUD will be in UTF-8, even if I start it with the following:

```
LC_ALL="sv_SE.is885915" gnome-mud
```

, resulting in "å", "ä" and "ö" displaying as squares in the text.

Is there any solution to this problem?

---

