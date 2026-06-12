---
title: "Lock package question"
date: 2005-10-25
forum: Desktop Environments
---

### Post by tagbre on 2005-10-25
Since the Ubuntu package of 'giftui' segfaults, I downloaded the package from a debian mirror and installed it. It works perfect, except that now I have the annoying "There is one update available" icon permanently on the tray (it wants to "update" to the original version.) I locked the package with synaptic but it didn't help. Version number isn't even older, I guess it's just the date which is newer. Any ideas?

---

### Post by mlomker on 2005-10-25
If you compile it from source and use Checkinstall to create the .deb package then you can give it whatever version number you want.  Or you could skip creating the .deb and just install it without creating a .deb and then Synaptic won't know about it.

---

### Post by tagbre on 2005-10-25
Thnx for the answer.
I wanted to avoid installing from source, that's why i looked for a debian package. I guess I'll have to do it anyway.

---

