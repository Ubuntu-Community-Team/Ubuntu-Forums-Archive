---
title: "Preventing a package to upgrade"
date: 2006-06-05
forum: Desktop Environments
---

### Post by lzap on 2006-06-05
Hello,

I have one extra repository with english directories for stardict. It regenerates every day so the update manager wants to install a new version every day. Its fairly big.

Can I prevent a repository or a package from upgrading? I mean - to force apt-get to ignore newer versions.

Thanks for help

---

### Post by Wermut on 2006-06-05
I use aptitude for package management. Pressing = prevents the selected package from upgrading. Maybe this is what you were looking for, but I am not sure if this setting is respected by other frontends such as adept or synaptic.

---

### Post by meng on 2006-06-05
Synaptic - find the package you want, then from the menu choose Packages > Lock Version.

---

