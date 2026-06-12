---
title: "start fluxbox with KDM?"
date: 2007-01-29
forum: Desktop Environments
---

### Post by Absurd on 2007-01-29
I know that there's a way to start fluxbox through gdm, but is there a way to start fluxbox through kdm?

I can't find .xinitrc

---

### Post by KaeseEs on 2007-01-29
You probably can't find your .xinitrc because you don't have one - it's not there by default.  Your ~/.xinitrc is a script that, if present, will be run when you start x without a desktop manager (ie. via either startx or xinit).  FWIW mine reads```
#! /bin/bash
fluxbox


```.

As for running Flux with KDM, it should only entail adding the Fluxbox session to your KDM sessions file.

---

