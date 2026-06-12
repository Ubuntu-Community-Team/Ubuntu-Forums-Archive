---
title: "Glest error: libvorbis"
date: 2007-12-29
forum: Gaming &amp; Leisure
---

### Post by blithen on 2007-12-29
Well I'm at a lost for this one.
I tried finding a .deb for it, and couldn't.
It's not in the repos.
Here is the error..
```

blithen@blithen-desktop:/usr/bin$ glest
./glest.bin: error while loading shared libraries: libvorbis.so.0: cannot open shared object file: No such file or directory
```

---

### Post by Vixis on 2007-12-29
try this
```
sudo apt-get install libvorbis0a
```

---

### Post by blithen on 2007-12-30
Tired that same error.
I would guess you would make a sym link but I don't know how to do that.

---

### Post by Vixis on 2007-12-30
try this symlink:
```
sudo ln -s libvorbis.so.0.4.0 /usr/lib/libvorbis.so.0
```

---

