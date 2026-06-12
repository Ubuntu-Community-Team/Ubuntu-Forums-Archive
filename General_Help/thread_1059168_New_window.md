---
title: "New window"
date: 2009-02-03
forum: General Help
---

### Post by MRRT on 2009-02-03
Hi. I have just installed intrepid and I'm having a strange behavior. When Compiz-fusion is enable every new window I open appear behind any existing window. It doesn't happen with CF disabled.

Can any one help?

Thanks

---

### Post by gettinoriginal on 2009-02-04
Try this:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
It will reset compiz to all default settings.  :p

---

### Post by MRRT on 2009-02-07
> **gettinoriginal said:**
> Try this:
```
gconftool-2 --recursive-unset -a /apps/compiz
```
It will reset compiz to all default settings.  :p

Thanks it worked just fine. I have to set up my plugins again, but that's no problem.

---

