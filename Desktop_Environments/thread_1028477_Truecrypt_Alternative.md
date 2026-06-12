---
title: "Truecrypt Alternative?"
date: 2009-01-02
forum: Desktop Environments
---

### Post by num on 2009-01-02
Is there an alternative to Truecrypt ([http://www.truecrypt.org/)?](http://www.truecrypt.org/)?) A program that can entire an entire hard drive?

---

### Post by num on 2009-01-02
anyone? :(

---

### Post by fargle on 2009-01-03
Yes, you can use the alternate install ISO to use the built-in dm_crypt to encrypt the whole drive in a LVM host and require a password on bootup to unlock it.

The nice thing about Truecrypt is that it's cross-platform so you can, for example, encrypt external drives with Truecrypt and FAT32 and read them on both Windows and Linux.  But it's not for system drives.

---

