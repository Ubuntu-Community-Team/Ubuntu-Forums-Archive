---
title: "Patching a makefile has errors"
date: 2011-03-07
forum: Desktop Environments
---

### Post by headlice on 2011-03-07
I am patching a makefile for my wireless card on an HP Pavilion dm1z fusion laptop.

Here is the output:

```
$ patch -p0 < rt5390sta-2.4.0.4-config.patch

patching file Makefile
Hunk #1 FAILED at 286.
Hunk #2 FAILED at 333.
2 out of 2 hunks FAILED -- saving rejects to file Makefile.rej
patching file os/linux/config.mk
Hunk #1 FAILED at 108.
1 out of 1 hunk FAILED -- saving rejects to file os/linux/config.mk.rej
```

What are the reasons why it would be failing?

---

