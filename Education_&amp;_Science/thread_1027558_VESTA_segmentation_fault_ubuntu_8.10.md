---
title: "VESTA segmentation fault ubuntu 8.10"
date: 2009-01-01
forum: Education &amp; Science
---

### Post by riglesias on 2009-01-01
Hello!
I've recently installed VESTA-i686, a 3D visualization program for structural models and 3D grid data, [http://www.geocities.jp/kmo_mma/crystal/en/vesta.htm](http://www.geocities.jp/kmo_mma/crystal/en/vesta.htm)
After apparently successful installation, I try to run the program and get
Segmentation fault

I've seen this kind of error previously posted in the x86 64-bit users forum. The solution was to update the graphics card driver (restricted NVIDIA driver). However, in my laptop the graphics card is an intel GMA 950 Gfx which seems to be updated:
$lspci
.............
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
.............

Any ideas on what should I do?

Thanks in advance

Roberto

---

### Post by NetFreeDiver on 2009-01-12
Hi Roberto,

I had the same problem. After installing new drivers for my Graphics Controller (ATI) it was fixed. But, I believe if you disable your CompizConfig ("Compiz Fusion Icon" does it easily) it may work. After reading many documentations and forums, it seems that compizconfig interferes with graphics settings.

Cheers,

Riza

---

### Post by riglesias on 2009-01-14
Dear Riza
Thank you for your answer. I tried to install the Compiz Fusion Icon as you suggested. I guess disabling means using Metacity instead of Compiz as the window manager. I did not get any improvement and the error message is still "segmentation fault".
Any other ideas?
Roberto

---

