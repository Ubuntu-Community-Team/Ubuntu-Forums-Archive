---
title: "GTKPod dependency (libatk1.0-0) and repository problems"
date: 2006-09-17
forum: Desktop Environments
---

### Post by cornycopious on 2006-09-17
I'm having trouble installing GTKPod.  It tells me the dependency libatk1.0-0 is unresolved, but libatk1.0-0 *is* already installed.  I got GTKPod (and then tried GTKPod-aac) from packages.ubuntulinux.org.  Both of them have the same dependency on libatk1.0-0. Then I tried adding the backport repository to see what happened if I tried installing GTKpod via terminal.  Terminal can not find anything related to GTKPod, even with backport enabled. When I try to install libatk1.0-0 it says "same version already installed".  I tried reinstalling it but that didn't help.

Thanks!
Alan

---

### Post by lamego on 2006-09-17
The dependency problem is because either you are missing the extra repositories or you have non official repositores on your list which are causing the problems.

Just enable the extra repositories:
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

And install gtkpod from synaptic.

---

### Post by cornycopious on 2006-09-17
Perfect, thank you!

---

