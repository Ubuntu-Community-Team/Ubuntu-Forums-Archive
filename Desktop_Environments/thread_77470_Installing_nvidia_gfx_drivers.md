---
title: "Installing nvidia gfx drivers"
date: 2005-10-16
forum: Desktop Environments
---

### Post by a12ctic on 2005-10-16
ok, ive almsot got it figured out, the only thing i need is the kernel sources, can someone tell me the apt-get command to grab them?

I already have the gcc and make

---

### Post by rumli on 2005-10-16
If you simply want to install the nvidia glx drivers, check out [http://ubuntuguide.org/#installnvidiadriver]("http://ubuntuguide.org/#installnvidiadriver").

---

### Post by linuxlover on 2005-10-16
It apt-cache search kernel-source to see if it has the proper source files listed
Then apt-get install kernel-source.
or

apt-get install kernel-headers does the same thing

---

