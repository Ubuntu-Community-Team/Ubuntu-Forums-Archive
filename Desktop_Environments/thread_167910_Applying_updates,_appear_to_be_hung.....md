---
title: "Applying updates, appear to be hung...."
date: 2006-04-29
forum: Desktop Environments
---

### Post by s1gnAl on 2006-04-29
I just did a fresh install on a new computer and I am applying updates. I appear to be hung while trying to install a new kernel, this is where it stopped in the terminal window:

```
Setting up linux-image-2.6.12-10-386 (2.6.12-10.30) ...
```

I'm afraid to kill the process and/or reboot because I don't want to hose my installation. Any ideas? It has been this way for the last hour. 

System specs:
Asus K8V SE motherboard
Athlon 64 3000 (socket 754)
Geforce 5900FX 256mb AGP card
512mb Crucial RAM PC-3200

---

### Post by Kethinov on 2006-04-29
You're probably safe killing it and trying it again. Even if it does bork that kernel, your last kernel should be perfectly okay since Ubuntu doesn't delete old kernels unless you explicity do so yourself.

---

