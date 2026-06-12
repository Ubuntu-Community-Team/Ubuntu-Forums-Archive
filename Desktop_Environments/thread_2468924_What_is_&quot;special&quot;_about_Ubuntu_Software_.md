---
title: "What is &quot;special&quot; about Ubuntu Software that causes pixelated fonts?"
date: 2021-11-14
forum: Desktop Environments
---

### Post by starkruzr2 on 2021-11-14
Like so:

[ATTACH=CONFIG]289469[/ATTACH]

Does anyone know what's going on here? 21.10 on a Tiger Lake with the GT2 Xe graphics. Hopefully an easy fix...

---

### Post by ActionParsnip on 2021-11-16
What is the output of:
```

sudo lshw -C display
xrandr
lsb_release -a
uname -a

```
Thanks

---

### Post by tea for one on 2021-11-16
There is a recently created utility, designed to provide the necessary information to allow forum members to offer advice.
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

---

