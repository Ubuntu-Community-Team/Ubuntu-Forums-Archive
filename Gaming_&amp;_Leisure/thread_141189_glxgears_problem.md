---
title: "glxgears problem"
date: 2006-03-07
forum: Gaming &amp; Leisure
---

### Post by TriggerHappyChewie on 2006-03-07
This is kind of a stupid question, but it bothers me.  I have 3d enabled and all that:

```
patrick@copland:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5642 (8.22.5)

```

Whenever I try to run glxgears, the little gears window comes up and they spin, but no FPS numbers appear in the terminal!  It has never worked in Ubuntu for me, only Fedora.

I don't know what is wrong...

---

### Post by Sutekh on 2006-03-07
Try ```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

---

### Post by TriggerHappyChewie on 2006-03-07
I didn't think you were serious...

But it worked....

Thanks!

---

### Post by Sutekh on 2006-03-07
I think too many people actually thought it was a reasonable/repeatable benchmarking test, so the devs made that obscure flag.

---

