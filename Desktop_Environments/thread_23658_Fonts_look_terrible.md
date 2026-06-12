---
title: "Fonts look terrible"
date: 2005-04-03
forum: Desktop Environments
---

### Post by rigga on 2005-04-03
Hi,

I have just installed kubuntu and done all the updates as at today however my fonts look awfull, even though I have chose antialias they still look bad in most of my applications almost like kde was compiled without truetype support.  i have installed the Microsoft fonts but it has made no difference, can anyone suggest how to resolve this?

Cheers

---

### Post by J. S. Jackson on 2005-04-04
I strongly suggest you think about enabling the autohinter.  Try several different settings.  Results vary depending on taste, and whether or not you're using a CRT or LCD.

```
sudo dpkg-reconfigure fontconfig
```

---

### Post by rigga on 2005-04-04
That fixed it !!!! thanks very much your help is appreciated.

---

### Post by J. S. Jackson on 2005-05-02
[QUOTE=rigga]That fixed it !!!! thanks very much your help is appreciated.[/QUOTE]
You're welcome.   :)

---

