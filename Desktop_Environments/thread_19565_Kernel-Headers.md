---
title: "Kernel-Headers?"
date: 2005-03-12
forum: Desktop Environments
---

### Post by kepsux on 2005-03-12
I'm a Ubuntu/Debain newbie, but not a Linux newbie. What' the process involved in installing kernel-headers on Ubuntu? I have tried to apt-get them...but no dice. 

```
sudo apt-get install kernel-headers-`uname -r`
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package kernel-headers-2.6.8.1-3-386

```


Thanks for any pointers in advance!

---

### Post by -DomiNator- on 2005-03-12
You can search .debs in apt with the command sudo apt-cache search blablabla, but while ubuntu hoary is running kernel 2.6.10, i only could find the 2.6.9 kernel headers and source so i couldn't run the ati driver from ati.com.

My workaround was to download a kernel form kernel.org and use it.

---

### Post by az on 2005-03-12
In ubuntu, it is linux-headers

apt-cache search linux headers
 


The same goes for linux-source instead of kernel-source,

---

### Post by kepsux on 2005-03-13
[QUOTE=azz]In ubuntu, it is linux-headers

apt-cache search linux headers
 


The same goes for linux-source instead of kernel-source,[/QUOTE]

Awesome. Thank you!

---

