---
title: "Switch to tty and back"
date: 2004-12-30
forum: Desktop Environments
---

### Post by grj on 2004-12-30
Most of the tools I use are command line tools so I simply run them from a tty. When doing this, I can move from one console to the other by pressing ALT + F1, etc. Sometimes I need to start up X. When in X I can go to a tty console by pressing CTRL + ALT + F1, etc. However, I cannot figure out how to get back to the tty running X after going to a console. I know I can run multiple terminal windows but would rather handle it the way asked.

Thanks,

Gary

---

### Post by Rancoras on 2004-12-30
If you press CTRL+ALT+F1 while in X, to get back to X, you press CTRL+ALT+F7.  X runs on VT7 by default.

---

### Post by grj on 2004-12-31
Thanks, that does it.

grj

---

### Post by subjectdenied on 2004-12-31
you can also use the chvt command (chvt terminal_of_desire)

---

