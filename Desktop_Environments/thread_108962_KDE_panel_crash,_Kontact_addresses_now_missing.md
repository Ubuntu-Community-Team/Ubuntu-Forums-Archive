---
title: "KDE panel crash, Kontact addresses now missing"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Seth Williamson on 2005-12-27
I am running Kubuntu 5.10, after having installed Ubuntu from CD--I upgraded to Kubuntu via apt-get.

A few days after I installed it, I noticed that, when I clicked on the Kontact icon, it would give me the "spinning clock" icon for a good deal of time, and then stop as if the app were then up--only it wasn't.  I had to click it a second time to make Kontact appear.

Yesterday I started to get error messages saying that the KDE panel had crashed.  I saved the backtrace for one of these.  Then yesterday, I also noticed that my Kontact addressbook for Kmail had vanished.

I just started kontact under kde in a terminal to see if I'd find any error messages, and I got this:

seth@orthobox:~$ kontact
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
seth@orthobox:~$ WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.

I don't know what this means.  Does anybody have any idea what's going on here?  And how to fix it?


Seth Williamson
Slings Gap
Franklin County, VA
USA

---

