---
title: "Lost the Ubuntu 3D login option (Ubuntu 12.04)"
date: 2012-09-27
forum: Desktop Environments
---

### Post by pschalkx on 2012-09-27
Hi guys,

I have lost the Ubuntu 3D login option (the one that appears on the splash screen).

What happened:

I installed compiz and the compiz settings manager. I could didn't find it useful so I removed all the compiz packages.

After logging out I now only have the 2D login option. I reinstalled compiz and the OpenGL compiz package to no avail.

Any suggestions on how to get the 3D login back? I´d hate to reinstall the whole system...

Thanks in advance!

---

### Post by Krytarik on 2012-09-29
Just (re)install the 'ubuntu-desktop' meta-package to reinstall the regular Unity as well as any other packages that were removed due to the removal of Compiz and have not been reinstalled since (and are covered by that meta-package or its dependencies/recommends):
```
sudo apt-get install ubuntu-desktop
```Regards.

---

