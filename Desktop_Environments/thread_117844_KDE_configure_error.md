---
title: "KDE configure error"
date: 2006-01-15
forum: Desktop Environments
---

### Post by Simpele on 2006-01-15
Hi

I'm looking to compile kavi2svcd, but I get the following error while running ./configure:

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

I was thinking that installing the package 'kde-develp' might help, but when I tried it in Adept, it said the package is broken. I believe this has something to do with the repositories, but I don't know which to add.

I'm using 64-bit Kubuntu 5.10 with KDE 3.5. Any help is greatly appreciated.

---

### Post by jbus on 2006-01-18
Try installing kdelibs4-dev first

Then install kdebase-dev

Hope it works for you, it worked for me.

---

