---
title: "gracefully close programs at logout? (instead of killing them)"
date: 2009-02-04
forum: Desktop Environments
---

### Post by jaygo on 2009-02-04
I'm using ubuntu + gnome 8.10 and upon logout, restart, etc., it kills most of my open programs causing them to crash and sometimes lose data. The exception I've found is when I've got gedit open, it may prompt me to save the document before closing.

I'd prefer to have the shutdown process close all my apps with the same effect as me clicking close on each of them. That way, I can take advantage of their built-in "save your file?" functionality. Perhaps even firefox wouldn't always start up with a crash report.

Ideas?

---

### Post by perixx on 2009-02-04
whoops, wrong one, sorry

---

### Post by jaygo on 2009-05-11
bump.

---

### Post by kpkeerthi on 2009-05-11
At shutdown, a TERM signal is first issued (**the first warning**). Programs can listen to this signal and can respond to it and optionally close itself gracefully. 

And after a few seconds, a KILL signal is issued to terminate all non-responding programs. It is not possible to trap the KILL signal and any program that did not heed to **the first warning** are brutally **terminated**.

Gedit was able to trap the TERM signal and hence it prompted you to save the unsaved file(s). So if any program did not close gracefully at shutdown, its the program's fault (a bug, may be) and not the Operating System's. The Operating System always gives all running programs a first chance to close itself gracefully.

---

### Post by mikezila on 2009-05-11
> **kpkeerthi said:**
> At shutdown, a KILL signal is first issued (**the first warning**). Programs can listen to this signal and can respond to it and optionally close itself gracefully. 

And after a few seconds, a TERM signal is issued to terminate all non-responding programs. It is not possible to trap the TERM signal and any program that did not heed to **the first warning** are brutally **terminated**.

Gedit was able to trap the KILL signal and hence it prompted you to save the unsaved file(s). So if any program did not close gracefully at shutdown, its the program's fault (a bug, may be) and not the Operating System's. The Operating System always gives all running programs a first chance to close itself gracefully.

I think you have TERM and KILL backwards.

---

### Post by kpkeerthi on 2009-05-11
> **mikezila said:**
> I think you have TERM and KILL backwards.
LOL!. Good catch. Updated the post.

---

