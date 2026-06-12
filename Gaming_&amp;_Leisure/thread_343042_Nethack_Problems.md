---
title: "Nethack Problems"
date: 2007-01-20
forum: Gaming &amp; Leisure
---

### Post by Pobega on 2007-01-20
I'm having problems with Nethack; I installed it, played it, and closed the terminal right away. Then I tried replaying the game, and I got an error:

> NetHack, Copyright 1985-2003
         By Stichting Mathematisch Centrum and M. Stephenson.
         See license for details.
Waiting for access to /var/games/nethack/perm.  (9 retries left).
Waiting for access to /var/games/nethack/perm.  (8 retries left).
Waiting for access to /var/games/nethack/perm.  (7 retries left).
Waiting for access to /var/games/nethack/perm.  (6 retries left).
Waiting for access to /var/games/nethack/perm.  (5 retries left).
Waiting for access to /var/games/nethack/perm.  (4 retries left).
Waiting for access to /var/games/nethack/perm.  (3 retries left).
Waiting for access to /var/games/nethack/perm.  (2 retries left).
Waiting for access to /var/games/nethack/perm.  (1 retries left).
Waiting for access to /var/games/nethack/perm.  (0 retries left).
I give up.  Sorry.
Perhaps there is an old /var/games/nethack/perm_lock around?

I have no clue what to do, I've done everything I could think of with the perm and perm_lock files but to no avail. Any ideas?

---

### Post by RomeReactor on 2007-01-20
Check in the system monitor if it is still running (System-->Administration-->System Monitor)

---

### Post by Pobega on 2007-01-20
Nope, definitley not running. It isn't in the System Monitor, and "*killall nethack*" killed no processes.

---

### Post by RomeReactor on 2007-01-20
Did you try deleting the lock?

```
sudo rm /var/games/nethack/perm_lock
```

---

### Post by Pobega on 2007-01-20
> **RomeReactor said:**
> Did you try deleting the lock?

```
sudo rm /var/games/nethack/perm_lock
```Actually, that was my problem. Out of all the file manipulations I tried with perm and perm_lock, I'm surprised I didn't try that, thanks a lot!

---

### Post by lokino on 2010-09-14
Thanks, this solved my problem too! =D>

---

