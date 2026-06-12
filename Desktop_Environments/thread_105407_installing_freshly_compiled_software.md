---
title: "installing freshly compiled software"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Niall Flinn on 2005-12-18
Hi folks,

I've just compiled a copy of Cinepaint 0.20-1 (a version of Gimp optimized for high bit-depth image editing) from the platform independant source archive. Everything seems to have gone OK, and I can run Cinepaint. The problem I have is that the executable and all the plugins etc are still in the directory I decompressed the source code to. How do I make sure all this stuff gets put in the correct places in my system? Do I need to create a .deb package and install that? If so, is there a tutorial on how to do this somewhere? 

Thanks,

Niall

---

### Post by N6546R on 2005-12-18
I use checkinstall to create and install a .deb for from-source programs:

checkinstall -D make install

Perry

---

### Post by Niall Flinn on 2005-12-18
Thanks Perry, that sounds like exactly what I was looking for - I'll give it a go!

Niall

---

