---
title: "XDCMP, gdm.conf, and server-Chooser"
date: 2005-09-19
forum: Desktop Environments
---

### Post by jpmcc on 2005-09-19
I want to be able to log on to several different hosts, so in *gdm.conf* I set
```
[servers]
#0=Standard
0=Chooser
```
So far so good. The *Chooser* screen lets me select which host to log in to; I then get the *Login* screen for that host. On exit, I return to the *Chooser* screen.
However, I find I have lost the Shutdown/Restart options from the *Login* screen, so I have no way to shutdown the computer other than *sudo poweroff* from a terminal window.

Is there a way to keep the Shutdown/Restart options on the *Login* screen?

Thanks - John

---

