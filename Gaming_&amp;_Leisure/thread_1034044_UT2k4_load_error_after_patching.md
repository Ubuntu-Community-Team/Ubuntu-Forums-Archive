---
title: "UT2k4 load error after patching"
date: 2009-01-07
forum: Gaming &amp; Leisure
---

### Post by beastrace91 on 2009-01-07
I am running Ubuntu 64bit and after patching UT2k4 to the latest version I now get this upon trying to load the game ```
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: wrong ELF class: ELFCLASS64
```

I found it is a common issue but I cannot figure out the fix, many old threads I found suggested installing some extra library I installed them but still no luck. Any suggestions? Please?

~Jeff

---

### Post by beastrace91 on 2009-01-16
*bump* Anyone know where I can download the "libSDL-1.2.so.0" file from? It is all I need to get this working...

~Jeff

---

### Post by Cappy on 2009-01-16
Look at the "Updating" section in:
[http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004)

---

### Post by beastrace91 on 2009-01-17
> **Cappy said:**
> Look at the "Updating" section in:
[http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004)

Your the best.

~Jeff

---

### Post by beastrace91 on 2009-01-17
Hey there,

That guide worked well, only thing not sure if this is for everyone but I also needed to go get ```
sudo apt-get install libstdc++5
``` before UT2004 would load, maybe that should get added to the guide?

~Jeff

---

