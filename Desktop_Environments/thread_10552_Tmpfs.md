---
title: "Tmpfs"
date: 2005-01-09
forum: Desktop Environments
---

### Post by rider343 on 2005-01-09
What is tmpfs located at /dev/shm?
what is his function?

Sorry for my trouble english  :neutral:

---

### Post by jdong on 2005-01-09
tmpfs was originally called 'shm fs', that's the shm reference.


It's like a "RamDisk" on steroids. It not only uses RAM, it's capable of using swap, too!

Therefore, it makes a great place to put temporary files during boot, or commonly used files, like the /etc folder, into tmpfs.

---

