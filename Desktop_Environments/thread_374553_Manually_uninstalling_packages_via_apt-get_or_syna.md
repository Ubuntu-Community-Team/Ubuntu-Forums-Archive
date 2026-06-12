---
title: "Manually uninstalling packages via apt-get or synaptic"
date: 2007-03-02
forum: Desktop Environments
---

### Post by jboehm on 2007-03-02
Hi,

I need to be able to refuse the removal of some files during a package uninstall via synaptic or apt-get.

I installed a package via apt-get then installed a later version from source.  Now I need to uninstall the apt-get version but keep it from deleting shared config files and data spaces.

Any idea how I do this?

Thanks,
Jon

---

### Post by adieb on 2007-03-02
i think there is a better way, but i´d do it that way:

if you deinstall something like "programm" it should keep its config stuff in "$home/.programm", but why not take a backup...

---

