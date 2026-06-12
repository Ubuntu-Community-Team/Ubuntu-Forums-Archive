---
title: "glx gears doesn't return reading"
date: 2006-03-25
forum: Desktop Environments
---

### Post by red devil on 2006-03-25
Hi,
I'm running Ubuntu 5.10 with the official Nvidia graphics driver for my 5200 FX card, downloaded and installed through Automatix.
However, I can't get a reading when I run glxgears, either as user or sudo - the gears turn but there's no framerate registered in my terminal window like I normally get.
Anyone any ideas - it's not a crucial thing, I'd just like to know how my setup is performing.
Thanks
;)

---

### Post by krusbjorn on 2006-03-25
Try "glxgears -printfps" or "glxgears -iacknowledgethatthistoolisnotabenchmark" if you find that easier to write.

---

### Post by red devil on 2006-03-25
Yep... that did the trick! I'm getting 2700fps, which sounds about right. Many thanks for the tip krusbjorn.

---

