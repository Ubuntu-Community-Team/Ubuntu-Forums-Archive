---
title: "Ubuntu 10.04 - libapt-pkg4.12 broken"
date: 2012-10-16
forum: Desktop Environments
---

### Post by 3boxes on 2012-10-16
Update manager is broken, & when I try to re-start my dual-boot XP/Ubuntu 10.04 386-based machine in recovery mode & repair broken packages, I get:

E:  Unable to correct dependencies
...
The following packages have unmet dependencies:
 libapt-pkg412: Depends: libc6 (>= 2.15) but 2.13-35 is installed 

Running sudo apt-get -f install produces the same error message.

How can I resolve this?

---

### Post by Cork87 on 2012-10-17
The package libc6 is to old for libapt-pkg4. Version 2.13-35 is currently installed but 2.15 is needed to complete the task. 

Try apt-get update libc6 to update libc6 or else download the libc6 package and install it manually: [http://packages.ubuntu.com/precise/libc6](http://packages.ubuntu.com/precise/libc6)

---

