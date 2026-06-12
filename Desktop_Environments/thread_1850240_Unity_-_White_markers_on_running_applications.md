---
title: "Unity - White markers on running applications"
date: 2011-09-26
forum: Desktop Environments
---

### Post by stocton12 on 2011-09-26
I have reinstalled Ubuntu 11.04 and I really like unity plugin. The problem that I have is that now in the launcher there are no white markers on the left and right of the running applications. Any ideas?

---

### Post by stocton12 on 2011-09-30
Anything?? :confused:

---

### Post by Krytarik on 2011-09-30
Make sure that the meta-package "ubuntu-desktop" is installed and, therefore, all of it's dependencies as well (this also includes the "unity" package and *its* dependecies):
```
sudo apt-get install --reinstall ubuntu-desktop
```If that doesn't help, try resetting all your Unity settings. Therefore, see the instructions under the section "Reset Unity" in this guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

And/or check if the issue is present in a new, fresh user account, too.

Hope any of this helps!

---

