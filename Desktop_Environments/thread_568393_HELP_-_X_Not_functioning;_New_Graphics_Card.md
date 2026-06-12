---
title: "HELP - X Not functioning; New Graphics Card"
date: 2007-10-05
forum: Desktop Environments
---

### Post by bluemike807 on 2007-10-05
Hi - I recently installed a new graphics card, upgrading from an ATI Radeon 9800XT to a X1600 :
Linux will no longer launch a GUI, saying that the X server settings are wrong and it cannot start.

What do I do? I cant even get a command line.

Please help

---

### Post by goatflyer on 2007-10-06
Restart and select recovery mode from the grub menu

at the root prompt type:

dpkg-reconfigure xserver-xorg

.. and answer the questions.

---

