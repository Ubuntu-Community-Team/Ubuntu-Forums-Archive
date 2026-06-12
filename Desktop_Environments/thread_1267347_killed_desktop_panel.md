---
title: "killed desktop panel"
date: 2009-09-15
forum: Desktop Environments
---

### Post by jomex on 2009-09-15
an application hung up so i killed it with xkill, but i accidentally hit the panel (LXDE). now it's quite funny because i got the opposite problem :) i can't [Alt]+[F2] to get it back. is there a way to spawn a process from a different console? like:
[Ctrl]+[Alt]+[F1]
lxpanel -> TTY7
[Ctrl]+[Alt]+[F7]
?

---

### Post by jomex on 2009-09-15
solved it:

[ctrl]+[alt]+[F1]
export DISPLAY=:0
xterm
[ctrl]+[alt]+[F7]
lxpanel &

btw: is there a way to mark threads as [SOLVED]?

---

### Post by jerrrys on 2009-09-15
its in the thread tools at the top of your thread

---

### Post by jomex on 2009-09-15
thx

---

