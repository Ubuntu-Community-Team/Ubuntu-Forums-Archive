---
title: "VMware 5 - How does it work? - Hoary"
date: 2005-05-04
forum: Desktop Environments
---

### Post by russx2 on 2005-05-04
**Woops! Mods, please move this to Hoary forum. Apologies!** 

Hi,

Just looking for a bit of info on what exactly the install process of vmware 5 does? I successfully installed it and it runs fine. However, it stopped ndiswrapper from functioning and as such I now have no network connectivity.

Does vmware recompile the kernel and hence break ndiswrapper? Or does it just need the current kernel sources to build its own modules?

Also, if I was to upgrade ubuntu's kernel in the future, does this mean I'd have to reinstall vmware?

Any advice would be appreciated  :-) 

Russ

p.s. On an unrelated note, if anyone happens to know how to compile apache with mod_rewrite in hoary (and not getting a 'missing GDBM' error) please give me a shout :-) Thanks.

---

### Post by jeb0921 on 2005-05-04
vmware only needs the kernel sources to build its modules.  As far as upgrading to a new kernel, I don't know if ou need to reinstall vmware or not.

---

