---
title: "Regular Unity no longer loads"
date: 2012-07-12
forum: Desktop Environments
---

### Post by rattata on 2012-07-12
I've been having a problem for a while where regular Unity will not load the top panel or the launcher. I can still launch the terminal, but I can't open the dash. I can still log out using Ctrl + Alt+ Del. Unity works perfectly fine in 2d, however.

I USED to be able to use regular Unity, so I don't know why it's not working now. Perhaps an update broke it? I don't know enough about Ubuntu to diagnose the issues, so I'm hoping I can get some help with it.

I'm using Ubuntu 12.04 on a Toshiba Satellite C670, which uses Intel.

---

### Post by Krytarik on 2012-07-12
Since you can't have an issue with proprietary video drivers, which can be broken by a kernel upgrade if installed manually, because there are no for Intel graphics, this should only be a settings issue - please see if following this guide helps fixing it:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Regards.

---

### Post by lolpenguin on 2012-07-13
```
unity --reset
```
If it was not mentioned in the link.

---

