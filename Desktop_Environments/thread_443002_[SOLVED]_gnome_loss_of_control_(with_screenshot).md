---
title: "[SOLVED] gnome loss of control (with screenshot)"
date: 2007-05-14
forum: Desktop Environments
---

### Post by ogomoe on 2007-05-14
This is a feisty 7.04 livecd instalI.

I don't know what I've done to alter my desktop, but now I have no control over my gnome (ubuntu -- not kubuntu, xubuntu, etc.) windows.

This is a Feisty Live CD install.  Here is a screenshot (130kb)...

I've tried changing my theme, but that was not the fix.

---

### Post by Ateo on 2007-05-14
Looks like your window decorator crashed. Does it fix anything if you run```
$ metacity --replace&
``` from terminal?

---

### Post by ogomoe on 2007-05-14
That was the fix!

Ateo, thank you very much.

---

