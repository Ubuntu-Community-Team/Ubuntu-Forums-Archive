---
title: "Virtual terminal problem"
date: 2010-08-25
forum: Desktop Environments
---

### Post by donkeyotay on 2010-08-25
Hello Everybody,
I have a problem with my virtual terminals (Ctrl+Alt+F1 - F6) whereby I cannot see the bottom of the screen. How do I configure this so the the bottom of the virtual screen is the bottom of the laptop screen?
Running 10.04.1 on Celeron M 1.5 w/1 GB RAM.
Many thanks
Simon

---

### Post by donkeyotay on 2010-08-25
Adding
```
stty rows 25
```to .zshrc fixed it.

---

