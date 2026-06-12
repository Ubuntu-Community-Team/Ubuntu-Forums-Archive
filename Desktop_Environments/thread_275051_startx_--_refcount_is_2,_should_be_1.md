---
title: "startx -- refcount is 2, should be 1"
date: 2006-10-10
forum: Desktop Environments
---

### Post by erikringmar on 2006-10-10
hi,

I left my computer on for a few days while I was away but on my return it's acting strangely.  I can't reboot from the regular splash screen.  Going into console mode and typing *serverx *I get an number of lines of messages and then

[INDENT]FreefontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1, fixing it.[/INDENT]

and then everything goes dead.  What to do?

yours,

Erik

---

### Post by gcastro on 2008-02-15
The fontpath message is a warning and happens when you exit X (somehow the fontpath is referenced twice but only unreferenced once, which results in this message).

There has to be some error before this, as X will only give the fontpath message when you exit from X.

For instance, my error was a .xsession file create in my home directory.

---

