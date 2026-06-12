---
title: "ALSA to OSS"
date: 2007-09-26
forum: Gaming &amp; Leisure
---

### Post by saltedfish on 2007-09-26
Im trying to swtich from ALSA to OSS. This is the culmination in a long line of problems ive been having. you may or may not have seen my other posts. Anyway:

First: I get this error when I open winecfg:

```

/home/<user>/.wine/system.reg is not a valid registry file
/home/<user>/.wine/userdef.reg is not a valid registry file
/home/<user>/.wine/user.reg is not a valid registry file

```

then some bumpf about drivers not installed

when i change from ALSA to OSS, the change doesnt hold. I hit apply, but when I reopen winecfg, its set back to ALSA.

help?

---

### Post by Ferrat on 2007-09-26
try installing 

AOSS

also, remove your .wine dir, sounds like it has been corrupted

---

### Post by saltedfish on 2007-09-26
how do i do that?

also: you mean remove  *all* of the wine folders and subdirectories? cause I got stuff installed in there that I'd like to keep. Maybe Im just not interpreting your words correctly.

---

### Post by janfsd on 2007-10-07
Well just open the console and type: rm -rf ~/.wine
If you want to save your old wine folder just rename it: mv ~/.wine ~/wine_backup
And try wine again, if it works then as Ferat said your wine configuration has been corrupted.

---

