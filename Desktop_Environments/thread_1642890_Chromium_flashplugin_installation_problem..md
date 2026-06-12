---
title: "Chromium flashplugin installation problem."
date: 2010-12-11
forum: Desktop Environments
---

### Post by piojunbabia on 2010-12-11
I am using wubi to install ubuntu 10.10 inside my xp. it worked fine.. then i installed Chromium. Of course we need to install flash player to view youtube videos. But I could not install the flash plugin.

i get these errors:

```
piojunbabia@ubuntu:~$ sudo apt-get install chromium-browser flashplugin-nonfree
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
piojunbabia@ubuntu:~$ 
piojunbabia@ubuntu:~$ 
```

can anyone help me? thank you...

---

### Post by sikander3786 on 2010-12-11
Please post the output of,

```
sudo dpkg --configure -a
```

---

