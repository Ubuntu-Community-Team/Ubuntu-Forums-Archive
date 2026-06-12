---
title: "winkey error"
date: 2006-02-11
forum: Desktop Environments
---

### Post by alfonz on 2006-02-11
Hi, hmm I got a small problem

I finaly got fed up with ATi's proprietary drivers and decided to install the fglrx drivers by following [this guide]("http://ubuntuforums.org/showthread.php?t=78466"). It worked like a charm and now I finaly have Accelerated graphics :D.

However, this also killed my winkey. I can no longer map the key with the Super R-L, the only thing that shows when in keyboard shortcuts now its a series of numbers and letters ie 0xe-3.

if I try to change the the winkey behaviour i get this error message.

```
Error activating XKB configuration.
This can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

I have remapped the terminal to another key so its not a serious problem, however if it can be fixed then any help will be apreciated.

Thanks again!

Now i can go play ut :D

---

