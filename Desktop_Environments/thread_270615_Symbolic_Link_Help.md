---
title: "Symbolic Link Help"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Brooze on 2006-10-03
$ sudo ldconfig
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

I have never dealt with symbolic links before so I don't even know where to start with fixing this.

---

### Post by mitch.c on 2006-10-03
> **Brooze said:**
> $ sudo ldconfig
ldconfig: /usr/lib32/libXxf86dga.so.1 is not a symbolic link

I have never dealt with symbolic links before so I don't even know where to start with fixing this.
I checked my system (Dapper) and /usr/lib32/libXxf86dga.so.1 is a symlink to /usr/lib/libXxf86dga.so.1.0.0. Why don't check the output of:
```
ls -l /usr/lib32/libXxf86dga.so.1*
```
If they are the same file, perhaps you could mv/rename /usr/lib32/libXxf86dga.so.1, and then:
```
sudo ln -sf /usr/lib/libXxf86dga.so.1.0.0 /usr/lib32/libXxf86dga.so.1
```
Just a thought.

---

