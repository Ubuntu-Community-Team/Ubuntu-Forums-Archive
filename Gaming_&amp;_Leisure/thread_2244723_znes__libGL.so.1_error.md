---
title: "znes  libGL.so.1 error"
date: 2014-09-18
forum: Gaming &amp; Leisure
---

### Post by ikki_72 on 2014-09-18
this happened on 14.04 amd64

```
$ zsnes 
zsnes: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

$ sudo apt-get install libgl1-mesa-glx:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:amd64 libgl1-mesa-dri:i386 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-dri is already the newest version.
libgl1-mesa-glx is already the newest version.
libgl1-mesa-dri:i386 is already the newest version.
libgl1-mesa-dri:i386 set to manually installed.
libgl1-mesa-glx:i386 is already the newest version.
libgl1-mesa-glx:i386 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

how to solve this?

---

### Post by ikki_72 on 2014-09-18
these are my libgl

```
$ sudo locate libGL.so.1
/usr/lib/i386-linux-gnu/mesa/libGL.so.1
/usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
/usr/lib/i386-linux-gnu/primus/libGL.so.1
/usr/lib/nvidia-331/libGL.so.1
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
/usr/lib/x86_64-linux-gnu/primus/libGL.so.1
/usr/lib32/nvidia-331/libGL.so.1
```

---

### Post by ikki_72 on 2014-09-22
solved with

```
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/libGL.so.1
```

---

