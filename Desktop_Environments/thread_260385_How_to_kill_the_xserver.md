---
title: "How to kill the xserver?"
date: 2006-09-18
forum: Desktop Environments
---

### Post by tomzero on 2006-09-18
Hello,
in order to complete the installation of the VMWare-Tools in need to have no XServer running. Whenever I kill X-Processes or gdm-Processes the Gnome-login-Screen immediately comes up again instead of showing an ascii terminal console.

How do I get rid of any running instance of X?

thanks in advance,

Tom

---

### Post by ayoli on 2006-09-18
try this:
```
sudo /etc/init.d/gdm stop
```

---

