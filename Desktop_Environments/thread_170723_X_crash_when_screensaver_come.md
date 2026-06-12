---
title: "X crash when screensaver come"
date: 2006-05-05
forum: Desktop Environments
---

### Post by SilvioTO on 2006-05-05
this morning, after latest update on breezy, when screensaver start, X reboot and show login screen. Any suggestion to resolve this problem?

Thanks.
Silvio.

---

### Post by tseliot on 2006-05-05
I had exactly the same problem.

You need to reinstall the drivers for your graphic card.

---

### Post by SilvioTO on 2006-05-05
I'll try, thanks.

---

### Post by SilvioTO on 2006-05-05
I'm reinstalled graphic driver and only with official nvidia version 1.0-8178 my pc don't freeze or restart X. Now the 3D screensaver don't work, a black screen only; strange. Not important thing, I'm disabled the screensaver. I'm waiting for Dapper!!

Hi!!

---

### Post by SilvioTO on 2006-05-05
I found the problem... my xorg.conf; I had tryed compiz-glx effect and after don't cancel options in it... :-$ :-o

---

