---
title: "Xserver-Xgl crash before login, found the problem"
date: 2006-06-10
forum: Desktop Environments
---

### Post by kayrune on 2006-06-10
With the xserver-xgl from the dapper repos it is working ok, however if I use the new versions of xgl and compiz from beerorkid repo then the xserver crash right after the nvidia logo.

I have now found what is causing this. It's the EVDEV mouse driver. If I use the default "mouse" driver everything is ok, as soon as I change xorg.conf to use evdev, the xserver crash without an error message on next login.

Can anyone confirm, and report this bug where it's supposed to ?

---

### Post by tommie-lie on 2006-06-21
[QUOTE=kayrune]Can anyone confirm, and report this bug where it's supposed to ?[/QUOTE]I can confirm this bug. There seems to be some bug in the device initialization function of Xglx that causes a segfault on termination of the function. I don't know the exact reason, but I posted the bug to the mailing list for further confirmations and a possible comment from the developers.

---

### Post by kayrune on 2006-07-15
Any news on this bug ?

---

### Post by tommie-lie on 2006-07-15
Unfortunately not and it still doesn't work.
I'll re-post my mail to the ML, maybe David overlooked it.

---

### Post by gils0040 on 2006-08-31
i can confirm this bug as well. i am using the beerorkid repos and xgl crashes on gdm start. if anyone finds a fix please post it! :)

---

