---
title: "bash history owned by root after sudo"
date: 2008-03-27
forum: Desktop Environments
---

### Post by Jonie on 2008-03-27
In hardy beta I noticed that bash could no longer remember commands history. It seems that after sudo the ,bash_history file was chowned by root. I can't recreate this error now, but it happened. The permissions were 660 as usual, but owner was root root.

---

### Post by Oldsoldier2003 on 2008-03-28
> **Jonie said:**
> In hardy beta I noticed that bash could no longer remember commands history. It seems that after sudo the ,bash_history file was chowned by root. I can't recreate this error now, but it happened. The permissions were 660 as usual, but owner was root root.

what can I say other than BETA!  :) The patches fly fast and furious I'm getting probably 40-50 patches a day so a problem can appear and disappear quite quickly.

---

### Post by edouardp on 2008-07-13
Just got this bug with a fresh install of ubuntu 8.04.1 so it's definitely in here, somewhere :p

---

