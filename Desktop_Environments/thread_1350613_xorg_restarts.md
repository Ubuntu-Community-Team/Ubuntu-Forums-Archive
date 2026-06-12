---
title: "xorg restarts"
date: 2009-12-09
forum: Desktop Environments
---

### Post by DaleEMoore on 2009-12-09
In a new 9.10 install Xorg restarts just like I'd run "sudo /etc/init.d/gdi restart" every few minutes. It does not do the restart if I'm not using the machine.

I moved the HDs to another machine that's the same hardware and get the same behaviour.

I haven't noticed anything in /var/log/messages, /var/log/Xorg.0.log, or /var/log/gdm/:0.log that would help me diagnose the problem.

Any suggestions are appreciated.
Dale E. Moore

---

### Post by DaleEMoore on 2009-12-12
Posted to VirtualBox bugtracker [here]("http://www.virtualbox.org/ticket/5719").
Posted to Ubuntu Forums [here]("http://ubuntuforums.org/showthread.php?t=1350613").
Posted to Ubuntu Launchpad [here]("https://bugs.launchpad.net/xserver-xorg-driver-vesa/+bug/495916").

---

### Post by DaleEMoore on 2009-12-17
I wiped the boot HD and installed Ubuntu 9.10. Copied .VirtualBox back and it's running without problems now.

---

