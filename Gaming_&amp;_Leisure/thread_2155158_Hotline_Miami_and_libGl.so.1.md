---
title: "Hotline Miami and libGl.so.1"
date: 2013-06-17
forum: Gaming &amp; Leisure
---

### Post by OmgItsPixelated on 2013-06-17
I bought the humble bundle 8 last week (or the week before I forgot) and only just got around to actually downloading the games. So after downloading and installing the .deb file for Hotline Miami I tried to run the game from the launcher but didn't get anything pop up so I ran it from the terminal and got this error

```
/opt/hotline-miami/hotline_launcher: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

But upon using locate in the terminal shows that I do have the above file

```
/usr/lib/i386-linux-gnu/mesa/libGL.so.1
/usr/lib/i386-linux-gnu/mesa/libGL.so.1.2.0
/usr/lib/i386-linux-gnu/primus/libGL.so.1
/usr/lib/nvidia-current-updates/libGL.so.1
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
/usr/lib/x86_64-linux-gnu/primus/libGL.so.1
/usr/lib32/nvidia-current-updates/libGL.so.1



```

So any ideas on how to fix this problem? I tried searching for answers but didn't find any.
Thanks in advance.

Computer is running Ubuntu 12.04

---

### Post by OmgItsPixelated on 2013-06-28
bump.

---

### Post by OmgItsPixelated on 2013-07-01
Bimp.

---

### Post by OmgItsPixelated on 2013-07-04
bamp.

---

