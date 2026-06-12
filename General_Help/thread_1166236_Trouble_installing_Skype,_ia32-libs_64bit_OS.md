---
title: "Trouble installing Skype, ia32-libs 64bit OS"
date: 2009-05-21
forum: General Help
---

### Post by J0henz on 2009-05-21
In my effort of trying to install Skype with the official amd64-package (yes, it works. i've tried it before) I can't satisfy all dependencies. The package **ia32-libs** will not install. When i run **sudo apt-get install ia32-libs** or **sudo apt-get -f install ia32-libs** I get the errormessage:
```
dpkg: error while handling /var/cache/apt/archives/ia32-libs_2.2ubuntu18_amd64.deb (--unpack):
 could not create "./usr/lib32/libGL.so.1.2": File or directory doesn't exist
dpkg-deb: sub-process killed by signal (Broken pipe)
Error while handling:
 /var/cache/apt/archives/ia32-libs_2.2ubuntu18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```(if the message is not entirely correct, that is because i'm translating from swedish)

What should I do to install the package, I have tried running **apt-get install -f** and **apt-get update**, but no succes.

---

### Post by J0henz on 2009-05-21
*bump*

---

### Post by J0henz on 2009-05-21
It all resolved itself when I removed the nvidia-177-driver.

---

