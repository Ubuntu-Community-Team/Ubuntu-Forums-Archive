---
title: "Enable Direct Rendering"
date: 2008-09-14
forum: Desktop Environments
---

### Post by glitch17 on 2008-09-14
Hi i have a project for school and I need direct rendering enabled but when compiz is enabled it gets disabled and doesn't come back on unless i disable compiz and restart. I have not configured my xorg.conf because I have no idea how (I was looking nothing I found worked, I couldn't enable compiz afterwards). I have an eee pc 1000H so I'm pretty sure the video card is an Intel 915 and I know I have the drivers installed because I looked and I'm using the eeepc kernel where ever it is (can't remember)
so could someone please help me enable direct rendering when compiz is enabled. Thanks in advance.

---

### Post by lswb on 2008-09-14
How are you determining of DRI is enabled? I remember there are some issues with intel graphics (that honestly I really don't understand) that cause misleading reporting of DRI from the glxinfo command. My laptop has intel 855 graphics, a little older version of your. I played around with this some time ago. I know that if you open a terminal and run:
```
glxinfo|grep rendering
```
it returns:
```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

If you then
```
unset LIBGL_ALWAYS_INDIRECT
```
and check glxinfo again it will report
```
direct rendering: Yes
```


Is there a particular program that needs DRI enabled and have you tried to run it yet? Hopefully someone knowledgeable on this subject will add to this thread as I'm curious about it also.

---

