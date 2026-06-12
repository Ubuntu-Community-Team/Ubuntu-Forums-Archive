---
title: "Adept confused"
date: 2006-01-14
forum: Desktop Environments
---

### Post by kmacc on 2006-01-14
Hi,

I've recently installed Kubuntu after runing Mandriva for ages and I've been getting all the software I use installed and working. Today I installed VariCAD but because of some dependencies which I had to force it is now listed in Adept as broken.

In reality the program works perfectly. The dependencies where just subtle naming issues with kdelibs and libqt3 which prevented the correct packages being detected on my computer. The deb was supposed to be for Debian 3.1.

I used the --force-depends option of gpkg and this made it work fine. I'm now just annoyed that it shows up as broken. Is there a way to convince the computer that things are not as bad as it seems? Is there a better way to force it?

Cheers,

kmacc

---

### Post by nrwilk on 2006-01-14
I'm not sure, but I think the only way to do this would be to install the generic versions of the dependencies, replacing the kubuntu-specific ones.

I could be wrong, though.

---

