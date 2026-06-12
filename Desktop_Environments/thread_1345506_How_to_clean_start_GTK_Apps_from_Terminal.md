---
title: "How to clean start GTK Apps from Terminal"
date: 2009-12-04
forum: Desktop Environments
---

### Post by jk.cheng on 2009-12-04
assume i want to open a file call sample.txt in home using gedit from terminal. How can i do it clean without leaving any hang-out or log in the terminal?

I have try both command below to send thing to bg, but it still show some output:
1. gedit ~/sample.txt & > /dev/null
2. gedit ~/sample.txt > /dev/null &

Any idea what else can i try?

---

### Post by VCoolio on 2009-12-04
nohup gedit filename > /dev/null 2>&1 &

Nohup means you can close the terminal and have gedit still running.
> /dev/null means stderr messages are redirected to nothing.
2>&1 means stdout messages are redirected to stderr, which was already redirected nothing, so no output anymore.
& means it goes to the background, so you'll just see a pid and then the terminal is available.

---

