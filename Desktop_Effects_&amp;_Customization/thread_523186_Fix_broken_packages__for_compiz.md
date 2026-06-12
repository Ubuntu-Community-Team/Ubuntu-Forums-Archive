---
title: "Fix broken packages??  for compiz"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by HanArar on 2007-08-11
Hi tried Installing Compiz fusion, but when updating I got 2 broken packages, and it tells me to fix them, but really don't know how.

Anyone can help me fix those broken packages ??

Thanks

---

### Post by EXCiD3 on 2007-08-11
Open synaptic, click  edit, click Fix broken packages, click reload, click mark all upgrades

Or you can do this from terminal:```
sudo dpkg --configure -a
```

You may try removing the faulty package and then reinstalling it also.

---

