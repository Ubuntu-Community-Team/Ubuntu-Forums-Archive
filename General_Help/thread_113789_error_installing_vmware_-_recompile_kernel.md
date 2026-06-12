---
title: "error installing vmware - recompile kernel?"
date: 2006-01-07
forum: General Help
---

### Post by nandasunu on 2006-01-07
I get this error during configuration:

> Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl
with CC environment variable pointing to the "gcc" version "3.4.5".


I have no clue how to recompile the kernel. please help :(

---

### Post by nandasunu on 2006-01-07
never mind, I have sorted the problem (with help of #kubuntu irc) :p

---

### Post by MartinG on 2006-01-07
No, you don't need to recompile the kernel, but you do need to install and use gcc-3.4. First install that```
sudo apt-get install gcc-3.4
```then, just before launching vmware-config.pl, do```
export CC=gcc-3.4
```This will tell vmware-config.pl to use the correct compiler.

All this assumes you have the headers for your running kernel installed :)```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by nandasunu on 2006-01-07
MartinG: Thanks for that, its all working great now.

---

