---
title: "UT2004 AMD x86-64; Nexuiz v1.5 x86-64; same problem?"
date: 2006-06-15
forum: Gaming &amp; Leisure
---

### Post by Oblong_Cheese on 2006-06-15
Hi all, when trying to run the UT2004 demo I receive the following error:

> 
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


I can verify that this file does exist at */usr/lib32/libstdc++.so.5*, so why are these games not working?

> 
owen@oblong:~$ ls -lh /usr/lib32/ | grep 'libstdc*5*'
lrwxrwxrwx 1 root root   18 2006-06-15 10:26 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root 721K 2005-10-26 22:25 libstdc++.so.5.0.7


:confused:

I have tried copying that file to the ut2004demo/System folder, and the ut2004demo folder... to no avail.

***Update!***

I fixed it simply by using Synaptic to install libstdc++5 -- for some reason it wasn't already installed, even though the file existed on my system? Oh well, UT2004 is working now, though without sound.

Both UT2004 and Wolf:ET complain about being unable to open the device /dev/dsp -- I'm running ubuntu-amd-k8 kernel.

Any ideas?

---

### Post by Oblong_Cheese on 2006-06-15
Bump.

:(

---

### Post by Oblong_Cheese on 2006-06-20
Bumpity bump.

---

