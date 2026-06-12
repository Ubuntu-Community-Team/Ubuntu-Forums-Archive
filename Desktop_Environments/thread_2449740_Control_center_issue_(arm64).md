---
title: "Control center issue (arm64)"
date: 2020-09-01
forum: Desktop Environments
---

### Post by ryniobl on 2020-09-01
Hello everybody :)

I'm extremely happy with Ubuntu MATE performance on my RaspberryPi 4 but there is one thing that is annoying. 
Right after system boot when the desktop is loaded, a Control Center window pops up, and it does so pretty often especially when I watch YouTube, it pops up on top of everything, and every time I have to close it and then it pops up again and again after few minutes. Is there any way to disable it or uninstall?

Richard

---

### Post by ActionParsnip on 2020-09-02
That would be the mate-control-center package but do a dry run (with no system changes) with:
```

sudo apt-get --simulate remove mate-control-center

```
I suggest you investigate why this is occurring though and use this as a last resort. If the above command starts pulling out lots of packages then it's a bad idea.
I personally run LXDE on Pi systems. Its super light and slick

---

