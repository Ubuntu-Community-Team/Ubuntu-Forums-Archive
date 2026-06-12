---
title: "Shutting down xserver"
date: 2005-01-29
forum: Desktop Environments
---

### Post by Ricapar on 2005-01-29
I'm trying to install drivers for my video card, but the X server can't be running during the install. How do I shut it down?

EDIT: Nevermind, I got it.

---

### Post by az on 2005-01-29
CTRL-ALT-F1

login

sudo killall gdm

(make and install your dirver)

sudo gdm

---

