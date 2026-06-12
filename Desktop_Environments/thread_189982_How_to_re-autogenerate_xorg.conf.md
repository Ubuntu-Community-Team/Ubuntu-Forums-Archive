---
title: "How to re-autogenerate xorg.conf?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by RPG405 on 2006-06-05
Hi, I installed Ubuntu 6.06 with a Dell CRT monitor. I just bought and installed a nice Samsung LCD flat panel (SyncMaster 730B). However, my xorg.conf file still shows my Dell CRT and does not list my Samsung (hence I hadn't had it when I installed Ubuntu). I do not know the specs of my monitor at length, and don't feel comfortable "guessing" on how to add my new monitor to the xorg.conf file. Is there a way to automatically (meaning with assistance from another program) add my Samsung to xorg.conf ? Or do I have to grin and bear my Dell's CRT settings on my Samsung.

Cheers, RPG

---

### Post by grigpi on 2006-06-05
Try:
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions.

---

