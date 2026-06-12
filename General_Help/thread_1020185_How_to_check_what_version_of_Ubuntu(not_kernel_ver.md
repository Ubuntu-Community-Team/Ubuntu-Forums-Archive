---
title: "How to check what version of Ubuntu(not kernel version)?"
date: 2008-12-23
forum: General Help
---

### Post by Vista1330 on 2008-12-23
How do I check what version of Ubuntu I am using?
Ok I installed from the disk that says Desktop edition but I understand u have the normal version and the 64bit version. My processor supports 64bit and in case of emergency I still have Vistax64(x64 stands for 64bit O/S version), so I am pretty sure my hardware supports 64bit O/S. I installed a device information/computer information software and I couldn't find anything about how many bits my O/S is using?

---

### Post by bodhi.zazen on 2008-12-23
uname -m

For version of Ubuntu

cat /etc/issue

---

### Post by tuxxy on 2008-12-23
To check if your running 64-bit open a terminal and type

```
uname -m
```You will see something like the following; x86_64 GNU/Linux

If you have the  x86_64 present your running 64-bit Ubuntu 

Also if you want the Ubuntu specific version enter

```
lsb_release -a
```

---

### Post by adult swim on 2008-12-23
if you go to a terminal and enter in ```
uname -a
``` it will return some information.  toward the end it will say someithing like i586, i686 or x86_64.  if it is x86_64 then you have the 64 bit version of ubuntu.  if it is not then its the 32 bit version.

---

