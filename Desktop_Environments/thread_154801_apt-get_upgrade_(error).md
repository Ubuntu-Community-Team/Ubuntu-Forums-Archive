---
title: "apt-get upgrade (error?)"
date: 2006-04-03
forum: Desktop Environments
---

### Post by bpont on 2006-04-03
Can anyone explain what this means?

```
bpont@pooose:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
bpont@pooose:~$

```

---

### Post by Qrk on 2006-04-04
It means that to upgrade those packages would require installing/removing something else. 

You can upgrade them using the "smarter" upgrade, which will resolve these issues.

```
sudo apt-get dist-upgrade
```

---

### Post by TitusDalwards on 2006-04-22
with that command, i tihnk i will update my kernel image am i right?

---

