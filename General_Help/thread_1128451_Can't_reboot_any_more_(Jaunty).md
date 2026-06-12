---
title: "Can't reboot any more (Jaunty)"
date: 2009-04-17
forum: General Help
---

### Post by Chris on 2009-04-17
Is it just me or did something get updated recently that makes it so you can't reboot any more?

If I try to reboot, either by the gnome menu "restart", by using "reboot" from a command line or pressing ctrl-alt-del from a console, I see the system shutdown graphic which counts all the way down then the boot**up** graphic appears and counts back up until X starts again.  :(

---

### Post by danwood76 on 2009-04-17
Are you saying it doesnt go all the way back to the POST screen but does do a shutdown restart according to the graphics.

WHen its reloading try hitting ctrl + alt + F1, that should show you the kernel output of it booting up.

---

### Post by Chris on 2009-04-17
Right, it was not actually rebooting the machine to the POST screen.

Turns out that it was because I installed the "kexec-tools" package.

Looks like this bug still exists in Jaunty:
[https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/251242](https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/251242)

Not getting a good feeling about the Jaunty release.

---

### Post by danwood76 on 2009-04-17
Theres still a few days of bug pounding to go :D

---

