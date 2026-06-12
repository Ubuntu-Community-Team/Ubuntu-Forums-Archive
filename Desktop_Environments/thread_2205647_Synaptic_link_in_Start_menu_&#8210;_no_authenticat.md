---
title: "Synaptic link in Start menu &#8210; no authentication prompt"
date: 2014-02-15
forum: Desktop Environments
---

### Post by engine on 2014-02-15
Kernel		: Linux 3.11.0-15-generic (i686)
Compiled		: #25-Ubuntu SMP Thu Jan 30 17:25:07 UTC 2014
Distribution		: Ubuntu 13.10
Desktop Environment		: LXDE (Lubuntu)

Start button, System tools, Synaptic doesn't prompt me for a password, so I can't actually download/install anything. (sudo synaptic works as required) What do I have to edit to get the link working correctly?

Thanks in advance!

---

### Post by Dennis N on 2014-02-15
Check the command being used in the menu. It should be:

**synaptic-pkexec**

Reference:
[http://www.freedesktop.org/software/polkit/docs/0.105/pkexec.1.html](http://www.freedesktop.org/software/polkit/docs/0.105/pkexec.1.html)

---

