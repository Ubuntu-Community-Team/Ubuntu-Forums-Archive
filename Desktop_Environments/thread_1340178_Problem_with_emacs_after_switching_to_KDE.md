---
title: "Problem with emacs after switching to KDE"
date: 2009-11-28
forum: Desktop Environments
---

### Post by k3nz13 on 2009-11-28
Hey guys,

I just switched over to KDE from Gnome in 9.10, and I get the following error now when I try to start emacs:

```
Font `-bitstream-bitstream vera sans mono-medium-r-*--*-100-*--*--*- Xcursor.theme: DMZ-Black' is not defined

```

From my observation, it seems that the default font and the cursor theme are being concatenated, but I have no idea how to fix this. Any suggestions?

---

### Post by jpkotta on 2009-11-28
How are you trying to start it?  Does this happen when you start it from the terminal?

---

### Post by k3nz13 on 2009-11-29
Yes. I have managed to alleviate the problem by writing an alias:
```

alias emacs='emacs23 --font monospace-10'
```

I can't seem to understand why I can't start it with the default command though. I have also checked in gnome if I can still use emacs (on the same machine, same install), and sure enough, it works.

---

