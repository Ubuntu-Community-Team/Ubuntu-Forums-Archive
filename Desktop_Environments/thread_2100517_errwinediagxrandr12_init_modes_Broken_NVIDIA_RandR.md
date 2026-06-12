---
title: "err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR"
date: 2013-01-02
forum: Desktop Environments
---

### Post by user2037 on 2013-01-02
Running Wine produces some errors which I suspect are preventing me from getting an Opengl game working:

"err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead."

It's not exactly clear how one activates the Nouveau driver with Ubuntu 12.04. I suspect deactivating the proprietary driver does it. Although, doing so did not seem to help (perhaps I need to restart).

Any ideas?

---

### Post by alexeusgr on 2013-02-04
For me the problem was solved by deleting .wine dir in /home

---

