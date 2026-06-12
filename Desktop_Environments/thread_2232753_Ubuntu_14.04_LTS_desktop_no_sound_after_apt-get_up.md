---
title: "Ubuntu 14.04 LTS desktop no sound after apt-get upgrade"
date: 2014-07-03
forum: Desktop Environments
---

### Post by fire-fly2 on 2014-07-03
Hi 
My Ubuntu 14.04 LTS desktop, it was working fine initially.I just did an apt-get upgrade, after that on sound. Any ideal how to fix this ?

Thanks

Cheers
fire-fly

---

### Post by fire-fly2 on 2014-07-04
Hi 
did the following and reboot.

sudo apt-get --reinstall install build-essential linux-headers-`uname -r`

problem solved

---

### Post by Bucky Ball on 2014-07-04
Good find and fix. Please use Thread Tools to mark the thread as solved and help future travelers. ;)

---

