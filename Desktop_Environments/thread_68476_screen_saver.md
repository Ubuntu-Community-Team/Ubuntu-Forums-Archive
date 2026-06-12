---
title: "screen saver"
date: 2005-09-23
forum: Desktop Environments
---

### Post by one_ro on 2005-09-23
Does anyone know how to start a screen saver from a shell? For example the clock screen saver.
Thx.

---

### Post by mlomker on 2005-09-23
[QUOTE=one_ro]Does anyone know how to start a screen saver from a shell? For example the clock screen saver.
Thx.[/QUOTE]

I spent a lot of time looking for an answer, but I can't figure it out.

**/usr/bin/kclock.kss** will open it but I can't find any command-line switches that will cause it to fill the screen.   ](*,)

---

### Post by one_ro on 2005-09-26
[QUOTE=mlomker]I spent a lot of time looking for an answer, but I can't figure it out.

**/usr/bin/kclock.kss** will open it but I can't find any command-line switches that will cause it to fill the screen.   ](*,)[/QUOTE]
Yep, the same happened to me. Argument --geometry doesn't seem to work. Strange though, because xclock _does_ work with -geometry...

---

### Post by one_ro on 2005-09-30
[QUOTE=mlomker]I spent a lot of time looking for an answer, but I can't figure it out.
**/usr/bin/kclock.kss** will open it but I can't find any command-line switches that will cause it to fill the screen.   ](*,)[/QUOTE]

Now here's a tip that I just got from Melchior FRANZ, the creator of this screeensaver:
$ dcop kdesktop KScreensaverIface save

Smooth :)

---

### Post by Takis on 2005-09-30
DCOP calls are so sweet.

---

