---
title: "no sound in second session"
date: 2005-04-20
forum: Desktop Environments
---

### Post by dovik on 2005-04-20
hi, when i launch a second graphical session, the sound doesn't work.

it's seems to be a problem of "right".

if i launch "Rhythmbox", an error occur : "could not open resource for writing"

the 2 users are in the "audio" group.

(i'm using Gnome)

(please, excuse my poor english)

---

### Post by ilari on 2005-04-20
[QUOTE=dovik]hi, when i launch a second graphical session, the sound doesn't work.

it's seems to be a problem of "right".

if i launch "Rhythmbox", an error occur : "could not open resource for writing"

the 2 users are in the "audio" group.

(i'm using Gnome)

(please, excuse my poor english)[/QUOTE]
 Your system might not be able to do hardware mixing, so that the two different esd-sound servers started by the two different users can not work side by side. You should check, if using ALSA-directly, or if using some kind of software mixing helps.

---

