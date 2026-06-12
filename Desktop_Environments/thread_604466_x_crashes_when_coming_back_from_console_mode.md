---
title: "x crashes when coming back from console mode"
date: 2007-11-06
forum: Desktop Environments
---

### Post by saugv on 2007-11-06
Hi,
I like to use the console mode using ctrl-alt-f1-f6. But here's the prob I am facing. While coming back to x mode using ctrl-alt-f7 it only shows a white screen. Any solutions?
Thanks,
saugv

---

### Post by bingoUV on 2007-11-06
> **saugv said:**
> Hi,
I like to use the console mode using ctrl-alt-f1-f6. But here's the prob I am facing. While coming back to x mode using ctrl-alt-f7 it only shows a white screen. Any solutions?
Thanks,
saugv

I had this problem and found a kind of solution to it. It was on intel GMA X3000 graphics. Which video card do you use? Post your /etc/X11/xorg.conf here.

---

### Post by saugv on 2007-11-07
> **bingoUV said:**
> I had this problem and found a kind of solution to it. It was on intel GMA X3000 graphics. Which video card do you use? Post your /etc/X11/xorg.conf here.

Attaching my xorg.conf.

---

### Post by bingoUV on 2007-11-07
You have not told me which graphics card you have, but try replacing i810 by intel in xorg.conf's device section.
```

    Driver      "intel"

```

---

