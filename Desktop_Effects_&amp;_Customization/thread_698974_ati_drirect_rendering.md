---
title: "ati drirect rendering"
date: 2008-02-16
forum: Desktop Effects &amp; Customization
---

### Post by supersonicdarky on 2008-02-16
I apparently do not have direct rendering enabled (for 3d games, open arena for example). Whenever I try to run something that requires it, X just crashes. Graphics is my weakest part in linux so I have no idea where to start. According to warsow; **Your OpenGL installation doesn't support direct rendering. If you have and NVIDIA or an ATI card you'll probably need to install the proprietary driver.**

I read somewhere that you have to choose between desktop effects or direct rendering. Is this true?

**ATI x1250 (onboard)**

```
kernel@fission:~$ glxinfo|grep direct
Xlib: extension "XFree86-DRI" missing on display ":2:0"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

---

