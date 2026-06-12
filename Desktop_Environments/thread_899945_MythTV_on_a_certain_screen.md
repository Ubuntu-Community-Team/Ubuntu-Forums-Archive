---
title: "MythTV on a certain screen"
date: 2008-08-24
forum: Desktop Environments
---

### Post by kg4gyt on 2008-08-24
I'm running two monitors on an NVIDIA card, using Xinerama, and I would like to keep using that mode so that I can drag windows between the two screens.

I start having trouble when I want to start MythTV.  I would like to run MythTV on the non-primary monitor, however no matter what I try, it always starts there.

Is there any way to force an application to run on a certain screen?

tia

---

### Post by txcrackers on 2008-08-25
In Xinerama, your screens are designated :0.0 and :0.1. Practically all X-based programs take the "display" command-line flag to specify which display to use. So...
```
mythfrontend -display :0.1
```
should do what you want.

---

