---
title: "[SOLVED] Problems with libopenal in Warsow"
date: 2009-02-11
forum: Gaming &amp; Leisure
---

### Post by Melcar on 2009-02-11
Intrepid 64bit.  Warsow can't load libopenal.so.0.  I do have the symbolic link from libopenal.so.1 to libopenal.so.0, and even made libopenal.so just in case.  The game used to work just fine on my previous Intrepid install.

---

### Post by Perfect Storm on 2009-02-11
Is the warsow you have compiled/build for 32-bit or 64-bit?

Try **ldd** the binary file.

---

### Post by Melcar on 2009-02-11
I'm using their 64bit binary.  This problem never happened before on any of my previous Ubuntu installs (the game would "just work").

---

### Post by Perfect Storm on 2009-02-11
Are you sure you have made the symblink correct? Sound like you messed up the symblink up.


edit:
Delete the previous symblink and make a new;
```
cd /usr/lib
sudo rm -rf libopenal.so.0
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
```

---

### Post by Melcar on 2009-02-11
Yeah, that worked.  Thanks.

---

