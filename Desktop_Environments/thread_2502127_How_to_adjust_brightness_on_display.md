---
title: "How to adjust brightness on display"
date: 2024-11-02
forum: Desktop Environments
---

### Post by satimis on 2024-11-02
Hi all,

Ubuntu 22.04
Display - Dell 4K 32" display

How to adjust the brightness of the disaplay ?

1) The control on the display seems not working
2) I have "brightness-controller" installed.  Also I can't make it to work.

Please help.  Thanks in advance.

Regards

---

### Post by Autodave on 2024-11-02
Have you tried resetting the monitor to factory specs and then try adjusting the brightness?  What model is the display?

---

### Post by iamjiwjr on 2024-11-02
There's a Gnome Extension called soft brightness plus. I've never used it, but it might help.

---

### Post by him610 on 2024-11-02
There a couple of ways from a terminal that work for me...
```

xgamma -gamma 0.8

```
or
```

xrandr --output (screen*) --brightness 0.8

```

*Run xrandr by itself to determine which screen to use

---

