---
title: "xorg.conf"
date: 2006-03-01
forum: Desktop Environments
---

### Post by xhie on 2006-03-01
I know I should probably know the answere to this by now but...

Say I change my xorg.conf file, which I do all the time, is there a way to get the changes to take affect without restarting X?

---

### Post by Ramses de Norre on 2006-03-01
I don't think so, X only reads the file at start up.

---

### Post by engla on 2006-03-01
It's almost certainly not possible.

What you could do is use either the console or a tool like Xgame to launch a new x session without closing the old one, to test your new settings.

---

