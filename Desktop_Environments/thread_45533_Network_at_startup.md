---
title: "Network at startup"
date: 2005-06-30
forum: Desktop Environments
---

### Post by stevanhe on 2005-06-30
Hi u all
I have a problem, my network card tryes to connect to the lan at every startup, it takes around 1 minute, i let you imagine how annoying...
How can I disable the boot of the network?

tnx

Stevanhe :)

---

### Post by moment on 2005-06-30
open a terminal. type:
```
sudo gedit /etc/network/interfaces
```
comment out the line with "auto eth0".
I recommend that you install "ifplugd" as well.

---

