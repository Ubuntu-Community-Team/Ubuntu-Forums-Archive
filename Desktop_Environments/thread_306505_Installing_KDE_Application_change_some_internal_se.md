---
title: "Installing KDE Application change some internal setting of gnome application - wine?"
date: 2006-11-25
forum: Desktop Environments
---

### Post by tomcheng76 on 2006-11-25
Hello
Recently i just aptitude installed Kdevelop, K3B, Amarok etc,  without installing KDE
when i enter winecfg and choose voice setting
here is the error
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/bomber/.kde/socket-ubuntu.
can't create mcop directory

however, if i  mkdir /tmp/ksocket-<user name>
it will be fine.
I just wondering why this happen. why does wine need to create link to .kde ?
I hope that this would not happen again, as it will drive me nuts ....
how to reset wine to use something like .gnome ?
thanks!

---

### Post by tomcheng76 on 2006-11-25
anyone know why would this happen?
and it seems i need to mkdir every time after i reboot...
hope someone can fix this annoying problem
any help would be appriciated

---

