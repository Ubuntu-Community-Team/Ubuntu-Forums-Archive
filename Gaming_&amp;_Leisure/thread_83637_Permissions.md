---
title: "Permissions"
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by tellnes on 2005-10-29
Is there a way in ubuntu to do what in windows is called "inherrited perrsmisions"? So i can set perrmissions on a folder, and the subfolder and files will innherit the permissions.

Also, running sudo et, makes et work with sound, i was playing fine for about and hour, then it just went out.
Is there a timeframe on running as sudo?

-tellnes-

---

### Post by paddyg on 2005-10-29
[QUOTE=tellnes]Is there a way in ubuntu to do what in windows is called "inherrited perrsmisions"? So i can set perrmissions on a folder, and the subfolder and files will innherit the permissions.

Also, running sudo et, makes et work with sound, i was playing fine for about and hour, then it just went out.
Is there a timeframe on running as sudo?

-tellnes-[/QUOTE]

chmod -R 755 /dir

(755 or whatever you'd like)

if you want to see what's happening:

chmod -R -v 755 /dir

for chmod options:

chmod --help

---

### Post by magnusbb on 2005-10-29
Is it possible to do this with Nautilus also?

---

### Post by paddyg on 2005-10-29
Never found that out. i've always used chmod, and it's very reliable (-R -v options). i think nautilus can only handle one file at a time.

---

