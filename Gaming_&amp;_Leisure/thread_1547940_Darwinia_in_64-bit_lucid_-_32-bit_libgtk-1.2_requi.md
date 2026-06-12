---
title: "Darwinia in 64-bit lucid - 32-bit libgtk-1.2 required"
date: 2010-08-07
forum: Gaming &amp; Leisure
---

### Post by Zorgoth on 2010-08-07
I cannot find a way to install the game "Darwinia" in 64-bit lucid...

It requires a libgtk-1.2.so.0 in lib32, and I can't find a package for installing 32-bit libgtk-1.2 in 64-bit lucid.  Ubuntu has dropped official support for libgtk-1.2, so I don't know what to do.

---

### Post by Perfect Storm on 2010-08-07
If you checked the sticky that says 64-bit gaming guides you'll found this: [http://gwos.org/doku.php/guides:64bit:darwinia](http://gwos.org/doku.php/guides:64bit:darwinia)

---

### Post by Zorgoth on 2010-08-07
I got it to install (thanks) but now when I try to run it it complains that 
```

/usr/local/games/darwinia/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)

```
- any suggestions on where I could find that?  Couldn't see it in the repostiories.

---

### Post by Perfect Storm on 2010-08-07
Did you:

sudo cp -r /usr/lib32/libgcc_s.so.1 /usr/local/games/darwinia/lib

---

### Post by Zorgoth on 2010-08-07
OK I've got it working now - missed part of the guide - indeed, that is exactly what i did not do

---

