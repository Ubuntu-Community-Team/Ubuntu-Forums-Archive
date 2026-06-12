---
title: "starting a second Xserver from console as non-root"
date: 2005-01-17
forum: Desktop Environments
---

### Post by vpalle on 2005-01-17
Im trying to run  startx -- :2 as non-root ( i use it to play quake3 ), but im getting:

Using authority file /tmp/.gdm0vyaSc
Writing authority file /tmp/.gdm0vyaSc
Using authority file /tmp/.gdm0vyaSc
Writing authority file /tmp/.gdm0vyaSc
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console

So I guess Im not authorized.. How do I get authorized?

---

### Post by vpalle on 2005-01-17
man Xwrapper.config

---

